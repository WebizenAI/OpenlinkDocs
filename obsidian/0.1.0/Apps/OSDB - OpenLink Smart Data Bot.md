https://osdb.openlinksw.com/osdb

OSDB is a Smart Agent that provides a single RESTful interface for interacting with a variety of Actions (operations) provided by APIs. Its only requirements are the APIs are HTTP-accessible and documented using one of the following:

- OpenAPI (formerly known as Swagger) Documents (JSON content-type).
- RDF language statements via HTML document metadata using Microdata, RDFa, RDF-Turtle or JSON-LD document notations -- using terms from the [Schema.org](https://schema.org/)  and [OpenLink Web Services](http://www.openlinksw.com/data/turtle/webservices.ttl)  vocabularies.
- JSON-LD, RDF-Turtle or RDF-XML documents -- using terms from the [Schema.org](https://schema.org/)  and [OpenLink Web Services](http://www.openlinksw.com/data/turtle/webservices.ttl)  vocabularies.

![](https://osdb.openlinksw.com/img/dastklohq01y.gif)

#### Users

- [User Guide](https://osdb.openlinksw.com/osdb/ui/help)
- [Services](https://osdb.openlinksw.com/osdb/ui/services)
- [Manage Services](https://osdb.openlinksw.com/osdb/ui/manage_services)

#### Developers

- [Configuration Guide](https://osdb.openlinksw.com/osdb/doc/config_guide)
- [REST API Documentation](https://osdb.openlinksw.com/osdb/doc/api/v1)
- [Access Control](https://osdb.openlinksw.com/osdb/doc/osdb_access_control.html)
- [OpenAPI Console ![](https://osdb.openlinksw.com/img/swagger.png)](https://osdb.openlinksw.com/osdb/api/console) 

At the current time OSDB has a built-in client binding to Facebook Messenger (with support for Alexa, Slack, Cortana, Siri and other agents planned). On the server side, it can bind to Virtuoso endpoints (using Sponger Middleware and/or SPARQL) and to 3rd party web services by importing machine-readable structured descriptions of these web services and the actions they provide.