https://docs.openlinksw.com/virtuoso/qsforxmlmodes/
### 3.9.1. FOR XML Execution Modes

Now we will consider the programmatical approach along side the visual interface approach. We will have one example of each of the modes of FOR XML combined with the [`xml_auto()`](https://docs.openlinksw.com/virtuoso/fn_xml_auto/) function to help us display the results simply.

For the programmatical examples to run smoothly using ISQL a number of steps are required to obtain textual output from the xml_auto() function which usually is expected to output directly to an HTTP target. To make the demonstration simpler a utility procedure will be created that will simply enable us to supply SQL and return XML using the [`xml_auto()`](https://docs.openlinksw.com/virtuoso/fn_xml_auto/) function.

create procedure xmla (in q varchar)
{
  declare st any;
  st := string_output ();
  xml_auto (q, vector (), st);
  result_names (q);
  result (string_output_string (st));
}

- _RAW_ mode produces an XML entity from each row of the result set, and does not attempt to construct hierarchies. Each row's data is enclosed in a ROW element and each column is either an attribute or child element.
    
    **Figure 3.55. SQL to XML using FOR XML RAW mode**
    
    ![SQL to XML using FOR XML RAW mode](https://docs.openlinksw.com/virtuoso/qsforxmlmodes/images/ui/qssql2xml103.png)
    
      
    
    The same SQL statement containing the FOR XML syntax is used in the visual interface shown above, and in the programmatical version shown below. This is because both use the xml_auto() function for generating results. In the visual interface once the settings and query have been confirmed you press the "Execute" button to store the query in the specified DAV location.
    
    xmla ('select "category"."CategoryID", "CategoryName",
        "ProductName", "ProductID"
        from "Demo".."Categories" "category", "Demo".."Products" as "product"
        where "product"."CategoryID" = "category"."CategoryID" FOR XML RAW');
    
    |   |   |
    |---|---|
    |![[Note]](https://docs.openlinksw.com/virtuoso/qsforxmlmodes/images/note.png)|Note:|
    |The xmla function is not a standard function but quick utility for quickly rendering a text output for the [`xml_auto()`](https://docs.openlinksw.com/virtuoso/fn_xml_auto/) function. The definition is at the top of this section|
    
    The resulting XML from either ISQL or the saved links on the visual interface will yield:
    
    <ROW CategoryID="1" CategoryName="Beverages" ProductName="Chai" ProductID="1">
    </ROW>
    <ROW CategoryID="1" CategoryName="Beverages" ProductName="Chang" ProductID="2">
    </ROW>
    <ROW CategoryID="1" CategoryName="Beverages" ProductName="Guaran Fantastica" ProductID="24">
    </ROW>
    <ROW CategoryID="1" CategoryName="Beverages" ProductName="Sasquatch Ale" ProductID="34">
    </ROW>
    <ROW CategoryID="1" CategoryName="Beverages" ProductName="Steeleye Stout" ProductID="35">
    </ROW>
    <ROW CategoryID="1" CategoryName="Beverages" ProductName="C(te de Blaye" ProductID="38">
    </ROW>
    <ROW CategoryID="1" CategoryName="Beverages" ProductName="Chartreuse verte" ProductID="39">
    </ROW>
    <ROW CategoryID="1" CategoryName="Beverages" ProductName="Ipoh Coffee" ProductID="43">
    </ROW>
    .....
    
- _AUTO_ mode. A hierarchy is constructed with one level for each table of the join for which at least one column is selected. The table whose column is first mentioned in the selection will be the topmost element, the next table its child etc. Each level of the tree will consist of one type of element. A parent element will have multiple children if consecutive rows do not differ in the column values coming from the parent element. When a table's column values differ from the previous row, the element and all children thereof are closed and a new element is started, with children filled out from other columns of the result set.
    
    **Figure 3.56. SQL to XML using FOR XML AUTO mode**
    
    ![SQL to XML using FOR XML AUTO mode](https://docs.openlinksw.com/virtuoso/qsforxmlmodes/images/ui/qssql2xml102.png)
    
      
    
    The same SQL statement containing the FOR XML syntax is used in the visual interface shown above, and in the programmatical version shown below. This is because both use the xml_auto() function for generating results. In the visual interface once the settings and query have been confirmed you press the execute button to store the query in the specified DAV location.
    
    xmla ('select "category"."CategoryID", "CategoryName",
        "ProductName", "ProductID"
        from "Demo".."Categories" "category", "Demo".."Products" as "product"
        where "product"."CategoryID" = "category"."CategoryID" FOR XML AUTO');
    
    |   |   |
    |---|---|
    |![[Note]](https://docs.openlinksw.com/virtuoso/qsforxmlmodes/images/note.png)|Note:|
    |The xmla function is not a standard function but quick utility for quickly rendering a text output for the [`xml_auto()`](https://docs.openlinksw.com/virtuoso/fn_xml_auto/) function. The definition is at the top of this section|
    
    The resulting XML from either ISQL or the saved links on the visual interface will yield:
    
    <category CategoryID="1" CategoryName="Beverages">
    <product ProductName="Chai" ProductID="1">
    </product>
    <product ProductName="Chang" ProductID="2">
    </product>
    <product ProductName="Guaranß Fantßstica" ProductID="24">
    </product>
    <product ProductName="Sasquatch Ale" ProductID="34">
    </product>
    <product ProductName="Steeleye Stout" ProductID="35">
    </product>
    <product ProductName="C(te de Blaye" ProductID="38">
    </product>
    <product ProductName="Chartreuse verte" ProductID="39">
    </product>
    <product ProductName="Ipoh Coffee" ProductID="43">
    </product>
    <product ProductName="Laughing Lumberjack Lager" ProductID="67">
    </product>
    .....
    
    |   |   |
    |---|---|
    |![[Note]](https://docs.openlinksw.com/virtuoso/qsforxmlmodes/images/note.png)|Note:|
    |In contrast to the RAW mode AUTO produces results that are more reasonable and intuitive. Only one category element is used for each category which contains all the children of that category.|
    
- _EXPLICIT_ mode gives more control on the resulting tree's structure while requiring a more elaborate query structure. In this mode, the query will be a UNION ALL of many joins and each row will specify exactly one element. Which type of element this is and where in the tree it will be placed are determined by the values of the 2 first columns, TAG and PARENT.
    
    **Figure 3.57. SQL to XML using FOR XML EXPLICIT mode**
    
    ![SQL to XML using FOR XML EXPLICIT mode](https://docs.openlinksw.com/virtuoso/qsforxmlmodes/images/ui/qssql2xml101.png)
    
      
    
    The same SQL statement containing the FOR XML syntax is used in the visual interface shown above, and in the programmatical version shown below. This is because both use the xml_auto() function for generating results. In the visual interface once the settings and query have been confirmed you press the execute button to store the query in the specified DAV location.
    
    xmla ('
    select 1 as tag, null as parent,
           "CategoryID" as [category!1!cid],
           "CategoryName" as [category!1!name],
           NULL as [product!2!pid],
           NULL as [product!2!name!element]
    from "Demo".."Categories"
    union all
    select 2, 1, "category" ."CategoryID", NULL, "ProductID", "ProductName"
        from "Demo".."Categories" "category", "Demo".."Products" as "product"
        where "product"."CategoryID" = "category"."CategoryID"
    order by [category!1!cid], 5
    FOR XML EXPLICIT');
    
    |   |   |
    |---|---|
    |![[Note]](https://docs.openlinksw.com/virtuoso/qsforxmlmodes/images/note.png)|Note:|
    |The xmla function is not a standard function but quick utility for quickly rendering a text output for the [`xml_auto()`](https://docs.openlinksw.com/virtuoso/fn_xml_auto/) function. The definition is at the top of this section|
    
    The resulting XML from either ISQL or the saved links on the visual interface will yield:
    
    <CATEGORY CID="1" NAME="Beverages">
    <PRODUCT PID="1">
     <NAME>Chai</NAME></PRODUCT>
    <PRODUCT PID="2">
     <NAME>Chang</NAME></PRODUCT>
    <PRODUCT PID="24">
     <NAME>Guaran&#225; Fant&#225;stica</NAME></PRODUCT>
    <PRODUCT PID="34">
     <NAME>Sasquatch Ale</NAME></PRODUCT>
    <PRODUCT PID="35">
     <NAME>Steeleye Stout</NAME></PRODUCT>
    <PRODUCT PID="38">
     <NAME>C&#244;te de Blaye</NAME></PRODUCT>
    <PRODUCT PID="39">
     <NAME>Chartreuse verte</NAME></PRODUCT>
    <PRODUCT PID="43">
     <NAME>Ipoh Coffee</NAME></PRODUCT>
    <PRODUCT PID="67">
     <NAME>Laughing Lumberjack Lager</NAME></PRODUCT>
    <PRODUCT PID="70">
     <NAME>Outback Lager</NAME></PRODUCT>
    <PRODUCT PID="75">
     <NAME>Rh&#246;nbr&#228;u Klosterbier</NAME></PRODUCT>
    <PRODUCT PID="76">
     <NAME>Lakkalik&#246;&#246;ri</NAME></PRODUCT>
    </CATEGORY>
    <CATEGORY CID="2" NAME="Condiments">
    <PRODUCT PID="3">
    .....
    
    |   |   |
    |---|---|
    |![[Note]](https://docs.openlinksw.com/virtuoso/qsforxmlmodes/images/note.png)|Note:|
    |In contrast again, the EXPLICIT mode produces exactly what we asked for.|
    

For more details about 'FOR XML, refer to [Rendering SQL Queries as XML](https://docs.openlinksw.com/virtuoso/forxmlforsql/) section of the XML Support chapter.