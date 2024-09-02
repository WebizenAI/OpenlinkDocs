Once you've installed Virtuoso, you should be able to run it and then go to http://localhost:8890/ in your browser.  
https://docs.openlinksw.com/virtuoso/defpasschange/

### 3.1.1. Default Passwords

When you start up Virtuoso for the first time, there are 3 user accounts defined:

**Table 3.1. Default users of Virtuoso**

|User Name|Default Password|Usage|
|:--|---|---|
|dba|dba|Default Database Administrator account.|
|dav|dav|WebDAV Administrator account.|
|vad|vad|WebDAV account for internal usage in VAD (disabled by default).|
|demo|demo|Default demo user for the demo database. This user is the owner of the Demo catalogue of the demo database.|
|soap|soap|SQL User for demonstrating SOAP services.|
|fori|fori|SQL user account for 'Forums' tutorial application demonstration in the Demo database.|

  

One database user and 2 WebDAV users. These users have their passwords set to default values. It is therefore important to change them immediately after the installation.

The one database user is the database administrator with username "dba" and password "dba". This can be changed using the [Interactive SQL](https://docs.openlinksw.com/virtuoso/configuringvirtuosoclients/) utility. When started without parameters, the ISQL tries to log on as dba with the default password. The SQL statement to change a user's password is:

set password <old password> <new password>

The password is an identifier, so take care to use proper quotation.

You can also use the graphical [Virtuoso Administration Interface](https://docs.openlinksw.com/virtuoso/dbadmin/) to administer Virtuoso database users.

The 2 WebDAV user accounts, dav and davuser also have their password set to their username. There are 2 easy ways to change them. Either use the GUI in Administration Interface under WebDAV Administration / WebDAV services / Users Administrator or use the SQL statement:

update WS.WS.SYS_DAV_USER set U_PASSWORD='<new password>'
where U_NAME='<username>'
    

Note quotation around varchar values. Please remember to perform these operations for all Virtuoso server instances installed. By default these are the Virtuoso with an empty database and Virtuoso [demo] with the demo database.