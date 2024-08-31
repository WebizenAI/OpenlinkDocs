|   |   |
|---|---|
|## Functions|   |
||[VAL.DBA.add_sid_to_url](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga756d433a798321a35d033b62c881b6ad) (varchar url, varchar service=null, varchar serviceId=null, varchar realm=null, varchar sidParamName="sid", varchar cookieSidName="sid", any options=null, varchar sid=null)|
||   |
||[VAL.DBA.create_login_page_url](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gaca0ee199741126f9b1fda4e52ab3b143) (varchar url, varchar deniedService=null, varchar deniedServiceId=null, varchar realm=null)|
||   |
||[VAL.DBA.default_smtp_server](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga5f68f8a4e9d8d4ccb6541b7565b8c4ab) ()|
||Reads the default smpt server from the Virtuoso configuration. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga5f68f8a4e9d8d4ccb6541b7565b8c4ab)|
||   |
||[VAL.DBA.email_address_for_service_id](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga0e3510e9b6a77b33558bd6d78814afc3) (varchar serviceId)|
||Find an email address for the given service id. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga0e3510e9b6a77b33558bd6d78814afc3)|
||   |
||[VAL.DBA.get_connection_realm](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gaad46a43c72959c862b8dc40015eafbce) (varchar fallback=null)|
||Get the realm for the current http connection. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gaad46a43c72959c862b8dc40015eafbce)|
||   |
||[VAL.DBA.get_default_realm](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gab4ad86ce5cd06213fa29ee6f2eab6292) ()|
||The default application realm. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gab4ad86ce5cd06213fa29ee6f2eab6292)|
||   |
||[VAL.DBA.get_profile_name](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gaca32625bec8fc5666c905918997e3c96) (varchar serviceId)|
||Get the full name for the given profile URI. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gaca32625bec8fc5666c905918997e3c96)|
||   |
||[VAL.DBA.get_profile_url](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga43385dfc887ccad03701cfc9f4a143c0) (varchar serviceId, varchar service=null)|
||Get a profile URL for a given service ID. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga43385dfc887ccad03701cfc9f4a143c0)|
||   |
||[VAL.DBA.http_to_https_uri](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga1fb3e8864649b678769092c6b52f72a3) (varchar uri, int checkForVhost=0)|
||Convert an HTTP URI into its HTTPS counterpart. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga1fb3e8864649b678769092c6b52f72a3)|
||   |
||[VAL.DBA.is_admin_user](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga6d55cc950a8e04c8e1372dad15521922) (varchar uname)|
||Check if a given SQL user is `dba` or in the admin group (role) [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga6d55cc950a8e04c8e1372dad15521922)|
||   |
||[VAL.DBA.new_user_session](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga4f5af9c98b75233c21a7edd7715ecc41) (varchar uname, varchar realm=null, int checkDeactivated=0, any options=null)|
||   |
||[VAL.DBA.remove_user_online_mapping](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga6d85d15c62b79c533cd103f3d12936dd) (varchar service, varchar serviceId)|
||   |
||[VAL.DBA.service_from_profile_uri](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga722e71c1b7f33de735cfa323083d5b65) (varchar url)|
||Extract service name from online account URI. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga722e71c1b7f33de735cfa323083d5b65)|
||   |
||[VAL.DBA.session_id_for_connection](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gaebc0aebc4bcbbb9933bf3f0a0d4bbe6d) (varchar sid, varchar serviceId, varchar realm=null, varchar sidParamName="sid")|
||   |
||[VAL.DBA.smtp_server_available](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga882a0ac491ca06f6514220b72f608bd2) ()|
||Check if a valid SMTP server has been configured. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga882a0ac491ca06f6514220b72f608bd2)|
||   |
||[VAL.DBA.thirdparty_services](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga94fd59580131de16c4c19e48cc60ef1d) ()|
||A simple map of all supported third-party authentication services, their labels, and oauth apikey urls. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga94fd59580131de16c4c19e48cc60ef1d)|
||   |
||[VAL.DBA.thirdparty_supported_services](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga81b14cfb51604d9f8e5c95f480a2babd) ()|
||A simple map of all the supported authentication services that can be used in thirdparty_authentication_url. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga81b14cfb51604d9f8e5c95f480a2babd)|
||   |
||[VAL.DBA.update_user_online_mapping](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gacca9cce5aa606bba90e105a88f5d9c80) (varchar service=null, varchar serviceId, varchar oauthSid=null, any uname)|
||   |
||[VAL.DBA.user_personal_uri](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga9a2e2f961dfa1e26ee0b420990781d17) (varchar uname)|
||An SQL user's personal URI. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga9a2e2f961dfa1e26ee0b420990781d17)|
||   |
||[VAL.DBA.username_for_online_account](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga354775a43d1d1d75abbfa7b205a66210) (varchar service=null, varchar serviceId, any cert=null, varchar webidGraph=null, varchar realm=null)|
||   |

## Detailed Description

The Authentication Tools API contains a set of convinience procedures which make working with VAL is vsp pages much simpler.

## Function Documentation

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga756d433a798321a35d033b62c881b6ad) add_sid_to_url()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.add_sid_to_url|(|varchar|_url_,|
|||varchar|_service_ = `null`,|
|||varchar|_serviceId_ = `null`,|
|||varchar|_realm_ = `null`,|
|||varchar|_sidParamName_ = `"sid"`,|
|||varchar|_cookieSidName_ = `"sid"`,|
|||any|_options_ = `null`,|
|||varchar|_sid_ = `null`|
||)|||

Create a new session and add the session id to the given URL for the given service and serviceId. Be aware that the serviceId should have been authenticated before calling this method.

This method is used by [VAL.DBA.thirdparty_authentication_default_callback()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a70bcb8306e4d6000da135bb30a22b20a "Default callback procedure for VAL.DBA.thirdparty_authentication_url.").

This procedure will also write a cookie header unless `cookieSidName` is set to `null`.

Parameters

|   |   |
|---|---|
|url|The URL to add the sid parameter to.|
|service|The authentication service that was used.|
|serviceId|The authenticated id, can be a WebID, a Facebook uri, etc..|
|realm|The application realm the new session should live in. See [VAL.DBA.get_default_realm()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gab4ad86ce5cd06213fa29ee6f2eab6292 "The default application realm.") for the default realm.|
|sidParamName|The parameter name used for the session id. Example: `...com/path?sid=6649987677`. If `null` no parameters will be added to the URL.|
|cookieSidName|The name used for the session id cookie. If `null` no cookie will be written. Setting both `sidParamName` and cookieSidName to `null` is useless.|
|options|An optional vector of options which is directly passed to [VAL.DBA.new_user_session()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga4f5af9c98b75233c21a7edd7715ecc41).|
|sid|The optional session id to use. If `null` then a new session will be created.|

Returns

A copy of `url` with an optionally added session id parameter.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gaca0ee199741126f9b1fda4e52ab3b143) create_login_page_url()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.create_login_page_url|(|varchar|_url_,|
|||varchar|_deniedService_ = `null`,|
|||varchar|_deniedServiceId_ = `null`,|
|||varchar|_realm_ = `null`|
||)|||

Creates a URL which allows to authenticate via any of the supported methods.

TODO: add an optional hint to the URI the resource was shared with

Parameters

|   |   |
|---|---|
|url|The URI of the resource to access.|
|deniedService|In case of a previous authentication attempt this is set to the service which was used. Can be any of the supported services like `webid`, `openid`, `facebook`, `dropbox`, etc...|
|deniedServiceId|In case of a previous authentication attempt this is set to the service id which the user authenticated with but which was not permitted to access the resource.|
|realm|The optional application realm to use.|

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga5f68f8a4e9d8d4ccb6541b7565b8c4ab) default_smtp_server()

|   |   |   |   |   |
|---|---|---|---|---|
|VAL.DBA.default_smtp_server|(||)||

Reads the default smpt server from the Virtuoso configuration.

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga0e3510e9b6a77b33558bd6d78814afc3) email_address_for_service_id()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.email_address_for_service_id|(|varchar|_serviceId_|)||

Find an email address for the given service id.

This procedure supports email addresses stored in the profile graph and sql account email addresses

Returns

An email address for `serviceId` or `null` if none could be determined.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gaad46a43c72959c862b8dc40015eafbce) get_connection_realm()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.get_connection_realm|(|varchar|_fallback_ = `null`|)||

Get the realm for the current http connection.

VAL allows to configure the application realm in the virtual dir options. This procedure will check for that option.

Warning

Be aware that authentication sessions have their own realm information which will override the virtual dir option in [VAL.DBA.get_authentication_details_for_connection()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga745878ab820820c45f26d15217824cfa "Checks for existing authentication information in the current connection.").

Returns

The application realm configured in the virtual dir or `fallback` if none was found.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gab4ad86ce5cd06213fa29ee6f2eab6292) get_default_realm()

|   |   |   |   |   |
|---|---|---|---|---|
|VAL.DBA.get_default_realm|(||)||

The default application realm.

Authentication information in [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) is typically connected to an application realm. If none is specified the default one is used as returned by this procedure.

Returns

The URI of the default application realm.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gaca32625bec8fc5666c905918997e3c96) get_profile_name()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.get_profile_name|(|varchar|_serviceId_|)||

Get the full name for the given profile URI.

Be aware that this procedure returns possibly private information and should only be shown to authorized people (like the one identified by the given `serviceId` itself).

Returns

The fullname of the given `serviceId` or `null` if none was found.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga43385dfc887ccad03701cfc9f4a143c0) get_profile_url()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.get_profile_url|(|varchar|_serviceId_,|
|||varchar|_service_ = `null`|
||)|||

Get a profile URL for a given service ID.

Not each service provides a deferenceble URL. This procedure tries hard to return a URL which people can visit to get information about the given `serviceId`.

Returns

A profile URL or `null` if none coudl be determined.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga1fb3e8864649b678769092c6b52f72a3) http_to_https_uri()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.http_to_https_uri|(|varchar|_uri_,|
|||int|_checkForVhost_ = `0`|
||)|||

Convert an HTTP URI into its HTTPS counterpart.

Parameters

|   |   |
|---|---|
|uri|The URI to convert to HTTPS. If this is already an HTTPS URI, it will be returned unaltered.|
|checkForVhost|If `1` then an additional check will be performed, ensuring that the HTTPS URI does actually exists, i.e. a corresponding virtual host exists.|

Returns

The HTTPS URL or null if SSL is not configured.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga6d55cc950a8e04c8e1372dad15521922) is_admin_user()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.is_admin_user|(|varchar|_uname_|)||

Check if a given SQL user is `dba` or in the admin group (role)

Returns

`1` If the given `uname` is an admin user, `0` otherwise.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga4f5af9c98b75233c21a7edd7715ecc41) new_user_session()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.new_user_session|(|varchar|_uname_,|
|||varchar|_realm_ = `null`,|
|||int|_checkDeactivated_ = `0`,|
|||any|_options_ = `null`|
||)|||

Create a new user session for the given user in the given realm. If `checkDeactivated` is `1` then no session will be created if the given user account has been disabled.

Parameters

|   |   |
|---|---|
|uname|The name to accociate the session with. This can be a SQL user account but also some VAL-supported service id like a WebID or a Facebook URI.|
|realm|The application realm to use. Defaults to [VAL.DBA.get_default_realm](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gab4ad86ce5cd06213fa29ee6f2eab6292 "The default application realm.") ().|
|checkDeactivated|If `1` the procedure will not create sessions for deactivated SQL accounts. Does nothing when creating a session for anything but a sql user account.|
|options|An optional vector of settings to save with the session in VS_STATE.|

Returns

The new session id as a varchar.

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga6d85d15c62b79c533cd103f3d12936dd) remove_user_online_mapping()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.remove_user_online_mapping|(|varchar|_service_,|
|||varchar|_serviceId_|
||)|||

Delete a user account mapping that has been created via [VAL.DBA.update_user_online_mapping()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gacca9cce5aa606bba90e105a88f5d9c80).

Be aware that triggers take care of removing temporary user accounts and such.

See also

[VAL.DBA.update_user_online_mapping()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gacca9cce5aa606bba90e105a88f5d9c80), [VAL.DBA.username_for_online_account()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga354775a43d1d1d75abbfa7b205a66210)

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga722e71c1b7f33de735cfa323083d5b65) service_from_profile_uri()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.service_from_profile_uri|(|varchar|_url_|)||

Extract service name from online account URI.

Example: "http://www.facebook.com/...." -> "facebook"

The extracted value may then be used to load a small icon from /val/img/social16/NAME.png

Returns

The name of the service or null.

See also

[http://localhost:8890/odsdox/group__ods__module__user.html#gac71c825dde239393bfc6124c7238153a](http://localhost:8890/odsdox/group__ods__module__user.html#gac71c825dde239393bfc6124c7238153a)

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gaebc0aebc4bcbbb9933bf3f0a0d4bbe6d) session_id_for_connection()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.session_id_for_connection|(|varchar|_sid_,|
|||varchar|_serviceId_,|
|||varchar|_realm_ = `null`,|
|||varchar|_sidParamName_ = `"sid"`|
||)|||

Check if the current HTTP session contains a valid session id. The session id can either be in the URL as parameter "sid" or in a cookie.

Parameters

|   |   |   |
|---|---|---|
|[out]|sid|The session id if a valid one was found.|
|[out]|serviceId|The service id or username for which the session was created.|
|[in,out]|realm|The realm of the session. If provided only session ids from the given realm will be returned. Caution: make sure to actually initialize the variable to `null` if it has no input value.|
||sidParamName|By default the session ID is stored in a cookie with name `sid`. The name can be changed via this parameter.|

Returns

`1` if a valid session id was found, `0` otherwise.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga882a0ac491ca06f6514220b72f608bd2) smtp_server_available()

|   |   |   |   |   |
|---|---|---|---|---|
|VAL.DBA.smtp_server_available|(||)||

Check if a valid SMTP server has been configured.

This function does a very dumb check: it tries to connect to the configured address and if that works, assumes it is an SMTP server.

Returns

`1` if mails can be sent via [VAL.DBA.send_notification_email()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ac8c3b94adee13f1aaebf76121b5b738b "Send a notification email to some email address from the system.") or smtp_send() in general, `0` if not.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga94fd59580131de16c4c19e48cc60ef1d) thirdparty_services()

|   |   |   |   |   |
|---|---|---|---|---|
|VAL.DBA.thirdparty_services|(||)||

A simple map of all supported third-party authentication services, their labels, and oauth apikey urls.

Returns

A vector of key/value pairs where each key maps to a vector containing a `label` and an `keyurl`. This includes the ODS instances from ODS_OAUTH_INSTANCES.

See also

[VAL.DBA.thirdparty_supported_services()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga81b14cfb51604d9f8e5c95f480a2babd "A simple map of all the supported authentication services that can be used in thirdparty_authenticati...")

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga81b14cfb51604d9f8e5c95f480a2babd) thirdparty_supported_services()

|   |   |   |   |   |
|---|---|---|---|---|
|VAL.DBA.thirdparty_supported_services|(||)||

A simple map of all the supported authentication services that can be used in thirdparty_authentication_url.

A vector of key/value pairs where each key maps to a supported service and each value is either `0` or `1`, depending on whether that service is usable (in other words: for which service a client key and secret is installed in OAUTH..APP_REG.)

vector('openid', 1, 'facebook', 1, 'twitter', 0, ....)

See also

[VAL.DBA.thirdparty_service_labels()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ad44f48c6401a9d2c8c031fcce2927282 "A simple map of all supported third-party authentication services and their labels.")

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gacca9cce5aa606bba90e105a88f5d9c80) update_user_online_mapping()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.update_user_online_mapping|(|varchar|_service_ = `null`,|
|||varchar|_serviceId_,|
|||varchar|_oauthSid_ = `null`,|
|||any|_uname_|
||)|||

Create or update a mapping of an online account to a user. Clients should only use this to store "fixed" mappings. For temporary user accounts use [VAL.DBA.username_for_online_account()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga354775a43d1d1d75abbfa7b205a66210) instead. For mapping two service ids use [VAL.DBA.add_same_as_relation()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a729ab2d639aac64165a925734e24d555 "Mark two service ids as being the same.").

**Caution:** Only call this procedure for mappings that are authenticated. Otherwise security might be breached when the wrong user names are suddenly related to an online account.

Parameters

|   |   |
|---|---|
|service|The service type. This parameter is optional and when not provided will be ignored. Its only point is to improve accuracy for clients having the service type available.|
|serviceId|The service id of the online account. This can be any of the supported types like WebID, Facebook URL, etc..|
|oauthSid|The OAuth session which references OAUTH..CLI_SESSIONS. This allows to reuse an OAuth access token for subsequent API calls. If this is `null` and a mapping is updated the existing value is used.|
|uname|The user to map the account to (can also be uid).|

Throws a signal on error.

See also

[VAL.DBA.username_for_online_account()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga354775a43d1d1d75abbfa7b205a66210), [VAL.DBA.remove_user_online_mapping()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga6d85d15c62b79c533cd103f3d12936dd), [VAL.DBA.add_same_as_relation()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a729ab2d639aac64165a925734e24d555 "Mark two service ids as being the same.")

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga9a2e2f961dfa1e26ee0b420990781d17) user_personal_uri()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.user_personal_uri|(|varchar|_uname_|)||

An SQL user's personal URI.

The profile URI of a given SQL user is the same as used by ODS for convinience.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga354775a43d1d1d75abbfa7b205a66210) username_for_online_account()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.username_for_online_account|(|varchar|_service_ = `null`,|
|||varchar|_serviceId_,|
|||any|_cert_ = `null`,|
|||varchar|_webidGraph_ = `null`,|
|||varchar|_realm_ = `null`|
||)|||

Get a mapped user account for the given online service id.

Parameters

|   |   |
|---|---|
|service|The service type. This parameter is optional and when not provided will be ignored. Its only point is to improve accuracy for clients having the service type available.|
|serviceId|The service id of the online account. This can be any of the supported types like WebID, Facebook URL, etc..|
|cert|The optional certificate for mapping WebIDs to SQL accounts via old-school ACLs.|
|webidGraph|The optional graph containing the details of the imported WebID profile.|
|realm|The optional application realm for checking ACLs.|

Returns

The name of the user account the given service id is mapped to.

Throws a signal in the case of an error.

See also

[VAL.DBA.update_user_online_mapping()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gacca9cce5aa606bba90e105a88f5d9c80), [VAL.DBA.remove_user_online_mapping()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga6d85d15c62b79c533cd103f3d12936dd)

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;