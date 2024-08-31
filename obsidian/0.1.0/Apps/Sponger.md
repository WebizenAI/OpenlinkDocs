# Virtuoso Sponger

- [What Is The Sponger?](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSponger#What%20Is%20The%20Sponger%3F)
- [Why is it Important?](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSponger#Why%20is%20it%20Important%3F)
- [How Does It Work?](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSponger#How%20Does%20It%20Work%3F)
- [Installation Steps](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSponger#Installation%20Steps)

- [Sponger Cartridges included in a Standard Virtuoso Installation](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSponger#Sponger%20Cartridges%20included%20in%20a%20Standard%20Virtuoso%20Installation)

- [Extractor Cartridges](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSponger#Extractor%20Cartridges)

- [Supported Standard Non-RDF Data Formats](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSponger#Supported%20Standard%20Non-RDF%20Data%20Formats)
- [Supported Vendor-specific Non-RDF Data Formats](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSponger#Supported%20Vendor-specific%20Non-RDF%20Data%20Formats)

- [Meta Cartridges](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSponger#Meta%20Cartridges)

- [Sponger Cartridge-based, Dynamic Linked Data Cloud](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSponger#Sponger%20Cartridge-based%2C%20Dynamic%20Linked%20Data%20Cloud)

- [Sponger pragmas](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSponger#Sponger%20pragmas)
- [Sponger Cartridge Configuration](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSponger#Sponger%20Cartridge%20Configuration)
- [Sponger Usage Examples](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSponger#Sponger%20Usage%20Examples)
- [Other Related Pages](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSponger#Other%20Related%20Pages)

## What Is The Sponger?

The Virtuoso Sponger is the [Linked Data](http://dbpedia.org/resource/Linked_Data) middleware component of Virtuoso. It generates Linked Data from a variety of data sources, and supports a wide variety of data representation and serialization formats. The Sponger is transparently integrated into Virtuoso's SPARQL Query Processor where it delivers URI de-referencing within SPARQL query patterns, across disparate data spaces. It also delivers configurable smart HTTP caching services. Optionally, it can be used by the [Virtuoso Content Crawler](http://docs.openlinksw.com/virtuoso/admui.webservices.html#importtargets) to periodically populate and replenish data within the native RDF Quad Store.

The Sponger is also a full-fledged HTTP proxy service, directly accessible via SOAP or REST interfaces.

As depicted below, [OpenLink](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/OpenLink)'s broad portfolio of Linked-Data-aware products supports a number of routes for creating or consuming Linked Data. The Sponger provides a key platform for developers to generate quality data meshes from unstructured or semi-structured data sources.

[![](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSponger/Sponger_LinkedDataGenOptions_2014_v3.png)](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSponger/Sponger_LinkedDataGenOptions_2014_v3.png)

## Why is it Important?

A majority of the worlds data naturally resides in non-Linked-Data form at the current time. The Sponger delivers middleware that accelerates the bootstrap of the Semantic Data Web by unobtrusively generating Linked Data (typically in RDF form, today) from non-Linked-Data data sources. This "Swiss army knife" for on-the-fly Linked Data generation provides a bridge between the traditional Document Web and the Linked Data Web ("Data Web").

Sponging non-Linked-Data Web sources and converting their data content to Linked Data exposes that data in a canonical form for querying and inference, and enables fast and easy construction of Linked-Data-driven "mesh-ups" (as opposed to code-driven Web 2.0 mash-ups).

Linked Data extraction and instance data generation products that offer functionality similar to that demonstrated by the Sponger are also commonly referred to as "RDFizers."

## How Does It Work?

Designed with a pluggable architecture, the Sponger's core functionality is provided by [Cartridges](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSpongerCartridge). Each cartridge includes [Data Extractors](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSpongerCartridgeExtractor) which extract data from one or more data sources, and [Ontology Mappers](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSpongerCartridgeOntologyMapper) which map the extracted data to one or more ontologies/schemas, en route to producing RDF Linked Data.

Cartridges are highly customizable, and can be developed using any language supported by the Virtuoso Server Extensions API. This enables generation of structured linked data from virtually any resource type, rather than limiting users to resource types supported by the default Sponger Cartridge collection bundled as part of the Virtuoso Sponger VAD package (cartridges_dav.vad).

(See [an animation of the concept](http://virtuoso.openlinksw.com/screencasts/virtuoso-rdf-middleware3.swf), if the embed above fails in your browser.)

The Sponger also includes a pluggable name resolution mechanism that enables Custom Resolvers for naming schemes (e.g., URNs) associated with protocols beyond HTTP. Examples of custom resolvers include:

|[URN handler](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSponger?sort=0&col=1)|[Sample URI](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSponger?sort=1&col=2)|[Resource Description](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSponger?sort=2&col=3)|[Linked Data View](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSponger?sort=3&col=4)|[Linked Data Graph](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSponger?sort=4&col=5)|[Needs](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSponger?sort=5&col=6)|
|---|---|---|---|---|---|
|DOI|`doi:10.1038/35057062`|[HTML Representation](https://linkeddata.uriburner.com/about/html/doi:10.1038/35057062)|[Linked Data View](https://linkeddata.uriburner.com/describe/?url=doi:10.1038/35057062)|[Data Explorer View](https://linkeddata.uriburner.com/ode/?uri=doi:10.1038/35057062)|`hslookup` plugin; and enabling of relevant mappers for `html`, `pdf`, `xml`, etc.|
|LSID|`urn:lsid:ubio.org:namebank:12292`|[HTML Representation](https://linkeddata.uriburner.com/about/html/urn:lsid:ubio.org:namebank:12292)|[Linked Data View](https://linkeddata.uriburner.com/describe/?url=urn:lsid:ubio.org:namebank:12292)|[Data Explorer View](https://linkeddata.uriburner.com/ode/?uri=urn:lsid:ubio.org:namebank:12292)|None|
|OAI|`oai:dcmi.ischool.washington.edu:article/8`|[HTML Representation](https://linkeddata.uriburner.com/about/html/oai:dcmi.ischool.washington.edu:article/8)|[Linked Data View](https://linkeddata.uriburner.com/describe/?url=oai:dcmi.ischool.washington.edu:article/8)|[Data Explorer View](https://linkeddata.uriburner.com/ode/?uri=oai:dcmi.ischool.washington.edu:article/8)|None|

Cache expiration is managed through the **`[MinExpiration](http://docs.openlinksw.com/virtuoso/databaseadmsrv.html#ini_SPARQL)`** parameter in the `virtuoso.ini` file.

## Installation Steps

1. A default Virtuoso installation includes the **`cartridges`** VAD package, which includes all publicly-available Sponger cartridges and associated components. Check to ensure it is installed using the **System Admin** -> **Packages** tab of the Virtuoso Conductor.
    - If listed as uninstalled, click the **install** button to the right of the package.
    - If the `cartridges` VAD is not listed, it can be [downloaded now](https://vos.openlinksw.com/owiki/wiki/VOS/VOSDownload#Other%20Virtuoso-related%20Packages). Install the `cartridges_dav.vad` package using the Conductor UI from the **System Admin** -> **Packages** tab or by using iSQL:  
        
          
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
        
          
        
2. To enable data insertion into the Quad Store via SPARQL queries, you need to [assign `SPARQL_SPONGE` privileges to user `SPARQL`](http://docs.openlinksw.com/virtuoso/rdfsparql.html#rdfsupportedprotocolendpointuri). (Note: more sophisticated security is provided via [WebID based ACL protection](http://docs.openlinksw.com/virtuoso/rdfsparql.html#sparqloauthendpointfoafssl) of your SPARQL endpoint).
3. [Configuring Sponger Cartridges](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtConfigureCartridges)
    - [Sponger Cartridges Registering API Key](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSpongerCartridge)
    - [Extractor Cartridges](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSponger#ExtractorCartridges)
    - [Meta Cartridges](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSponger#MetaCartridges)
    - [See also our doc](http://docs.openlinksw.com/virtuoso/virtuososponger.html#virtuosospongercreatecustcartrrgst)

### Sponger Cartridges included in a Standard Virtuoso Installation

There are a few kinds of Cartridge, and many of each kind are included in a standard Virtuoso installation. Click [here](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSpongerCartridgeSupportedDataSources) for a breakdown of [OpenLink](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/OpenLink)-supported Data Sources.

#### Extractor Cartridges

An Extractor Cartridge processes a Resource of a given format, extracting RDF according to rules appropriate to that format. External data does not come into play; only the content of the Resource fed to the Sponger.

##### Supported Standard Non-RDF Data Formats

These Cartridges handle open formats -- typically community-developed, openly-documented, and freely-licensed data structures.

- [Complete list of supported Standard Non-RDF Data Formats](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSpongerCartridgeSupportedDataSourcesNonRDF)

##### Supported Vendor-specific Non-RDF Data Formats

These Cartridges handle closed formats -- typically proprietary; sometimes undocumented; possibly licensed to no-one except the format originator. Sometimes data may not be parsed as desired or expected, as many of these Cartridges have required reverse-engineering of the data format in question.

- [Complete list of supported Vendor-specific Non-RDF Data Formats](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSpongerCartridgeSupportedDataSourcesVendorNonRDF)

#### Meta Cartridges

A Meta Cartridge submits a Resource to a third-party Web Service for processing. Returned RDF supplements the RDF generated by Extractor and other Meta Cartridges. Locally generated RDF may also be submitted to the third-party services, instead-of or in-addition-to the original Resource itself.

Default Sponger behavior is for all installed Meta Cartridges to be brought to bear on all submitted Resources.

- [Complete list of supported Meta Cartridges](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSpongerCartridgeSupportedDataSourcesMeta)
- [Meta Cartridge Usage via REST Request](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSpongerCartridgeSupportedDataSourcesMetaREST)
- [Parametrized Examples of Meta Cartridge Usage via REST Request](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamples)

### Sponger Cartridge-based, Dynamic Linked Data Cloud

Click the image for a full-size, clickable version!

[![Sponger Cloud PNG](https://vos.openlinksw.com/owiki/wiki/VOS/ClickableVirtSpongerCloud/sponger-cloud.png)](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/ClickableVirtSpongerCloud)

## Sponger pragmas

Virtuoso's Sponger is a sophisticated piece of middleware that provides full Linked Data fidelity for pre-existing data objects or resources. This Linked Data is then accessible via HTTP-based Web Services, and SPARQL is enhanced with Sponger pragmas and some optional additions to the FROM clause. See [full list of supported pragmas and usage examples](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSpongerLinkedDataHooksIntoSPARQL).

## Sponger Cartridge Configuration

# Sponger Cartridge Configuration and Implementation Notes

The links below provide guidelines for configuring individual Sponger cartridges and/or implementation details:

### Background Information

- [Sponger OAuth Support via VAL](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/SpongerOAuthSupport)

### Extractor and Meta Cartridges

- [AngelList](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtCartConfigAngelList)
- [Crunchbase](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtCartConfigCrunchbase)
- [Disqus](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtCartConfigDisqus)
- [Facebook](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtCartConfigFacebook)
- [Foursquare](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtCartConfigFoursquare)
- [Google+](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtCartConfigGooglePlus)
- [Instagr.am](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtCartInstagramOAuth)
- [LinkedIn](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtCartConfigLinkedIn)
- [DataTXT](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtCartConfigDataTXT) (used to be Spaziodati)
- [Twitter](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtCartConfigTwitter)
- [XING](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtCartConfigXing)

- [Google Knowledge Graph meta cartridge](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtCartImplGoogleKnowledgeGraphMeta)

### Query Language Cartridges

- [Query Language Cartridges](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSpongerCartridgeSupportedDataSourcesQueryLanguages)
    - Freebase Query Editor
    - WolframAlpha
    - Yahoo! Query Language (YQL)

# OpenLink-supplied Virtuoso Sponger Cartridges

There are a few kinds of Cartridge, and many of each kind are included in a standard Virtuoso installation.

- [Extractor Cartridges](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSpongerCartridgeSupportedDataSources#Extractor%20Cartridges)

- [Supported Standard Non-RDF Data Formats](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSpongerCartridgeSupportedDataSources#Supported%20Standard%20Non-RDF%20Data%20Formats)
- [Supported Vendor-specific Non-RDF Data Formats](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSpongerCartridgeSupportedDataSources#Supported%20Vendor-specific%20Non-RDF%20Data%20Formats)

- [Meta Cartridges](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSpongerCartridgeSupportedDataSources#Meta%20Cartridges)
- [Sponger Cartridge based Dynamic Linked Data Cloud](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSpongerCartridgeSupportedDataSources#Sponger%20Cartridge%20based%20Dynamic%20Linked%20Data%20Cloud)
- [Related](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSpongerCartridgeSupportedDataSources#Related)

## Extractor Cartridges

An Extractor Cartridge processes a Resource of a given format, extracting RDF according to rules appropriate to that format. External data does not come into play; only the content of the Resource fed to the Sponger.

### Supported Standard Non-RDF Data Formats

These Cartridges handle open formats — typically community-developed, openly-documented, and freely-licensed data structures.

- [Complete list of supported Standard Non-RDF Data Formats](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSpongerCartridgeSupportedDataSourcesNonRDF)

### Supported Vendor-specific Non-RDF Data Formats

These Cartridges handle closed formats — typically proprietary; sometimes undocumented; possibly licensed to no-one except the format originator. Sometimes data may not be parsed as desired or expected, as many of these Cartridges have required reverse-engineering of the data format in question.

- [Complete list of supported Vendor-specific Non-RDF Data Formats](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSpongerCartridgeSupportedDataSourcesVendorNonRDF)

## Meta Cartridges

A Meta Cartridge submits a Resource to a third-party Web Service for processing. Returned RDF supplements the RDF generated by Extractor and other Meta Cartridges. Locally generated RDF may also be submitted to the third-party services, instead-of or in-addition-to the original Resource itself.

Default Sponger behavior is for all installed Meta Cartridges to be brought to bear on all submitted Resources.

- [Complete list of supported Meta Cartridges](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSpongerCartridgeSupportedDataSourcesMeta)
- [Meta Cartridge Usage via REST Request](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSpongerCartridgeSupportedDataSourcesMetaREST)
- [Parametrized Examples of Meta Cartridge Usage via REST Request](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSpongerCartridgeSupportedDataSourcesMetaRESTExamples)