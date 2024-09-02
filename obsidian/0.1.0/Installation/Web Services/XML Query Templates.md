https://docs.openlinksw.com/virtuoso/qstxmlqtemplates/
### 3.7.2. XML Query Templates

Virtuoso XML templates allow execution of SQL/XML queries over HTTP to obtain an XML document in response and/or perform some operation in the database using [updategrams](https://docs.openlinksw.com/virtuoso/updategrams/) . XML templates can be executed from within Virtuoso procedure language using the [`xml_template()`](https://docs.openlinksw.com/virtuoso/fn_xml_template/) function. XML templates support two types of action: SQL based or updategram based. SQL query based templates must contain the FOR XML clause used in a SELECT statement and hence cannot update the database. Updates to the database can only occur from an updategram. The XML document returned from calling an XML template can be served either raw, or transformed using XSLT.

XML templates provide quick easy access to results from a SQL query as usual, but now this can be saved to a file. The results are not saved, just the query definition. You can use this feature to rapidly produce dynamic reports that can potentially be rendered in different ways by providing an alternate stylesheet. The report can be refined on the fly by providing parameters for the query. The output is reachable via HTTP directly by providing the URL to the template.

|   |   |
|---|---|
|![[Tip]](https://docs.openlinksw.com/virtuoso/qstxmlqtemplates/images/tip.png)|See Also:|
|The [XML Templates](https://docs.openlinksw.com/virtuoso/xmltemplates/) Section|

XML Templates can also be published just like normal store procedures. This is achieved by using a PL wrapper around the XML template. Then the store procedure is published in the normal way.

Stylesheets transformations with be inactive for published XML templates invoked from SOAP.

|   |   |
|---|---|
|![[Tip]](https://docs.openlinksw.com/virtuoso/qstxmlqtemplates/images/tip.png)|See Also:|
|The Publishing Stored Procedures Section above for a further description of publishing XML Templates.|