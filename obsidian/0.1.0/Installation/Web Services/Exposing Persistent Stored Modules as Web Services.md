https://docs.openlinksw.com/virtuoso/qstexpwsmodules/
## 3.7. Exposing Persistent Stored Modules as Web Services

Virtuoso SQL stored procedures and functions can be exposed as SOAP services very simply from Virtuoso, whether they are native Virtuoso or on remote data sources. This powerful ability means that any database servers already existing within an organization can easily become a component in an eBusiness solution using Virtuoso. All you need is a few simple steps that typically take mere minutes to complete:

- **Choose your stored procedure(s).**  The procedures that you want to expose can either be native Virtuoso stored procedures, or remote stored procedures that can be linked in using the Remote Procedures user interface.
    
- **Choose a virtual directory.**  Because SOAP services need to be exposed and accessed via HTTP a Virtuoso virtual directory must be used. Either use the existing SOAP virtual directory or create a new one.
    
- **Publish procedures to virtual directory.**  The user specified as SOAP account on the virtual directory must have execute privileges on the procedures. Use the Publish options on the virtual directory user interface.
    
- **Test the VSMX output.**  Once procedures have been published as SOAP services they are automatically described by WSDL and testable using Virtuoso's VSMX feature.
    

XML Query Templates provide a direct way to store SQL in an XML file on the Virtuoso server that when executed, i.e. fetched from a web browser, actually returns the results of the query.

The C Interface chapter describes how users can define custom built-in functions, from C or other programming languages, that can be used from within Virtuoso PL. This also means that VSE's can also be published as a Web Service!