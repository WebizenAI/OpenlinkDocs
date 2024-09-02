# Chapter 16. RDF Data Access and Data Management

**Abstract**

Starting with version 4.5, Virtuoso provides built-in support for SPARQL, the standard query language for RDF and the semantic web. Adoption of SPARQL with Virtuoso is effortless, as any existing SQL client applications and stored procedures can take advantage of SPARQL simply by using it in the place of or inside SQL queries. Additionally, Virtuoso offers the standard SPARQL protocol to HTTP clients. From version 5.0.7, Virtuoso can be used as the RDF store/query processor of the Jena and Sesame RDF frameworks.

This chapter discusses Virtuoso's RDF triple storage and query capabilities. This discusses storing RDF data as well as mapping existing relational data into RDF for SPARQL access. Numerous SPARQL language extensions and standard compliance are covered.

In this chapter SPARQL and SPASQL are used as siblings.

|   |   |
|---|---|
|![[Tip]](https://docs.openlinksw.com/virtuoso/ch-rdfandsparql/images/tip.png)|See Also:|
|- [Virtuoso ODBC RDF extensions for SPASQL](https://docs.openlinksw.com/virtuoso/odbcimplementationext/)<br>    <br>- [Geometry Data Types and Spatial Index Support](https://docs.openlinksw.com/virtuoso/sqlrefgeospatial/)|

**Table of Contents**

16.1. [Data Representation](https://docs.openlinksw.com/virtuoso/rdfdatarepresentation/)

16.1.1. [IRI_ID Type](https://docs.openlinksw.com/virtuoso/rdfiriidtype/)

16.1.2. [RDF_BOX Type](https://docs.openlinksw.com/virtuoso/rdfboxtype/)

16.1.3. [RDF_QUAD and other tables](https://docs.openlinksw.com/virtuoso/rdfquadtables/)

16.1.4. [Short, Long and SQL Values](https://docs.openlinksw.com/virtuoso/rdfsqlmodes/)

16.1.5. [Programatically resolving DB.DBA.RDF_QUAD.O to SQL](https://docs.openlinksw.com/virtuoso/rdfsqlsparqlresolve/)

16.1.6. [Special Cases and XML Schema Compatibility](https://docs.openlinksw.com/virtuoso/rdfxmlschemacompat/)

16.1.7. [SQL Compiler Support - QUIETCAST option](https://docs.openlinksw.com/virtuoso/rdfquietcast/)

16.1.8. [Dynamic Renaming of Local IRI's](https://docs.openlinksw.com/virtuoso/rdfdynamiclocal/)

16.2. [SPARQL](https://docs.openlinksw.com/virtuoso/rdfsparql/)

16.2.1. [SPARQL Implementation Details](https://docs.openlinksw.com/virtuoso/rdfsparqlimplementationextent/)

16.2.2. [Query Constructs](https://docs.openlinksw.com/virtuoso/rdfpredicatessparql/)

16.2.3. [SPARQL Web Services & APIs](https://docs.openlinksw.com/virtuoso/rdfsparqlprotocolendpoint/)

16.2.4. [Troubleshooting SPARQL Queries](https://docs.openlinksw.com/virtuoso/sparqldebug/)

16.2.5. [SPARQL Inline in SQL](https://docs.openlinksw.com/virtuoso/rdfsparqlinline/)

16.2.6. [API Functions](https://docs.openlinksw.com/virtuoso/rdfapi/)

16.2.7. [Useful Internal Functions](https://docs.openlinksw.com/virtuoso/rdfinternalfunctions/)

16.2.8. [Default and Named Graphs](https://docs.openlinksw.com/virtuoso/rdfdefaultgraph/)

16.2.9. [Calling SQL from SPARQL](https://docs.openlinksw.com/virtuoso/rdfsqlfromsparql/)

16.2.10. [SPARQL DESCRIBE](https://docs.openlinksw.com/virtuoso/rdfsqlfromsparqldescribe/)

16.2.11. [Transitivity in SPARQL](https://docs.openlinksw.com/virtuoso/rdfsparqlimplementatiotrans/)

16.2.12. [Supported SPARQL-BI "define" pragmas](https://docs.openlinksw.com/virtuoso/rdfsparqlimplementatioptragmas/)

16.2.13. [Built-in bif functions](https://docs.openlinksw.com/virtuoso/rdfsparqlbif/)

16.2.14. [Sending SOAP Requests to Virtuoso SPARQL Endpoint](https://docs.openlinksw.com/virtuoso/rdfsparqlsoap/)

16.2.15. [Use of Hash Join With RDF](https://docs.openlinksw.com/virtuoso/rdfsparqlhashjoin/)

16.3. [Extensions](https://docs.openlinksw.com/virtuoso/sparqlextensions/)

16.3.1. [Using Full Text Search in SPARQL](https://docs.openlinksw.com/virtuoso/rdfsparqlrulefulltext/)

16.3.2. [SPARUL -- an Update Language For RDF Graphs](https://docs.openlinksw.com/virtuoso/rdfsparul/)

16.3.3. [Business Intelligence Extensions for SPARQL](https://docs.openlinksw.com/virtuoso/sparqlbi/)

16.4. [RDF Graphs Security](https://docs.openlinksw.com/virtuoso/rdfgraphsecurity/)

16.4.1. [RDF Graph Groups](https://docs.openlinksw.com/virtuoso/rdfgraphsecuritygroups/)

16.4.2. [NOT FROM and NOT FROM NAMED Clauses](https://docs.openlinksw.com/virtuoso/rdfgraphsecuritynotfrom/)

16.4.3. [Graph-Level Security](https://docs.openlinksw.com/virtuoso/rdfgraphsecuritylevel/)

16.4.4. [Graph-Level Security and SQL](https://docs.openlinksw.com/virtuoso/rdfgraphsecuritylevelrow/)

16.4.5. [Understanding Default Permissions](https://docs.openlinksw.com/virtuoso/rdfgraphsecurityunddefperm/)

16.4.6. [Initial Configuration of SPARQL Security](https://docs.openlinksw.com/virtuoso/rdfgraphsecurityintconfsec/)

16.4.7. [Application Callbacks for Graph Level Security](https://docs.openlinksw.com/virtuoso/rdfgraphsecurityappcallb/)

16.4.8. [Graph-level security and sponging](https://docs.openlinksw.com/virtuoso/rdfgraphsecurityspongeprivate/)

16.5. [Linked Data Views over RDBMS Data Source](https://docs.openlinksw.com/virtuoso/rdfviewsrdbms/)

16.5.1. [Introduction](https://docs.openlinksw.com/virtuoso/rdfviewsintro/)

16.5.2. [Rationale](https://docs.openlinksw.com/virtuoso/rdfviewrationale/)

16.5.3. [Quad Map Patterns, Values and IRI Classes](https://docs.openlinksw.com/virtuoso/rdfviewquadmapatternsvalueandiriclasses/)

16.5.4. [Configuring RDF Storages](https://docs.openlinksw.com/virtuoso/rdfviewconfiguringrdfstorages/)

16.5.5. [Translation Of SPARQL Triple Patterns To Quad Map Patterns](https://docs.openlinksw.com/virtuoso/rdfviewtranslationofpatterns/)

16.5.6. [Describing Source Relational Tables](https://docs.openlinksw.com/virtuoso/rdfviewdescribingsourcerelationaltables/)

16.5.7. [Function-Based IRI Classes](https://docs.openlinksw.com/virtuoso/rdfviewiriusingfunction/)

16.5.8. [Connection Variables in IRI Classes](https://docs.openlinksw.com/virtuoso/rdfconnvarsiniriclasses/)

16.5.9. [Lookup Optimization -- BIJECTION and RETURNS Options](https://docs.openlinksw.com/virtuoso/rdfviewbijandreturns/)

16.5.10. [Join Optimization -- Declaring IRI Subclasses](https://docs.openlinksw.com/virtuoso/rdfviewsubclasses/)

16.5.11. [RDF Metadata Maintenance and Recovery](https://docs.openlinksw.com/virtuoso/rdfmetadatarecovery/)

16.5.12. [Split Linked Data View](https://docs.openlinksw.com/virtuoso/splitrdfview/)

16.5.13. [Linked Data Views and recursive FK relationships](https://docs.openlinksw.com/virtuoso/rdfviewsrcur/)

16.6. [Automated Generation of Linked Data Views over Relational Data Sources](https://docs.openlinksw.com/virtuoso/rdfrdfviewgnr/)

16.6.1. [Introduction](https://docs.openlinksw.com/virtuoso/rdfrdfviewgnrintro/)

16.6.2. [One Click Linked Data Generation & Deployment](https://docs.openlinksw.com/virtuoso/rdfrdfviewgnroneclick/)

16.6.3. [Manual Linked Data Generation & Deployment using the Conductor's HTML-based wizard](https://docs.openlinksw.com/virtuoso/rdfrdfviewgnrwizzard/)

16.6.4. [Manual Linked Data Generation & Deployment using iSQL command-line](https://docs.openlinksw.com/virtuoso/rdfrdfviewgnrisql/)

16.7. [Virtuoso R2RML Support](https://docs.openlinksw.com/virtuoso/r2rml/)

16.7.1. [What is R2RML?](https://docs.openlinksw.com/virtuoso/r2rmlwhat/)

16.7.2. [Why use it?](https://docs.openlinksw.com/virtuoso/r2rmlwhy/)

16.7.3. [How do I use it with Virtuoso?](https://docs.openlinksw.com/virtuoso/r2rmlhow/)

16.7.4. [Known Limitations](https://docs.openlinksw.com/virtuoso/r2rmlknlim/)

16.7.5. [Generating an R2RML based Linked Data View from iSQL command-line](https://docs.openlinksw.com/virtuoso/r2rmlgenlviewisql/)

16.7.6. [Virtuoso Conductor R2RML Import Wizard](https://docs.openlinksw.com/virtuoso/r2rmlcondwiz/)

16.7.7. [Generate Transient and/or Persistent Linked Data Views atop Remote Relational Data Sources Using Conductor](https://docs.openlinksw.com/virtuoso/r2rmlgentransperslviewrs/)

16.8. [Examples of Linked Data Views](https://docs.openlinksw.com/virtuoso/rdfviewsenterpr/)

16.8.1. [Simple Mapping Example -- Northwind Linked Data View](https://docs.openlinksw.com/virtuoso/rdfviewnorthwindexample1/)

16.8.2. [BSBM to RDF](https://docs.openlinksw.com/virtuoso/rdfviewsenterprbsm/)

16.8.3. [TPCH to RDF](https://docs.openlinksw.com/virtuoso/rdfviewsbusint/)

16.8.4. [TPCD to RDF](https://docs.openlinksw.com/virtuoso/rdfviewsbusinttpcd/)

16.8.5. [Thalia to RDF](https://docs.openlinksw.com/virtuoso/rdfviewsbusintthalia/)

16.8.6. [Musicbrainz to RDF](https://docs.openlinksw.com/virtuoso/rdfviewsbusintmbr/)

16.8.7. [Virtuoso ODS to RDF](https://docs.openlinksw.com/virtuoso/rdfviewsbusintods/)

16.8.8. [Sybase using demonstration 'pubs2' database](https://docs.openlinksw.com/virtuoso/rdfviewsenterprsyb/)

16.8.9. [Virtuoso's Northwind based Demo Database (Tutorials variant) to RDF](https://docs.openlinksw.com/virtuoso/rdfviewsenterprtn/)

16.8.10. [SQL Server's Northwind Demo Database](https://docs.openlinksw.com/virtuoso/rdfviewsenterprsn/)

16.8.11. [Oracle Demonstration 'HR' Database](https://docs.openlinksw.com/virtuoso/rdfviewsenterohr/)

16.8.12. [Oracle using the demonstration 'Human Resources' database](https://docs.openlinksw.com/virtuoso/rdfviewsenterprohd/)

16.8.13. [DB2 using the demonstration 'Sample' database](https://docs.openlinksw.com/virtuoso/rdfviewsenterprdb/)

16.8.14. [Informix using demonstration 'Stores' database](https://docs.openlinksw.com/virtuoso/rdfviewsenterprinf/)

16.8.15. [Ingres using demonstration 'Tutorial' database](https://docs.openlinksw.com/virtuoso/rdfviewsenterpringr/)

16.8.16. [Progress (SQL-89) using demonstration 'iSports' database](https://docs.openlinksw.com/virtuoso/rdfviewsenterprs89/)

16.8.17. [Progress (SQL-92) using demonstration 'iSports' database](https://docs.openlinksw.com/virtuoso/rdfviewsenterprs92/)

16.9. [RDF Insert Methods in Virtuoso](https://docs.openlinksw.com/virtuoso/rdfinsertmethods/)

16.9.1. [Using API functions](https://docs.openlinksw.com/virtuoso/rdfinsertmethodsapifunct/)

16.9.2. [SPARQL endpoint REST API](https://docs.openlinksw.com/virtuoso/rdfinsertmethodshttppost/)

16.9.3. [HTTP PUT using Content-Type: application/rdf+xml](https://docs.openlinksw.com/virtuoso/rdfinsertmethodshttpput/)

16.9.4. [SPARQL Insert using LOAD](https://docs.openlinksw.com/virtuoso/rdfinsertmethodsload/)

16.9.5. [SPARQL Insert via /sparql endpoint](https://docs.openlinksw.com/virtuoso/rdfindertmethodsparqlendpoint/)

16.9.6. [SPARQL Insert via SPARQL endpoint REST API and ODS wiki](https://docs.openlinksw.com/virtuoso/rdfinsertmethodsparqlqueryandodswiki/)

16.9.7. [Using WebDAV](https://docs.openlinksw.com/virtuoso/rdfinsertmethodwebdav/)

16.9.8. [Using Virtuoso Crawler](https://docs.openlinksw.com/virtuoso/rdfinsertmethodvirtuosocrawler/)

16.9.9. [Using SPARQL Query and Sponger (i.e. we Fetch the Network Resources in the FROM Clause or values for the graph-uri parameter in SPARQL protocol URLs)](https://docs.openlinksw.com/virtuoso/rdfinsertmethodsparqlqueryandsponger/)

16.9.10. [Using Virtuoso PL APIs](https://docs.openlinksw.com/virtuoso/rdfinsertmethodplapis/)

16.9.11. [Using SIMILE RDF Bank API](https://docs.openlinksw.com/virtuoso/rdfinsertmethodsimilerdfbankapi/)

16.9.12. [Using RDF NET](https://docs.openlinksw.com/virtuoso/rdfinsertmethodrdfnet/)

16.9.13. [Using the RDF Proxy (Sponger) Service](https://docs.openlinksw.com/virtuoso/rdfinsertmethodproxy/)

16.10. [RDFizer Middleware (Sponger)](https://docs.openlinksw.com/virtuoso/virtuososponger/)

16.10.1. [What Is The Sponger?](https://docs.openlinksw.com/virtuoso/virtuosospongerintro/)

16.10.2. [Why is it Important?](https://docs.openlinksw.com/virtuoso/virtuosospongerimp/)

16.10.3. [How Does It Work?](https://docs.openlinksw.com/virtuoso/virtuosospongerworkpr/)

16.10.4. [Installation Steps](https://docs.openlinksw.com/virtuoso/virtuosospongerinstall/)

16.10.5. [Using The Sponger](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/)

16.10.6. [Consuming the Generated RDF Structured Data](https://docs.openlinksw.com/virtuoso/virtuosospongerconsm/)

16.10.7. [RDF Cartridges Use Cases](https://docs.openlinksw.com/virtuoso/virtuosospongercartridgesextractorusecases/)

16.10.8. [Cartridge Architecture](https://docs.openlinksw.com/virtuoso/virtuosospongerarch/)

16.10.9. [Sponger Programmers Guide](https://docs.openlinksw.com/virtuoso/rdfspongerprogrammerguide/)

16.10.10. [Sponger and Nanotations](https://docs.openlinksw.com/virtuoso/virtuosospongernnt/)

16.10.11. [Sponger Usage Examples](https://docs.openlinksw.com/virtuoso/virtuosospongersampleuses/)

16.11. [Virtuoso Faceted Browser Installation and configuration](https://docs.openlinksw.com/virtuoso/virtuosospongerfacetinstall/)

16.11.1. [Prerequisites](https://docs.openlinksw.com/virtuoso/virtuosospongerfacetinstallprereq/)

16.11.2. [Pre Installation](https://docs.openlinksw.com/virtuoso/virtuosospongerfacetinstallpreinst/)

16.11.3. [VAD Package Installation](https://docs.openlinksw.com/virtuoso/virtuosospongerfacetinstallvadinst/)

16.11.4. [Post Installation](https://docs.openlinksw.com/virtuoso/virtuosospongerfacetinstallposinst/)

16.11.5. [URI Labels](https://docs.openlinksw.com/virtuoso/virtuosospongerfaceurilabels/)

16.11.6. [Usage Statistics](https://docs.openlinksw.com/virtuoso/virtuosospongerfaceusagest/)

16.11.7. [Examples](https://docs.openlinksw.com/virtuoso/virtuosospongerfacetexample/)

16.12. [Virtuoso Faceted Web Service](https://docs.openlinksw.com/virtuoso/virtuosospongerfacent/)

16.12.1. [Customizing](https://docs.openlinksw.com/virtuoso/virtuosospongerfacentcust/)

16.12.2. [Examples](https://docs.openlinksw.com/virtuoso/virtuosospongerfacentexamples/)

16.12.3. [WebService Interface](https://docs.openlinksw.com/virtuoso/virtuosospongerfacentui/)

16.13. [Linked Data](https://docs.openlinksw.com/virtuoso/rdfiridereferencing/)

16.13.1. [IRI Dereferencing For FROM Clauses, "define get:..." Pragmas](https://docs.openlinksw.com/virtuoso/rdfinputgrab/)

16.13.2. [IRI Dereferencing For Variables, "define input:grab-..." Pragmas](https://docs.openlinksw.com/virtuoso/rdfinputgrab_01/)

16.13.3. [URL rewriting](https://docs.openlinksw.com/virtuoso/urlrewriting/)

16.13.4. [Examples of other Protocol Resolvers](https://docs.openlinksw.com/virtuoso/rdfiridereferencingexamples/)

16.13.5. [Faceted Views over Large-Scale Linked Data](https://docs.openlinksw.com/virtuoso/rdfiridereferencingfacet/)

16.14. [Inference Rules & Reasoning](https://docs.openlinksw.com/virtuoso/rdfsparqlrule/)

16.14.1. [Introduction](https://docs.openlinksw.com/virtuoso/rdfsparqlruleintro/)

16.14.2. [Making Rule Sets](https://docs.openlinksw.com/virtuoso/rdfsparqlrulemake/)

16.14.3. [Changing Rule Sets](https://docs.openlinksw.com/virtuoso/rdfsparqlrulechange/)

16.14.4. [Subclasses and Subproperties](https://docs.openlinksw.com/virtuoso/rdfsparqlrulesubclassandsubprop/)

16.14.5. [OWL sameAs Support](https://docs.openlinksw.com/virtuoso/rdfsameas/)

16.14.6. [Implementation](https://docs.openlinksw.com/virtuoso/rdfsparqlruleimpl/)

16.14.7. [Enabling Inferencing](https://docs.openlinksw.com/virtuoso/rdfsparqlruleenableinfr/)

16.14.8. [Examples](https://docs.openlinksw.com/virtuoso/rdfsparqlruleexamples/)

16.14.9. [Identity With Inverse Functional Properties](https://docs.openlinksw.com/virtuoso/rdfsparqlruleinversefunc/)

16.14.10. [Inference Rules and SPARQL with Transitivity Option](https://docs.openlinksw.com/virtuoso/rdfsparqlruletransoption/)

16.14.11. [Inference Rules, OWL Support and Relationship Ontology](https://docs.openlinksw.com/virtuoso/rdfsparqlruleowlrelation/)

16.15. [RDF and Geometry](https://docs.openlinksw.com/virtuoso/rdfsparqlgeospat/)

16.15.1. [Programmatic Manipulation of Geometries in RDF](https://docs.openlinksw.com/virtuoso/rdfsparqlgeospatprog/)

16.15.2. [Creating Geometries From RDF Data](https://docs.openlinksw.com/virtuoso/rdfsparqlgeospatcrg/)

16.15.3. [Using Geometries With Existing Databases](https://docs.openlinksw.com/virtuoso/rdfsparqlgeospatusg/)

16.15.4. [GEO Spatial Examples](https://docs.openlinksw.com/virtuoso/rdfsparqlgeospatexmp/)

16.16. [RDF Replication](https://docs.openlinksw.com/virtuoso/rdfreplication/)

16.17. [RDF Performance Tuning](https://docs.openlinksw.com/virtuoso/rdfperformancetuning/)

16.17.1. [General](https://docs.openlinksw.com/virtuoso/rdfperfgeneral/)

16.17.2. [RDF Index Scheme](https://docs.openlinksw.com/virtuoso/rdfperfrdfscheme/)

16.17.3. [Index Scheme Selection](https://docs.openlinksw.com/virtuoso/rdfindexschemesel/)

16.17.4. [Manage Public Web Service Endpoints](https://docs.openlinksw.com/virtuoso/rdfperfindexes/)

16.17.5. [Erroneous Cost Estimates and Explicit Join Order](https://docs.openlinksw.com/virtuoso/rdfperfcost/)

16.17.6. [Using "swappiness" parameter ( Linux only )](https://docs.openlinksw.com/virtuoso/ch16s17s06/)

16.17.7. [Get All Graphs](https://docs.openlinksw.com/virtuoso/rdfperfgetallgraphs/)

16.17.8. [Rename RDF Graph and RDF Graph Groups](https://docs.openlinksw.com/virtuoso/rdfrenamegraph/)

16.17.9. [Dump and Reload Graphs](https://docs.openlinksw.com/virtuoso/rdfperfdumpandreloadgraphs/)

16.17.10. [RDF dumps from Virtuoso Quad store hosted data into NQuad dumps](https://docs.openlinksw.com/virtuoso/rdfperfdumpintonquads/)

16.17.11. [Dump Linked Data View Graph to n3](https://docs.openlinksw.com/virtuoso/rdfperfdumpandreloadgraphsn3/)

16.17.12. [Loading RDF](https://docs.openlinksw.com/virtuoso/rdfperfloading/)

16.17.13. [Using SPARUL](https://docs.openlinksw.com/virtuoso/rdfperfsparul/)

16.17.14. [DBpedia Benchmark](https://docs.openlinksw.com/virtuoso/rdfperfgeneraldbpedia/)

16.17.15. [RDF Store Benchmarks](https://docs.openlinksw.com/virtuoso/rdfstorebenchmarks/)

16.17.16. [Fast Approximate RDF Graph Diff and Patch](https://docs.openlinksw.com/virtuoso/fastapproxdiffandpatch/)

16.17.17. [RDB2RDF Triggers](https://docs.openlinksw.com/virtuoso/rdb2rdftriggers/)

16.18. [RDF Data Access Providers (Drivers)](https://docs.openlinksw.com/virtuoso/rdfnativestorageproviders/)

16.18.1. [Virtuoso Jena Provider](https://docs.openlinksw.com/virtuoso/rdfnativestorageprovidersjena/)

16.18.2. [Virtuoso Sesame Provider](https://docs.openlinksw.com/virtuoso/rdfnativestorageproviderssesame/)

16.18.3. [Virtuoso Redland Provider](https://docs.openlinksw.com/virtuoso/rdfnativestorageproviderredland/)

16.19. [RDF Graph Replication](https://docs.openlinksw.com/virtuoso/rdfgraphreplication/)

16.19.1. [Replication Scenarios](https://docs.openlinksw.com/virtuoso/rdfgraphreplicationscenr/)

16.19.2. [Replication Topologies](https://docs.openlinksw.com/virtuoso/rdfgraphreplicationtopl/)

16.19.3. [Set up RDF Replication via procedure calls](https://docs.openlinksw.com/virtuoso/rdfgraphreplicationsql/)