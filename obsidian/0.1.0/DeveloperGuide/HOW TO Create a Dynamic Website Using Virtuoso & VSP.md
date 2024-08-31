HOWTO: Create a Dynamic Website Using Virtuoso & VSP

|   |
|---|
|Difficulty Level: Beginner|
|SUMMARY: **As organizations move towards a semantic web, everyone's looking for ingenious ways of providing customers with disparate types of information. What would help is if a customer could consume this information without the need to navigate the website, containing items of interest, every time the site is updated with something new. The Virtuoso product set delivers several methods in its promise to deliver simple but effective solutions, which can allow the consumption or delivery of content that will propel any organisation regardless of size.**|
|Related Articles & Attachments<br><br>o **[Generating RSS Using Virtuoso and SQL/XML](https://www.openlinksw.com/articles/webvirtvsp/rssvirtsqlx.htm)**|

With XML's versatility and simplicity, we have a neutral way of consuming content regardless of platform. One such area that has benefited greatly from XML is the syndication of data content, commonly known as Website Syndication

In this series of papers, we'll explore how OpenLink Software utilizes Website Syndication. OpenLink Software, through the use of syndication, publishes information relating to new customer downloads, customer support tracking etc… This means information is always readily available. Furthermore by making this information dynamic, human intervention is kept to a minimum.

This paper will focus on one method of Syndication, RSS (**R**eally **S**imple **S**yndication). RSS is currently at version 2.0 with imminent changes in the [pipeline](http://www.eweek.com/article2/0,4149,1307748,00.asp "???????????????????????????_???????????"). Currently, the two most popular versions are 2.0 and 0.91, which we will be using in this project.

This article will not focus on RSS, but instead the various ways Virtuoso can be used to produce RSS content. The assumption is the reader is aware of the technology.

One certainty is organizations understand the importance of making information readily available. With XML, we are simplifying the process by which organizations can achieve this. Syndication is not new; websites such as Moreover have long realized the importance of this.

For this project, we will use a real-time scenario. Within OpenLink Software, as new Articles and Press-Releases become available they are stored online for users to consume through HTML or PDF. Therein lies the problem: unless a customer visits the website, they are unlikely to know about any new information. Furthermore, with the widespread nuisance that is spam, emails are no longer an effective method when disseminating data across organizations.

RSS provides us with a mechanism whereby, customers are kept informed when new publications and announcements are made available for public consumption. More importantly there isn't a requirement to navigate our website via a web browser. This is all made possible by the use of News Aggregators which provide a non-intrusive approach. In other words, you only subscribe to news information you're interested in. All part of what makes the Semantic web so appealing.

In the first part of this series we will look at creating a Database driven website using Virtuoso and its Procedure Language VSP. Any programmer familiar with Perl, PHP, C or Basic will soon be able to see the simplicity of this language and be able to deploy the same data-driven websites in far less time with far less code as we will see shortly. This process is composed of four stages:

i. Create Tables

ii. Create Virtual Directory

iii. Creating the User Interfaces

iv. Adding Markup

**Please Note: This paper is not a how to on programming with the Virtuoso Procedural language, VSP. If you are interested in learning more about vsp, please take advantage of some excellent resources available via either [http://docs.openlinksw.com](http://docs.openlinksw.com/) or our online tutorial [http://demo.openlinksw.com](http://demo.openlinksw.com/)**

### Stage 1: Creating the Database Tables

The first stage is to create the tables we will use to store our information on the Feeds. There are 5 tables in total.

1. **Item** – Contains the list of items that will be used to store the feeds.

2. **Channel** – Contains a list of template Channels.

3. **Subject** – Optional: Used to group individual articles by their subjects.

4. **Category** – Optional: Categorizes the different articles.

5. **Author** – As there are several authors, we use this table to store the list.

There are two ways of creating tables

o Open an instance of the Virtuoso Admin Assistant by referencing in your browser [http://localhost:8890/](http://localhost:8890/ "???????????????????????????_???????????") if the Demo instance is being used. Select the Interactive SQL option from the menu:

Administration –> Query Tools –> Relational Data using SQL

|   |
|---|
|Figure 1. Interactive SQL screen showing SQL statement to be executed|
|![SQL](https://www.openlinksw.com/images/web_fig1.gif)|

o An alternative method is the OpenLink Interactive SQL tool, isql, which can run files with .sql extensions provided a list suitable of sql statements exist within it. This tool is located in the binary directory of your Virtuoso Installation. On running this application, you issue the command (load tablecreate.sql;), provided the file is in the same directory that you are running the isql tool from.

|   |   |
|---|---|
|TIP|_Please see attached **[zip](https://www.openlinksw.com/articles/webvirtvsp/tblcreate.zip)** file for the tablecreate.sql file. This contains the table schemas and_ batch insert statements used to populate the Category, Subject and Authors tables amongst others.<br><br>In the create table statement, **rss..tablename**: where “**rss**” is the name of the database. This databse will be dynamically created when we run our 1st create statement. Database names are case sensitive.|

On creating the tables, we now have our repository. The next stage is to create the Virtual directory.

### 

### Stage 2: Creating the Virtual Directory

Before Virtuoso can host a Web page, we must first create a Virtual Directory within Virtuoso. This will be used to store any dynamic web pages (VSP) or plain HTML pages. Virtuoso provides its own Web Server so this makes its a simple task.

From the Admin Assistant menu select:

1. **Administrator -> Internet Domains –> HTTP Virtual Directories**

2. Select **“Edit URL Mappings”**

3. Add **Virtual Directory**

4. As the files will be stored on the local file system, select **File System** as the template to use

5. The only requirement for this page is that, values are added for both Logical and Physical path options. The rest can use default values.  
The **Logical Path** will be the web url. In this case, /rssfeeds. The **Physical Path** is the local filesystem directory that contains the files to be used.  
If a default home page exists, enter it here.

6. Select **“Add”**.  

|   |
|---|
|Figure 2: Virtual Directory page showing Logical and Physical Path values|
|![SQL](https://www.openlinksw.com/images/web_fig2.gif)|

### Stage 3: Creating the User Interfaces

At this stage, we will create the user interfaces which will be the entry points for adding data into the system.

There are three interfaces used in this project.

· index.htm - Main entry point.

· channel.vsp - Used to populate the Channel table

· item.vsp - Used to populate the Item table

|   |
|---|
|Figure 3: Main data entry screen for adding values to Channel Table|
|![SQL](https://www.openlinksw.com/images/web_figure3.gif)|

This page has a dual functionality. Firstly, we can select which RSS version will be used. As mentioned earlier, this system will provide support for both version 2.0 and 0.91. The default version is 2.0. Further developments on this system can cater for future RSS versions.

|   |   |
|---|---|
|TIP|_Not all RSS elements have been included. To add any new fields, simply edit the Channel table with an “Alter” statement and add the necessary columns then edit this this page to reflect your new changes._|

All mandatory channel elements are listed on the page plus optional elements. It is important to note that, as this page caters for version 2.0 and 0.91, not all channels listed will be supported by version 0.91.

  

In **Figure 4** we can see a sample of the Items page. In this page, we've introduced some more controls, i.e drop-down (combo) boxes. These boxes are dyncamically driven. Their underlying content is derived from data stored in the remote tables, Author, Category and Subject. This is by virtue of the foreign key constraints in the Item table

|   |
|---|
|Figure 4: Main interface for adding new Item feeds|
|![SQL](https://www.openlinksw.com/images/web_figure4.gif)|

On completion, we will add some VSP code to make these pages dynamic.

### Stage 4: Adding Markup

It is important to understand the function of the Virtuoso Server Pages subsystem. This is an integral part of the Virtuoso server. It is normally enabled, so that Virtuoso listens at a configurable port for incoming HTTP requests. Virtuoso can thus act as a generic Web server, either serving static content from the file system or WebDAV, or dynamic content generated by executing SQL and stored procedure code embedded into (HTML or XML) in VSP documents.

Using Virtuoso PL (Procedure Language), we can create very dynamic pages which have the added advantage of being compiled immediatelyupon execution. This means the web pages are stored in memory similar to an application, and this allows for faster execution.

|   |   |
|---|---|
|TIP|All VSP specific markup is represented as a processing instruction ().<br><br><?vsp … ?><br><br>This markup introduces Virtuoso PL code to a VSP page, which otherwise may normally contain HTML markup. Therefore, it is possible to mix Virtuoso PL code with HTML or XML to provide rich and dynamic sites.|

In **Figures 5-7**, we show how vsp code has been added to channel.vsp to make the pages dynamic. We initially declare variables along with their associated datatypes. If the datatype is unknown, we can stipulate a catch all of **any**. We populate these variables with parameter values using the Virtuoso function **get_keyword**. These in turn are passed to an insert statement to add to our database.

|   |
|---|
|Figure 5: Variable declarations and datatypes|
|<?vsp  <br>declare _rssver , _title, _link, _desc, _lang, _copy, _manage, _webm, _pubdate, _catid, _cat, _gen varchar;|

|   |
|---|
|Figure 6: **get_keyword:** performs a case sensitive search for the occurrence of a keyword on a page. If found, it returns the element following the occurrence of the keyword. If not found it returns the default argument or NULL if the default is not supplied.|
|_rssver := get_keyword('rssver', params, '');<br><br>_title := get_keyword('chtxt_title', params, '');<br><br>_link := get_keyword('chtxt_link', params, '');<br><br>_desc := get_keyword('chtxt_desc', params, '');<br><br>_lang:= get_keyword('chtxt_lang', params, '');<br><br>_copy := get_keyword('ichxt_copy', params, '');<br><br>_manage := get_keyword('chtxt_manage', params, '');<br><br>_webm := get_keyword('chtxt_webm', params, '');<br><br>_pubdate := get_keyword('chtxt_pubdate', params, '');<br><br>_gen := 'Virtuoso Universal Server';|

|   |
|---|
|Figure 7: **The Insert statement**. When the Submit button is pressed, it checks for a keyword value of “Add New Channel”, if this exists, it will run the insert statement|
|if ({?'Submit'} = 'ADD New Channel')<br><br>{insert into rss..channel<br><br>(rssversion, chantitle , chanlink, chandesc , chanlang , chancopy , chanmanager , chanwebmaster, chanpubdate , changen )<br><br>values<br><br>(_rssver, _title , _link , _desc , _lang , _copy, _manage, _webm, (now()), _gen); }?>|

|   |   |
|---|---|
|TIP|In the code sample, the HTML has been removed for clarity, the placeholders get their values from parameters sent by the form controls (input box, select etc...) when the Submit button is pressed.|

|   |
|---|
|Figure 8: Code implementation in item.vsp|
|<?vsp<br><br>declare _itmTitle , _itmlink , _itmdesc , _itmauth , _itmcat , _itmsub varchar;<br><br>declare _itmcomm, _itmpubdate, _itmchanid varchar;<br><br>_itmTitle := get_keyword('ittxt_title', params, '');<br><br>_itmlink := get_keyword('ittxt_link', params, '');<br><br>_itmdesc := get_keyword('ittxt_desc', params, '');<br><br>_itmauth := get_keyword('ittxt_auth', params, '');<br><br>_itmcat := get_keyword('ittxt_cat', params, '');<br><br>_itmsub := get_keyword('ittxt_sub', params, '');<br><br>_itmcomm := get_keyword('ittxt_comm', params, '');<br><br>_itmpubdate := get_keyword('ittxt_pubdate', params, '');<br><br>_itmchanid := get_keyword('ittxt_chanid', params, '');<br><br>if ({?'Submit'} = 'Submit Item for RSS')<br><br>{insert into rss..item (itemtitle , itemlink , itemdesc, itemauth , itemcat , itemsub , itemcomm, itempubdate , itemchanid)<br><br>values<br><br>(_itmTitle , _itmlink , _itmdesc, atoi({?'ittxt_auth'}), atoi({?'ittxt_cat'}), atoi({?'ittxt_sub'}), _itmcomm, _itmpubdate , _itmchanid);<br><br>}?>|

The main difference between the channel and item pages is the introduction of select (combo/drop-down) boxes and vsp code interspersed with html.

|   |
|---|
|Figure 9: This shows the Select control been populated with the contents of the Subject table. We store the Subjectid value under the covers, this will be stored in the Item table, and show the Subject Name in the control. We also make use the SQL-92 functions **atoi** and **cast**|
|<TR><br><br><TD><FONT size="2">Category</FONT></TD><br><br><TD><select name="ittxt_sub" size="1"><br><br><?vsp for(select subid, subname from rss..subject order by 2) do ?><br><br><option value="<?= subid?>" <?= (_itmsub, cast(subid as varchar))?>> <?=subname?></option> <?vsp ?> </select></TD> <TD>(2.0/0.91)</FONT></TD></TR>|

On completion, we are now ready to insert new records. Your Item page should resemble the page below. The Select controls, with the exception of the Channel control, have been populated with records. The Channel drop-down will only be populated when we enter new values into our channel table via the channel.vsp interface.

|   |
|---|
|Figure 10: Finished Item page showing data populated Drop-down boxes|
|![SQL](https://www.openlinksw.com/images/web_figure10.gif)|

### Conclusion:

This article has provided an insight into Virtuoso's ability to act as a powerful yet simplistic tool for creating Dynamic data-driven website. This has been made possible by the use of VSP.  
  
To conclude this stage, we've laid the framework for producing RSS content by creating the backbone of the project. We've introduced the Virtuoso Procedural language, VSP, and shown a method that can be used for inserting and retrieving records. We've also seen how VSP interacts with HTML to produce data-driven web pages. To simplify the process of creating dynamic pages, we've merely introduced some of the capabilities of VSP. This is intentional and for those looking to develop more complex systems or interested in learning more about Virtuoso's Procedural Language, the resources outlined earlier are available both online and as RSS feeds.  
  
On completing this stage, we are in a position to delve deeper into Virtuoso VSP and show how we can generate RSS content using some of the tools Virtuoso provides. The next series of papers on RSS will use the VSP pages (Channel and Item) as well as the database tables and contents we've just created. They will act as the backdrop for the remainder of this project. The next stage of this project will focus on the different methods that Virtuoso can use to generate RSS content, firstly by generating XML content and then formatting the XML resultset into a format that provides RSS feeds. The different methods we will explore are:

Virtuoso VSP

SQLX

SCHEMA MAPPING

FOR XML