## Virtuoso Authentication Layer

Source: https://docs.openlinksw.com/valdocs/index.html 

Virtuoso provides numerous options for access control - some specific to a particular realm. For instance:

- Protected SPARQL endpoints associated with specific authentication methods, e.g. /sparql-auth, /sparql-oauth, /sparql-webid
- SPARQL roles restrict the types of SPARQL commands a database user may perform.
- Graph level security allows the setting of permissions bit masks to set the read/write (and sponge) permissions on specific RDF graphs to control public or specific user access.

However, OpenLink’s preferred generic access control mechanism for Virtuoso is VAL, the Virtuoso Authentication Layer. VAL provides a generic ACL layer which can be used to protect many Virtuoso resources including SPARQL endpoints or graphs, WebDAV resources and access to the Sponger or individual Sponger cartridges.

VAL provides both authentication and access control services to Virtuoso through an internal Virtuoso API or by two public HTTP APIs, a ‘standard’ HTTP API and a RESTful variant, which manage rules and groups via their URLs. Both are Turtle-based. VAL supports systems like OpenID and a variety of OAuth services such as Facebook, Google, or Twitter.

Typically, users attempting to access a VAL-protected resource must first login and authenticate themselves through a VAL-supplied authentication dialog. After establishing a VAL session, their access permissions on the resource are checked. Virtuoso LDP resources and containers could be protected in this way, once the required VAL hooks are in place.

The supported authentication methods are:

- HTTP authentication (for users with a Virtuoso SQL user login)
- Basic PKI
- [OpenID](http://openid.net/specs/openid-authentication-2_0.html)
- [WebID + TLS](http://www.w3.org/wiki/WebID)
- Third party OAuth services (see also [Supported 3rd Party Services](https://docs.openlinksw.com/valdocs/val_services.html#val_services_third_party))

VAL’s generic ACL layer is fully RDF-based, storing rules and groups in the triple store in private graphs, and describing rules using [the W3C acl ontology](http://www.w3.org/ns/auth/acl#) and the [OpenLink ACL ontology](http://www.openlinksw.com/ontology/acl#). The system also supports restrictions which restrict arbitrary values based on the authenticated user. These can be used to limit the number of query results, enforce quotas etc.

In addition to the API VAL will install a new 401_page and 403_page for the /DAV vhost. SSL-enabled sites need to be manually configured via [VAL.DBA.create_val_vhosts()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a59db7e5873c813d54fdd85fd1ed03c01 "Create the necessary virtual hosts for using VAL authentication on the given endpoint.") to do the same on the https counterpart. The path of the new authentication page is `/val/authenticate`.vsp. This page can of course also be customized. It is recommended to look at its code to tweak the look.

# VAL Low-Level Authentication API

VAL provides the procedures required for any component in Virtuoso to use these authentication methods (see also [VAL Authentication API](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html)). There are basically two workflows:

## VAL OAuth-like Workflow

The OAuth-like workflow applies to OpenID as well as all supported OAuth-based services.

The workflow for a client is always the same irrespective of the service type:

1. The client requests an authentication URL via [VAL.DBA.thirdparty_authentication_url()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga6240c9d79e5a9816f7aa03cdbf73a170 "Create an authentication URL for any supported 3rd-party service.")
2. The client navigates to the returned URL allowing the user to authenticate with the 3rd party service.
3. The 3rd party service redirects to the generic callback procedure [VAL.DBA.thirdparty_callback()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#aae548a70d5c0aa191b0f0547cf98f0e8) which will complete the authentication procedure by for example requesting an OAuth access token. It will then call a previously configured procedure for custom processing and finally write an HTML 303 redirection result.

For more details of the possible parameters see the procedure documentation.

## VAL's Session Support

VAL supports the creation and usage of standard Virtuoso sessions as stored in `VSPX_SESSIONS`. Sessions are created via [VAL.DBA.new_user_session()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga4f5af9c98b75233c21a7edd7715ecc41) or [VAL.DBA.add_sid_to_url()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga756d433a798321a35d033b62c881b6ad).

This is the default mechanism for [VAL.DBA.thirdparty_authentication_url()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga6240c9d79e5a9816f7aa03cdbf73a170 "Create an authentication URL for any supported 3rd-party service."). [VAL.DBA.add_sid_to_url()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga756d433a798321a35d033b62c881b6ad) will create a new session id and add it to the given URL.

# VAL High-Level API

In addition to the low-level authentication API VAL also provides an `authentication.vsp` page and two procedures [VAL.DBA.get_authentication_details_for_connection()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga745878ab820820c45f26d15217824cfa "Checks for existing authentication information in the current connection.") and [VAL.DBA.logout()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga3b4ad3ebbecda2375698fff095d64f77 "Clear authentication information.") which allow to easily integrate [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") authentication into any Virtuoso application. Create a login link via [VAL.DBA.create_login_page_url()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gaca0ee199741126f9b1fda4e52ab3b143), let `authenticate.vsp` do most of the work and check the result via [VAL.DBA.get_authentication_details_for_connection()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga745878ab820820c45f26d15217824cfa "Checks for existing authentication information in the current connection.").

See [Adding VAL Support to a VSP-based Application](https://docs.openlinksw.com/valdocs/val_tutorials.html#val_tutorials_authenticate_vsp) for details.

# Configuration

Certain aspects of VAL require properly configured SSL endpoints for `/val/api` and `/DAV`. The former provides an https callback URL for OpenID and OAuth (always recommended but also mandatory for Box.com and Salesforce), the latter requires a custom 40x_page to enable all the VAL authentication methods.

VAL provides [VAL.DBA.setup_val_host()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a5677b0a2e39c8d6c92bc5683a331047c "Setup a VAL host.") which allows to create the necessary vhosts for a given host.

Also registry setting `val_always_use_https_callbacks` can be set to `1` for VAL to always use https callback URLs, not only for the services which require it.

See [VAL Configuration](https://docs.openlinksw.com/valdocs/val_configuration.html) for more configuration options.