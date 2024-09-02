https://docs.openlinksw.com/virtuoso/qstexpwspls/

### 3.7.1. Publishing Stored Procedures as Web Services

[¶](https://docs.openlinksw.com/virtuoso/qstexpwspls/#qstexpwssps)

#### Choosing Stored Procedures to Expose

You can either expose native Virtuoso stored procedures (previously defined or newly created) using the CREATE PROCEDURE statement, or stored procedures from other database types can be linked into Virtuoso using an ODBC datasource.

Virtuoso lists available stored procedures for each catalog in Conductor under: _/Database/External Data Sources/External Linked Objects / with checked "Stored Procedures"_ .

To link a stored procedure from another database system we must first create a valid data source that leads to a connection to that database. Once verified proceed to the Remote Procedures page. Select the "Link objects" link for a data source.

**Figure 3.38. Linking Procedures from Remote Data Sources**

![Linking Procedures from Remote Data Sources](https://docs.openlinksw.com/virtuoso/qstexpwspls/images/ui/admrmtprocs001.png)

  

Select the check-box "Store Procedures". Click the "Apply" button. As result will be shown the list of available procedures.

**Figure 3.39. Linking Procedures from Remote Datasources**

![Linking Procedures from Remote Datasources](https://docs.openlinksw.com/virtuoso/qstexpwspls/images/ui/admrmtprocs002.png)

  

Select the check-boxes for the procedures you want to link and click the "Link" button.

**Figure 3.40. Linking Procedures from Remote Datasources**

![Linking Procedures from Remote Datasources](https://docs.openlinksw.com/virtuoso/qstexpwspls/images/ui/admrmtprocs003.png)

  

You will be presented with a new page listing the chosen procedures and their data type information. This gives you an opportunity to alter the data type mappings that Virtuoso will use both internally and for any future interactions with the SOAP server. If you do not want to specify any special type information the details can be left as default.

**Figure 3.41. Linking Procedures from Remote Datasources**

![Linking Procedures from Remote Datasources](https://docs.openlinksw.com/virtuoso/qstexpwspls/images/ui/admrmtprocs004.png)

  

For each remote procedure you may change how they will be referenced within Virtuoso by making changes to the fields for _Catalog_ , _Owner_ , _Link as_ , and _Description_ fields. These fields define how you will find the linked procedure locally to Virtuoso only and do not affect the remote data source.

For each procedure there is an option to _PL Wrapper Requirement_ . This option is required if your remote procedure is capable of returning a resultset that you want to process via Virtuoso. Can be _SOAP Execution_ , _SQL Execution_ or _None_ . Also you can specify _Return Type_ , _Data Type_ , _SOAP Type_ .

Once the details are correct press the "Link" button.

|   |   |
|---|---|
|![[Tip]](https://docs.openlinksw.com/virtuoso/qstexpwspls/images/tip.png)|See Also:|
|[Linking Remote Procedures](https://docs.openlinksw.com/virtuoso/dbadmin/)|

[¶](https://docs.openlinksw.com/virtuoso/qstexpwspls/#qstexpwsvirtdir)

#### Defining Virtual Directories

Before any procedures native or linked can be exposed as SOAP Services a location in HTTP space must be defined. From Conductor _Web Application Server/Virtual Domains & Directories_ you make a new URL Mappings. Click on the _New Directory_ link for the {Default Web Site} line to begin defining a new SOAP mapping.

**Figure 3.42. Virtual Directories**

![Virtual Directories](https://docs.openlinksw.com/virtuoso/qstexpwspls/images/ui/admvirtdir001.png)

  

Select for "Type" from the list the value "SOAP access point" and click the "Next" button.

**Figure 3.43. Virtual Directories Mappings**

![Virtual Directories Mappings](https://docs.openlinksw.com/virtuoso/qstexpwspls/images/ui/admvirtdir003.png)

  

You will then be presented with the following tabs: "Virtual Directory Information", "Authentication", "Web Service Option", "WS Security" and "Publish Objects". Particular options to note are "Virtual Directory Information" and "Publish Objects".

**Figure 3.44. Virtual Directories**

![Virtual Directories](https://docs.openlinksw.com/virtuoso/qstexpwspls/images/ui/admvirtdir004.png)

  

In _Publish Objects_ you can select Virtuoso stored procedures, or remotely linked procedures to be published as SOAP web services. Also you can publish Pl Modules, User Defined Types, or Saved Queries.

**Figure 3.45. Publish Objects**

![Publish Objects](https://docs.openlinksw.com/virtuoso/qstexpwspls/images/ui/admvirtdir005.png)

  

|   |   |
|---|---|
|![[Tip]](https://docs.openlinksw.com/virtuoso/qstexpwspls/images/tip.png)|See Also:|
|[Virtual Directories](https://docs.openlinksw.com/virtuoso/admui.internetdomains/)|

[¶](https://docs.openlinksw.com/virtuoso/qstexpwspls/#qstexpspublishbtn)

#### Publishing Procedures to a Virtual Directory

If you already have a virtual directory defined and know what procedures you want to expose as web services you will have to repeat some of the steps in the section above. From Conductor go to _Web Application Server/Virtual Domains & Directories_ . Click on the "folder" icon for your {Default Web Site}. You will find the list of previously existing mappings, from which you can select the mapping that you want to edit by pressing on its _Edit_ link. Note, the virtual directory should have type "SOAP".

**Figure 3.46. Virtual Directories**

![Virtual Directories](https://docs.openlinksw.com/virtuoso/qstexpwspls/images/ui/admvirtdir006.png)

  

Go to tab "publish Objects" to expose/hide your procedures, Pl Modules, User Defined Types and Saved Queries.

**Figure 3.47. Publish Objects**

![Publish Objects](https://docs.openlinksw.com/virtuoso/qstexpwspls/images/ui/admvirtdir008.png)

  

The "Procedures" tab presents the list of available procedures. You can select a catalogue in order to list the procedures you want to publish. When the procedures to be published are selected, you can either click the "Publish Selected" button, or before this to click the "Edit Description" button.

**Figure 3.48. Choosing Procedure aPublish**

![Choosing Procedure aPublish](https://docs.openlinksw.com/virtuoso/qstexpwspls/images/ui/admvirtdir007.png)

  

[¶](https://docs.openlinksw.com/virtuoso/qstexpwspls/#qstexpsvsmxtest)

#### Testing SOAP Services Using VSMX

Virtual directory definitions have a _Logical Path_ field, which is reference in URL to find the correct SOAP services. If you connect to Virtuoso on _http://example.com:8890/_ , and defined your virtual directory with the logical path of _/mysoap_ then you will be able to test the following URLs:

|   |
|---|
|http://example.com:8890/mysoap/services.wsdl|
|http://example.com:8890/mysoap/services.vsmx|

**Figure 3.49. Services.wsdl**

![Services.wsdl](https://docs.openlinksw.com/virtuoso/qstexpwspls/images/ui/admvirtdir009.png)

  

**Figure 3.50. Services.vsmx**

![Services.vsmx](https://docs.openlinksw.com/virtuoso/qstexpwspls/images/ui/admvirtdir010.png)

  

The WSDL description is a standards-based description of the Web Services available from /mysoap. The VSMX page is a Virtuoso generated test page allowing you to test SOAP services. This feature should improve your development time.