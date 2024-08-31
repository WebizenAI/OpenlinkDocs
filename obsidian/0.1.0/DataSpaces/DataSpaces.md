# OpenLink Data Spaces

- [What are Data Spaces?](https://ods.openlinksw.com/wiki/ODS/#What%20are%20Data%20Spaces%3F)

- [Why are Data Spaces important?](https://ods.openlinksw.com/wiki/ODS/#Why%20are%20Data%20Spaces%20important%3F)

- [What is](https://ods.openlinksw.com/wiki/ODS/#What%20is)

- [Challenges Alleviated via ODS](https://ods.openlinksw.com/wiki/ODS/#Challenges%20Alleviated%20via%20ODS)
- [Product Features](https://ods.openlinksw.com/wiki/ODS/#Product%20Features)

- [Query Service Support](https://ods.openlinksw.com/wiki/ODS/#Query%20Service%20Support)
- [Publishing Protocol Support](https://ods.openlinksw.com/wiki/ODS/#Publishing%20Protocol%20Support)
- [Web Services](https://ods.openlinksw.com/wiki/ODS/#Web%20Services)

- [Application Components](https://ods.openlinksw.com/wiki/ODS/#Application%20Components)
- [News](https://ods.openlinksw.com/wiki/ODS/#News)
- [Getting Started](https://ods.openlinksw.com/wiki/ODS/#Getting%20Started)

- [Installation Guides](https://ods.openlinksw.com/wiki/ODS/#Installation%20Guides)
- [How Do I...](https://ods.openlinksw.com/wiki/ODS/#How%20Do%20I...)
- [Intranet Quick Start Guides](https://ods.openlinksw.com/wiki/ODS/#Intranet%20Quick%20Start%20Guides)

- [Third-Party Platform Integration](https://ods.openlinksw.com/wiki/ODS/#Third-Party%20Platform%20Integration)

- [Installation Guides](https://ods.openlinksw.com/wiki/ODS/#Installation%20Guides)
- [Live Demonstrations](https://ods.openlinksw.com/wiki/ODS/#Live%20Demonstrations)

- [FAQs](https://ods.openlinksw.com/wiki/ODS/#FAQs)
- [ODS Tutorials](https://ods.openlinksw.com/wiki/ODS/#ODS%20Tutorials)
- [Reference Guides](https://ods.openlinksw.com/wiki/ODS/#Reference%20Guides)
- [Weblogs & Commentary](https://ods.openlinksw.com/wiki/ODS/#Weblogs%20%26%20Commentary)
- [Additional Information](https://ods.openlinksw.com/wiki/ODS/#Additional%20Information)

## What are Data Spaces?

A named structured data cluster within a distributed data network where each item of data (each "datum") has a unique identifier. Fundamental characteristics of data spaces include:

- Each Data Item is a Data Object endowed with a unique HTTP-based Identifier
- Data Object Identity is distinct from its Content, Structure, and Location (Address)
- Data Object Representation is delivered via structured content constrained by a Schema (in this case the Entity-Attribute-Value model)
- Creation, Update, and Deletion privileges are controlled by the Data Space owner.

In relation to the Web, data spaces provide clustered points of access to data object; basically, they provide structured data access partitioning just as 'machine names' provide name oriented partitioning for DNS and 'table names' the same for database systems.

### Why are Data Spaces important?

Data Spaces provide a powerful conceptual model based virtualization layer that sits atop heterogeneous data sources. They enable the creation, publication, and general management of structured data items (data objects) from a pool of disparate data sources. Examples include:

- Structured profiles for individuals or organizations (and other groups) exposing rich metadata for:
    - Online Accounts
    - Favorite Things
    - Likes and Dislikes
    - Areas of Interest
    - Product & Service Wish-Lists
    - Product & Service Offer-Lists
- Shared application spaces such as:
    - file sharing
    - calendars
    - bookmarks
    - feed subscriptions
    - blogs
    - wikis
    - discussions & conversations
    - instant messaging
    - publish (upstream) & subscribe (downstream) model data exchange

## What is OpenLink Data Spaces?

ODS is an industry standards-compliant data space platform that includes a broad collection of distributed collaborative applications covering: blogs, wikis, shared bookmarks, file management, calendaring, email, photo galleries, discussion forums, polls, and more.

Every item of data within an ODS instance is endowed with a de-referenceable URI. This enables any HTTP-compatible client to obtain a negotiated representation of the description of any ODS data item.

### Challenges Alleviated via ODS

User content across the Web, both Intranet and Extranet, is growing exponentially, while time, attention, and comprehension of the resulting data streams is at best static, and typically shrinking. Compounding the problem is the fact that the exponential growth of user generated data has resulted in a proliferation of data silos, due to the popularity of Web 2.0 solution patterns.

All of this is happening at a time when individuals and organizations alike are seeking to do more with less, by exploiting the agility-producing powers of "Open Data Access" across enterprise and/or Web domains.

### Product Features

#### Query Service Support

ODS supports a number of Query Services:

- [GData](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsGData)
- OpenSearch
- XQuery/XPath over HTTP
- Full Text Search over HTTP
- [SPARQL](http://virtuoso.openlinksw.com/wiki/main/Main/VOSSPARQL)

#### Publishing Protocol Support

ODS supports the following publishing protocols:

- [GData](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsGData)
- Atom 1.0
- Moveable Type
- MetaWeblog
- Blogger

#### Web Services

- [SOAP & REST APIs](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsFrameworkProgrammersGuideWebServices)

### Application Components

- [ODS-Framework](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsFramework) -- An [OpenID](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSOpenID)- and [Yadis](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSYadis)-compliant Framework for building Distributed Collaborative Applications that are equipped with Single-Sign-On (SSO) functionality and auto-generated RDF Data Spaces
- [ODS-Addressbook](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsAddressbook) -- An Address Book Manager
- [ODS-Bookmark-Manager](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsBookmarkManager) -- A Shared Bookmark Manager
- [ODS-Briefcase](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsBriefcase) -- A WebDAV[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebDAV&parent=ODSIndex)-based Unified Storage Solution that incorporates automated extraction and management of metadata
- [ODS-Calendar](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsCalendar) -- A Calendar manager
- [ODS-Community](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsCommunity) -- Group/Community Mode service for all of the ODS-* applications
- [ODS-Discussions](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsDiscussions) -- Web-based Newsgroups Aggregator and Reader.
- [ODS-eCRM](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdseCRM) -- Web-based Customer Relationship Manager.
- [ODS-Feed-Manager](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsFeedManager) -- An RSS 1.0, RSS 2.0, Atom, OPML, and OCS Feed Aggregator
- [ODS-Gallery](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsGallery) -- Photo & General Media Sharing
- [ODS-Mail](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsMail) -- A Web-based Email Client
- [ODS-Polls](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsPolls) -- Polls Manager
- [ODS-Weblog](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsBlog) -- A comprehensive blogging platform supporting all the major publishing protocols (Atom, Moveable Type, Meta Weblog, and Blogger) and includes automatic generation of content-syndication gems in RSS 1.0, RSS 2.0, Atom, SIOC, OPML, OCS, and other formats
- [ODS-Wiki](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsWiki) -- A Wiki Platform supporting the Atom Publishing Protocol, Twiki, MediaWiki[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/MediaWiki&parent=ODSIndex) (Wikimedia), and Creole markup dialects

### News

- [ODS OpenID and Yadis Release](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSOpenIDAnnounceText)
- [ODS OpenID support](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSOpenID)
- [ODS Yadis support](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSYadis)
- [ODS RDF Sink folder support](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSRDFSinkFolder)
- [OpenSocial API support](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSProgrammersGuideOpenSocial)
- [ODS <a>++ Links support](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsAPlusLinks)
- [WebDAV browse feature for ODS users](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsWebDAVBrowse)
- [(ODS) accounts perform SPARUL over SPARQL using the new "/sparql-auth" endpoint](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsSPARQLAuth)
- [Virtuoso ODS Ubiquity Commands support](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/VirtuosoOdsUbiquity)

### Getting Started

ODS is pre-installed as part of the demonstration database (`demo.db`) bundled with OpenLink[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OpenLink&parent=ODSIndex) Virtuoso Open-Source Edition. If you are running the server with the default demo database configuration, simply point your browser to `[http://localhost:8890/ods](http://localhost:8890/ods)`. See [Setting up ODS](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsConfig) for a simple configuration guide.

#### Installation Guides

- [Installing and Configuring ODS](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsConfig)
- [Amazon Elastic Compute Cloud (EC2)](http://virtuoso.openlinksw.com/wiki/main/Main/VirtInstallationEC2)

#### How Do I...

- [Get a Personal URI via ODS in 5 minutes or less!](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/GetAPersonalURIIn5MinutesOrLess)
- [Generate an X.509 Certificate hosted WebID?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSGenerateX509Certificate)
- [How can I use the WebID Identity Provider Proxy Service?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSWebIDIdpProxy)
- [How can I use the Delegated WebID Verification Service?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSWebIDIdP)
- [Constrain Resource Access To Group Members using SPARQL ASK Query and Web-accessible Linked Data?](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSPARQLSecurityWebIDSPARQLASKExample)
- [Constrain Resource Access Using Social Relationship Semantics and WebID?](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSPARQLSecurityWebIDSocialRelationshipSPARQLASKExample)
- [Use WebID Protocol?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSManageWebIDFeatures)
- [Set up PubSubHub in ODS?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/VirtODSPubSubHub)
- [Set Up PubSubHub to use WebID Protocol- or IP-based control lists?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/VirtPubSubHubACL)
- [Set up WebID ACL for ODS Dataspace Instance?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSWebIDACLInstanceSetting)
- [Use the OAuth supported features?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSManageOAuthFeatures)
- [Use the OAuth-Simple Web Discovery feature?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSManageOAuthWG)
- [Use the REST supported features?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSManageRESTFeatures)
- [Create & Share Automatic Content Tagging Rules](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/VirtTaggingManagement)
- [Use ODS Application Endpoints (URL Redirection)?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsAccessPoints)
- [Set up Login Authentication Keys?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsSetLoginAuthenticaionKeys)
- [Give My Data Space Content Tags Meaning via MOAT Ontology](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/VirtMOATSettings)
- [Get Data into Virtuoso Quad Store via the ODS-Briefcase's special RDF Sink Folder](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSRDFSinkFolder)
- [Manage my resources, bookmarks, contacts, calendar events and tasks?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSAppManageResources)
- [Use the Virtuoso ODS Ubiquity Commands?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/VirtuosoOdsUbiquity)
- [Set <a>++ links?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsAPlusLinks)
- [Register ODS User with OpenID2?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsOpenIDRegister)
- [Use WebDAV extractor to insert triples via SPARUL into the Quad Store](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/VirtWebDAVInsertQuadStore)
- [Learn About Virtuoso's SPARQL Query Language Support, By Example?](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSPARQLRef)
- [Manage Facebook integration?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsFacebookIntegration)
- [Use the Semantic Pingback?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSSemanticPingback)
- [Perform the Distributed Social Network use case specified by SWATO level 0?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSSWATOTutorial)
- [Perform SPARUL over SPARQL using the "/sparql-auth" endpoint?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsSPARQLAuth)
- [Synchronize my events, tasks and contacts using SyncML?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/VirtSyncMLAndroidToVirtuoso)
- [Administrate ODS User Profile using Third Party Languages?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/VirtuosoAppODSUsers)
- [Use SPARQL to Query?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSSPARQLQuerying)

#### Intranet Quick Start Guides

- [General Intranet Quick Start Guides](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsGettingStarted) by functionality realm

### Third-Party Platform Integration

#### Installation Guides

- [MediaWiki](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsIntegrationMediaWiki)
- [WordPress](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsIntegrationWordPress)
- [phpBB](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsIntegrationphpBB)
- [Drupal](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsIntegrationDrupal)
- [Facebook - Installation & Configuration](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsIntegrationFacebook)

#### Live Demonstrations

- [MediaWiki Demo Instance](http://demo.openlinksw.com/mediawiki/)
- [WordPress Demo Instance](http://demo.openlinksw.com/wp/)
- [phpBB3 Demo Instance](http://demo.openlinksw.com/phpBB3)
- [Drupal Demo Instance](http://demo.openlinksw.com/drupal)

### FAQs

- [Data Space FAQ](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/DataSpaceFAQ)
- [ODS FAQ](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsFAQ)

### ODS Tutorials

- [ODS-Profile Manger Usage Guide](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSProfileManagerGuide)
- [ODS SIOC Query Tutorial](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/VOSODSSparqlSamples)
- [ODS Ubiquity Commands Tutorials](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/VirtuosoOdsUbiquityTutorials)
- [OAuth Ubiquity Tutorial](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/VirtuosoOdsUbiquityTutorialsOAuth)
- [SPARQL OAuth Tutorial](http://virtuoso.openlinksw.com/wiki/main/Main/VirtOAuthSPARQL)
- [WebID Protocol & SPARQL Endpoint ACLs Tutorial](http://virtuoso.openlinksw.com/wiki/main/Main/VirtAuthFOAFSSLACL)
- [Register ODS User with OpenID2 Tutorial](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OdsOpenIDRegister)
- [SWATO Tutorial](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSSWATOTutorial)

### Reference Guides

- [SPARQL Tutorials Part 1: Using SIOC to Model the Linked Data Web](http://virtuoso.openlinksw.com/presentations/SPARQL_Tutorials/SPARQL_Tutorials_Part_1/SPARQL_Tutorials_Part_1.html)
- [SPARQL Tutorials Part 2: SPARQL Extensions in the Virtuoso Universal Server](http://virtuoso.openlinksw.com/presentations/SPARQL_Tutorials/SPARQL_Tutorials_Part_2/SPARQL_Tutorials_Part_2.html)
- [SPARQL Tutorials Part 3: SPARQL and Analytics](http://virtuoso.openlinksw.com/presentations/SPARQL_Tutorials/SPARQL_Tutorials_Part_3/SPARQL_Tutorials_Part_3.html)
- [SPARQL Tutorials Part 4: Exploring FOAF-, Atom OWL-, Annotea-, and SKOS-based Data Spaces on the Linked Data Web](http://virtuoso.openlinksw.com/presentations/SPARQL_Tutorials/SPARQL_Tutorials_Part_4/SPARQL_Tutorials_Part_4.html)
- [ODS Programmers' Guide](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSProgrammersGuide)
- [ODS SIOC Reference](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSSIOCRef)
- [Virtuoso OAuth Programmers' Guide](http://virtuoso.openlinksw.com/wiki/main/Main/VirtuosoOAuthProgrammersGuide).

### Weblogs & Commentary

- [Virtuoso Technology Blog](http://virtuoso.openlinksw.com/blog/)
- [Kingsley Idehen's Blog Data Space](http://www.openlinksw.com/blog/~kidehen)
- [Kingsley Idehen's Data Space commentary and articles](http://www.openlinksw.com/weblog/public/search.vspx?blogid=127&q=data%20spaces&type=text&output=html)
- [Orri Erling's Weblog Data Space](http://www.openlinksw.com/weblogs/oerling/).

### Additional Information

- [ODS Tips and Tricks Collection](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSTipsAndTricksGuide)
- [Understanding Data](http://goo.gl/pdkRI)
- [Understanding Data Objects](http://goo.gl/CBEZY).