https://docs.openlinksw.com/virtuoso/confodbcdsn/
### 3.3.1. Configuring Your ODBC Data Sources

Before you can link a table into Virtuoso, you need to configure an ODBC datasource. It is quite likely that you already have ODBC data sources defined. If so, you can skip this part of the tour.

If you do not have any data sources defined, you should configure your datasource using an appropriate ODBC driver. The ODBC driver may come from the database vendor or a third-party middleware vendor, such as OpenLink Software. You will need to configure your ODBC datasource in accordance with the directions from your driver vendor.

In this part of the tour, we show sample DSN configuration information for some database vendor drivers. These examples of working data sources are not meant to replace the instructions from the driver vendor. In your specific installation other parameters may be necessary.

To define ODBC data sources on Windows XP/95/98/NT, in the Control Panel go to Administrative Tools and then click the Data Sources (ODBC) icon.

This first datasource uses OpenLink Generic ODBC Driver V6.0 to create DSN to a MySQL 5.x database.

**Figure 3.7. OpenLink Mutli Tier DSN Configuration with database MySQL 5.x**

![OpenLink Mutli Tier DSN Configuration with database MySQL 5.x](https://docs.openlinksw.com/virtuoso/confodbcdsn/images/virttour1.png)

  

The next example is an Informix 7 datasource using the driver from Informix Software, Inc.

**Figure 3.8. Informix Driver DSN Configuration**

![Informix Driver DSN Configuration](https://docs.openlinksw.com/virtuoso/confodbcdsn/images/virttour2.gif)

  

The next few images show a Microsoft SQL Server 6.5 datasource using the Microsoft Corporation SQL Server driver.

**Figure 3.9. MS SQL Server DSN Configuration**

![MS SQL Server DSN Configuration](https://docs.openlinksw.com/virtuoso/confodbcdsn/images/virttour3.gif)

  

**Figure 3.10. MS SQL Server DSN Configuration**

![MS SQL Server DSN Configuration](https://docs.openlinksw.com/virtuoso/confodbcdsn/images/virttour4.gif)

  

**Figure 3.11. MS SQL Server DSN Configuration**

![MS SQL Server DSN Configuration](https://docs.openlinksw.com/virtuoso/confodbcdsn/images/virttour5.gif)

  

**Figure 3.12. MS SQL Server DSN Configuration**

![MS SQL Server DSN Configuration](https://docs.openlinksw.com/virtuoso/confodbcdsn/images/virttour6.gif)

  

**Figure 3.13. MS SQL Server DSN Configuration**

![MS SQL Server DSN Configuration](https://docs.openlinksw.com/virtuoso/confodbcdsn/images/virttour7.gif)

  

Finally, review the configuration information for your default local Virtuoso datasource, named "_Local Virtuoso_ ".

**Figure 3.14. OpenLink Virtuoso DSN Configuration**

![OpenLink Virtuoso DSN Configuration](https://docs.openlinksw.com/virtuoso/confodbcdsn/images/virttour8.png)

  

DSNs can be created and configured within the Virtuoso Conductor. Go to "Database", then to "External Data Sources" and then go to "Configure Data Sources" tab. Click the "Add System DSN", or "Add User DSN", or "Add File DSN" button.

**Figure 3.15. Creating a new DSN**

![Creating a new DSN](https://docs.openlinksw.com/virtuoso/confodbcdsn/images/newdsn.png)