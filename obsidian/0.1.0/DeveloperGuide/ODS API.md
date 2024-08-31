## ODS.OdsFrameworkProgrammersGuideWebServices

- [ODS Data Spaces Framework API](https://ods.openlinksw.com/wiki/ODS/OdsFrameworkProgrammersGuideWebServices#ODS%20Data%20Spaces%20Framework%20API)

- [API - Getting Started](https://ods.openlinksw.com/wiki/ODS/OdsFrameworkProgrammersGuideWebServices#API%20-%20Getting%20Started)
- [ODS Data Spaces Framework API Services UI Endpoint](https://ods.openlinksw.com/wiki/ODS/OdsFrameworkProgrammersGuideWebServices#ODS%20Data%20Spaces%20Framework%20API%20Services%20UI%20Endpoint)

- [Related](https://ods.openlinksw.com/wiki/ODS/OdsFrameworkProgrammersGuideWebServices#Related)

## ODS Data Spaces Framework API

### API - Getting Started

|   |   |   |
|---|---|---|
|ODS_CREATE_USER|Automatic creation of new user without going trough web registration procedure.|   |
||in _username varchar,|login for user to create|
||in _passwd varchar,|password for created user|
||in _email varchar,|email address for user|
||in _host varchar := '',|desired domain for which user will be created, if not supplied URIQA default host will be taken|
||in creator_username varchar :='',|if registration for domain is prohibited authentication of administrator of the domain is required in order to authorize account create|
||in _creator_passwd varchar :=''|password for authorized administrator;|
||in _is_searchable integer:=0|optional value to determine if new user data is searchable;|
||in _show_activity integer:=0|optional value to determine if new user is shown on activity dashboard on ODS home page;|
||||
||RESULT is INTEGER (created user id) if successful, otherwise varchar - ERROR MESSAGE;|   |

|   |   |   |
|---|---|---|
|ODS_CREATE_NEW_APP_INST|creates instance of determined type for given user|   |
||in app_type varchar,|VALID WA_TYPE of application to create|
||in inst_name varchar,|desired name for the instance|
||in owner varchar,|username of the owner of the instance|
||in model int := 0,|refers to Membership model(Open,Closed,Invitation only,Approval based)|
||in pub int := 1,|refers to Visible to public property|
||in inst_descr varchar := null|description for the instance|
||result is INTEGER (instance id)if successful, otherwise varchar - ERROR MESSAGE|   |

|   |   |   |
|---|---|---|
|ODS_DELETE_USER|Delete user true authenticated SOAP call|   |
||in _username varchar,|username to be deleted|
||in _delDAV integer := 1,|optional delete of user owned DAV content|
||in auth_username varchar :='',|authentication of administrator of the domain is required in order to authorize account delete|
||in _auth_passwd varchar :=''|password for authorized administrator;|
||result is 1 if successful, otherwise varchar - ERROR MESSAGE|   |

Access to procedures granted to GDATA_ODS SOAP user using [/ods_services] web services endpoint .

It is supposed to use shttp when using the SOAP procedure for creating user authenticated by admin account.

### ODS Data Spaces Framework API Services UI Endpoint

ODS Wiki Services UI endpoint:

  

http://host:port/ods_services/services.vsmx

ODS Wiki Services wsdl Endpoint:

  

http://host:port/ods_services/services.wsdl