Virtuoso supports a number of data access API's such as ODBC and JDBC. They both provide high performance native connectivity to the Virtuoso database system.
https://docs.openlinksw.com/virtuoso/qsclientcon/ 
### 3.2.1. ODBC

The Virtuoso driver for ODBC is available for Windows and most Unix operating systems. For Windows the you can configure a data source that utilizes the driver in the familiar way via the ODBC Administrator. This is very easy windows and wizards based process. On Unix the process has historically not been so simple. We have been trying to a achieve the same level of usability under Unix through our support of the [iODBC project](http://www.iodbc.org/) . For more information and details about how to configure the Virtuoso driver for ODBC please go to the [Virtuoso Driver for ODBC](https://docs.openlinksw.com/virtuoso/virtdsnsetup/) section.
https://docs.openlinksw.com/virtuoso/qsodbc/ 
### 3.2.2. JDBC

The Virtuoso driver for JDBC is a type 4 native driver which is available for all Java platforms. This means that you have a single jar file, for which to include into your classpath, and then the driver is ready for use by your applications. The connection URL typically consists of:

jdbc:virtuoso://hostname:port/UID=uid/PWD=pwd

More information about the JDBC driver can be found in the [Virtuoso Driver for JDBC](https://docs.openlinksw.com/virtuoso/virtuosodriverjdbc/) section. The JDBC driver also supports SSL encrypted connections. This JDBC driver is an excellent companion to any web enabled applications especially when combined with Virtuoso's other features such as WSDL and SOAP.
https://docs.openlinksw.com/virtuoso/qajdbc/

### 3.2.3. OLEDB

Virtuoso gives application developers an opportunity to utilize OLE DB interfaces for their database programming needs. OLE DB is a Microsoft developed and promoted technology for uniform data access across diverse data sources. Many applications make indirect use of OLE DB through a higher level ADO interface.

VIRTOLEDB is the native [OLE DB provider for Virtuoso](https://docs.openlinksw.com/virtuoso/virtoledb/) . This enables applications to access a Virtuoso server using OLE DB interfaces. VIRTOLEDB provides implementation for all required and many optional OLE DB interfaces.
https://docs.openlinksw.com/virtuoso/qsoledb/ 