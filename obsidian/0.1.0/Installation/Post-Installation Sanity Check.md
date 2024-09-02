https://docs.openlinksw.com/virtuoso/postinstsanity/
#### Verify by ISQL

Verify usability of your Virtuoso server by executing the following command from your command line prompt:

isql

From the ISQL prompt enter the following SQL command:

select * from DB.DBA.SYS_USERS;

This should produce a resultset containing one record if everything has been implemented correctly to this point.

**Figure 3.1. ISQL in Telnet**

![ISQL in Telnet](https://docs.openlinksw.com/virtuoso/postinstsanity/images/ln-inst3.gif)

  

[¶](https://docs.openlinksw.com/virtuoso/postinstsanity/#posttesthttp)

#### Verify by HTTP

A quick way to check that the database is running, is to point a browser to the http port. The following example URLs will show the System Manager for the default, and the demo Virtuoso databases:

http://example.com:8889/
http://example.com:8890/
http://a_virtuoso_server.org:8890/

On a Windows Client there is a shortcut to the _OpenLink Virtuoso Conductor_ in the OpenLink Virtuoso program group.

You will be presented with the OpenLink Virtuoso Conductor screen:

**Figure 3.2. Virtuoso Conductor**

![Virtuoso Conductor](https://docs.openlinksw.com/virtuoso/postinstsanity/images/ln-inst4.png)

  

[¶](https://docs.openlinksw.com/virtuoso/postinstsanity/#posttestqry)

#### Verify by web based SQL query

Click on the _Conductor_ link to enter the Virtuoso Server Administration Conductor Interface. You will be presented with a login form, type in the correct details for the database DBA user, by default this is username=dba; password=dba.

**Figure 3.3. Virtuoso Conductor - Login Form**

![Virtuoso Conductor - Login Form](https://docs.openlinksw.com/virtuoso/postinstsanity/images/ln-inst-login.png)

  

Got to tab "Database" and then go to tab "Interactive SQL".

**Figure 3.4. Virtuoso Conductor - Interactive SQL**

![Virtuoso Conductor - Interactive SQL](https://docs.openlinksw.com/virtuoso/postinstsanity/images/ln-inst-isql.png)

  

Enter the SQL Statement command "SELECT * FROM SYS_USERS" in the SQL Statement text area. Note that only valid SQL can be supplied, so you cannot type a database command such as "tables;". Also, note that the ";" is not valid in this context. Press _Execute_ .

You should see the SQL results, as shown below.

**Figure 3.5. Virtuoso Conductor - SQL Results**

![Virtuoso Conductor - SQL Results](https://docs.openlinksw.com/virtuoso/postinstsanity/images/ln-inst-isql2.png)

  

|   |   |   |
|---|---|---|
|[Prev](https://docs.openlinksw.com/virtuoso/defpasschange/)|[Up](https://docs.openlinksw.com/virtuoso/newadminui/)|[Next](https://docs.openlinksw.com/virtuoso/administeringtheserver/)|
|3.1.1. Default Passwords|[Home](https://docs.openlinksw.com/virtuoso/index/)|3.1.3. Administering Your Virtuoso Installation|