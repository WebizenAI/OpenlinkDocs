https://docs.openlinksw.com/virtuoso/qssqltoxml/

## 3.9. SQL to XML

Virtuoso enables you to develop eBusiness solutions that use XML as both a Data Source and Data Interchange format. Your XML Data documents can take the form of Pure XML Documents, or documents that are transformed from SQL-XML on the fly. By supporting the XPATH query language for XML Data, you are able to use an industry standard query language to query entire XML Documents or portions of XML Documents stored within Virtuoso. Virtuoso's inclusion of an XSLT transformation engine then allow you to transform XML data for other needs. These XML documents are openly accessible to user agents such as Web Browsers via HTTP and/or WebDAV. These XML documents are described as being dynamic because they have varying degrees of sensitivity to changes that occur in the underlying database tables from which the XML data originates. Virtuoso allows you to create two types of XML documents from homogeneous or heterogeneous SQL Data on the fly:

|   |
|---|
|_Transient_ The materialization of the XML Document occurs at the time of file opening, this implies that data from the original SQL database(s) is retrieved and then transformed into XML in one operation. This format of SQL-XML document is highly sensitive to source database(s) changes.|
|_Persistent (Time Synchronized)_ - The materialization of the XML Document re-occurs at a user configurable interval after initial creation. This is a caching scheme which is less sensitive to changes in the source databases(s) in favor of performance.|

SQL-XML documents may be Valid or Well Formed XML documents, this includes support for both DTDs and XML Schemas which my be external entity references or inlined within the XML Documents prologue in the case of DTDs.

Virtuoso supports an extended SQL syntax that is identical to that implemented by Microsoft SQL Server for the purpose of creating SQL-XML documents. These SQL extensions take the form of a new "FOR XML" clause that includes three main options which control the structure of the resulting XML document tree. These options are _RAW_ , _AUTO_ and _EXPLICIT_ .

Virtuoso's HTML based graphical interface includes a user friendly mechanism for creating dynamic XML documents from SQL data using the "FOR XML" extended SQL syntax. The dynamic XML documents created by this process are typically stored in Virtuoso's WebDAV repository. Documents stored in this repository are accessible by any XML consuming client application via HTTP, Windows Web Folders, or any other WebDAV or HTTP compliant environment. A description of the interface in general can be found in the [SQL-XML Statements](https://docs.openlinksw.com/virtuoso/admui.xmlservices/) in the Visual Server Administration Interface section.

From Conductor _XML/SQL_XML_ you can execute SQL query with options on how to produce XML structures from the results.

**Figure 3.52. SQL to XML**

![SQL to XML](https://docs.openlinksw.com/virtuoso/qssqltoxml/images/ui/qssql2xml001.png)

  

The illustration above depicts the fact that only minor changes to standard SQL are required in order to create powerful dynamic XML documents from SQL. It also illustrates how the entire process of controlling the type and format of the XML documents and their actually WebDAV storage is all achieved without any programming. The XML document extract below is a depiction of the XML document tree produced using the "FOR XML" AUTO option.

**Figure 3.53. SQL to XML results**

![SQL to XML results](https://docs.openlinksw.com/virtuoso/qssqltoxml/images/ui/qssql2xml002.png)

  

The Virtuoso Demo database provides a set of sample tables in the Demo catalogue, and some sample XML views that use them. The "StoredQueries" tab lists saved XML Views as shown below.

**Figure 3.54. SQL to XML save views**

![SQL to XML save views](https://docs.openlinksw.com/virtuoso/qssqltoxml/images/ui/qssql2xml003.png)

  

You can press _Edit_ to edit them, or _Delete_ to remove them or click on the XML FILE itself to see the results in your default browser, a sample of the output is shown above.