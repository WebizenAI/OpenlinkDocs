# Adding VAL Support to a VSP-based Application

VAL provides the means to easily add authentication and ACL support to existing or new vsp-based applications. This tutorial shows the three main steps to add authentication and ACL protection to an application. We are using `curi` - the Compressed URI Service as an example.

For `curi` we want to add login information, a means for the user to logout, and ACLs to protect the service.

## Check for existing authentication information

The first and simplest step is to check if the user already provided authentication information as supported by VAL. This can simply be achieved by calling [VAL.DBA.get_authentication_details_for_connection()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga745878ab820820c45f26d15217824cfa "Checks for existing authentication information in the current connection.") at the top of the `vsp` page:

declare val_serviceId, val_sid, val_realm, val_uname varchar;

declare val_isRealUser integer;

declare val_cert any;

-- Important since "realm" is an "inout" parameter!

val_realm := null;

[VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html).[DBA](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html).get_authentication_details_for_connection (

sid=>val_sid,

serviceId=>val_serviceId,

uname=>val_uname,

isRealUser=>val_isRealUser,

realm=>val_realm,

cert=>val_cert);

Note

[VAL.DBA.get_authentication_details_for_connection()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga745878ab820820c45f26d15217824cfa "Checks for existing authentication information in the current connection.") will honor a non-null `realm` parameter and only return authentication data for the given realm. Additionally it will honor the `app_realm` setting in the virtual dir serving the page in question. Thus, there are basically two ways to define the realm for an application: 1. Set it in the virtual dir, and 2. Force it manually via the `realm` parameter.

After the call to [VAL.DBA.get_authentication_details_for_connection()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga745878ab820820c45f26d15217824cfa "Checks for existing authentication information in the current connection.") the application can use the information. The most important one is the value of `val_serviceId` which defines who is authenticated. If it is `null` then the user has not authenticated yet.

## Adding Login and Logout Links

VAL provides an authentication and a logout page to support the most simple login and logout links possible. Given that the application page is stored in `pageUrl` the following links can be used:

<a href="/val/authenticate.vsp?returnto=<?/pageUrl?>">Login</a>

<a href="/val/logout.vsp?returnto=<?/pageUrl?>">Logout</a>

However, in our case a dedicated login page is more desirable since it allows to configure certain aspects of `authenticate.vsp`. Thus, we create a new page `login.vsp` with the following content (or at least parts of it):

<?vsp

connection_set ('__val_auth_page__', '/c/login.vsp');

connection_set ('__val_req_res_label__', 'Compressed URI Service');

connection_set ('__val_oauth_scope__', 'profile');

?>

<?include /DAV/VAD/val/authenticate.vsp ?>

The settings should be obvious:

- `__val_auth_page__` We tell `authenticate.vsp` to use `login.vsp` instead of its own URL for all login links.
- `__val_req_res_label__` A custom label for the login dialog to tell the user which service they log into.
- `__val_oauth_scope__` The optional OAuth scope to use (`basic`, `profile`, or `dav`). This is only of interest for applications that reuse the created OAuth sessions for additional API calls to the 3rd-party service.

So we end up with code for creating a login/logout box like the following:

if (val_serviceId is not null) {

http (sprintf ('Logged in as %s', val_serviceId));

http (sprintf ('<a href="/val/logout.vsp?returnto=%U">Logout</a>', pageUrl));

}

else {

http (sprintf ('<a href="login.vsp?returnto=%U">Login</a>', pageUrl));

}

Once the user authenticates, they will be redirected to the `pageUrl` with a newly created `sid` cookie. the logout page will remove that cookie.

**Tip:** A slightly nicer logged in message with link can be created with code like the following which makes use of the two utility procedures [VAL.DBA.get_profile_url()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga43385dfc887ccad03701cfc9f4a143c0 "Get a profile URL for a given service ID.") and [VAL.DBA.get_profile_name()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gaca32625bec8fc5666c905918997e3c96 "Get the full name for the given profile URI."):

declare x, n varchar;

x := [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html).[DBA](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html).get_profile_url (val_serviceId);

n := coalesce ([VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html).[DBA](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html).get_profile_name (val_serviceId), val_serviceId);

if (not x is null)

http (sprintf ('<a href="%s">%V</a>', x, n));

else

http (n);

Warning

Be aware that WebID logout is not always possible as it requires a redirect to the non-ssl protected application page.

## 40x Pages

A typical situation for authentication-enabled applications is forcing the user to authenticate. Ideally this is done via `40x` page options in the virtual directory in combination with VAL's `authenticate.vsp` page (which is also used for login links). One simply creates a new file `40x.vsp` which has the following content:

<?vsp

connection_set ('__val_req_res__', 'urn:virtuoso:access:curi');

connection_set ('__val_req_acl_scope__', 'urn:virtuoso:val:scopes:curi');

connection_set ('__val_req_res_label__', 'Compressed URI Service');

connection_set ('__val_auth_page__', '/c/login.vsp');

if (isstring (http_param ('error.msg')))

connection_set ('__val_err_msg__', http_param ('error.msg'));

?>

<?include /DAV/VAD/val/authenticate.vsp ?>

`authenticate.vsp` can be configured via a set of connection settings:

- `__val_req_res__` The resource which is protected, ie which requires the login. This is only used to retrieve ownership information for the "request access" dialog that `authenticate.vsp` will show if access was denied. This will default to the `returnto` URL if not provided, and should that also be `null` (as is the case if `authenticate.vsp` is used as `40x_page`) then the requested URL will be used.
- `__val_req_acl_scope__` The ACL scope in which the above resource is protected. This is only used to retrieve ownership information for the "request access" dialog that `authenticate.vsp` will show if access was denied. If not given, then no "request access" dialog is shown.
- `__val_req_res_label__` An optional label for the login dialog showing the user for which service they are authenticating.
- `__val_auth_page__` We tell `authenticate.vsp` to use our custom page `login.vsp` instead of its own URL for all login links.
- `**val_err_msg**` An error message indicating any kind of error. This should be set to `http_param ('error.msg')` for the simple reason that Virtuoso does clear the http params before processing the 40x page.

This page will be used as `40x` page in the virtual directory configuration:

[DB](https://docs.openlinksw.com/valdocs/namespaceDB.html).[DBA](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html).VHOST_DEFINE (

lpath=>'/c',

ppath=>'/DAV/VAD/c_uri/',

is_dav=>1,

vsp_user=>'CURI',

ses_vars=>0,

opts=>vector (

'url_rewrite', 'c_uri_lst',

'401_page', '40x.vsp',

'403_page', '40x.vsp'),

is_default_host=>0

);

Then the application can raise a permission denied error as shown in the following example:

if (val_serviceId is null) {

http_status_set(401);

}

else {

connection_set ('__val_denied_service_id__', val_serviceId);

http_status_set(403);

}

return '';

If `val_serviceId` is `null` then the user has not logged in and the application simply requests that they do. Otherwise `403` indicates that permission was denied to the authenticate user. The authenticated has to be communicated to `authenticate.vsp` via the `__val_denied_service_id__` connection setting.

## Using ACL Rules to Protect A Web Service

In [40x Pages](https://docs.openlinksw.com/valdocs/val_tutorials.html#val_tutorials_authenticate_vsp_3) we saw how to use `authenticate.vsp` as a `40x_page`. Now we will add ACL protection to the `curi` service and put the new 40x_page to use.

We want to be able to grant people the right to create new compressed URIs and others the right to read these. To that end we define a new scope `urn:virtuoso:val:scopes:curi` which is only used for `curi` and a virtual resource URI which is used to grant permissions: `urn:virtuoso:access:curi` These URIs are arbitrary, they simply follow a random scheme to be easily recognizable. In theory they could be any URI one wanted to use.

VAL makes use of scope definitions to get default access modes for disabled scopes (the default). Thus we start by defining our new scope in the corresponding VAL acl schema graph (Hint: standard scopes for DAV, etc. are defined in the OpenLink ACL ontology, example: oplacl:Dav):

sparql

prefix acl: <http://www.w3.org/ns/auth/acl#>

prefix oplacl: <http://www.openlinksw.com/ontology/acl#>

insert into <urn:virtuoso:val:acl:schema> {

<urn:virtuoso:val:scopes:curi> a oplacl:Scope ;

rdfs:label "Compressed URIs" ;

rdfs:comment """SQL ACL scope which contains all ACL rules granting permission to create and read compressed URIs. By default anyone can fully use the service.""" ;

oplacl:hasApplicableAccess oplacl:Read, oplacl:Write ;

oplacl:hasDefaultAccess oplacl:Read, oplacl:Write .

};

The most important part is `oplacl:hasDefaultAccess` which defines the access modes used in case ACL evaluation has not been enabled for the `curi` scope. In this case everyone is allowed to create and read compressed URIs.

Now at the top of the `create.vsp` page which allows to create new compressed URIs we add the following ACL check (after the code from [40x Pages](https://docs.openlinksw.com/valdocs/val_tutorials.html#val_tutorials_authenticate_vsp_3)):

if (not val_isRealUser or not [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html).[DBA](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html).is_admin_user (val_uname)) {

if (not [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html).[DBA](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html).check_access_mode_for_resource (

serviceId=>val_serviceId,

resource=>'urn:virtuoso:access:curi',

realm=>val_realm,

scope=>'urn:virtuoso:val:scopes:curi',

mode=>[VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html).[DBA](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html).oplacl_iri ('Write'),

webidGraph=>val_webidGraph,

certificate=>val_cert,

honorScopeState=>1)

) {

connection_set ('__val_denied_service_id__', val_serviceId);

connection_set ('__val_req_acl_mode__', [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html).[DBA](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html).oplacl_iri ('Write'));

if (val_serviceId is null)

http_status_set(401);

else

http_status_set(403);

return '';

}

}

Some of this code we already know from before. But the big first part is new. First we check if we are logged in as an admin user. VAL provides us with the convinience procedure [VAL.DBA.is_admin_user()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga6d55cc950a8e04c8e1372dad15521922 "Check if a given SQL user is dba or in the admin group (role)") for that. Of course only "real" users, ie. SQL users, can be administrators of the V instance. In case no admin credentials were provided we continue with the ACL check using [VAL.DBA.check_access_mode_for_resource()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga02d2eab7b4a0c696c72ec6c064ebe982 "Convinience procedure to check for a specific mode on one resource.") which allows to check for exactly one mode on one resource for one service id. Here we use all the details that were provided by [VAL.DBA.get_authentication_details_for_connection()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga745878ab820820c45f26d15217824cfa "Checks for existing authentication information in the current connection.") and combine them with the resource and scope URIs we defined above.

Since we want to create a compressed URI we use the `oplacl:Write` access mode. Should no ACL exist which grants access we continue to raise a `40x` error. But before we do that we set two more variables:

- `__val_denied_service_id__` This is important as it allows `authenticate.vsp` to know that access has been denied to a certain person and the user should be asked to login again. Without this setting, `authenticate.vsp` would simply return to the `returnto` URL if authentication information could be found. This would result in an endless loop. Should no authentication information exist yet then `authenticate.vsp` will simply ask for it.
- `__val_req_acl_mode__` Like the resource and the scope settings above the mode is only used for the "request access" dialog. It allows `authenticate.vsp` to create a more detailed access request message to the resource owner.

Finally we add the same code to the `get.vsp` page which handles the conversion of comressed to uncompressed URIs. The only difference is the access mode:

if (not val_isRealUser or not [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html).[DBA](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html).is_admin_user (val_uname)) {

if (not [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html).[DBA](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html).check_access_mode_for_resource (

serviceId=>val_serviceId,

resource=>'urn:virtuoso:access:curi',

realm=>val_realm,

scope=>'urn:virtuoso:val:scopes:curi',

mode=>[VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html).[DBA](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html).oplacl_iri ('Read'),

webidGraph=>val_webidGraph,

certificate=>val_cert,

honorScopeState=>1)

) {

connection_set ('__val_denied_service_id__', val_serviceId);

connection_set ('__val_req_acl_mode__', [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html).[DBA](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html).oplacl_iri ('Read'));

if (val_serviceId is null)

http_status_set(401);

else

http_status_set(403);

return '';

}

}

## The Request Access Dialog

`authenticate.vsp` provides a simple dialog through which users can request access to a certain resource, should it have been denied. This dialog is shown by `authenticate.vsp` if the following conditions hold true:

- The user has been denied access, i.e. `__val_denied_service_id__` is `non-null` (See [40x Pages](https://docs.openlinksw.com/valdocs/val_tutorials.html#val_tutorials_authenticate_vsp_3) for details).
- The owner of the resource access has been denied to can be determined. This means `__val_req_res__` has to be `non-null` and an owner has to be set (DAV resources are handled as special cases, for every other resource see [VAL.DBA.set_resource_ownership()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga39324e0e0cf5fcaf259dac362357b92c "Set the owner of a resource in a given scope."), [VAL.DBA.add_ownership_graph()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga3eb4fcc5cff60079013beebdf58c9ae3 "Add a resource ownership graph.") and friends.)
- VAL has a means to contact the owner. That means an email address has to be known (see also [VAL.DBA.email_address_for_service_id()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga0e3510e9b6a77b33558bd6d78814afc3 "Find an email address for the given service id.")) and the instance's sendmail configuration has to be valid (see also [VAL.DBA.smtp_server_available()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga882a0ac491ca06f6514220b72f608bd2 "Check if a valid SMTP server has been configured.")).

Once these conditions are fulfilled then the user has the option to write a message to the owner of the resource, requesting to grant them access.

## Running an Application Under a Specific SQL User Account

In the case of `curi` the vsp pages are not executed as `dba` but using the dedicated account `CURI` which improves security and is generally recommended. However, since most of the internal VAL API procedures require special permissions this user needs to be granted the `VAL_AUTH` and `VAL_ACL` roles to be able to execute:

grant VAL_AUTH to CURI;

grant VAL_ACL to CURI;

(The API documentation contains hints about which role grants the right to execute a specific procedure in said procedure's documentation.)

# Enforcing SPARQL ACL Rules

As explained in [SPARQL ACL Rules - Defining access to private graphs](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_sparql) [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") handles SPARQL ACL rules as a special case, using the fixed rule scope oplacl:PrivateGraphsScope ([VAL.DBA.get_sparql_scope()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga27e327bb4de4c515266db21601600c0b "The IRI of the Private named graphs ACL rule scope.")) and a graph security callback. The following example shows how all the different pieces of [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") can be used to perform ACL-protected SPARQL queries (as done by `sparql.vsp`).

Imagine the actual SPARQL query is stored in variable `query`.

First we get the authentication information for the current connection. It is important to set `val_realm` to `null` because it is an `inout` variable which has to be tested against `null` in the procedure.

declare val_serviceId, val_sid, val_realm, val_uname, val_webidGraph varchar;

declare val_isRealUser integer;

declare val_cert any;

-- Set the inout variable to null since we want to get the used realm back

val_realm := null;

-- Use a tmp graph for the WebID profile

val_webidGraph := uuid();

-- Fetch the authentication details

VAL.DBA.get_authentication_details_for_connection (

sid=>val_sid,

serviceId=>val_serviceId,

uname=>val_uname,

isRealUser=>val_isRealUser,

realm=>val_realm,

cert=>val_cert,

webidGraph=>val_webidGraph);

We use `sid` as name for the cookie which stored the session id. This is the default but can be set to any value required. (However, be aware that `authenticate.vsp` currently does not allow to change this.)

After the call to [VAL.DBA.get_authentication_details_for_connection()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga745878ab820820c45f26d15217824cfa "Checks for existing authentication information in the current connection.") we know if a user is logged in or not and can act accordingly. One might either want to show a login link or simply proceed to execute the query as user `nobody` (which means that only public ACL rules apply).

-- Set the effective user (when using WS.WS."/!sparql/")

connection_set ('SPARQLUserId', 'VAL_SPARQL_ADMIN');

-- Set the effective user (when directly executing the query)

set_user_id ('VAL_SPARQL_ADMIN');

-- Set the application realm to use in the sparql graph security callback

connection_set ('val_sparql_rule_realm', val_realm);

-- Let the callback know about the mapped SQL user for system permissions

if (not val_uname is null)

connection_set ('val_sparql_uname', val_uname);

-- let the callback know about the webid tmp graph

connection_set ('val_sparql_webid_graph', val_webidGraph);

-- inject the graph security callback function into the query

query := sprintf ('define sql:gs-app-callback "VAL_SPARQL_PERMS" define sql:gs-app-uid "%s" ', coalesce (val_serviceId, 'nobody')) || query;

As recommended we execute the query as user `VAL_SPARQL_ADMIN` to get full access to the entire triple store. We then use the callback to restrict that access according to the ACL rules setup in the current realm. We do not use `dba` for security reasons. `VAL_SPARQL_ADMIN` is a special user which has full access to all public and private graphs. The permissions reported by the callback include not only the _implied_ permissions set by [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") ACL rules, but also the _physical_ graph permissions set by `RDF_USER_PERMS_SET`.

Finally we can execute the query and clear the temporary WebID graph:

sparql clear graph ?:val_webidGraph;