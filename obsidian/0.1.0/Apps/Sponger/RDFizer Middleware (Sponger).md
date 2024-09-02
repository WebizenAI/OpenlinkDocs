### 16.10.1. What Is The Sponger?

The Virtuoso Sponger is the Linked Data middleware component of Virtuoso that generates Linked Data from a variety of data sources, supporting a wide variety of data representation and serialization formats. The sponger is transparently integrated into Virtuoso's SPARQL Query Processor where it delivers URI de-referencing within SPARQL query patterns, across disparate data spaces. It also delivers configurable smart HTTP caching services. Optionally, it can be used by the [Virtuoso Content Crawler](https://docs.openlinksw.com/virtuoso/admui.webservices/) to periodically populate and replenish data within the native RDF Quad Store.

The sponger is a fully fledged HTTP proxy service that is also directly accessible via SOAP or REST interfaces.

As depicted below, OpenLink's broad portfolio of Linked-Data-aware products supports a number of routes for creating or consuming Linked Data. The Sponger provides a key platform for developers to generate quality data meshes from unstructured or semi-structured data sources.

**Figure 16.96. OpenLink Linked Data generation options**

![OpenLink Linked Data generation options](https://docs.openlinksw.com/virtuoso/virtuosospongerintro/images/Sponger_LinkedDataGenOptions_2014_v3.png)

  

Architecturally, the Sponger is comprised of a number of Cartridges two types of cartridges: Extractor and Meta Cartridges. Extractor Cartridges focus on data extraction and transformation services while the Meta Cartridges provide lookups and joins across other linked data spaces and Web 2.0 APIs. Both cartridge types are themselves comprised of a data extractors and RDF Schema/Ontology Mapper components.

Cartridges are is highly customizable. Custom cartridges can be developed using any language supported by the Virtuoso Server Extensions API enabling structured linked data generation from resource types not available in the default Sponger Cartridge collection bundled -- as part of the Virtuoso [Cartridges VAD package](http://s3.amazonaws.com/opldownload/uda/vad-packages/6.3/virtuoso/cartridges_dav.vad) .

**Figure 16.97. Virtuoso metadata extraction & RDF structured data generation**

![Virtuoso metadata extraction & RDF structured data generation](https://docs.openlinksw.com/virtuoso/virtuosospongerintro/images/linked_data_gen_opts4.png)

![Virtuoso metadata extraction & RDF structured data generation](https://docs.openlinksw.com/virtuoso/virtuosospongerintro/images/linked_data_gen_opts4.png)### 16.10.2. Why is it Important?

A majority of the worlds data naturally resides in non RDF form at the current time. The Sponger delivers middleware that accelerates the bootstrap of the Semantic Data Web by generating RDF from non RDF data sources, unobtrusively. This "Swiss army knife" for on-the-fly Linked Data generation provides a bridge between the traditional Document Web and the Linked Data Web ("Data Web").

Sponging data from non-RDF Web sources and converting it to RDF exposes the data in a canonical form for querying and inference, and enables fast and easy construction of linked data driven mesh-ups as opposed to code driven Web 2.0 mash-ups.

The RDF extraction and instance data generation products that offer functionality demonstrated by the Sponger are also commonly referred to as RDFizers.

### 16.10.3. How Does It Work?

When an RDF aware client requests data from a network accessible resource via the Sponger the following events occur:

- A requests in made for data in RDF form, and if RDF is returned nothing further happens
    
- If RDF isn't returned, then the Sponger passes the data through a Metadata Extraction Pipeline process (using Metadata Extractors)
    
- The extracted data is transformed to RDF via a Mapping Pipeline process (RDF is extracted by way of Ontology matching and mapping) that results in RDF Entities (instance data) generation
    
- RDF Entities are returned to the client
    

The imported data forms a local cache and its invalidation rules conform to those of traditional HTTP clients (Web Browsers). Thus, expiration time is determined based on subsequent data fetches of the same resource (note: the first data load will record the 'expires' header) with current time compared to expiration time stored in the local cache. If HTTP 'expires' header data isn't returned by the source data server, then the "Sponger" will derive it's own invalidation time frame by evaluating the 'date' header and 'last-modified' HTTP headers. Irrespective of path taken, local cache invalidation is driven by an assessment of current time relative to recorded expiration time.

To manage the cache expiration, set the _MinExpiration_ parameter in your Virtuoso.ini file.

Read full description of the parameter in the [[SPARQL] ini section](https://docs.openlinksw.com/virtuoso/dbadm/) .

Designed with a pluggable architecture, the Sponger's core functionality is provided by Cartridges. Each cartridge includes Data Extractors which extract data from one or more data sources, and Ontology Mappers which map the extracted data to one or more ontologies/schemas, and route to producing RDF Linked Data.

The Schema Mappers are typically XSLT (e.g. GRDDL and other OpenLink Mapping Schemas) or Virtuoso PL based. The Metadata Extractors may be developed in Virtuoso PL, C/C++, Java, or any other language that can be integrated into the Virtuoso via it's server extensions APIs.

The Sponger also includes a pluggable name resolution mechanism that enables the development of Custom Resolvers for naming schemes (e.g. URNs) associated with protocols beyond HTTP. Examples of custom resolvers include:

- [LSID](http://dbpedia.org/resource/LSID)
    
- [DOI](http://dbpedia.org/resource/DOI)

###   
16.10.4. Installation Steps

1. Download the [Cartridges VAD package](http://s3.amazonaws.com/opldownload/uda/vad-packages/6.3/virtuoso/cartridges_dav.vad) .
    
2. Install the cartridges_dav.vad package by using the Conductor UI or by using iSQL:
    
    SQL> DB.DBA.VAD_INSTALL('tmp/cartridges_dav.vad',0);
    SQL_STATE  SQL_MESSAGE
    VARCHAR  VARCHAR
    _______________________________________________________________________________
    
    00000    No errors detected
    00000    Installation of "Linked Data Cartridges" is complete.
    00000    Now making a final checkpoint.
    00000    Final checkpoint is made.
    00000    SUCCESS
    
    6 Rows. -- 1078 msec.
    
3. [Cartridge Configuration](https://docs.openlinksw.com/virtuoso/rdfspongerprogrammerguide/)
    
    - [Extractor Cartridges](https://docs.openlinksw.com/virtuoso/virtuosospongerarch/)
        
    - [Meta Cartridges](https://docs.openlinksw.com/virtuoso/virtuosospongerarch/)
        
    

See Also: [Cartridges Package content description.](https://docs.openlinksw.com/virtuoso/rdfspongerprogrammerguide/)

### 16.10.5. Using The Sponger

The Sponger can be invoked via the following mechanisms:

1. [Virtuoso SPARQL query processor](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/)
    
2. [RDF Proxy Service](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/)
    
3. [OpenLink RDF client applications](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/)
    
4. [ODS-Briefcase (Virtuoso WebDAV)](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/)
    
    - a component of the OpenLink Data Spaces distributed collaborative application platform
    
5. [Directly via Virtuoso PL](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/)
    

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/#virtuosospongerusageprocessor)

#### SPARQL Query Processor IRI Dereferencing

The Sponger is transparently integrated into the Virtuoso SPARQL query processor, where it supports IRI dereferencing.

Virtuoso extends the SPARQL Query Language such that it is possible to download RDF resources from a given IRI, parse, and then store the resulting triples in a graph, with all three operations performed during the SPARQL query-execution process. The IRI/URI of the graph used to store the triples is usually equal to the URL where the resources are downloaded from, consequently the feature is known as "IRI/URI dereferencing". If a SPARQL query instructs the SPARQL processor to retrieve the target graph into local storage, then the SPARQL sponger will be invoked.

The SPARQL extensions for IRI dereferencing are described below. Essentially these enable downloading and local storage of selected triples either from one or more named graphs, or based on a proximity search from a starting URI for entities matching the select criteria and also related by the specified predicates, up to a given depth. For full details see section [Linked Data - IRI Dereferencing](https://docs.openlinksw.com/virtuoso/rdfiridereferencing/) .

Note: For brevity, any reference to URI/IRIs above or in subsequent sections implies an HTTP URI/IRI, where IRI is an internationalized URI. Similarly, in the context of the Sponger, the term IRI in the Virtuoso reference documentation should be taken to mean an HTTP IRI.

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/#virtuosospongerusageprocessor_01)

##### SPARQL Extensions for IRI Dereferencing of FROM Clauses

In addition to the "define get:..." SPARQL extensions for IRI dereferencing in FROM clauses, Virtuoso supports dereferencing SPARQL IRIs used in the WHERE clause (graph patterns) of a SPARQL query via a set of "define input:grab-..." pragmas.

Consider an RDF resource which describes a member of a contact list, user1, and also contains statements about other users, user2 anduser3 , known to him. Resource user3 in turn contains statements about user4 and so on. If all the data relating to these users were loaded into Virtuoso's RDF database, the query to retrieve the details of all the users could be quite simple. e.g.:

sparql
prefix foaf: <http://xmlns.com/foaf/0.1/>
prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
select ?id ?firstname ?nick
where
  {
    graph ?g
      {
        ?id rdf:type foaf:Person .
        ?id foaf:firstName ?firstname .
        ?id foaf:knows ?fn .
        ?fn foaf:nick ?nick .
      }
   }
limit 10;

But what if some or all of these resources were not present in Virtuoso's quad store? The highly distributed nature of the Linked Data Web makes it highly likely that these interlinked resources would be spread across several data spaces. Virtuoso's 'input:grab-...' extensions to SPARQL enable IRI dereferencing in such a way that all appropriate Network resources are loaded, i.e. "being fetched", during query execution, even if some of the Network resources are not known beforehand. For any particular resource matched, and if necessary downloaded, by the query, it is possible to download related resources via a designated predicate path(s) to a specifiable depth i.e. number of 'hops', distance, or degrees of separation (i.e compute Transitive Closures in SPARQL).

Using Virtuoso's 'input:grab-' pragmas to enable sponging, the above query might be recast to:

sparql
define input:grab-var "?more"
define input:grab-depth 10
define input:grab-limit 100
define input:grab-base "http://www.openlinksw.com/dataspace/kidehen@openlinksw.com/weblog/kidehen@openlinksw.com%27s%20BLOG%20%5B127%5D/1300"
prefix foaf: <http://xmlns.com/foaf/0.1/>
prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>

select ?id ?firstname ?nick
where {
    graph ?g {
               ?id rdf:type foaf:Person .
               ?id foaf:firstName ?firstname .
               ?id foaf:knows ?fn .
               ?fn foaf:nick ?nick .
               optional { ?id rdfs:SeeAlso ?more }
            }
}
limit 10;

Another example showing a designated predicate traversal path via the input:grab-seealso extension is:

sparql
define input:grab-iri <http://www.openlinksw.com/dataspace/kidehen@openlinksw.com/weblog/kidehen@openlinksw.com%27s%20BLOG%20%5B127%5D/sioc.ttl>
define input:grab-var "id"
define input:grab-depth 10
define input:grab-limit 100
define input:grab-base "http://www.openlinksw.com/dataspace/kidehen@openlinksw.com/weblog/kidehen@openlinksw.com%27s%20BLOG%20%5B127%5D/1300"
define input:grab-seealso <foaf:maker>
prefix foaf: <http://xmlns.com/foaf/0.1/>

select ?id
where
  {
    graph ?g
      {
        ?id a foaf:Person .
      }
  }
limit 10;

A list of the input:grab pragmas is given below:

- input:grab-var specifies the name of the SPARQL variable whose values should be used as IRIs of resources that should be downloaded.
    
- input:grab-iri specifies an IRI that should be retrieved before executing the rest of the query, if it is not in the quad store already. (This pragma can be included multiple times).
    
- input:grab-seealso (or its synonym input:grab-follow-predicate) specifies a predicate IRI to be used when traversing a graph. (This pragma can be included multiple times).
    
- input:grab-limit sets the maximum number of resources (graph subject or object nodes) to be retrieved from a target graph.
    
- input:grab-depth sets the maximum 'degrees of separation' or links (predicates) between nodes in the target graph.
    
- input:grab-all "yes" instructs the SPARQL processor to dereference everything related to the query. All variables and literal IRIs in the query become values for input:grab-var and input:grab-iri. The resulting performance may be very bad.
    
- input:grab-base specifies the base IRI to use when converting relative IRIs to absolute. (Default: empty string).
    
- input:grab-destination overrides the default IRI dereferencing and forces all retrieved triples to be stored in the specified graph.
    
- input:grab-loader identifies the procedure used to retrieve each resource via HTTP, parse and store it. (Default: DB.DBA.RDF_SPONGE_UP)
    
- input:grab-resolver identifies the procedure that resolves IRIs and determines the HTTP method of retrieval. (Default: DB.DBA.RDF_GRAB_RESOLVER_DEFAULT)
    

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/#virtuosospongerusageprocessorex)

##### SPARQL Processor Usage Example

Network Resource Fetch can be performed directly from within the SPARQL processor.

After logging into Virtuoso's Conductor interface, the following query can be issued from the Interactive SQL (iSQL) panel:

sparql
define get:uri "http://www.ivan-herman.net/foaf.html"
define get:soft "soft"
select * from <http://mygraph> where {?s ?p ?o}

Here the sparql keyword invokes the SPARQL processor from the SQL interface and the RDF data fetched from page http://www.ivan-herman.net/foaf.html is loaded into the local RDF quad store as graph http://mygraph .

The new graph can then be queried using the basic SPARQL client normally available in a default Virtuoso installation at http://example.com/sparql/. e.g.:

select * from <http://mygraph> where {?s ?p ?o}

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/#virtuosospongerusageproxy)

#### RDF Proxy Service

The Sponger's functionality is also exposed via an in-built REST style Web service. This web service takes a target URL and either returns the content "as is" or tries to transform (by sponging) to RDF. Thus, the proxy service can be used as a 'pipe' for RDF browsers to browse non-RDF sources.

When the cartridges package is installed, Virtuoso reserves the path '/about/[id|data|rdf|html]/http/' for Sponger Proxy URI Service. For example, if a Virtuoso installation on host example.com listens for HTTP requests on port 8080 then client applications should use a 'service endpoint' string equal to 'http://example.com:8080/about/[id|data|rdf|html]/http/'. If the cartridges package is not installed, then the service uses the path '/proxy/rdf/'.

Note: The old Sponger Proxy URI Service pattern '/proxy/' is now deprecated.

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/#virtuosospongerusageproxyex1)

##### Example 1

The following URLs return information about musician John Cale, gleaned from the MusicBrainz music metadatabase, rendered as RDF or HTML respectively. (The Network Resource fetched data is available in the HTML rendering through the foaf:primaryTopic property.)

- http://demo.openlinksw.com/about/rdf/http://musicbrainz.org/artist/72c090b6-a68e-4cb9-b330-85278681a714.html
    
- http://demo.openlinksw.com/about/html/http/musicbrainz.org/artist/72c090b6-a68e-4cb9-b330-85278681a714.html
    

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/#virtuosospongerusageproxyex2)

##### Example 2

The file http://www.ivan-herman.net/foaf.html contains a short profile of the W3C Semantic Web Activity Lead Ivan Herman. This XHTML file contains RDF embedded as RDFa. Running the file through the Sponger via Virtuoso's RDF proxy service extracts the embedded FOAF data as pure RDF, as can be seen by executing:

$ curl -L -H "Accept:application/rdf+xml" http://linkeddata.uriburner.com/about/id/entity/http/www.ivan-herman.net/foaf.html
<?xml version="1.0" encoding="utf-8" ?>
<rdf:RDF xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#" xmlns:rdfs="http://www.w3.org/2000/01/rdf-schema#">
  <rdf:Description rdf:about="http://linkeddata.uriburner.com/about/id/http/www.ivan-herman.net/foaf.html#Person1Stat"><scovo:dimension xmlns:scovo="http://purl.org/NET/scovo#" rdf:resource="http://rdfs.org/ns/void#numberOfResources"/></rdf:Description>
  <rdf:Description rdf:nodeID="b145981159"><rdf:rest rdf:nodeID="b145981158"/></rdf:Description>
  <rdf:Description rdf:about="http://linkeddata.uriburner.com/about/id/entity/http/www.mendeley.com/profiles/ivan-herman"><foaf:accountName xmlns:foaf="http://xmlns.com/foaf/0.1/">ivan-herman</foaf:accountName></rdf:Description>
  etc ..
  <rdf:Description rdf:nodeID="b145981130"><http-voc:elementName xmlns:http-voc="http://www.w3.org/2006/http#">text/html</http-voc:elementName></rdf:Description>
</rdf:RDF>

(linkeddata.uriburner.com hosts a public Virtuoso instance.) Though this example demonstrates the action of the /about/id/entity/ service quite transparently, it is a basic and unwieldy way to view RDF. As described earlier, the OpenLink Data Explorer uses the same proxy service to provide a more polished means to extract and view fetched RDF data.

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/#virtuosospongerusageproxyurlist)

##### Usage of the Sponger Middleware via REST patterns

Delegation and proxies are part of the Internet and Web's federated architecture. Thus, developers of RESTful applications benefit immensely from the ability to leverage Sponger functionality via delegation to it as a proxy.

The following table presents list of the supported URL parameters:

**Table 16.9.** 

|Parameter|Value|Description|Example|
|---|---|---|---|
|_refresh_|clean|_Usage_ : for overwriting. The 'clean' usage explicitly clears the graph i.e. will cause the Sponger to drop cache even if it is marked to be in the fly. Thus, if fetched cache by some reason is left in some inconsistent state like shutdown during Network Resource fetching, then 'clean' is required as it doesn't check cache state. _Note_ : must be used with caution as other threads may be doing fetching of network resources at same time.|[Explicitly clear the graph](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/twitter.com/kidehen?@Lookup@=&refresh=clean)|
|_sponger:get_|add|_Usage_ : Add new triples to named graphs, progressively. This is the default value for the parameter sponger:get. May be used together with refresh=<seconds> to overwrite the expiration in the cache.|[Add new triples and refresh on every 10 seconds](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/twitter.com/kidehen?sponger:get=add&refresh=10)|
|_sponger:get_|soft|_Usage_ : Network Resource Fetch data subject to cache invalidation mode and associated rules of instance. May be used together with refresh=<seconds> to overwrite the expiration in the cache.|[Network Resource Fetch data with option _soft_ and refresh on every 10 seconds](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/twitter.com/kidehen?sponger:get=soft&refresh=10)|
|_sponger:get_|replace|_Usage_ : Replace subject to cache invalidation mode and rules, but coverage includes non fetched triples if such exist in a given named graph. may be used together with refresh=<seconds> to overwrite the expiration in the cache.|[Replace data and refresh on every 10 seconds](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/twitter.com/kidehen?sponger:get=replace&refresh=10)|

  

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/#virtuosospongerusageclapp)

#### OpenLink RDF Client Applications

OpenLink currently provides two main RDF client applications:

- [OpenLink Data Explorer](http://ode.openlinksw.com/) (ODE)
    
- [iSPARQL](http://demo.openlinksw.com/isparql)
    

ODE is a Linked Data explorer packaged as a Firefox plugin (support for other browsers is planned). iSPARQL is an interactive AJAX-based SPARQL query builder with support for SPARQL QBE, bundled as part of the [OpenLink Ajax Toolkit](http://oat.openlinksw.com/) (OAT). Both RIA clients utilise sponging extensively.

The ODE plugin is dual faceted - RDF data can be viewed and explored natively, through its integral RDF browser, or, as described above, rendered as HTML through ODE's 'View Page Metadata' option. The screenshots below show ODE's RDF browser being launched through the 'View Linked Data Sources' popup menu.

**Figure 16.98. Launching ODE's RDF browser**

![Launching ODE's RDF browser](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/images/twitter_home.png)

  

The RDF browser then displays RDF data fetched via the Crunchbase cartridge.

**Figure 16.99. ODE RDF browser displaying Crunchbase network resource fetched data**

![ODE RDF browser displaying Crunchbase network resource fetched data](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/images/twitter_ode_rdf.png)

  

iSPARQL directs queries to the configured SPARQL endpoint. When targetting a Virtuoso /sparql service, Virtuoso specific sponging options can be enabled through the 'Preferences' dialog box.

The iSPARQL sponger settings are appended to SPARQL queries through the 'should-sponge' query parameter. These are translated to IRI dereferencing pragmas on the server as follows:

**Table 16.10.** 

|iSPARQL sponging setting|/sparql endpoint: "should-sponge" query parameter value|SPARQL processor directives|
|---|---|---|
|Use only local data|N/A|N/A|
|Retrieve remote RDF data for all missing source graphs|soft|define get:soft "soft"|
|Retrieve all missing remote RDF data that might be useful|grab-all|define input:grab-all "yes" define input:grab-depth 5 define input:grab-limit 100|
|Retrieve all missing remote RDF data that might be useful including seeAlso references|grab-seealso|define input:grab-all "yes" define input:grab-depth 5 define input:grab-limit 200 define input:grab-seealso <http://www.w3.org.2000/01/rdf-schema#seeAlso> define input:grab-seealso <http://xmlns.com/foaf/0.1/seeAlso>|
|Try to download all referenced resources|grab-everything|define input:grab-all "yes" define input:grab-intermediate "yes" define input:grab-depth 5 define input:grab-limit 500 define input:grab-seealso <http://www.w3.org.2000/01/rdf-schema#seeAlso> define input:grab-seealso <http://xmlns.com/foaf/0.1/seeAlso>|

  

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/#virtuosospongerusagebrief)

#### ODS-Briefcase (Virtuoso WebDAV)

ODS-Briefcase is a component of [OpenLink Data Spaces](http://virtuoso.openlinksw.com/wiki/main/Main/OdsIndex) (ODS), a new generation distributed collaborative application platform for creating Semantic Web presence via Data Spaces derived from weblogs, wikis, feed aggregators, photo galleries, shared bookmarks, discussion forums and more. It is also a high level interface to the Virtuoso WebDAV repository.

ODS-Briefcase offers file-sharing functionality that includes the following features:

- Web brower-based interactions
    
- Web Services (direct use of the HTTP based WebDAV protocol)
    
- SPARQL query language support - all WebDAV resources are exposed as SIOC ontology instance data (RDF data sets)
    

When resources or documents are put into the ODS Briefcase and are made publicly readable (via a Unix-style +r permission or ACL setting) and the resource in question is of a supported content type, metadata is automatically extracted at file upload time.

Note: ODS-Briefcase extracts metadata from a wide array of file formats, automatically.

The extracted metadata is available in two forms, pure WebDAV and RDF (with RDF/XML or N3/Turtle serialization options), that is optionally synchronized with the underlying Virtuoso Quad Store.

All public readable resources in WebDAV have their owner, creation time, update time, size and tags published, plus associated content type dependent metadata. This WebDAV metadata is also available in RDF form as a SPARQL queriable graph accessible via the SPARQL protocol endpoint using the WebDAV location as the RDF data set URI (graph or data source URI).

You can also use a special RDF_Sink folder to automate the process of uploading RDF resources files into the Virtuoso Quad Store via WebDAV or raw HTTP. The properties of the special folder control whether sponging (RDFization) occurs. Of course, by default, this feature is enabled across all Virtuoso and ODS installations (with an ODS-Briefcase Data Space instance enabled).

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/#virtuosospongerusagebriefex)

##### Raw HTTP Example for Extracting Metadata using CURL

Username: demo
Password: demo
Source File: wine.rdf
Destination Folder:
http://demo.openlinksw.com/DAV/home/demo/rdf_sink/
Content Type: application/rdf+xml

$ curl -v -T wine.rdf -H content-type:application/rdf+xml http://demo.openlinksw.com/DAV/home/demo/rdf_sink/ -u demo:demo

Finally, you can also get RDF data into Virtuoso's Quad Store via WebDAV using the Virtuoso Web Crawler utility (configurable via the Virtuoso Conductor UI). This feature also provides the ability to enable or disable Sponging as depicted below.

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/#virtuosospongerusagebriefint)

##### Sponger and ODS-Briefcase Structured Data Extractor Interrelationship

As the Sponger and ODS-Briefcase both extract structured data, what is the relationship between these two facilities?

The principal difference between the two is that the Sponger is anRDF data crawler & generator, whereas Briefcase's structured data extractor is a WebDAV resourcefilter. The Briefcase structured data extractor is aimed at providing RDF data from WebDAV resources. Thus, if none of the available Sponger cartridges are able to extract metadata and produce RDF structured data, the Sponger calls upon the Briefcase extractor as the last resort in the RDF structured data generation pipeline.

**Figure 16.100. Conductor's content import configuration panel**

![Conductor's content import configuration panel](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/images/fig2_top.png)

  

**Figure 16.101. Conductor's content import configuration panel**

![Conductor's content import configuration panel](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/images/fig2_bottom.png)

  

**Figure 16.102. Conductor's content import configuration panel**

![Conductor's content import configuration panel](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/images/fig2_bottom2.png)

  

**Figure 16.103. Conductor's content import configuration panel**

![Conductor's content import configuration panel](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/images/fig2_bottom3.png)

  

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongerusage/#virtuosospongerusagedirect)

#### Directly via Virtuoso PL

Sponger cartridges are invoked through a cartridge hook which provides a Virtuoso PL entry point to the packaged functionality. Should you wish to utilize the Sponger from your own Virtuoso PL procedures, you can do so by calling these hook routines directly. Full details of the hook function prototype and how to define your own cartridges are presented [here](https://docs.openlinksw.com/virtuoso/rdfspongerprogrammerguide/) .

### 16.10.6. Consuming the Generated RDF Structured Data

The generated RDF-based structured data (RDF) can be consumed in a number of ways, depending on whether or not the data is persisted in Virtuoso's RDF Quad Store.

If the data is persisted, it can be queried through the Virtuoso SPARQL endpoint associated with any Virtuoso instance: /sparql. The RDF is exposed in a graph typically identified using a URL matching the source resource URL from which the RDF data was generated. Naturally, any SQL query can also access this, since SPARQL can be freely intermixed with SQL via Virtuoso's SPASQL (SPARQL inside SQL) functionality. RDF data is also accessible through Virtuoso's implementation of the URIQA protocol.

If not persisted, as is the case with the RDF Proxy Service, the data can be consumed by an RDF aware Web client, e.g. an RDF browser such as the OpenLink Data Explorer (ODE).

### 16.10.7. RDF Cartridges Use Cases

This section contains examples of Web resources which can be transformed by RDF Cartridges. It also states where additional setup for given cartridges is needed i.e. keys account names etc.

_Service based:_

- amazon
    
    needs: api key
    example: http://www.amazon.com/gp/product/0553383043
    
- ebay
    
    needs: account, api-key
    example: http://cgi.ebay.com/RARE-DAY-IN-FAIRY-LAND-ELEPHANT-FOLIO-20-FULL-COLOR_W0QQitemZ140209597189QQihZ004QQcategoryZ29223QQssPageNameZWDVWQQrdZ1QQcmdZViewItem
    
- flickr needs: api-key example: http://farm1.static.flickr.com/212/496684670_7122c831ed.jpg
    
- mbz
    
    example: http://musicbrainz.org/release/37e955d4-a53c-45aa-a812-1b23b88dbc13.html
    
- mql (freebase)
    
    example: http://www.freebase.com/view/en/beta_ursae_majoris
    
- facebook
    
    needs: api-key, secret, persistent-session-id
    example: http://www.facebook.com/profile.php?id=841100003
    
- yahoo-stock
    
    example: http://finance.yahoo.com/q?s=AAPL
    
- yahoo-traffic
    
    example: http://local.yahooapis.com/MapsService/V1/trafficData?appid=YahooDemo&street=701+First+Street&city=Sunnyvale&state=CA
    
- Bugzilla
    
    example: https://bugzilla.mozilla.org/show_bug.cgi?id=251714
    
- SVG
    
- OO document
    
    needs: unzip plugin
    
- Wikipedia
    
    needs: php plugin & dbpedia extractor
    example: http://wikipedia.org/wiki/London
    
- Opencalais
    
- iCalendar
    

_GRDDL_

- Google Base (google)
    
    example: http://www.google.com/base/feeds/snippets/17891817243016304554
    
- eRDF
    
- RDFa
    
- hCard
    
- hCalendar
    
- hReview
    
- relLicense
    
- XBRL
    
- HR-XML
    
- DC
    
- geoURL
    
- Ning
    
- XFN
    
- xFolk
    

_URN handlers_

**Table 16.11. URN handlers List**

|URN handler|Sample URI|Resource Description|Linked Data View|Linked Data Graph|Needs|
|:--|---|---|---|---|---|
|LSID|urn:lsid:ubio.org:namebank:12292|[HTML Representation](http://demo.openlinksw.com/about/html/urn:lsid:ubio.org:namebank:12292)|[Linked Data View](http://demo.openlinksw.com/describe/?url=urn:lsid:ubio.org:namebank:12292)|[Data Explorer View](http://demo.openlinksw.com/ode/?uri=urn:lsid:ubio.org:namebank:12292)|none|
|DOI|doi:10.1038/35057062|[HTML Representation](http://demo.openlinksw.com/about/html/doi:10.1038/35057062)|[Linked Data View](http://demo.openlinksw.com/describe/?url=doi:10.1038/35057062)|[Data Explorer View](http://demo.openlinksw.com/ode/?uri=doi:10.1038/35057062)|Needs hslookup plugin, relevant html, pdf, xml etc. mappers enabled.|
|OAI|oai:dcmi.ischool.washington.edu:article/8|[HTML Representation](http://demo.openlinksw.com/about/html/oai:dcmi.ischool.washington.edu:article/8)|[Linked Data View](http://demo.openlinksw.com/describe/?url=oai:dcmi.ischool.washington.edu:article/8)|[Data Explorer View](http://demo.openlinksw.com/ode/?uri=oai:dcmi.ischool.washington.edu:article/8)|none|

  

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongercartridgesextractorusecases/#virtuosospongerrdfmappers)

#### SPARQL IRI Dereferencing

The Virtuoso SPARQL engine (called for brevity just SPARQL below) supports IRI Dereferencing, however it understands only RDF data, that is it can retrieve only files containing RDF/XML, turtle or N3 serialized RDF data, if format is unknown it will try mapping with built-in WebDAV metadata extractor. In order to extend this feature with dereferencing web or file resources which naturally don't have RDF data (like PDF, JPEG files for example) is provided a special mechanism in SPARQL engine. This mechanism is called RDF mappers for translation of non-RDF data files to RDF.

In order to instruct the SPARQL to call a RDF mapper it needs to be registered and it will be called for a given URL or MIME type pattern. In other words, when unknown for SPARQL format is received during URL dereferencing process, it will look into a special registry (a table) to match either the MIME type or IRI using a regular expression, if match is found the mapper function will be called.

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongercartridgesextractorusecases/#virtuosospongerproxy)

##### Sponger Proxy service

Sponger functionality is also exposed via Virtuoso's "/proxy/rdf/" endpoint, as an in-built REST style Web service available in any Virtuoso standard installation. This web service takes a target URL and either returns the content "as is" or tries to transform (by sponging) to RDF. Thus, the proxy service can be used as a 'pipe' for RDF browsers to browse non-RDF sources.

For more information see [RDF Sponger Proxy service](https://docs.openlinksw.com/virtuoso/rdfsparqlprotocolendpoint/)

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongercartridgesextractorusecases/#virtuosospongercache)

##### Cache Invalidation

To clear cache on all values of HS_LOCAL_IRI of the SYS_HTTP_SPONGE table use:

SPARQL clear graph <A-Named-Graph>;

### 16.10.8. Cartridge Architecture

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongerarch/#virtuosospongerarchcr)

#### What is a Cartridge?

See full description [here](https://docs.openlinksw.com/virtuoso/rdfspongerprogrammerguide/)

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongerarch/#virtuosospongercartridgesextr)

#### Extractor Cartridges

An Extractor Cartridge processes a Resource of a given format, extracting RDF according to rules appropriate to that format. External data does not come into play; only the content of the Resource fed to the Sponger.

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongerarch/#virtuosospongercartridgesstand)

##### Supported Standard Non-RDF Data Formats

These Cartridges handle open formats - typically community-developed, openly-documented, and freely-licensed data structures.

**Table 16.12.** 

|Cartridge|Sample URI|Resource Description|Linked Data Graph|
|---|---|---|---|
|AB Meta|[example](http://abmeta.org/album2.html)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/abmeta.org/album2.html)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://abmeta.org/album2.html)|
|Atom|[example](http://www.openlinksw.com/blog/~kidehen/gems/atom.xml)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.openlinksw.com/blog/~kidehen/gems/atom.xml)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.openlinksw.com/blog/~kidehen/gems/atom.xml)|
|CSV|[example](http://data.london.gov.uk/datafiles/business-economy/employment-projections-sector-2009.csv)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/data.london.gov.uk/datafiles/business-economy/employment-projections-sector-2009.csv)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://data.london.gov.uk/datafiles/business-economy/employment-projections-sector-2009.csv)|
|DC|[example](http://dublincore.org/2008/01/14/dcterms.rdf)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/dublincore.org/2008/01/14/dcterms.rdf)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://dublincore.org/2008/01/14/dcterms.rdf)|
|eRDF|[example](http://www.w3.org/2001/sw/grddl-wg/doc29/hotel-data.html)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.w3.org/2001/sw/grddl-wg/doc29/hotel-data.html)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.w3.org/2001/sw/grddl-wg/doc29/hotel-data.html)|
|hAudio|[example](http://alpha.libre.fm/user/weborganics)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/alpha.libre.fm/user/weborganics)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://alpha.libre.fm/user/weborganics)|
|hCalendar|[example](http://www.maine.gov/portal/government/calendar.shtml)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.maine.gov/portal/government/calendar.shtml)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.maine.gov/portal/government/calendar.shtml)|
|hCard|[example](http://dbaron.org/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/dbaron.org/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://dbaron.org/)|
|hListing|[example](http://feedback.ebay.com/ws/eBayISAPI.dll?ViewFeedback2&userid=manganos&ftab=AllFeedback&frm=284&iid=5863912155)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/feedback.ebay.com/ws/eBayISAPI.dll?ViewFeedback2&userid=manganos&ftab=AllFeedback&frm=284&iid=5863912155)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://feedback.ebay.com/ws/eBayISAPI.dll?ViewFeedback2&userid=manganos&ftab=AllFeedback&frm=284&iid=5863912155)|
|hNews|[example](http://www.semissourian.com/story/1620555.html)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.semissourian.com/story/1620555.html)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.semissourian.com/story/1620555.html)|
|hProduct|[example](http://www.roger-junca.com/Roti-de-magret-du-Sud-ouest-produit-89.html)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.roger-junca.com/Roti-de-magret-du-Sud-ouest-produit-89.html)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.roger-junca.com/Roti-de-magret-du-Sud-ouest-produit-89.html)|
|HR-XML|[example](http://ns.hr-xml.org/2_5/HR-XML-2_5/SEP/ResumeExample.xml)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/ns.hr-xml.org/2_5/HR-XML-2_5/SEP/ResumeExample.xml)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://ns.hr-xml.org/2_5/HR-XML-2_5/SEP/ResumeExample.xml)|
|hRecipe|[example](http://www.bbc.co.uk/food/recipes/beef_tacos_with_salsa_67130%01hrecipe)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/www.bbc.co.uk/food/recipes/beef_tacos_with_salsa_67130%01hrecipe)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.bbc.co.uk/food/recipes/beef_tacos_with_salsa_67130)|
|hResume|[example](http://brev.name/resume/brev-resume.html)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/brev.name/resume/brev-resume.html)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://brev.name/resume/brev-resume.html)|
|hReview|[example](http://www.concertbuzz.net/genres/classic-rock/jethro-tull.html)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.concertbuzz.net/genres/classic-rock/jethro-tull.html)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.concertbuzz.net/genres/classic-rock/jethro-tull.html)|
|HTTP in RDF|[example](http://linkeddata.uriburner.com/about/rdf/http://data.london.gov.uk/datafiles/business-economy/employment-projections-sector-2009.csv)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/linkeddata.uriburner.com/about/rdf/http://data.london.gov.uk/datafiles/business-economy/employment-projections-sector-2009.csv)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://linkeddata.uriburner.com/about/rdf/http://data.london.gov.uk/datafiles/business-economy/employment-projections-sector-2009.csv)|
|iCalendar|[example](http://www.mozilla.org/projects/calendar/caldata/AustrianHolidays.ics)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.mozilla.org/projects/calendar/caldata/AustrianHolidays.ics)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.mozilla.org/projects/calendar/caldata/AustrianHolidays.ics)|
|Microsoft Word 2003 XML Document|[example](http://ec2-174-129-156-25.compute-1.amazonaws.com/DAV/office_tests/word2003xml.xml)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/ec2-174-129-156-25.compute-1.amazonaws.com/DAV/office_tests/word2003xml.xml)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://ec2-174-129-156-25.compute-1.amazonaws.com/DAV/office_tests/word2003xml.xml)|
|Microsoft XML Spreadsheet 2003|[example](http://mathewpeet.org/thesis/programs/spreadsheet/XRDCALC-LATTICEPARAM.xls)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/mathewpeet.org/thesis/programs/spreadsheet/XRDCALC-LATTICEPARAM.xls)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://mathewpeet.org/thesis/programs/spreadsheet/XRDCALC-LATTICEPARAM.xls)|
|Microsoft Documents|[example](http://data.london.gov.uk/datafiles/business-economy/employment-projections-sector-2009.csv)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/linkeddata.uriburner.com/about/rdf/http://data.london.gov.uk/datafiles/business-economy/employment-projections-sector-2009.csv)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://linkeddata.uriburner.com/about/rdf/http://data.london.gov.uk/datafiles/business-economy/employment-projections-sector-2009.csv)|
|OData|[example](http://services.odata.org/Northwind/Northwind.svc/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://services.odata.org/Northwind/Northwind.svc/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://services.odata.org/Northwind/Northwind.svc/)|
|OO document|[example](http://www.pitonyak.org/AndrewMacro.odt)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.pitonyak.org/AndrewMacro.odt)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.pitonyak.org/AndrewMacro.odt)|
|OPML|[example](http://news.bbc.co.uk/rss/feeds.opml)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/news.bbc.co.uk/rss/feeds.opml)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://news.bbc.co.uk/rss/feeds.opml)|
|PPTX|[example](http://download.microsoft.com/download/4/D/E/4DE0D83D-7845-4FD1-9A8E-12F532EC81BC/Keynote.pptx)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/download.microsoft.com/download/4/D/E/4DE0D83D-7845-4FD1-9A8E-12F532EC81BC/Keynote.pptx)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://download.microsoft.com/download/4/D/E/4DE0D83D-7845-4FD1-9A8E-12F532EC81BC/Keynote.pptx)|
|RDFa|[example](http://virtuoso.openlinksw.com/presentations/Creating_Deploying_Exploiting_Linked_Data2/Creating_Deploying_Exploiting_Linked_Data2_TimBL_v3.html)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/virtuoso.openlinksw.com/presentations/Creating_Deploying_Exploiting_Linked_Data2/Creating_Deploying_Exploiting_Linked_Data2_TimBL_v3.html)|[Data Explorer View](http://virtuoso.openlinksw.com/presentations/Creating_Deploying_Exploiting_Linked_Data2/Creating_Deploying_Exploiting_Linked_Data2_TimBL_v3.html)|
|RSS|[example](http://microformats.org/feed/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/microformats.org/feed/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://microformats.org/feed/)|
|Slidy|[example](http://slideshow.rubyforge.org/microformats.html)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/slideshow.rubyforge.org/microformats.html)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://slideshow.rubyforge.org/microformats.html)|
|vCalendar|[example](http://upcoming.org/event/130719/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/upcoming.org/event/130719/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://upcoming.org/event/130719/)|
|vCard|[example](http://tech.yahoo.com/pr/apple-ipod-video-30gb-black-mp3-player/1992981873)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/tech.yahoo.com/pr/apple-ipod-video-30gb-black-mp3-player/1992981873)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://tech.yahoo.com/pr/apple-ipod-video-30gb-black-mp3-player/1992981873)|
|WebDAV Metadata|[example](http://data.london.gov.uk/datafiles/business-economy/employment-projections-sector-2009.csv)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/linkeddata.uriburner.com/about/rdf/http://data.london.gov.uk/datafiles/business-economy/employment-projections-sector-2009.csv)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://linkeddata.uriburner.com/about/rdf/http://data.london.gov.uk/datafiles/business-economy/employment-projections-sector-2009.csv)|
|XBRL|[example](http://www.sec.gov/Archives/edgar/data/51143/000110465908059468/ibm-20080429.xml)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.sec.gov/Archives/edgar/data/51143/000110465908059468/ibm-20080429.xml)|[Data Explorer View](http://www.sec.gov/Archives/edgar/data/51143/000110465908059468/ibm-20080429.xml)|
|XFN Profile|[example](http://www.molly.com/people.php)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.molly.com/people.php)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.molly.com/people.php)|
|XFN Profile2|[example](http://www.molly.com/people.php)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.molly.com/people.php)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.molly.com/people.php)|
|xHTML|[example](http://virtuoso.openlinksw.com/Whitepapers/html/AIW_Virtuoso_SOA.htm)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/virtuoso.openlinksw.com/Whitepapers/html/AIW_Virtuoso_SOA.htm)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://virtuoso.openlinksw.com/Whitepapers/html/AIW_Virtuoso_SOA.htm)|
|XHTML|[example](http://www.lespetitescases.net/semantique-et-xhtml)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.lespetitescases.net/semantique-et-xhtml)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.lespetitescases.net/semantique-et-xhtml)|

  

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongerarch/#virtuosospongercartridgesnonstand)

##### Supported Vendor-specific Non-RDF Data Formats

These Cartridges handle closed formats - typically proprietary; sometimes undocumented; possibly licensed to no-one except the format originator. Sometimes data may not be parsed as desired or expected, as many of these Cartridges have required reverse-engineering of the data format in question.

**Table 16.13.** 

|Cartridge|Needs|Sample URI|Resource Description|Linked Data Graph|
|---|---|---|---|---|
|Amazon|API Key|[example](http://www.amazon.com/gp/product/0553383043)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.amazon.com/gp/product/0553383043)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.amazon.com/gp/product/0553383043)|
|BestBuy|API Key|[example](http://www.bestbuy.com/site/KOSS+-+Pro+DJ100+Professional+Over-the-Ear+Headphones+-+Black/9745789.p?skuId=9745789&id=1218165774336)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.bestbuy.com/site/KOSS+-+Pro+DJ100+Professional+Over-the-Ear+Headphones+-+Black/9745789.p?skuId=9745789&id=1218165774336)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.bestbuy.com/site/KOSS+-+Pro+DJ100+Professional+Over-the-Ear+Headphones+-+Black/9745789.p?skuId=9745789&id=1218165774336)|
|Bing|none|[example](http://www.bing.com/community/members/livesearch/default.aspx)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.bing.com/community/members/livesearch/default.aspx)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.bing.com/community/members/livesearch/default.aspx)|
|Bugzillas|none|[example](https://bugzilla.mozilla.org/show_bug.cgi?id=251714)|[HTML Representation](http://linkeddata.uriburner.com/about/html/https://bugzilla.mozilla.org/show_bug.cgi?id=251714)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=https://bugzilla.mozilla.org/show_bug.cgi?id=251714)|
|CNET|API Key|[example](http://shopper.cnet.com/samsung-moment-sprint/4014-6452_9-33775546.html)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/linkeddata.uriburner.com/about/rdf/http://shopper.cnet.com/samsung-moment-sprint/4014-6452_9-33775546.html)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://linkeddata.uriburner.com/about/rdf/http://shopper.cnet.com/samsung-moment-sprint/4014-6452_9-33775546.html)|
|CrunchBase|none|[example](http://linkeddata.uriburner.com/about/rdf/http://www.crunchbase.com/company/radar-music-videos)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/linkeddata.uriburner.com/about/rdf/http://www.crunchbase.com/company/radar-music-videos)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://linkeddata.uriburner.com/about/rdf/http://www.crunchbase.com/company/radar-music-videos)|
|Delicious|none|[example](http://delicious.com/popular/blog)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/delicious.com/popular/blog)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://delicious.com/popular/blogI)|
|Digg|none|[example](http://digg.com/general_sciences/At_Last-Stem_Cells_without_Side_Effects_)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/digg.com/general_sciences/At_Last-Stem_Cells_without_Side_Effects_)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://digg.com/general_sciences/At_Last-Stem_Cells_without_Side_Effects_)|
|Discogs|php plugin, DBpedia Extractor|[example](http://www.discogs.com/Todd-Barton-and...ic-Poetry-Of-The-Kesh/release/2053074)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.amazon.com/o/ASIN/0553383043)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.amazon.com/o/ASIN/0553383043)|
|Disqus|API Key, API Account|[example](http://www.scripting.com/stories/2009/02/01/wheresYourData.html#disqus_thread)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.scripting.com/stories/2009/02/01/wheresYourData.html#disqus_thread)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.scripting.com/stories/2009/02/01/wheresYourData.html#disqus_thread)|
|DOI|hslookup plugin; relevant html-, pdf-, xml-, etc., -mappers enabled|[example](http://doi.ieeecomputersociety.org/10.1109/MIC.2008.16)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/doi.ieeecomputersociety.org/10.1109/MIC.2008.16)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://doi.ieeecomputersociety.org/10.1109/MIC.2008.16)|
|Dublin Core|none|[example](http://dublincore.org/documents/2002/07/31/dcmes-xml/dcmes-xml-dtd.shtml)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/dublincore.org/documents/2002/07/31/dcmes-xml/dcmes-xml-dtd.shtml)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://dublincore.org/documents/2002/07/31/dcmes-xml/dcmes-xml-dtd.shtml)|
|eBay|account, API Key|[example](http://cell-phones.shop.ebay.com/Cell-Phones-Smartphones-/3312/i.html?LH_TopRatedSellers=1&LH_ItemCondition=1&Brand=Apple%2520iPhone&LH_Price=100..%40c&_nkw=%22iphone+4%22&_trkparms=65%253A15%257C66%253A2%257C39%253A1&_dmd=1&_dmpt=Cell_Phones&_mPrRngCbx=1&_sc=1&_sticky=1&_trksid=p3907.m551&_sop=12&_sc=1%26clkid%3D6198561558861688578&_qi=RTM733776)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/cell-phones.shop.ebay.com/Cell-Phones-Smartphones-/3312/i.html?LH_TopRatedSellers=1&LH_ItemCondition=1&Brand=Apple%2520iPhone&LH_Price=100..%40c&_nkw=%22iphone+4%22&_trkparms=65%253A15%257C66%253A2%257C39%253A1&_dmd=1&_dmpt=Cell_Phones&_mPrRngCbx=1&_sc=1&_sticky=1&_trksid=p3907.m551&_sop=12&_sc=1%26clkid%3D6198561558861688578&_qi=RTM733776)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://cell-phones.shop.ebay.com/Cell-Phones-Smartphones-/3312/i.html?LH_TopRatedSellers=1&LH_ItemCondition=1&Brand=Apple%2520iPhone&LH_Price=100..%40c&_nkw=%22iphone+4%22&_trkparms=65%253A15%257C66%253A2%257C39%253A1&_dmd=1&_dmpt=Cell_Phones&_mPrRngCbx=1&_sc=1&_sticky=1&_trksid=p3907.m551&_sop=12&_sc=1%26clkid%3D6198561558861688578&_qi=RTM733776)|
|Evri|none|[example](http://www.evri.com/organization/general-motors-0x4938f)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.evri.com/organization/general-motors-0x4938f)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.evri.com/organization/general-motors-0x4938f)|
|Facebook|API key and secret, OAuth token [See details](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtCartConfigFacebook)|[example](http://www.facebook.com/people/Richard-Max-Koster/1319314117)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.facebook.com/people/Richard-Max-Koster/1319314117)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.facebook.com/people/Richard-Max-Koster/1319314117)|
|Flickr|API Key|[example](http://farm1.static.flickr.com/212/496684670_7122c831ed.jpg)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/www.google.com/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.amazon.com/o/ASIN/0553383043)|
|Freebase|none|[example](http://www.freebase.com/view/location)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.freebase.com/view/location)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.freebase.com/view/location)|
|Geonames|none|[example](http://ws.geonames.org/search?q=london&maxRows=10&type=rdf)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/ws.geonames.org/search?q=london&maxRows=10&type=rdf)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://ws.geonames.org/search?q=london&maxRows=10&type=rdf)|
|geoURL|none|[example](http://geourl.org/near?p=wiki.worldflicks.org/saanen.html)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/geourl.org/near?p=wiki.worldflicks.org/saanen.html)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://geourl.org/near?p=wiki.worldflicks.org/saanen.html)|
|Get Satisfaction|none|[example](http://getsatisfaction.com/mozilla/topics/ubiquity_mostly_fails_on_mac_ppc)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/getsatisfaction.com/mozilla/topics/ubiquity_mostly_fails_on_mac_ppc)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://getsatisfaction.com/mozilla/topics/ubiquity_mostly_fails_on_mac_ppc)|
|Google+|API key [See details](http://edit-wiki.usnet.private/dataspace/dav/wiki/VOS/VirtCartConfigGooglePlus)|[example](https://plus.google.com/106795562240032292110)|[HTML Representation](http://linkeddata.uriburner.com/about/html/https/plus.google.com/106795562240032292110)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=https://plus.google.com/106795562240032292110)|
|Google Base|none|[example](http://www.google.com/base/feeds/snippets)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.google.com/base/feeds/snippets/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.google.com/base/feeds/snippets)|
|Google Book|none|[example](http://books.google.com/books?id=SRadJIuhVjAC&dq=GOOGLE&ie=ISO-8859-1&source=gbs_gdata)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://books.google.com/books?id=SRadJIuhVjAC&dq=GOOGLE&ie=ISO-8859-1&source=gbs_gdata)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://books.google.com/books?id=SRadJIuhVjAC&dq=GOOGLE&ie=ISO-8859-1&source=gbs_gdata)|
|Google Document|none|[example](http://docs.google.com/Present?docid=dc7jvc6m_1056g8fs54hp)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/docs.google.com/Present?docid=dc7jvc6m_1056g8fs54hp)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://docs.google.com/Present?docid=dc7jvc6m_1056g8fs54hp)|
|Google Social Graph|none|[example](http://socialgraph.apis.google.com/lookup?q=http://example.com/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/socialgraph.apis.google.com/lookup?q=http://example.com/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://socialgraph.apis.google.com/lookup?q=http://example.com/)|
|Google Spreadsheet|none|[example](http://spreadsheets.google.com/pub?key=p9pdwsai2hDMsLkXsoM05KQ&gid=1)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/spreadsheets.google.com/pub?key=p9pdwsai2hDMsLkXsoM05KQ&gid=1)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://spreadsheets.google.com/pub?key=p9pdwsai2hDMsLkXsoM05KQ&gid=1)|
|Hoovers|none|[example](http://www.hoovers.com/openlink/--ID__104304--/free-co-factsheet.xhtml)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.hoovers.com/openlink/--ID__104304--/free-co-factsheet.xhtml)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.hoovers.com/openlink/--ID__104304--/free-co-factsheet.xhtml)|
|ISBN|API Key|[example](http://isbndb.com/search-all.html?kw=King+Stephen)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/isbndb.com/search-all.html?kw=King+Stephen)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://isbndb.com/search-all.html?kw=King+Stephen)|
|LastFM|API Key|[example](http://www.last.fm/music/+noredirect/Teddy+Pendegrass)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.last.fm/music/+noredirect/Teddy+Pendegrass)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.last.fm/music/+noredirect/Teddy+Pendegrass)|
|LibraryThing|API Key|[example](http://www.librarything.com/work/1060)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.librarything.com/work/1060)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.librarything.com/work/1060)|
|LinkedIn|API key and secret, OAuth token [See details](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtCartConfigLinkedIn)|[example](http://www.linkedin.com/in/kidehen)|[HTML Representation](http://uriburner.com/about/html/http/uriburner.com/about/id/entity/http/www.linkedin.com/in/kidehen)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.linkedin.com/in/kidehen)|
|LSID|none|[example](http://lsid.tdwg.org/urn:lsid:ubio.org:namebank:11815)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/lsid.tdwg.org/urn:lsid:ubio.org:namebank:11815)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://lsid.tdwg.org/urn:lsid:ubio.org:namebank:11815)|
|Meetup|API Key|[example](http://www.meetup.com/Nonpracticing-Lawyers-Social-Support-Group/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.meetup.com/Nonpracticing-Lawyers-Social-Support-Group/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.meetup.com/Nonpracticing-Lawyers-Social-Support-Group/)|
|MusicBrainz|none|[example](http://musicbrainz.org/release/37e955d4-a53c-45aa-a812-1b23b88dbc13.html)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/musicbrainz.org/release/37e955d4-a53c-45aa-a812-1b23b88dbc13.html)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://musicbrainz.org/release/37e955d4-a53c-45aa-a812-1b23b88dbc13.html)|
|Ning Metadata|none|[example](http://www.ning.com/search?q=new+york+city&sf=rs&rs=1)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.ning.com/search?q=new+york+city&sf=rs&rs=1)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.ning.com/search?q=new+york+city&sf=rs&rs=1)|
|OAI|none|[example](http://news.cnet.com/IBM%2C-screensaver-to-tackle-smallpox/2100-1008_3-983374.html)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/news.cnet.com/IBM%2C-screensaver-to-tackle-smallpox/2100-1008_3-983374.html)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://news.cnet.com/IBM%2C-screensaver-to-tackle-smallpox/2100-1008_3-983374.html)|
|Open Social|none|[example](http://socialgraph.apis.google.com/otherme?pretty=1&q=www.openlinksw.com/blog/~kidehen/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/socialgraph.apis.google.com/otherme?pretty=1&q=www.openlinksw.com/blog/~kidehen/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://socialgraph.apis.google.com/otherme?pretty=1&q=www.openlinksw.com/blog/~kidehen/)|
|OpenLibrary|none|[example](http://openlibrary.org/b/OL1230137M)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/openlibrary.org/b/OL1230137M)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://openlibrary.org/b/OL1230137M)|
|OpenStreetMap|none|[example](http://openstreetmap.org/?lat=57.6569&lon=11.8886&zoom=14&layers=B000FTF)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/openstreetmap.org/?lat=57.6569&lon=11.8886&zoom=14&layers=B000FTF)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://openstreetmap.org/?lat=57.6569&lon=11.8886&zoom=14&layers=B000FTF)|
|oReilly|none|[example](http://oreilly.com/catalog/9780596523206/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/oreilly.com/catalog/9780596523206/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://oreilly.com/catalog/9780596523206/)|
|Picasa|none|[example](http://picasaweb.google.com/lh/explore#utm_medium=embed&utm_source=pwalogin)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://picasaweb.google.com/lh/explore#utm_medium=embed&utm_source=pwalogin)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://picasaweb.google.com/lh/explore#utm_medium=embed&utm_source=pwalogin)|
|Radio Pop|none|[example](http://www.radiopop.co.uk/users/tristanf/friends.xml)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.radiopop.co.uk/users/tristanf/friends.xml)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.radiopop.co.uk/users/tristanf/friends.xml)|
|relLicense|none|[example](http://creativecommons.org/licenses/by-nc/3.0/us/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/creativecommons.org/licenses/by-nc/3.0/us/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://creativecommons.org/licenses/by-nc/3.0/us/)|
|Revyu|none|[example](http://revyu.com/people/smonroe/about/html)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/revyu.com/people/smonroe/about/html)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://revyu.com/people/smonroe/about/html)|
|Rhapsody|none|[example](http://mp3.rhapsody.com/playlistdetail?playlistId=ply.25288413)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/mp3.rhapsody.com/playlistdetail?playlistId=ply.25288413)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://mp3.rhapsody.com/playlistdetail?playlistId=ply.25288413)|
|SalesForce.com|API Key,user login|[example](http://linkeddata.uriburner.com/about/rdf/https://na6.salesforce.com/0038000000ViF6k#this)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/linkeddata.uriburner.com/about/rdf/https://na6.salesforce.com/0038000000ViF6k#this)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://linkeddata.uriburner.com/about/rdf/https://na6.salesforce.com/0038000000ViF6k#this)|
|SlideShare|API Key, SharedSecret|[example](http://www.slideshare.net/rumito/rdf-views-of-sql-data-power-point-presentation-1-173180/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.slideshare.net/rumito/rdf-views-of-sql-data-power-point-presentation-1-173180/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.slideshare.net/rumito/rdf-views-of-sql-data-power-point-presentation-1-173180/)|
|SlideSix|none|[example](http://slidesix.com/view/ESWC2008SPARQLBIOpenLink)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/slidesix.com/view/ESWC2008SPARQLBIOpenLink)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://slidesix.com/view/ESWC2008SPARQLBIOpenLink)|
|SVG|none|[example](http://www.schepers.cc/semweb/rdf-diagram.svg)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.schepers.cc/semweb/rdf-diagram.svg)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.schepers.cc/semweb/rdf-diagram.svg)|
|Tesco|none|[example](http://www.tesco.com/superstore/xpi/6/xpi54427686.htm)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.tesco.com/superstore/xpi/6/xpi54427686.htm)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.tesco.com/superstore/xpi/6/xpi54427686.htm)|
|Tumblr|none|[example](http://cupcakesoftheday.tumblr.com/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://cupcakesoftheday.tumblr.com/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://cupcakesoftheday.tumblr.com/)|
|TWFY (theyworkforyou)|API Key|[example](http://www.theyworkforyou.com/mp/diane_abbott/hackney_north_and_stoke_newington)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.theyworkforyou.com/mp/diane_abbott/hackney_north_and_stoke_newington)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.theyworkforyou.com/mp/diane_abbott/hackney_north_and_stoke_newington)|
|Twitter|API key and secret, OAuth token [See details](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtCartConfigTwitter)|[example](http://twitter.com/kidehen)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://twitter.com/kidehen)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://twitter.com/kidehen)|
|Ustream|none|[example](http://www.ustream.tv/recorded/4848859/highlight/55618)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.ustream.tv/recorded/4848859/highlight/55618)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.ustream.tv/recorded/4848859/highlight/55618)|
|Web Resource CC (Licenses)|none|[example](http://creativecommons.org/licenses/by-nc-nd/2.5/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/creativecommons.org/licenses/by-nc-nd/2.5/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://creativecommons.org/licenses/by-nc-nd/2.5/)|
|Wikipedia|none|[example](http://en.wikipedia.org/wiki/House_MD)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://en.wikipedia.org/wiki/House_MD)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://en.wikipedia.org/wiki/House_MD)|
|xFolk|none|[example](http://blogmarks.net/marks/tag/hdd)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/blogmarks.net/marks/tag/hdd)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://blogmarks.net/marks/tag/hdd)|
|Yahoo! Finance|none|[example](http://finance.yahoo.com/q?s=AAPL)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/finance.yahoo.com/q?s=AAPL)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://finance.yahoo.com/q?s=AAPL)|
|Yahoo! SearchMonkey|none|[example](http://tech.groups.yahoo.com/group/ysearchboss/message/1983)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/tech.groups.yahoo.com/group/ysearchboss/message/1983)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://tech.groups.yahoo.com/group/ysearchboss/message/1983)|
|Yahoo! Traffic Data|none|[example](http://local.yahooapis.com/MapsService/rss/trafficData.xml?appid=YdnDemo&street=701+First+Avenue&city=Sunnyvale&state=CA)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/local.yahooapis.com/MapsService/rss/trafficData.xml?appid=YdnDemo&street=701+First+Avenue&city=Sunnyvale&state=CA)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://local.yahooapis.com/MapsService/rss/trafficData.xml?appid=YdnDemo&street=701+First+Avenue&city=Sunnyvale&state=CA)|
|Yahoo! Weather|none|[example](http://weather.yahooapis.com/forecastrss?p=94089)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/weather.yahooapis.com/forecastrss?p=94089)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://weather.yahooapis.com/forecastrss?p=94089)|
|Yelp|none|[example](http://api.yelp.com/business_review_search?term=yelp&tl_lat=37.9&tl_long=-122.5&br_lat=37.788022&br_long=-122.399797&limit=3&ywsid=XXXXXXXXXXXXXXXXXX)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/api.yelp.com/business_review_search?term=yelp&tl_lat=37.9&tl_long=-122.5&br_lat=37.788022&br_long=-122.399797&limit=3&ywsid=XXXXXXXXXXXXXXXXXX)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://api.yelp.com/business_review_search?term=yelp&tl_lat=37.9&tl_long=-122.5&br_lat=37.788022&br_long=-122.399797&limit=3&ywsid=XXXXXXXXXXXXXXXXXX)|
|Youtube|none|[example](http://www.youtube.com/watch?v=rOsPKjbMvxY)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.youtube.com/watch?v=rOsPKjbMvxY)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.youtube.com/watch?v=rOsPKjbMvxY)|
|Zillow|none|[example](http://www.zillow.com/homedetails/26-George-Rd-Maynard-MA-01754/57086765_zpid)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.zillow.com/homedetails/26-George-Rd-Maynard-MA-01754/57086765_zpid)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.zillow.com/homedetails/26-George-Rd-Maynard-MA-01754/57086765_zpid)|

  

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongerarch/#virtuosospongercartridgesmeta)

#### Meta Cartridges

A Meta Cartridge submits a Resource to a third-party Web Service for processing. Returned RDF supplements the RDF generated by Extractor and other Meta Cartridges. Locally generated RDF may also be submitted to the third-party services, instead-of or in-addition-to the original Resource itself.

Default Sponger behavior is for all installed Meta Cartridges to be brought to bear on all submitted Resources:

**Table 16.14.** 

|Cartridge|Needs|Sample URI|Resource Description|Linked Data Graph|Notes|
|---|---|---|---|---|---|
|Alchemy|API Key|[example](http://linkeddata.uriburner.com/about/id/entity/http/jira.codehaus.org/browse/CONTINUUM-884%01alchemy_entity_1)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/jira.codehaus.org/browse/CONTINUUM-884)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://jira.codehaus.org/browse/CONTINUUM-884)||
|Amazon Search for products|API Key, secret|[example](http://www.amazon.com/o/ASIN/0553383043#this)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.amazon.com/o/ASIN/0553383043)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.amazon.com/o/ASIN/0553383043)||
|BBC Links||[example](http://news.bbc.co.uk/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://twitter.com/bbcnews)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://twitter.com/bbcnews)||
|BestBuy Search for products|API Key|[example](http://www.bestbuy.com/site/KOSS+-+Pro+DJ100+Professional+Over-the-Ear+Headphones+-+Black/9745789.p?skuId=9745789&id=1218165774336)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.bestbuy.com/site/KOSS+-+Pro+DJ100+Professional+Over-the-Ear+Headphones+-+Black/9745789.p?skuId=9745789&id=1218165774336)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.bestbuy.com/site/KOSS+-+Pro+DJ100+Professional+Over-the-Ear+Headphones+-+Black/9745789.p?skuId=9745789&id=1218165774336)||
|Bing|API Key|[example](http://www.bing.com/videos/watch/video/cap-reattached-to-leaking-bp-well/6kn9out)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/twitter.com/bing)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://twitter.com/bing)||
|Bit.ly||[example](http://bit.ly/cGwRgc)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.springerlink.com/content/528h15634q332p02/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.springerlink.com/content/528h15634q332p02/)||
|CNET Search for products|API Key|[example](http://www.xomreviews.com/shopper.cnet.com)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.xomreviews.com/shopper.cnet.com)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.xomreviews.com/shopper.cnet.com)||
|Collecta||[example](http://www.crunchbase.com/company/microsoft)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.crunchbase.com/company/microsoft)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.crunchbase.com/company/microsoft)|Check rdfs:seeAlso [links](http://localhost:9301/about/html/http/social.msdn.microsoft.com/Forums/en-US/wpf/thread/108fbffc-c849-4d60-ab3e-00c425342aaf) found for microsoft.|
|Crunchbase||[example](http://www.crunchbase.com/company/radar-music-videos)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://techcrunch.com/2010/05/02/rapportive/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://techcrunch.com/2010/05/02/rapportive/)||
|Dapper Search||[example](http://www.dapper.net/dapplications/Blotter/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.alexa.com/siteinfo/dapper.net)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.alexa.com/siteinfo/dapper.net)||
|DBpedia Meta||[example](http://dbpedia.org/page/TweetDeck)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.programmableweb.com/api/dbpedia)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.programmableweb.com/api/dbpedia)||
|Delicious Meta|User Login|[example](http://delicious.com/tag/crunchbase)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/www.crunchbase.com/company/google)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://linkeddata.uriburner.com/about/id/entity/http/www.crunchbase.com/company/google)||
|Digg.com||[example](http://google.com/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/google.com/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://google.com/)|Check rdfs:seeAlso the [links](http://mashable.com/2010/07/12/google-app-inventor/) from Digg.com .|
|Discogs|API Key, php plugin, DBpedia Extractor|[example](http://www.discogs.com/Todd-Barton-and...ic-Poetry-Of-The-Kesh/release/2053074)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.amazon.com/o/ASIN/0553383043)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.amazon.com/o/ASIN/0553383043)||
|Document Links||example|HTML Representation|Data Explorer View||
|eBay Search for products|account, API Key|[example](http://shop.ebay.com/stores/__W0QQLHQ5fSellerWithStoreZ1QQ_nkwZtoys?_rdc=1)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/wordpress.xdroop.com/space/HotWheels/Buying+Hotwheels+On+eBay)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://wordpress.xdroop.com/space/HotWheels/Buying+Hotwheels+On+eBay)||
|Evri Meta||[example](http://www.evri.com/organization/apple-store-0x60ee5)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.evri.com/organization/apple-store-0x60ee5)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.evri.com/organization/apple-store-0x60ee5)||
|Facebook|API Key, secret, persistent-session-id.|[See details](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtCartConfigFacebook)|[example](http://www.facebook.com/people/Richard-Max-Koster/1319314117)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.facebook.com/people/Richard-Max-Koster/1319314117)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.facebook.com/people/Richard-Max-Koster/1319314117)||
|Flickr Search for photos|API Key|[example](http://farm5.static.flickr.com/4034/4406875198_7e562051cc.jpg)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/www.google.com/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://linkeddata.uriburner.com/about/id/entity/http/www.google.com/)||
|FOAF-Search||[example](http://www.slideshare.net/kidehen)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/www.slideshare.net/kidehen/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.slideshare.net/kidehen)|Check rdfs:seeAlso at: [link1](http://identi.ca/user/14092) , [link2](http://semantictweet.com/kidehen#me) , [link3](http://myopenlink.net:8890/dataspace/person/kidehen#this)|
|Foursquare||[example](http://foursquare.com/scobleizer)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/foursquare.com/scobleizer)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://foursquare.com/scobleizer)||
|Freebase NYTC|API Key|[example](http://linkeddata.uriburner.com/about/html/http/rdf.freebase.com/ns/en.john_kerry)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/html/http://www.freebase.com/view/en/john_kerry)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://linkeddata.uriburner.com/about/html/http://www.freebase.com/view/en/john_kerry)||
|Freebase NYTCF|API Key|[example](http://linkeddata.uriburner.com/about/html/http/rdf.freebase.com/ns/en.john_kerry)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/html/http://www.freebase.com/view/en/john_kerry)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://linkeddata.uriburner.com/about/html/http://www.freebase.com/view/en/john_kerry)||
|FriendFeed||[example](http://friendfeed.com/informationweek/0f212311/web-link-shrinkage-powers-spam-surge)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.informationweek.com/news/security/vulnerabilities/showArticle.jhtml?articleID=218401098)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.informationweek.com/news/security/vulnerabilities/showArticle.jhtml?articleID=218401098)||
|Geonames Meta||[example](http://ws.geonames.org/search?q=london&maxRows=10&type=rdf)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/ws.geonames.org/search?q=london&maxRows=10&type=rdf)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://ws.geonames.org/search?q=london&maxRows=10&type=rdf)||
|Geopoints||[example](http://www.geopoint.nl/en/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.mit.edu/~6.170/api/ps2/GeoPoint.html)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.mit.edu/~6.170/api/ps2/GeoPoint.html)||
|Gowalla||[example](http://gowalla.com/spots/7163409)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://gowalla.com/spots/7163409)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://gowalla.com/spots/7163409)||
|Get Glue Meta|User Login|[example](http://getglue.com/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://blog.adaptiveblue.com/?p=4746)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://blog.adaptiveblue.com/?p=4746)||
|Get Glue||[example](http://getglue.com/smartlinks)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.readwriteweb.com/archives/get_glue_on_your_iphone.php)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.readwriteweb.com/archives/get_glue_on_your_iphone.php)||
|Google Buzz||[example](http://google.com/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/google.com/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://google.com/)||
|Google Book||[example](http://www.google.com/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.google.com/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.google.com/)|Check rdfs:seeAlso links like [this one](http://books.google.com/*)|
|Google Plus||[example](https://plus.google.com/112399767740508618350)|[HTML Representation](http://linkeddata.uriburner.com/about/html/https://plus.google.com/112399767740508618350)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=https://plus.google.com/112399767740508618350)||
|Google Places||[example](http://maps.google.com/maps?cid=9095091124955696692)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://maps.google.com/maps?cid=9095091124955696692)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://maps.google.com/maps?cid=9095091124955696692)||
|Google Search||[example](http://linkeddata.uriburner.com/about/id/entity/http/www.google.com/finance?q=NYSE:MON%01Recognition1)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.google.com/finance?q=NYSE:MON)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.google.com/finance?q=NYSE:MON)||
|Google Social Graph||[example](http://www.openlinksw.com/dataspace/person/kidehen@openlinksw.com/about.rdf)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/www.openlinksw.com/blog/~kidehen/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/www.openlinksw.com/blog/~kidehen/)||
|Guardian|API Key|[example](http://www.guardian.co.uk/politics/2010/mar/15/gordon-brown-continue-as-labour-leader)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.alexa.com/siteinfo/guardian.co.uk)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.alexa.com/siteinfo/guardian.co.uk)||
|Hoovers|API Key|[example](http://www.hoovers.com/openlink/--ID__104304--/free-co-factsheet.xhtml)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.hoovers.com/company/OpenLink_Software_Inc/rfcyfci-1.html)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.hoovers.com/company/OpenLink_Software_Inc/rfcyfci-1.html)||
|Jigsaw (company)||[example](http://google.com/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/google.com/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://google.com/)|Check the c:location [link](proxy:entity/http/www.google.com/%23address)|
|Jigsaw (person)||[example](http://www.crunchbase.com/person/todd-sharp)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/www.crunchbase.com/person/todd-sharp)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.crunchbase.com/person/todd-sharp)|Check several Jigsaw search seeAlso [link](http://www.jigsaw.com/scid5307274/todd_sharp.xhtml) .|
|Journalisted||[example](http://journalisted.com/walter-gammie)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/whois.domaintools.com/journalisted.com)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://whois.domaintools.com/journalisted.com)||
|Last.FM|API Key|[example](http://linkeddata.uriburner.com/about/id/entity/http/www.last.fm/music/Rod+Stewart/Greatest+Hits)|[HTML Representation](http://linkeddata.uriburner.com/about/id/entity/http/www.last.fm/music/Rod+Stewart/Greatest+Hits)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.last.fm/music/Rod+Stewart/Greatest+Hits)||
|LinkedIn|API Key and Session Key;|[See details](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtLinkedInMeta)|[example](http://linkeddata.uriburner.com/about/id/entity/http/www.jigsaw.com/scid34931678/vinod_khosla.xhtml)|[HTML Representation](http://linkeddata.uriburner.com/about/id/entity/http/www.jigsaw.com/scid34931678/vinod_khosla.xhtml)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.jigsaw.com/scid34931678/vinod_khosla.xhtml)||
|Local Search||example|HTML Representation|Data Explorer View||
|LOD||[example](http://lod.openlinksw.com/b3s/search.vsp?q=1)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/lod.openlinksw.com/b3s/search.vsp?q=1)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://lod.openlinksw.com/b3s/search.vsp?q=1)||
|MIME Type||example|HTML Representation|Data Explorer View||
|New York Times|API Key|[example](http://www.nytimes.com/2005/03/17/technology/circuits/17stat.html?ex=1268715600&en=6840507aca561cf8&ei=5090&partner=rssuserland)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/download.cnet.com/New-York-Times-Crosswords-Monthly-Subscription/3000-2111_4-10918973.html)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://download.cnet.com/New-York-Times-Crosswords-Monthly-Subscription/3000-2111_4-10918973.html)||
|NPR Meta|API Key|[example](http://www.crunchbase.com/company/google)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.crunchbase.com/company/google)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.crunchbase.com/company/google)|Check rdfs:seeAlso links like: [link1](http://www.npr.org/templates/rss/podcast.php?id=510236) ; [link2](http://www.npr.org/templates/rss/podcast.php?id=510235) ; [link3](http://www.npr.org/templates/rss/podcast.php?id=510213) .|
|NYT: The Article Search||[example](http://twitter.com/bbcnews)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/twitter.com/bbcnews)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://twitter.com/bbcnews)|Check the rdfs:seeAlso: [link](proxy:entity/http/twitter.com/bbcnews%23nytimes_1) .|
|NYT: The TimesTags||[example](http://linkeddata.uriburner.com/about/html/http/rdf.freebase.com/ns/en.john_kerry)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/html/http://www.freebase.com/view/en/john_kerry)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://linkeddata.uriburner.com/about/html/http://www.freebase.com/view/en/john_kerry)||
|OpenCalais|any html page|[example](http://d.opencalais.com/er/company/ralg-tr1r/7cf71bb9-2969-35d3-8fa1-3723bdb5958c)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/news.cnet.com/8301-13505_3-9805771-16.html)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://news.cnet.com/8301-13505_3-9805771-16.html)||
|Oreilly Search for products||[example](http://linkeddata.uriburner.com/about/html/http/oreilly.com/catalog/9780596007973)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/oreilly.com/catalog/9780596007973/?@Lookup@=17&refresh=0)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://linkeddata.uriburner.com/about/id/entity/http/oreilly.com/catalog/9780596007973/?@Lookup@=17&refresh=0)||
|Primal||[example](http://www.google.com/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.google.com)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.google.com)|Check the set of sioc:topic and scot:hasScot.|
|ProgrammableWeb||[example](http://linkeddata.uriburner.com/about/id/entity/http/www.productwiki.com/samsung-un46c6400%01Product)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/www.productwiki.com/samsung-un46c6400%01Product)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://linkeddata.uriburner.com/about/id/entity/http/www.productwiki.com/samsung-un46c6400%01Product)||
|Provenance||[example](http://www.amazon.com/Catch-22-Joseph-Heller/dp/0684833395/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.amazon.com/Catch-22-Joseph-Heller/dp/0684833395/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.amazon.com/Catch-22-Joseph-Heller/dp/0684833395/)||
|Punkt||[example](http://linkeddata.uriburner.com/about/id/entity/http/www.youtube.com/watch?v=DrZvn1qckIs)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/www.youtube.com/watch?v=DrZvn1qckIs)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://linkeddata.uriburner.com/about/id/entity/http/www.youtube.com/watch?v=DrZvn1qckIs)||
|RapLeaf||[example](http://www.facebook.com/people/Roman-Korolenko/1465877213)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.crunchbase.com/service-provider/ivan-pr)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.crunchbase.com/service-provider/ivan-pr)||
|SameAs.org||[example](http://sameas.org/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.ckan.net/package/sameas)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.ckan.net/package/sameas)||
|Sindice||[example](http://sindice.com/developers/inspector?doReasoning=true&q=tim+berners+lee&qt=term&url=http%3A%2F%2Fwww.nylon.gr%2Ftag%2Ftim-berners-lee%2F)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.killerstartups.com/Web20/sindice-com-the-semantic-web-index)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.killerstartups.com/Web20/sindice-com-the-semantic-web-index)||
|SimpleGeo||[example](https://simplegeo.com/SG_0ODZdCvKJeB22EyTOyiLxO_37.772357_-122.405783@1294081369/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/https://simplegeo.com/SG_0ODZdCvKJeB22EyTOyiLxO_37.772357_-122.405783@1294081369/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=https://simplegeo.com/SG_0ODZdCvKJeB22EyTOyiLxO_37.772357_-122.405783@1294081369/)||
|Technorati|API Key|[example](http://support.technorati.com/support/siteguide/tags)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/download.cnet.com/Technorati-Tag/3000-12565_4-10658084.html)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://download.cnet.com/Technorati-Tag/3000-12565_4-10658084.html)||
|Tesco Product Search|User Login, DeveloperKey, ApplicationKey|[example](http://www.tesco.com/groceries/Product/Details/?id=252330678)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.tesco.com/groceries/Product/Details/?id=252330678)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.tesco.com/groceries/Product/Details/?id=252330678)|Check set of Tesco rdfs:seeAlso links like [this one](tesco:groceries/Product/Details/?id=252990345) .|
|Topsy||[example](http://google.com/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/google.com/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://google.com/)|Check the [rdfs:seeAlso](http://www1.folha.uol.com.br/folha/informatica/ult124u675304.shtml) from topsy.com.|
|TrueKnowledge||[example](http://www.microsoft.com/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.microsoft.com)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.microsoft.com)|Check set of rdfs:seeAlso links like: [link1](http://www.microsoft.com/) ; [link2](http://www.microsoft.com/worldwide) ; [link3](http://en.wikipedia.org/wiki/Microsoft) .|
|Tweetme||[example](http://google.com/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/google.com/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://google.com/)|Check the [rdfs:seeAlso](http://tweetmeme.com/story/12017895) link.|
|Twitter Meta|User Login|[example](http://twitter.com/Techmeme/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.techmeme.com/081001/p43)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.techmeme.com/081001/p43)||
|uClassify||[example](http://linkeddata.uriburner.com/about/id/entity/http/www.openlinksw.com/blog/~kidehen/%01Russian)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/html/http://www.openlinksw.com/blog/~kidehen/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://linkeddata.uriburner.com/about/html/http://www.openlinksw.com/blog/~kidehen/)||
|Uclassify||[example](http://www.crunchbase.com/company/google)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.crunchbase.com/company/google)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.crunchbase.com/company/google)|Check diff langs uc:class: [link](proxy:entity/http/www.crunchbase.com/company/google%23Arabic)|
|UMBEL|min-score, max-results|[example](http://fgiasson.com/blog/index.php/2008/08/29/umbel-as-a-coherent-framework-to-support-ontology-development/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/umbel.zitgist.com/api_philosophy.php)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http/umbel.zitgist.com/api_philosophy.php)||
|USA Today Best-Selling Books||[example](http://api.usatoday.com/open/bestsellers/books/titles?title=HARRY+POTTER&api_key=8ge2bvrna8x27wvc84qhz3e7&encoding=xml)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://api.usatoday.com/open/bestsellers/books/titles?title=HARRY+POTTER&api_key=8ge2bvrna8x27wvc84qhz3e7&encoding=xml)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://api.usatoday.com/open/bestsellers/books/titles?title=HARRY+POTTER&api_key=8ge2bvrna8x27wvc84qhz3e7&encoding=xml)||
|Ustream||[example](http://www.ustream.tv/recorded/4848859/highlight/55618)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.ustream.tv/recorded/4848859/highlight/55618)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.ustream.tv/recorded/4848859/highlight/55618)|Check rdfs:seeAlso links like: [this one](http://www.ustream.tv/recorded/7039249/highlight/75027) .|
|Virtuoso Faceted Web Service||example|HTML Representation|Data Explorer View||
|voID Statistics||example|HTML Representation|Data Explorer View||
|whoisi?||[example](http://whoisi.com/api/getPersonForURL?app=example&url=http://boatcovers.bestdealsoffer.com/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=)||
|World Bank|API Key|[example](http://linkeddata.uriburner.com/about/html/http/web.worldbank.org/WBSITE/EXTERNAL/TOPICS/EXTEDUCATION/0,,contentMDK:20263110~menuPK:531742~pagePK:210058~piPK:210062~theSitePK:282386,00.html)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.lib.berkeley.edu/doemoff/govinfo/intl/gov_ibrd.html)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.lib.berkeley.edu/doemoff/govinfo/intl/gov_ibrd.html)||
|WorldCat Basic Search||[example](http://www.crunchbase.com/company/yahoo)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.crunchbase.com/company/yahoo)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.crunchbase.com/company/yahoo)|Check seeAlso links like [this one](http://worldcat.org/oclc/613205142) .|
|xISBN|API Key|[example](http://isbndb.com/d/book/a_concise_history_of_italy_a02.html)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://isbndb.com/d/book/a_concise_history_of_italy_a02.html)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://isbndb.com/d/book/a_concise_history_of_italy_a02.html)|Check set of owl:sameAs links: [link1](http://purl.org/NET/book/isbn/0670236489#book) ; [link2](http://purl.org/NET/book/isbn/0500450102#book) .|
|XRD||[example](http://s2.googleusercontent.com/webfinger/?q=john@gmail.com)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/hueniverse.com/xrd/)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://hueniverse.com/xrd/)||
|Yahoo BOSS|API Key|[example](http://boss.yahooapis.com/ysearch/web/v1/UNITED+STATES?appid=cxgCRk3V34ElK7Amd8ieyy9eELzD7QrpAHTzOv6MeEBz56JUUgGi1x2vf_.pE.c-&format=xml&view=searchmonkey_rdf)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/twitter.com/kidehen?@Lookup@=10&refresh=0)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://linkeddata.uriburner.com/about/html/http://linkeddata.uriburner.com/about/id/entity/http/twitter.com/kidehen?@Lookup@=10&refresh=0)||
|Yahoo Geocode|API Key|[example](http://local.yahooapis.com/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http://www.programmableweb.com/api/yahoo-local-search)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.programmableweb.com/api/yahoo-local-search)||
|Yelp Search for business|API Key|[example](http://www.smallbusinesssem.com/inc-magazine-goes-deep-on-yelp/2669/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.readwriteweb.com/archives/yelp_assembles_small_business_advisory_board.php)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://www.readwriteweb.com/archives/yelp_assembles_small_business_advisory_board.php)||
|Zemanta|API Key, min-score, max-results|[example](http://developer.zemanta.com/wiki/helloworld/ruby)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/kobesearch.cpan.org/htdocs/Net-Zemanta/Net/Zemanta/Suggest.pm.html)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http://kobesearch.cpan.org/htdocs/Net-Zemanta/Net/Zemanta/Suggest.pm.html)||
|Zillow|API Key|[example](http://www.zillow.com/homedetails/26-George-Rd-Maynard-MA-01754/57086765_zpid/)|[HTML Representation](http://linkeddata.uriburner.com/about/html/http/www.crunchbase.com/company/zillow)|[Data Explorer View](http://linkeddata.uriburner.com/ode/?uri=http/www.crunchbase.com/company/zillow)||

  

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongerarch/#virtuosospongercartridgetypesmetarest)

##### Meta Cartridge Usage via REST Request

Description.vsp underlies the /about/html/ page, and accepts the parameters described below.

**Table 16.15.** 

|Parameter|Value|Description|Example|
|---|---|---|---|
|_@Lookup@_||The type of lookup||
||No Value|When value is not given (i.e., _@Lookup@=_ ), all will work as if the parameter were not present. %BR% The "Lookup" name is chosen to distinguish between parameters belonging to the URL being processed, and parameters for the Sponger.|[Refresh the graph with all current cartridges, either type](http://linkeddata.uriburner.com/about/html/http://www.apple.com/?@Lookup@=&refresh=0)|
||_0_|NLP meta only|[Execute only NLP meta extraction](http://linkeddata.uriburner.com/about/html/http://www.apple.com/?@Lookup@=0&refresh=0)|
||_-2_|Keywords-based only|[Execute only keywords-based meta extraction](http://linkeddata.uriburner.com/about/html/http://www.apple.com/?@Lookup@=-2&refresh=0)|
||_x,y..._|A list of meta cartridges to be executed, by their unique IDs. The ID column can be found in _Conductor -&gt; Linked Data -&gt; Sponger -&gt; Meta Cartridges_|[Execute only CNET (ID=19) and NYT: The TimesTags (ID=22) meta cartridges](http://linkeddata.uriburner.com/about/html/http://www.apple.com/?@Lookup@=19,22&refresh=0)|
|_refresh=0,1,2 etc._||_Usage_ : for cache invalidation. When used 1 or larger number (n), adds _get:refresh "N"_ (explicit refresh interval in seconds) as a directive to Sponger. A refresh of zero ("0") seconds will make a new graph on the next lookup with the '_@Lookup@_ ' parameter value.|[Refresh the graph with all current cartridges](http://linkeddata.uriburner.com/about/html/http://www.apple.com/?@Lookup@=&refresh=0)|
|_refresh=clean_||_Usage_ : for overwriting. The 'clean' usage explicitly clears the graph i.e. will cause the Sponger to drop cache even if it is marked to be in the fly. Thus, if network resource fetched cache by some reason is left in some inconsistent state like shutdown during the fetching, then 'clean' is required as it doesn't check cache state. _Note_ : must be used with caution as other threads may be doing Network Resource Fetch at same time.||

  

[¶](https://docs.openlinksw.com/virtuoso/virtuosospongerarch/#virtuosospongercartridgetypesmetarestexamples)

##### Meta Cartridges Parametrized Examples

All examples in the table below start from the same Resource, http://www.news.com, and submit it to the Sponger for processing with the single listed Meta Cartridge.

It can be informative to start by seeing what the results would be [with no Meta Cartridges at all](http://linkeddata.uriburner.com/about/html/http/www.news.com/?@Lookup@=99999&refresh=0) .

If you have a lot of time to spare, you may want to see what the results would be [with all Meta Cartridges combined](http://linkeddata.uriburner.com/about/html/http/www.news.com/?@Lookup@=&refresh=0) . As may be obvious, this must wait for each of the above services to respond, so it may take quite some time to return.

**Table 16.16.** 

|Cartridge|URL Pattern|Example|
|---|---|---|
|Alchemy|@Lookup@=8&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL1)|
|Amazon Search for products|@Lookup@=13&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL2)|
|BBC|@Lookup@=1665&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL3)|
|BestBuy Search for products|@Lookup@=14&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL4)|
|Bing|@Lookup@=11&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL5)|
|Bit.ly|@Lookup@=915&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL6)|
|CNET|@Lookup@=19&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL7)|
|Crunchbase|@Lookup@=839&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL8)|
|Dapper|@Lookup@=243&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL9)|
|DBpedia|@Lookup@=26&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL10)|
|Delicious Meta|@Lookup@=23&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL11)|
|Discogs|@Lookup@=840&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL12)|
|Document Links|@Lookup@=34&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL13)|
|eBay|@Lookup@=18&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL14)|
|Evri Meta|@Lookup@=3966&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL15)|
|Flickr Search for photos|@Lookup@=16&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL16)|
|Freebase NYTC|@Lookup@=5&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL17)|
|Freebase NYTCF|@Lookup@=4&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL18)|
|Geonames Meta|@Lookup@=24&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL19)|
|Geopoints|@Lookup@=3731&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL20)|
|Get Glue Meta|@Lookup@=25&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL21)|
|Google Search|@Lookup@=1382&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL22)|
|Google Social Graph|@Lookup@=30&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL23)|
|Guardian|@Lookup@=28&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL24)|
|Hoovers|@Lookup@=2&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL25)|
|Journalisted|@Lookup@=3174&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL26)|
|Local Search|@Lookup@=15&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL27)|
|LOD|@Lookup@=21&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL28)|
|MIME Type|@Lookup@=1029&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL29)|
|New York Times|@Lookup@=22&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL30)|
|NPR Meta|@Lookup@=29&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL31)|
|NYT: The Article Search|@Lookup@=9&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL32)|
|NYT: The TimesTags|@Lookup@=22&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL33)|
|OpenCalais|@Lookup@=1&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL34)|
|Oreilly Search for products|@Lookup@=17&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL35)|
|RapLeaf|@Lookup@=2745&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL36)|
|SameAs.org|@Lookup@=3257&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL37)|
|Sindice|@Lookup@=12&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL38)|
|Technorati|@Lookup@=27&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL39)|
|Tesco|@Lookup@=31&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL40)|
|TrueKnowledge|@Lookup@=3967&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL41)|
|Twitter|@Lookup@=4020&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL42)|
|uClassify|@Lookup@=3086&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL43)|
|UMBEL|@Lookup@=6&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL44)|
|Ustream|@Lookup@=3902&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL45)|
|Virtuoso Faceted Web Service|@Lookup@=21&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL46)|
|voID Statistics|@Lookup@=35&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL47)|
|whoisi?|@Lookup@=3052&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL48)|
|World Bank|@Lookup@=3&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL49)|
|XRD|@Lookup@=3650&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL50)|
|Yahoo BOSS|@Lookup@=10&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL51)|
|Yahoo Geocode|@Lookup@=2855&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL52)|
|Yelp Search for business|@Lookup@=20&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL53)|
|Zemanta|@Lookup@=7&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL54)|
|Zillow|@Lookup@=32&refresh=0|[cURL example](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamplescURL55)|