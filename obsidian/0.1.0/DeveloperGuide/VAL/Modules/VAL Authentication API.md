|   |   |
|---|---|
|## Functions|   |
||[VAL.DBA.digest_authentication](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga23ffe8209155d65fb7f44f1fc0213189) (varchar uname, varchar nonce, varchar pwdHash)|
||   |
||[VAL.DBA.get_authentication_details_for_connection](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga745878ab820820c45f26d15217824cfa) (varchar sid, varchar serviceId, varchar uname, int isRealUser, varchar realm=null, varchar sidParamName="sid", any cert, varchar webidGraph=null)|
||Checks for existing authentication information in the current connection. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga745878ab820820c45f26d15217824cfa)|
||   |
||[VAL.DBA.logout](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga3b4ad3ebbecda2375698fff095d64f77) (varchar sid=null, varchar sidParamName="sid")|
||Clear authentication information. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga3b4ad3ebbecda2375698fff095d64f77)|
||   |
||[VAL.DBA.oauth_refresh_token](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#gae780b9ab20c441bb27991994762821ae) (varchar service=null, varchar serviceId=null, int force=0, varchar oauthSid=null, varchar scope=null)|
||Refresh an OAuth access token based on service type and service id. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#gae780b9ab20c441bb27991994762821ae)|
||   |
||[VAL.DBA.request_login_nonce](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#gac3fc7b80455871fa062e721f81b3cf0f) ()|
||   |
||[VAL.DBA.thirdparty_authentication_url](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga6240c9d79e5a9816f7aa03cdbf73a170) (varchar service, varchar data, varchar callback, varchar successProc=null, varchar errorProc=null, any params=null, varchar scope="basic", varchar clientIp=null, varchar realm=null)|
||Create an authentication URL for any supported 3rd-party service. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga6240c9d79e5a9816f7aa03cdbf73a170)|
||   |

## Detailed Description

The VAL Authentication API provides a set of procedures to easily integrate authentication functionality into vsp pages.

## Function Documentation

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga23ffe8209155d65fb7f44f1fc0213189) digest_authentication()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.digest_authentication|(|varchar|_uname_,|
|||varchar|_nonce_,|
|||varchar|_pwdHash_|
||)|||

Perform digest authentication in a slightly more secure way than plain pwds. The pwdHash uses a nonce as generated via [VAL.DBA.request_login_nonce()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#gac3fc7b80455871fa062e721f81b3cf0f) in combination with the password like so:

pwdHash := md5 (pwd || nonce);

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga745878ab820820c45f26d15217824cfa) get_authentication_details_for_connection()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.get_authentication_details_for_connection|(|varchar|_sid_,|
|||varchar|_serviceId_,|
|||varchar|_uname_,|
|||int|_isRealUser_,|
|||varchar|_realm_ = `null`,|
|||varchar|_sidParamName_ = `"sid"`,|
|||any|_cert_,|
|||varchar|_webidGraph_ = `null`|
||)|||

Checks for existing authentication information in the current connection.

This procedure checks for authentication information like a session ID, a WebID client certificate, or basic HTTP authentication and fills the output parameters accordingly. The following authentication mechanisms are checked:

- A Session ID which can either be given as a URL parameter to the requested URL or as a Cookie. The default [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) callback handler for [VAL.DBA.thirdparty_authentication_url()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga6240c9d79e5a9816f7aa03cdbf73a170 "Create an authentication URL for any supported 3rd-party service.") creates such session ids.
- A client certificate with an optionally embedded WebID.
- Basic HTTP authentication

Afterwards the 3rd-party service ID or WebID is mapped to an existing SQL user account by the following means:

- ODS online account mapping (if ODS is installed)
- SPARQL ACL rules mapping service ids to SQL users

If successful the SPARQLUserId is set to the authenticated SQL user for the benetif of the SPARQL engine.

Parameters

|   |   |   |
|---|---|---|
|[out]|sid|Will be set to the session id if one has been found, `null` otherwise. Be aware that an empty session does not mean "no authentication information". HTTP digest auth or WebID does not result in a session id.|
|[out]|serviceId|Will be set to the 3rd-party serviceID connected to the session, the WebID embedded in the client certificate. If the session maps to an actual SQL user the `serviceId` will be set to their profile URI ([VAL.DBA.user_personal_uri()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga9a2e2f961dfa1e26ee0b420990781d17 "An SQL user's personal URI.")).|
|[out]|uname|Will be set to the SQL username if the authentication information could be mapped to one, `null` otherwise.|
|[out]|isRealUser|Will be set to `1` if `uname` refers to an actual user, `0` if `uname` refers to a dummy SPARQL ACL rule user account which is only used for mapping. This is useful only for UIs which want to display the correct login identifier. If `isRealUser` is `1` then the UI should show that name, otherwise it should show the `serviceID` instead.|
|[in,out]|realm|The optional application realm to be used. If provided only authentication information matching the realm will be returned. If `null` then the realm from the virtual directory will be used instead (see also [Virtual Host Specific Realm](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_realms_vhost)). Should the realm not be set in the virtual dir options it will be set to the realm of the found authentication information, falling back to the default for authentication information without a realm.|
||sidParamName|The name of the URL parameter and cookie used to store the session id. Default to `sid`.|
|[out]|cert|The optional client certificate which was used for authentication. Will be non-null for WebID and client cert authentication. Use this in calls to procedures like [VAL.DBA.check_acls_for_resource()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9a2351c047a02b3ce8457e49c804e3d8 "Find permissions for resources as set by ACL rules in a certain realm.") and friends.|
||webidGraph|The optional graph URI to use for storing the WebID profile details. If null then a tmp graph will be created and cleared after the checks are finished. If the profile details are required after the authentication checks for something like authorization then providing a graph URI is a good idea.|

Returns

`0` if no useful authentication information could be found, otherwise one of the following:

- `1` - In case of authentication via a session id
- `2` - In case of authentication via WebID or a client certificate
- `3` - In case of HTTP authentication
- `4` - In case of OAuth authentication

See also

[Supported Authentication Methods](https://docs.openlinksw.com/valdocs/val_services.html#val_services_auth_methods)

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga3b4ad3ebbecda2375698fff095d64f77) logout()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.logout|(|varchar|_sid_ = `null`,|
|||varchar|_sidParamName_ = `"sid"`|
||)|||

Clear authentication information.

This procedure performs a full [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) logout: it invalidates the session, removes the session cookie and resets the SPARQLUserId.

If no session id is given it is determined using [VAL.DBA.session_id_for_connection()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gaebc0aebc4bcbbb9933bf3f0a0d4bbe6d)

Returns

`1` if logout was performed, `0` if no session id was found and nothing was done.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#gae780b9ab20c441bb27991994762821ae) oauth_refresh_token()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.oauth_refresh_token|(|varchar|_service_ = `null`,|
|||varchar|_serviceId_ = `null`,|
|||int|_force_ = `0`,|
|||varchar|_oauthSid_ = `null`,|
|||varchar|_scope_ = `null`|
||)|||

Refresh an OAuth access token based on service type and service id.

Parameters

|   |   |
|---|---|
|service|The type of service. One of the supported types. See the ODS API documentation for details.|
|serviceId|The service ID. In most cases this is a profile URI. See the ODS API documentation for details.|
|force|If `1` the token will always be refreshed even if the expiration time is not reached yet. FIXME: does this at all make sense? If the token is revoken manually then we need to re-authenticate via UI anyway!|
|oauthSid|Optional sid to identify the exact session to update. If this is `null` then the latest valid session is updated.|
|scope|Optional Update the token with the given scope. Either 'profile' or 'basic'. Defaults to `null` in which case the first matching token is used, independant of its scope.|

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#gac3fc7b80455871fa062e721f81b3cf0f) request_login_nonce()

|   |   |   |   |   |
|---|---|---|---|---|
|VAL.DBA.request_login_nonce|(||)||

Public HTTP API method which allows clients such as authenticate.vsp to request a nonce for slightly safer digest login without https. The nonce will be tied to the client IP and can only be used once.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga6240c9d79e5a9816f7aa03cdbf73a170) thirdparty_authentication_url()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.thirdparty_authentication_url|(|varchar|_service_,|
|||varchar|_data_,|
|||varchar|_callback_,|
|||varchar|_successProc_ = `null`,|
|||varchar|_errorProc_ = `null`,|
|||any|_params_ = `null`,|
|||varchar|_scope_ = `"basic"`,|
|||varchar|_clientIp_ = `null`,|
|||varchar|_realm_ = `null`|
||)|||

Create an authentication URL for any supported 3rd-party service.

The user should be directed to the returned URL to log into the service and approve the sharing of information.

Parameters

|   |   |
|---|---|
|service|The service to authenticate with. This can be any supported OAuth service or `openid`. See also [Supported 3rd Party Services](https://docs.openlinksw.com/valdocs/val_services.html#val_services_third_party).|
|data|Optional information required for login. Thus far only `openid` requires the actual OpenID URL.|
|callback|The callback URL. Be aware that the third-party service will never see this URL since we use an internal callback URL which will handle the further processing based on the value of this URL and `successProc`.|
|successProc|The name of a procedure to call for custom processing of the authentication data. Defaults to [thirdparty_authentication_default_callback()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a70bcb8306e4d6000da135bb30a22b20a "Default callback procedure for VAL.DBA.thirdparty_authentication_url."). This procedure needs to return the final redirection URL based on the `url` parameter described below. The generic authentication callback procedure will, once authentication was successful, call this procedure with the following parameters:<br><br>- Callback URL (matches `callback`)<br>- The custom parameters (matches `params`).<br>- Service name (matches `service`)<br>- Service ID as returned by the service. This is typically a profile URL as used to identify 3rd-party accounts internally. In case of OpenID this is the authenticated OpenID URL.<br>- A vector containing a map of profile details from the service. This map can contain the following values:<br>    - `username` A username extracted from the 3rd-party service account. This username might be constructed. It is mainly useful if a new account should be created based on this information (for example ODS).<br>    - `email` - An email address extracted from the 3rd-party service account. Can be null.<br>    - `fullname` - The full name extracted from the 3rd-party service account. Can be null.<br>    - `image` - The URL to the profle image extracted from the 3rd-party service account. Can be null.<br>- A vector containing a map of OAuth information from the authentication process. This is a copy of the OAuth session data that is also accessible via the oauth session id (see below) from `OAUTH.DBA.CLI_SESSIONS`. It can contain the following information:<br>    - `access_token` - The optional OAuth access token. This is required to perform calls to the 3rd-party service.<br>    - `refresh_token` - The optional OAuth refresh token.<br>    - `expire` - The optional access token expiration time. This is an actual datetime value indicating the time the access token will expire. If this value is null then the access token will never expire.<br>- The internal OAuth sid which allows to identify this OAuth session in OAUTH.DBA.CLI_SESSIONS. `null` for `openid`.|
|errorProc|The name of a procedure to call in case of an error. Like `successProc` this procedure needs to return the redirection URL, however containing optional error information constructed from the parameters below. If not specified the plain url as provided in `callback` is used with additional parameter `error.msg`. Customizing this is typically not required. The procedure needs to handle the following parameters:<br><br>- Callback URL (matches `callback`)<br>- The custom parameters (matches `params`).<br>- Service name (matches `service`)<br>- The error state (varchar)<br>- The error message (varchar)|
|params|A vector of custom paramers which will be forwared to the callback procedure. This is a means to have state without persisting it.|
|scope|The scope of the authentication. [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) currently supports three meta-scopes which are mapped to the service-dependent scope values if applicable. The scopes can also be combined by comma-separation.<br><br>- `basic` - This will just request basic profile information like username and email<br>- `profile` - This will request read access to the full profile including friend lists, posts, etc.<br>- `dav` - This will request read/write access to a service's filesystem (GDrive, DropBox, etc.)<br>- `post` - This will request permisions to create new posts like status updates or Tweets or Blog entries.|
|clientIp|Force the IP address of the client to a different value. Some OAuth services enforce the client IP be the same for all steps but allow to set it once in the beginning. This is normally not required as it is figured out by default. However, if an ODS proxy is in use the automatically determined client IP will differ from the one of the client. In that case this should be set to the actual client which will also perform the authentication step with the 3rd party service.|
|realm|The optional application realm in which authentication should be performed. This falls back to the default realm ([VAL.DBA.get_default_realm()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gab4ad86ce5cd06213fa29ee6f2eab6292 "The default application realm.")).|

Returns

A new authentication URL to which the client should navigate. On error a signal is thrown.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;