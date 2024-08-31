|   |   |
|---|---|
|## Functions|   |
|acl.rule.|[VAL.VAL.delete](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga6fc68796871aceab36f663c9e580f83e) (varchar uri)|
||Delete an existing rule. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga6fc68796871aceab36f663c9e580f83e)|
||   |
|acl.rule.|[VAL.VAL.get](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga5f84db9b1b48866081dce9a481efd3fb) (varchar uri, varchar format=null)|
||   |
|acl.rule.|[VAL.VAL.list](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga4482c35b46473f3d5150478f3ed309c7) (varchar format=null)|
||List all existing rules in the current realm. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga4482c35b46473f3d5150478f3ed309c7)|
||   |
|acl.permissions.|[VAL.VAL.list](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga139024c82a319b2cd350e5dddc785d27) (varchar uri=null, varchar scope=null, varchar mode=null)|
||List permissions of the authenticated user for a given resource or scope. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga139024c82a319b2cd350e5dddc785d27)|
||   |
||[VAL.VAL.login](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga20284486a193239f08c9885596f01762) (varchar service)|
||Logs in a UI-less client, returning a session ID through a cookie `sid`. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga20284486a193239f08c9885596f01762)|
||   |
||[VAL.VAL.logout](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga45612b6dc47b262c761ee6bd98e866ce) ()|
||Logs out a UI-less client which logged in through [VAL.VAL.login](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga20284486a193239f08c9885596f01762 "Logs in a UI-less client, returning a session ID through a cookie sid."). [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga45612b6dc47b262c761ee6bd98e866ce)|
||   |
|acl.rule.|[VAL.VAL.new](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#gacb2dde6a02c97a7961971b710ff2ae39) (varchar ruleData=null, varchar format=null)|
||Create a new ACL rule. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#gacb2dde6a02c97a7961971b710ff2ae39)|
||   |
|acl.rule.|[VAL.VAL.update](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#gaa4823dd6df2da5874e34424b37f4f401) (varchar uri, varchar ruleData=null, varchar format=null, int overwrite=1)|
||Change an ACL rule's properties. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#gaa4823dd6df2da5874e34424b37f4f401)|
||   |

## Detailed Description

**Tip:** Maybe you would rather use the [The RESTful ACL API](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#val_acl_restful_api).

The public HTTP API provides API functions to manage rules and groups. It is entirely turtle-based, meaning that input and output is in turtle format. By default [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") installs a virtual directory at `/val/api` which means the API calls will be available as `[http://HOST/val/api/acl.rule.new](http://host/val/api/acl.rule.new)` and so on. All VAL-supported authentication mechanisms are supported. This includes session ids, OAuth, HTTP digest auth, and [WebID](http://www.w3.org/wiki/WebID). Be aware, though, that only the session id carries an application realm at the moment. All other authentication mechanisms will result in usage of the default realm `oplacl:DefaultRealm`.

# The RESTful ACL API

The RESTful ACL API allows to create, update, delete, and list rules and groups using typical RESTful patterns. Two base URLs serve as entry points:

- `[http://HOST/acl/rules](http://host/acl/rules)` - Will list existing rules via a `GET` operation and allows to create new rules by `POST`ing them.
- `[http://HOST/acl/groups](http://host/acl/groups)` - Will list existing groups via a `GET` operation and allows to create new groups by `POST`ing them.
- `[http://HOST/acl/restrictions](http://host/acl/restrictions)` - Will list existing restrictions via a `GET` operation and allows to create new restrictions by `POST`ing them.

Existing rules, groups and restrictions can be manipulated directly via their URLs. An HTTP `DELETE` will remove them; an HTTP `PATCH` allows to add members or conditions to groups and modes to rules; an HTTP `PUT` allows to overwrite entire groups, rules or restrictions (excluding the realm which cannot be changed).

The APIs prominent data exchange format is `turtle`.

For usage examples see [ACL API Examples Using Curl](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_examples_curl).

## Function Documentation

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga6fc68796871aceab36f663c9e580f83e) delete()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|acl restriction VAL.VAL.delete|(|varchar|_uri_|)||

Delete an existing rule.

Delete a single condition from a conditional group.

Delete an existing group.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga5f84db9b1b48866081dce9a481efd3fb) get()

|   |   |   |   |
|---|---|---|---|
|acl restriction VAL.VAL.get|(|varchar|_uri_,|
|||varchar|_format_ = `null`|
||)|||

Get the details of one specific rule.

Get the details of one specific group.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga4482c35b46473f3d5150478f3ed309c7) list() [1/2]

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|acl restriction VAL.VAL.list|(|varchar|_format_ = `null`|)||

List all existing rules in the current realm.

List all existing groups.

Lists all ACL groups defined by the authenticated user in the current application realm. The latter is defined by the authentication context/realm.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga139024c82a319b2cd350e5dddc785d27) list() [2/2]

|   |   |   |   |
|---|---|---|---|
|acl.permissions. VAL.VAL.list|(|varchar|_uri_ = `null`,|
|||varchar|_scope_ = `null`,|
|||varchar|_mode_ = `null`|
||)|||

List permissions of the authenticated user for a given resource or scope.

Each user can request the permissions they have on certain resources. The result will be a set of "virtual" ACL rules representing those permissions. These "virtual" rules do not necessarily exist like that in the system. They are merely used to communicate the permissions to the client.

Parameters

|   |   |
|---|---|
|uri|The optional URI of the resource to request permissions for. If omitted permissions for all resources in the given scope are returned.|
|scope|The optional scope of the resources to check permissions for. While this can perfectly be combined with `uri`, it does not add any additional information. If omitted the permissions in all scopes are returned.|
|mode|The optional mode to request. This can be set if the client needs to know if the user has a certain permission (like `oplacl:Read`) on a resource. If omitted all granted modes are returned.|

The following example shows a set of permissions on three named graphs (authentication omitted for brevity):

$ curl "http://HOST/val/api/acl.permissions.list?scope=urn%3Avirtuoso%3Aval%3Ascopes%3Asparql"

@prefix acl: <http://www.w3.org/ns/auth/acl#>

@prefix oplacl: <http://www.openlinksw.com/ontology/acl#>

:acl0 a acl:Authorization ;

oplacl:hasAccessMode <http://www.w3.org/ns/auth/acl#Read> ;

acl:accessTo <urn:foobar4> ;

acl:agent <acct:115338406@dropbox.com> .

:acl1 a acl:Authorization ;

oplacl:hasAccessMode <http://www.w3.org/ns/auth/acl#Read> ;

oplacl:hasAccessMode <http://www.openlinksw.com/ontology/acl#GrantRead> ;

acl:accessTo <urn:foobar3> ;

acl:agent <acct:115338406@dropbox.com> .

:acl2 a acl:Authorization ;

oplacl:hasAccessMode <http://www.w3.org/ns/auth/acl#Read> ;

oplacl:hasAccessMode <http://www.w3.org/ns/auth/acl#Write> ;

acl:accessTo <urn:foobar> ;

acl:agent <acct:115338406@dropbox.com> .

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga20284486a193239f08c9885596f01762) login()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.VAL.login|(|varchar|_service_|)||

Logs in a UI-less client, returning a session ID through a cookie `sid`.

The procedure is exposed as endpoint http[s]://HOST/val/api/login. This endpoint is intended for use by UI-less (non-browser) clients to authenticate without going via `authenticate.vsp`. The returned session ID can then be used with other [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) HTTP APIs which require authentication, for example [VAL.VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html)."acl.rule.list" etc.

Parameters

|   |   |
|---|---|
|service|The service to authenticate with. Supported services are: `webid`, `digest` or `basic`.|

Authentication using WebID requires https. HTTP digest authentication is supported on both https and http. HTTP basic authentication is only supported on https. A username supplied using digest or basic authentication must identify a SQL user. A WebID need not have a corresponding SQL account.

All sessions are created in the default realm `oplacl:DefaultRealm`.

Returns

A JSON string reporting the login status.

On successful login, returns a JSON string of the form:

- { "status": "success", "httpcode": "<http_status_code>" "message": "Login successful. Logged in as <service_id>." }

Errors are reported using a JSON string of the form:

- { "status": "error", "httpcode": "<http_status_code>", "code": "<err_code>", "message": "<err_msg>" }

To authenticate using a certificate or HTTP authentication, it is sufficient to call [VAL.DBA.get_authentication_details_for_connection](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga745878ab820820c45f26d15217824cfa "Checks for existing authentication information in the current connection."). However that routine just authenticates the client, it doesn't create a session. If an endpoint protected by [VAL.DBA.get_authentication_details_for_connection](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga745878ab820820c45f26d15217824cfa "Checks for existing authentication information in the current connection.") is called directly without a session ID, a WebID client would be authenticated each time before the HTTP request (e.g. a SPARQL query) is serviced, but performing a full WebID authentication each time is expensive. It requires a network fetch to retrieve the profile document etc. Similarly, HTTP digest authentication requires an initial challenge-response exchange, as does HTTP basic authentication if the client doesn't supply an Authorization header with the initial request.

When making multiple calls to a [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) protected endpoint from a non-browser client, using a session ID incurs less overhead. So, using `/val/api/login` to obtain a session ID is beneficial though not mandatory. The non-browser client, e.g. a node.js application, is responsible for capturing the `sid` session cookie returned via a 'Set-Cookie' header and for providing the session cookie in subsequent calls to a [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) endpoint through a 'Cookie' request header. The client should take care to destroy the session once finished by calling [VAL.VAL.logout](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga45612b6dc47b262c761ee6bd98e866ce "Logs out a UI-less client which logged in through VAL.VAL.login.").

If using HTTP basic authentication, virtuoso.ini must contain

[Client]

SQL_ENCRYPTION_ON_PASSWORD = 1

to ensure Virtuoso returns the correct WWW-Authenticate header with any initial 401 authentication-challenge response, ie. returns header 'WWW-Authenticate: Basic realm=...' rather than 'WWW-Authenticate: Digest realm=...'. SQL_ENCRYPTION_ON_PASSWORD signifies a clear text (actually a base64 encoded) password will be supplied. Consequently, basic authentication via /val/api/login is only supported over https.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga45612b6dc47b262c761ee6bd98e866ce) logout()

|   |   |   |   |   |
|---|---|---|---|---|
|VAL.VAL.logout|(||)||

Logs out a UI-less client which logged in through [VAL.VAL.login](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga20284486a193239f08c9885596f01762 "Logs in a UI-less client, returning a session ID through a cookie sid.").

The procedure is exposed as endpoint http[s]://HOST/val/api/logout. It destroys a session created by [VAL.VAL.login](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga20284486a193239f08c9885596f01762 "Logs in a UI-less client, returning a session ID through a cookie sid."). The session ID of the session to terminate must be supplied in a 'Cookie' header as cookie `sid`.

Returns

A JSON string reporting the logout status.

On successful logout, returns the JSON string:

- { "status": "success", "httpcode": "200", "message": "Logout successful." }

Errors are reported using a JSON string of the form:

- { "status": "error", "httpcode": "<http_status_code>", "code": "<err_code>", "message": "<err_msg>" }

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#gacb2dde6a02c97a7961971b710ff2ae39) new()

|   |   |   |   |
|---|---|---|---|
|acl restriction VAL.VAL.new|(|varchar|_ruleData_ = `null`,|
|||varchar|_format_ = `null`|
||)|||

Create a new ACL rule.

Create a new Group, static or conditional.

Typically this procedure will be redirected to from a PUT URL rewrite rule.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#gaa4823dd6df2da5874e34424b37f4f401) update()

|   |   |   |   |
|---|---|---|---|
|acl group VAL.VAL.update|(|varchar|_uri_,|
|||varchar|_groupData_ = `null`,|
|||varchar|_format_ = `null`,|
|||int|_overwrite_ = `0`|
||)|||

Change an ACL rule's properties.

- Posting a condition to a group will add it (if it is a conditional group)
- Posting an entire group will overwrite it, including the conditions
    
    Parameters
    
    |   |   |
    |---|---|
    |overwrite|If 1 the provided members will replace the existing ones, if not, they will be added (POST vs. PATCH I guess?)|