[VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") provides a generic ACL layer which can be used to protect any resource. It is fully RDF-based, storing rules and groups in the triple store in private graphs, and describing rules via [the W3C acl ontology](http://www.w3.org/ns/auth/acl#) and the [OpenLink ACL ontology](http://www.openlinksw.com/ontology/acl#). The system provides both an internal API (accessible via VSP procedures) and a public HTTP API. In general it is recommended to use the latter as it includes VAL-powered authentication. The following chapters give an overview of the [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") ACL system and its usage in clients.

In addition to rules the system supports restrictions which, instead of granting access to resources, restrict arbitrary values based on the authenticated user. This can be used to limit the number of query results, enforce complex quotas, or any other numeric value. See [ACL Restrictions](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_restrictions) for details.

[VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") has special handling for two scopes ([Rule Scopes](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_rule_scopes)) of resources: graphs in the triple store (scope IRI oplacl:PrivateGraphs, see also [VAL.DBA.get_sparql_scope()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga27e327bb4de4c515266db21601600c0b "The IRI of the Private named graphs ACL rule scope.")) and Virtuoso DAV resources (scope oplacl:Dav, see also [VAL.DBA.get_dav_scope()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gabf8e31f7ee7b8babb2432ee54ce4a387 "The IRI of the DAV ACL rule scope.")). For details see [SPARQL ACL Rules - Defining access to private graphs](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_sparql) and [DAV ACL Rules](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_dav).

# ACL Rule System Overview

The ACL rule system provides the possibility for any authenticated person (this includes 3rd-party service ids which have no corresponding Virtuoso SQL account) to create ACL rules for any resource they own or that they have been granted the right for. Each rule and each group lives in an application realm. An arbitrary number of application realms can be created or used. The public HTTP API will always use the realm from the authentication information (or fall back to the default `oplacl:DefaultRealm` if the authentication information does not provide an application realm). The internal API has parameters to set the realm in addition to the rule or group details.

The most basic example of an ACL rule below grants read access for `[http://www.facebook.com/foobar](http://www.facebook.com/foobar)` to resource `[http://me.com/bla:](http://me.com/bla:)`

@prefix oplacl: <http://www.openlinksw.com/ontology/acl#> .

@prefix acl: <http://www.w3.org/ns/auth/acl#> .

<#rule> a acl:Authorization ;

oplacl:hasAccessMode oplacl:Read ;

acl:agent <http://www.facebook.com/foobar> ;

acl:accessTo <http://me.com/bla> ;

oplacl:hasScope <urn:myscope> .

In addition to individual persons ACL rules can grant access for a simple group, a conditional group, or everyone, i.e. make a resource public. The latter is achieved by granting access to `foaf:Agent:`

@prefix foaf: <http://xmlns.com/foaf/0.1/> .

<#group> acl:agentClass foaf:Agent .

Conditional groups do not consist of a list of members but instead define a set of conditions. Every authenticated person matching these conditions is seen as part of the group. See [Conditional Groups](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_groups_conditional) for details.

## Supported Rule Permission Modes

The ACL system is aware of the following permissions - there is, however, no restriction on the permissions to be stored, meaning an application can define their own permission and use that.

- oplacl:Read - The grantee is allowed to read the resource in question.
- oplacl:Write - The grantee is allowed to write or even delete the resource in question.
- oplacl:Sponge - The grantee is allowed to sponge into or from the given graph. This permissions obviously does only apply to SPARQL realm data (see also [SPARQL ACL Rules - Defining access to private graphs](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_sparql)).
- oplacl:GrantRead - The grantee is allowed to define ACL rules which grant read permissions on the given resource to others.
- oplacl:GrantWrite - The grantee is allowed to define ACL rules which grant write permissions on the given resource to others.
- oplacl:GrantSponge - The grantee is allowed to define ACL rules which grant sponge permissions on the given resource to others. This permissions obviously does only apply to SPARQL realm data (see also [SPARQL ACL Rules - Defining access to private graphs](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_sparql)).

## Individuals - Supported Person Identifiers

IRIs are used to denote (name or "refer to") agents (people, places, software, machines, or other entities capable of mechanized operation) in the ACL system. Any service supported by [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") is also supported in this system. In other words: any agent IRI that can be verified via [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") authentication can be used as the target of a resource access privilge grant. This ranges from Facebook URIs and G+ accounts to Mozilla Persona identifiers and [WebID](http://www.w3.org/wiki/WebID)s (See the [ODS API documentation](http://web.ods.openlinksw.com/odsdox/group__ods__module__user.html#gada9926a1513e45b817e6f15ec9faf882) for a full list with examples.).

Internal Virtuoso SQL accounts are denoted by their personal data space URI, even if ODS is not installed. This means that SQL user `foobar` is denoted by personal URI `[http://HOST/dataspace/person/foobar#this](http://host/dataspace/person/foobar#this)`.

## Groups

Simple groups which consist of a set of members are defined as `foaf:Group` (or more presise its sub-class oplacl:StaticGroup which is merely used for easy distinction from conditional groups - oplacl:ConditionalGroup).

Statis groups are defined as follows:

@prefix foaf: <http://xmlns.com/foaf/0.1/> .

@prefix oplacl: <http://www.openlinksw.com/ontology/acl#> .

<#group> a foaf:Group, oplacl:StaticGroup ;

foaf:name "My Friends" ;

foaf:member <http://www.linkedin.com/in/bugsbunny> ,

<acct:123456789@dropbox.com> .

### Conditional Groups

A conditional group does not consist of a set of members but a set of conditions. Each personal IRI matching all of these conditions is seen as being in that group. As such, the member of a conditional group are not a fixed set and can change at any point in time.

Conditional Groups have their roots in [WebID](http://www.w3.org/wiki/WebID) authentication which means that many of the possible conditions refer to details of an X.509 client certificate. But the very generic SPARQL ASK query condition type allows to create virtually any condition type possible.

The following examples give an idea of the possibilities of conditional groups. The full set of possible conditions can be taken from the [OpenLink ACL Ontology](http://www.openlinksw.com/ontology/acl#Condition).

**Example:** Query condition

@prefix foaf: <http://xmlns.com/foaf/0.1/> .

@prefix oplacl: <http://www.openlinksw.com/ontology/acl#> .

<#group> a oplacl:ConditionalGroup ;

foaf:name "Everyone I know" ;

oplacl:hasQuery """

ask where {

graph <urn:mygraph> {

<http://www.facebook.com/me> foaf:knows ^{uri}^ .

}

}

""" .

This condition consists of a simple sparql ask query which checks if the authenticated user is known to a certain other identity as claimed in a certain graph. If `urn:mygraph` was a private graph controlled by the owner of the rule, then the group would be defined by the triples in that graph. The special notation `^{uri}^` is a placeholder for the authenticated personal IRI. Another supported placeholder is `^{graph}^` which refers to the graph containing the [WebID](http://www.w3.org/wiki/WebID) profile data.

## Recursive Rules

VAL supports recursive rules using oplacl:RecursiveAuthorizarion based on two concepts: file-system type URI-based recursion and relation-based recursion.

### Recursion Based On The URI

A recursive rule grants access to all sub-resources which start with the same prefix. This is typical for file systems: a recursive rule that grants access to `[http://HOST/DAV/home/foobar/test/](http://host/DAV/home/foobar/test/)` will also grant access to all children like `[http://HOST/DAV/home/foobar/test/hello.txt](http://host/DAV/home/foobar/test/hello.txt)`.

### Recursion Based On Relations

dcterms:hasPart relations in the VAL ACL schema graph `urn:virtuoso:val:acl:schema` ([VAL.DBA.get_acl_schema_graph()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga1c832c5509c57c7dcb4f1128ff656d8f "The VAL ACL Schema graph IRI.")) are taken into account. That means that a rule granting access to something like `urn:test` in combination with a triple like

sparql

prefix dcterms: <http://purl.org/dc/terms/>

insert into <urn:virtuoso:val:acl:schema> {

<urn:test> dcterms:hasPart <urn:test:child> .

<urn:test:child> dcterms:hasPart <urn:test:grandchild> .

}

will grant access to `urn:test:child` and `urn:test:grandchild` also.

## Resource Ownership

As mentioned above an authenticated user can only create ACL rules for resources they own or for which the owner granted them the corresponding grant permission (see [Supported Rule Permission Modes](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_permissions) for details). Resource ownership is stored in special graphs. These graphs are controlled by the application. Typically they are private graphs which need to be registered with the system via [VAL.DBA.add_ownership_graph()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga3eb4fcc5cff60079013beebdf58c9ae3 "Add a resource ownership graph.") and removed via [VAL.DBA.remove_ownership_graph()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gaa0dfb4fcb31b5bb3a6f51d9e5d6269da "Remove a resource ownership graph."). The resource ownership in these graphs is controlled by the application (not by [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") - the only exception is SPARQL, i.e. ownership of named graphs. see also [SPARQL ACL Rules - Defining access to private graphs](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_sparql)) via triples like

<https://plus.google.com/1056872387> foaf:made <http://HOST/something> .

This triple states that the Google Plus account `[https://plus.google.com/1056872387](https://plus.google.com/1056872387)` owns resource `[http://HOST/something](http://host/something)`.

Warning

Be aware that graph ownership for named graphs is controlled by [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") for internal reasons. Compare [VAL.DBA.add_graph_ownership()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ab5856e17c84a9224f4cbb58b3d7b5923), [VAL.DBA.set_graph_ownership()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a1b330f04d1153b55f8bcb1aa55bf5df4), and [VAL.DBA.remove_graph_ownership()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a22ecd911ad04cde5ea46b6a12e55828f).

DAV resource ownership is the second special case in [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules."). Instead of checking the ownership graphs [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") will check the actual `SQL` ownership of the resource and compare that to the authenticated user. Non SQL-users (3rd-party accounts) require `oplacl:GrantRead` etc. permissions instead. [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") uses a hook into the Virtuoso DAV system which will create grant ACL rules should a 3rd-party account create a new resource.

**Tip:** Since `dba` is allowed to create rules for any resource without restrictions one could even do without ownership by granting `oplacl:GrantRead` and friends to the "owner" or a resource. Even more important this allows for situations in which a user owns the data in a graph but is not allowed to change it via SPARQL - as is the case with ODS graphs which are controlled and populated through the ODS SQL tables.

## Application Realms

Each ACL rule, group, and restriction is defined in a specific application realm which is stored with the rule or group using the oplacl:hasRealm and with each restriction using the oplres:hasRealm property. Each application realm defines a distinct set of rules, groups, and restrictions. In the case of the public HTTP API the realm is taken from the authentication information, meaning that all API functions will only handle rules, groups and restrictions from the current realm. The internal API allows to specifiy the realm as a parameter which makes it more powerful (but with great power comes great responsibiliy - do not use it lightly).

The default realm is `oplacl:DefaultRealm`. This will use be used by [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") if no realm is specified.

### Virtual Host Specific Realm

The application realm can be configured in the virtual host options using the keyword `app_realm`. This will make VAL default to the configured realm rather than `oplacl:DefaultRealm`.

If one for example wanted to create a SPARQL endpoint which used a different set of ACL rules and groups from the default `/sparql` endpoint, one could create the corresponding virtual dir as follows:

[DB](https://docs.openlinksw.com/valdocs/namespaceDB.html).[DBA](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html).VHOST_DEFINE (

lpath=>'/mysparql',

ppath=>'/DAV/VAD/val/sparql',

is_dav=>1,

def_page=>'sparql.vsp',

vsp_user=>'dba',

ses_vars=>0,

opts=>vector (

'401_page', '401.vsp',

'403_page', '403.vsp',

'app_realm', 'urn:virtuoso:val:realms:myrealm'

),

is_default_host=>0

);

[VAL.DBA.get_authentication_details_for_connection()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga745878ab820820c45f26d15217824cfa "Checks for existing authentication information in the current connection.") will use the configured realm if no other is provided by the application page.

Warning

Be aware that for this to work properly the authentication page needs to be served from the same virtual host. Otherwise it will simply use the default realm again. See [Adding Login and Logout Links](https://docs.openlinksw.com/valdocs/val_tutorials.html#val_tutorials_authenticate_vsp_2) for an example.

## Rule Scopes

Each ACL rule has a scope like `oplacl:hasScope oplacl:PrivateGraphs`. This scope groups ACL rules by the type of resource they protect.

Scopes can be any arbitrary URI the application chooses to use. Ideally, however, they should be defined in the private acl schema graph `urn:virtuoso:val:acl:schema` ([VAL.DBA.get_acl_schema_graph()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga1c832c5509c57c7dcb4f1128ff656d8f "The VAL ACL Schema graph IRI.")). A typical scope definition looks as follows:

oplacl:Query a oplacl:Scope ;

rdfs:label "Query ACL Scope" ;

rdfs:comment """Query ACL scope which contains all ACL rules granting permission to perform SQL or SPARQL operations

in general. The latter is complemented by the private named graphs scope which contains rules for named graph access.""" ;

oplacl:hasApplicableAccess oplacl:Read, oplacl:Write, oplacl:Sponge, oplacl:CreatePublicGraph, oplacl:CreatePrivateGraph ;

oplacl:hasDefaultAccess oplacl:Read, oplacl:Write, oplacl:Sponge .

All scopes stored in the VAL scope graph can be accessed via convinience procedures [VAL.DBA.acls_enabled_for_scope()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gaf81eb3387fa574373af0282bf772a4a4 "Checks if ACL rule evaluation is enabled for a given scope.") and [VAL.DBA.get_default_access_for_scope()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga0c9da57d48c38613d17f593917d2e3ce "Get the list of default access modes for a given scope.") which allow applications to support disabling of ACL checks.

VAL itself defines three scopes by default for which it contains optimizations:

- `private` `named` `graphs` (scope IRI oplacl:PrivateGraphs, see also [VAL.DBA.get_sparql_scope()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga27e327bb4de4c515266db21601600c0b "The IRI of the Private named graphs ACL rule scope.")) groups rules protecting named graphs. This scope needs to be used for ACL rules if one wants to use [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.")'s SPARQL callback to enforce ACL rules. See [SPARQL ACL Rules - Defining access to private graphs](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_sparql) for details.
- `query` (scope IRI oplacl:Query, see also [VAL.DBA.get_query_scope()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gad7d45951926e95727372402cd3e97b51 "The IRI of the Query ACL rule scope.")) groups ACL rules to grant general permission to perform SQL or SPARQL queries, including access to the Virtuoso Sponging engine.
- `dav` (scope IRI oplacl:Dav, see also [VAL.DBA.get_dav_scope()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gabf8e31f7ee7b8babb2432ee54ce4a387 "The IRI of the DAV ACL rule scope.")) groups rules protecting dav resources, i.e. files and folders.

Additional scopes include:

- The Sponger Cartridges scope (oplacl:SpongerCartridges) groups ACL rules to grant permissions to use specific Sponger Cartridges. By default (i.e. when the scope is disabled) everybody is allowed to use all cartridges.
- The OAuth Scope (oplacl:OAuth) groups ACL rules granting access to the OAuth server part of [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules."). This includes the creation of OAuth applications. By default anyone can write which means create OAuth applications.

Scopes can easily be enabled and disabled in a certain realm by setting the corresponding value in the scope graph. If one for example wanted to enable system-wide evaluation of SPARQL rules in the default realm:

sparql

prefix oplacl: <http://www.openlinksw.com/ontology/acl#>

with <urn:virtuoso:val:config>

delete {

oplacl:DefaultRealm oplacl:hasDisabledAclScope oplacl:PrivateGraphs .

}

insert {

oplacl:DefaultRealm oplacl:hasEnabledAclScope oplacl:PrivateGraphs .

};

Be aware though that VAL's ACL rule checking procedures typically do not evaluate these scope settings. It is up to applications to enforce them. The only exception are the Virtuoso ACL hook procedures and the `/sparql` implementation which can be seen as clients to VAL themselves.

## Storage of Rules and Groups

Rules and groups are stored in private named graphs within the triple store. Each application realm typically has its own set of graphs for rules, groups, and restrictions. These graph IRIs can be customized as explained in [Customizing the ACL Graphs](https://docs.openlinksw.com/valdocs/val_configuration.html#val_configuration_acl_graphs).

The default graphs use the default hostname (`HOST` in the example below) of the Virtuoso instance and build a URI based on that and the realm URI.

**Example:** The default graph which stores the rules in the default realm is the following:

http://HOST/acl/graph/rules/http%3A%2F%2Fwww.openlinksw.com%2Fontology%2Facl%23DefaultRealm

Ideally one does not have to care about the graphs or how rules are stored, unless one wants to manage them without the API for whatever reason (not recommended since it circumvents the ownership checks).

Should one choose to manually manage rules it is important to note that the API adds the used realm to all created entities. For rules and groups:

<#rule> oplacl:hasRealm oplacl:DefaultRealm .

and for restrictions:

<#rest> oplres:hasRealm oplacl:DefaultRealm .

This essentially means that one could theoreticall use a single graph for all realms and all types of ACL resources.

# Querying Rules/Checking Permissions

The ACL API provides several ways to check for permissions. For internal use there are [VAL.DBA.check_acls_for_resource()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9a2351c047a02b3ce8457e49c804e3d8 "Find permissions for resources as set by ACL rules in a certain realm.") and friends which return a mapping of resources to their modes, as well as [VAL.DBA.find_acl_permissions_basic()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gae69de59e6668f5462635a0e6074f55de) and friends which create a result set instead that can be looped over.

Alternatively HTTP clients can use [VAL.VAL.acl.permissions.list()](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga4482c35b46473f3d5150478f3ed309c7 "List all existing rules in the current realm.") to get the permissions for a specific resource for the authenticated user.

As always using the HTTP API is recommended but vsp application developers might find it simpler to use the internal API.

Permissions for named graphs are a special case which is described in [SPARQL ACL Rules - Defining access to private graphs](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_sparql) and [Enforcing SPARQL ACL Rules](https://docs.openlinksw.com/valdocs/val_tutorials.html#val_tutorials_sparql_acl).

# SPARQL ACL Rules - Defining access to private graphs

The ACL system is a generic system which allows to define rules for any type of resource. To make life easier for developers [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") does handle sparql ACL rules as a special case.

As such [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") defines one special scope oplacl:PrivateGraphs ([VAL.DBA.get_sparql_scope()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga27e327bb4de4c515266db21601600c0b "The IRI of the Private named graphs ACL rule scope.")) which is used to store rules and groups pertaining named graphs. In addition ownership of named graphs is handled as a special case directly by [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules."). Compare [VAL.DBA.add_graph_ownership()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ab5856e17c84a9224f4cbb58b3d7b5923), [VAL.DBA.set_graph_ownership()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a1b330f04d1153b55f8bcb1aa55bf5df4), and [VAL.DBA.remove_graph_ownership()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a22ecd911ad04cde5ea46b6a12e55828f).

In order to make use of these ACL rules the `sql:gs-app-callback` SPARQL pragma needs to be used as follows:

define sql:gs-app-callback "VAL_SPARQL_PERMS"

This will tell the query engine to use the [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") graph security callback for graph permission checks. In addition the authenticated service id needs to be set with the `sql:gs-app-uid` pragma:

define sql:gs-app-uid "http://www.facebook.com/foobar"

This is the id which is used to evaluate ACL rules.

The special `uid` value `"nobody"` is supported to represent the fact that no user has logged in. In that case only public rules will be applied, ie. only graphs that are public according to the acl rules are accessed:

define sql:gs-app-uid "nobody"

If system permissions for `SQL` users should be taken into account (in addition to the ACL rules) - obviously this only applies to service ids that actually map to a `SQL` account - then the mapped username (or uid) needs to be set via:

connection_set ('val_sparql_uname', 'foobar');

Typically one would use the value provided by [VAL.DBA.get_authentication_details_for_connection()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga745878ab820820c45f26d15217824cfa "Checks for existing authentication information in the current connection.").

Also the application realm for the ACL rules can be changed from the default `oplacl:DefaultRealm` via a connection setting before issuing the query:

connection_set ('val_sparql_rule_realm', 'urn:myrealm');

Finally it is highly recommended to cache the [WebID](http://www.w3.org/wiki/WebID) profile (in the case of WebID authentication) in a temporary graph and set that graph via:

connection_set ('val_sparql_webid_graph', tmpWebidGraph);

That way the callback can pick it up and reuse it for all permission checks. Otherwise the profile has to be fetched for every permission check which results in a considerable performance drop. The simplest way to achieve this is to let [VAL.DBA.get_authentication_details_for_connection()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga745878ab820820c45f26d15217824cfa "Checks for existing authentication information in the current connection.") fetch the data by providing the temporary graph IRI to it and clearing the graph after executing the sparql query.

Warning

Be aware that ACL rules enforced via the callback only apply to private graphs. In other words for any graph Virtuoso SQL user `nobody` has access to ACLs will not be evaluated.

See [Enforcing SPARQL ACL Rules](https://docs.openlinksw.com/valdocs/val_tutorials.html#val_tutorials_sparql_acl) for an example.

It is recommended to run sparql queries as user `dba` since the Virtuoso graph security system only allows to lower permissions via the callback, not raise them. Thus, we need a user that has access to all graphs, including private graphs.

# DAV ACL Rules

The ACL system is generic in that it can be used to protect any resource clients with to protect. It does, however, include some special handling of Virtuoso DAV resources:

- VAL supports two types of DAV URLs to declare rules:
    1. The internal URLs using the absolute path in the DAV system grant generic access. An example looks like `dav:/DAV/home/demo/foobar.txt`.
    2. The URLs as seen by http clients which only grant access via that particular protocol (`http` vs. `https`) and virtual dir. An example could look like `[http://www.host.com/files/demo/foobar.txt](http://www.host.com/files/demo/foobar.txt)` which would use a virtual dir `/files` -> `/DAV/home`.
- Resource ownership for DAV resources (when using the correct DAV scope [VAL.DBA.get_dav_scope()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gabf8e31f7ee7b8babb2432ee54ce4a387 "The IRI of the DAV ACL rule scope.")) is checked via the unix-style permissions in the DAV system itself rather than checking the ownership graphs.

By installing VAL three hook procedures are created which integrate the ACL system with DAV:

- [DB.DBA.DBEV_CHECK_CONNECTION_AUTHENTICATION()](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#ab11662f0ac480f44e8e2f346c45155fc "Virtuoso callback for internal authentication.")
- [DB.DBA.DBEV_CHECK_PERMISSIONS()](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#a8b44e54066d7da56710fd0d1d285df4f "Virtuoso callback for internal ACLs.")
- [DB.DBA.DBEV_RES_CREATION_POST()](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#ac5b7f4185d0471f8c84e382790e3715f)

These procedures are used by the DAV system to check the ACLs setup in the DAV scope ([VAL.DBA.get_dav_scope()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gabf8e31f7ee7b8babb2432ee54ce4a387 "The IRI of the DAV ACL rule scope.")). The most interesting hook is [DB.DBA.DBEV_RES_CREATION_POST()](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#ac5b7f4185d0471f8c84e382790e3715f). It will create the necessary grant rules which allows a 3rd-party account without a connected SQL account to control newly created resources. This is very important as account like that cannot own DAV resources in a classical way. In fact, new resources created in such a context will have classical unix-style permissions of `000000000–` and be owned by the `nobody` user. This ensures that only the creating user can actually read and write those resources.

See [ACL Rule Examples](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_examples_rules) for examples of DAV access rules.

# ACL Restrictions

Besides classical ACL rules VAL allows to create restrictions. Restrictions can be seen as configuration values that are specific for a given person. Other than rules they do not grant rights but maximum or minimum limits on certain values. A typical example are request rates on an HTTP connection.

Restrictions, like rules, have a resource which they restrict. This is denotes by `oplres:hasRestrictedResource`. In addition one resource can have multiple restrictions attached to it by using the optional `oplres:hasRestrictedParameter`.

The internal VAL API provides some procedures to check restriction values:

- [VAL.DBA.find_restrictions_min()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga945480c6422506359ba72652b1b6e35e "Get the minimum restriction value for a given resource.")
- [VAL.DBA.find_restrictions_max()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gad3f57510dc6b58c3ab7a8aa548d92ec3 "Get the maximum restriction value for a given resource.")
- [VAL.DBA.find_restrictions()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gab7485fb9ae3ba202e9e27b6741a21901 "Find the restriction values for a given resource.")

In addition there is the public HTTP and RESTful APIs.

# The Public ACL HTTP API

See [The RESTful ACL API](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#val_acl_restful_api) and [VAL Public ACL HTTP API](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html).

# The Internal ACL API

See [VAL Internal ACL API](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html).

# The Internal ACL Utility API

See [VAL Internal ACL Utility API](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html).

# ACL Examples

## ACL Rule Examples

**Example:** Simple ACL rule sharing named graph `urn:foobar` with `facebook` ID `[http://www.facebook.com/john.tester](http://www.facebook.com/john.tester)`:

The scope oplacl:PrivateGraphs is reserved by [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") to handle rules granting permissions to named graphs.

@prefix oplacl: <http://www.openlinksw.com/ontology/acl#> .

@prefix acl: <http://www.w3.org/ns/auth/acl#> .

<#rule> a acl:Authorization ;

oplacl:hasAccessMode oplacl:Read ;

acl:accessTo <urn:foobar> ;

acl:agent <http://www.facebook.com/john.tester> ;

oplacl:hasScope oplacl:PrivateGraphs .

**Example:** ACL rule allowing Mozilla Persona identity `[harry@gmail.com](https://docs.openlinksw.com/valdocs/val_acl.html#)` to create ACL rules on named graph `urn:foobar`:

@prefix oplacl: <http://www.openlinksw.com/ontology/acl#> .

@prefix acl: <http://www.w3.org/ns/auth/acl#> .

<#rule> a acl:Authorization ;

rdfs:label "Allowed to grant read for urn:foobar" ;

oplacl:hasAccessMode oplacl:GrantRead ;

acl:accessTo <urn:foobar> ;

acl:agent <acct.persona:harry@gmail.com> ;

oplacl:hasScope oplacl:PrivateGraphs .

**Example:** ACL rule granting read/write permissions to a group of ids:

Given that a group with IRI `[http://HOST/acl/groups/42](http://host/acl/groups/42)` (substitute `HOST` with the appropriate value) was created before.

For examples of groups including conditional ones see [ACL Group Examples](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_examples_groups).

@prefix oplacl: <http://www.openlinksw.com/ontology/acl#> .

@prefix acl: <http://www.w3.org/ns/auth/acl#> .

<#rule> a acl:Authorization ;

oplacl:hasAccessMode oplacl:Read, oplacl:Write ;

acl:accessTo <urn:foobar> ;

acl:agent <http://HOST/acl/groups/42> ;

oplacl:hasScope oplacl:PrivateGraphs .

**Example:** ACL rule which grants generic access to DAV resource `/DAV/home/demo/foobar`.txt for LinkedIn ID `horstmeier:`

This rule allows `horstmeier` to access the DAV resource via any protocol and any virtual directory.

@prefix oplacl: <http://www.openlinksw.com/ontology/acl#> .

@prefix acl: <http://www.w3.org/ns/auth/acl#> .

<#rule> a acl:Authorization ;

oplacl:hasAccessMode oplacl:Read ;

acl:accessTo <dav:/DAV/home/demo/foobar.txt> ;

acl:agent <http://www.linkedin.com/in/horstmeier> ;

oplacl:hasScope oplacl:Dav .

**Example:** ACL rule which grants http-only access to DAV resource `/DAV/home/demo/foobar`.txt for LinkedIn ID `hildemeier:`

This rule allows `hildemeier` to access the DAV resource only via http.

@prefix oplacl: <http://www.openlinksw.com/ontology/acl#> .

@prefix acl: <http://www.w3.org/ns/auth/acl#> .

<#rule> a acl:Authorization ;

oplacl:hasAccessMode oplacl:Read ;

acl:accessTo <http://HOST/DAV/home/demo/foobar.txt> ;

acl:agent <http://www.linkedin.com/in/hildemeier> ;

oplacl:hasScope oplacl:Dav .

**Example:** ACL rule which grants http-only access to DAV resource `/home/demo/foobar`.txt for SQL user `joey:`

This rule allows `joey` to access the DAV resource only via http and only via the `/home` virtual dir serving that path.

@prefix oplacl: <http://www.openlinksw.com/ontology/acl#> .

@prefix acl: <http://www.w3.org/ns/auth/acl#> .

<#rule> a acl:Authorization ;

oplacl:hasAccessMode oplacl:Read ;

acl:accessTo <http://HOST/home/demo/foobar.txt> ;

acl:agent <http://HOST/dataspace/person/joey#this> ;

oplacl:hasScope oplacl:Dav .

**Example:** Recursive ACL rule which grants access to all DAV resources below `/DAV/home/demo/Public/` to everyone (Caution: recursive DAV rules should always use a trailing slash for the resource URL):

@prefix oplacl: <http://www.openlinksw.com/ontology/acl#> .

@prefix acl: <http://www.w3.org/ns/auth/acl#> .

@prefix foaf: <http://xmlns.com/foaf/0.1/> .

<#rule> a acl:Authorization, oplacl:RecursiveAuthorizarion ;

oplacl:hasAccessMode oplacl:Read ;

acl:accessTo <http://HOST/home/demo/Public/> ;

acl:agentClass foaf:Agent ;

oplacl:hasScope oplacl:Dav .

Warning

Should you decide to create rules manually using `SPARQL` `INSERT` (not recommended because it circumvents the security checks for ownership) be aware that the realm needs to be set on each rule:

<#rule> oplacl:hasRealm oplacl:DefaultRealm .

## ACL Group Examples

**Example:** A simple group which enumerates its members

@prefix foaf: <http://xmlns.com/foaf/0.1/> .

<#group> a foaf:Group ;

foaf:name "Some people" ;

foaf:member <http://dduck.wordpress.com> ,

<http://peterparker.tumblr.com/> .

**Example:** A conditional group which includes every validated X.509 client certificate. In other words: A rule which uses this group as an agent grants access to anyone who can provide a verifiable X.509 client certificate.

@prefix oplacl: <http://www.openlinksw.com/ontology/acl#> .

@prefix foaf: <http://xmlns.com/foaf/0.1/> .

<#group> a oplacl:ConditionalGroup ;

foaf:name "Valid Client Certificates" ;

oplacl:hasCondition [

a oplacl:GroupCondition, oplacl:GenericCondition ;

oplacl:hasCriteria oplacl:CertVerified ;

oplacl:hasComparator oplacl:EqualTo ;

oplacl:hasValue 1

] .

**Example:** A conditional group which includes every validated [WebID](http://www.w3.org/wiki/WebID). In other words: A rule which uses this group as an agent grants access to anyone who can provide a valid WebID certificate.

@prefix oplacl: <http://www.openlinksw.com/ontology/acl#> .

@prefix foaf: <http://xmlns.com/foaf/0.1/> .

<#group> a oplacl:ConditionalGroup ;

foaf:name "Valid WebIDs" ;

oplacl:hasCondition [

a oplacl:GroupCondition, oplacl:GenericCondition ;

oplacl:hasCriteria oplacl:WebIDVerified ;

oplacl:hasComparator oplacl:EqualTo ;

oplacl:hasValue 1

] .

**Example:** A conditional group which includes every validated identity (aka NetID). In other words: A rule which uses this group as an agent grants access to anyone who can provide a valid identifier (NetID). This includes [WebID](http://www.w3.org/wiki/WebID)s, Facebook accounts, OpenIDs, etc..

@prefix oplacl: <http://www.openlinksw.com/ontology/acl#> .

@prefix foaf: <http://xmlns.com/foaf/0.1/> .

<#group> a oplacl:ConditionalGroup ;

foaf:name "Valid Identifiers" ;

oplacl:hasCondition [

a oplacl:GroupCondition, oplacl:GenericCondition ;

oplacl:hasCriteria oplacl:NetID ;

oplacl:hasComparator oplacl:IsNotNull ;

oplacl:hasValue 1

] .

**Example:** A conditional group which includes identities based on a `SPARQL` `ASK` query. The conditional group defines one condition that has a query which simply checks if the authenticated user is mentioned as an object in a `foaf:knows` statement. So any identifier which is `foaf:known` to ODS user `trueg` will be part of the group.

@prefix oplacl: <http://www.openlinksw.com/ontology/acl#> .

@prefix foaf: <http://xmlns.com/foaf/0.1/> .

<#group> a oplacl:ConditionalGroup ;

foaf:name "People I foaf:know" ;

oplacl:hasCondition [

a oplacl:GroupCondition, oplacl:QueryCondition ;

oplacl:hasQuery "ask where { <http://trueg.dyndns.org:8890/dataspace/person/trueg#this> foaf:knows ^{uri}^ }"

] .

**Example:** A conditional group which includes any [WebID](http://www.w3.org/wiki/WebID) that claims to be a person in their profile. `^{graph}^` will be replaced with the profile graph corresponding to the authenticated identity, while `^{uri}^` will be replaced with the authenticated service identifier URI.

@prefix oplacl: <http://www.openlinksw.com/ontology/acl#> .

@prefix foaf: <http://xmlns.com/foaf/0.1/> .

<#group> a oplacl:ConditionalGroup ;

foaf:name "Persons" ;

oplacl:hasCondition [

a oplacl:GroupCondition, oplacl:QueryCondition ;

oplacl:hasQuery "ask where { graph ^{graph}^ { ^{uri}^ a foaf:Person } . }"

] .

Warning

Should you decide to create groups manually using `SPARQL` `INSERT` (not recommended because it circumvents the security checks for ownership) be aware that the realm needs to be set on each group:

<#group> oplacl:hasRealm oplacl:DefaultRealm .

## ACL Restrictions Examples

Restrictions, like rules, always apply to an agent or agent class.

**Example:** Restriction which sets a maximum of 1000 result set rows for the Virtuoso /sparql endpoint:

@prefix oplres: <http://www.openlinksw.com/ontology/restrictions#> .

@prefix foaf: <http://xmlns.com/foaf/0.1/> .

<#rest> a oplres:Restriction ;

rdfs:label "Restrict max result set rows" ;

oplres:hasRestrictedResource <urn:virtuoso:sparql:maxresultsetrows> ;

oplres:hasAgentClass foaf:Agent ;

oplres:hasMaxValue "1000"^^xsd:decimal .

**Example:** Restriction which makes an exception to the above rule by allowing a group of premium customers to query more rows:

@prefix oplres: <http://www.openlinksw.com/ontology/restrictions#> .

<#rest> a oplres:Restriction ;

rdfs:label "Restrict max result set rows for premium customers" ;

oplres:hasRestrictedResource <urn:virtuoso:sparql:maxresultsetrows> ;

oplres:hasAgent <http://HOST/acl/groups/9> ;

oplres:hasMaxValue "100000"^^xsd:decimal .

This example depends on a static group which enumerates the premium customers:

@prefix foaf: <http://xmlns.com/foaf/0.1/> .

<#group> a foaf:Group ;

foaf:name "Premium customers" ;

foaf:member <http://dduck.wordpress.com> ,

<http://peterparker.tumblr.com/> .

Warning

Should you decide to create restrictions manually using `SPARQL` `INSERT` (not recommended because it circumvents the security checks for ownership) be aware that the realm needs to be set on each restriction:

<#rest> oplres:hasRealm oplacl:DefaultRealm .

## ACL API Examples Using Curl

The following examples assume that a user session has been created via one of the login pages like `/sparql` or, if using a non-browser client, via `/val/api/login` (see [VAL.VAL.login](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga20284486a193239f08c9885596f01762 "Logs in a UI-less client, returning a session ID through a cookie sid.")) or through ODS. Other authentication mechanisms like HTTP digest login or OAuth are also supported, but they will always result in usage of the default realm.

**Example:** Obtain a session ID using /val/api/login with WebID authentication:

# curl -ikL --cert-type P12 --cert mycert.p12:mypassword https://HOST/val/api/login?service=webid

HTTP/1.1 200 OK

...

Set-Cookie: sid=c295ed6ff661...; path=/; expires=Mon, 13 Nov 2017 14:34:18 GMT

Content-Length: 181

{"status": "success", "httpcode": "200" "message": "Login successful. Logged in as: http://WEBID_HOST/sample_webid.ttl#identity" }

**Example:** Obtain a session ID using /val/api/login with HTTP digest authentication:

# curl -iL -u dba:dba --digest http://HOST/val/api/login?service=digest

HTTP/1.1 401 Unauthorized

...

WWW-Authenticate: Digest realm="http://www.openlinksw.com/ontology/acl#DefaultRealm", domain="/val/api/login", nonce="dc4268...", opaque="5ebe22...", stale="false", qop="auth", algorithm="MD5"

Content-Length: 0

HTTP/1.1 200 OK

...

Set-Cookie: sid=28b9c4af7e4...; path=/; expires=Thu, 16 Nov 2017 10:20:27 GMT

Content-Length: 92

{ "status": "success", "httpcode": "200" "message": "Login successful. Logged in as dba." }

**Example:** Create an ACL rule using the `GET`-based ACL API:

# curl "http://HOST/val/api/acl.rule.new?sid=SID \

&ruleData=%3Ax+a+acl%3AAuthorization+%3B%0A++foaf%3Aname+%22Allowed+to+grant+read+for+urn%3Afoobar%22+%3B%0A++\

acl%3Amode+oplacl%3AGrantRead+%3B%0A++acl%3AaccessTo+%3Curn%3Afoobar%3E+%3B%0A++acl%3Aagent+%3Cacct.persona%3Aharry%40gmail.com\

%3E+%3B%0A++oplacl%3AhasScope+%3Curn%3Avirtuoso%3Aval%3Ascopes%3Asparql%3E+.\

&format=text%2Fturtle"

**Example:** Create an ACL rule using the `REST`ful API. reading the rule from file `rule.ttl`:

# curl -X POST -H "Content-Type: text/turtle" -d @rule.ttl http://HOST/acl/rules?sid=SID

**Example:** Add a member to a group using the `REST`ful API:

# curl -X PATCH -H "Content-Type: text/turtle" -d "<#group> a foaf:Group ; foaf:member <acct:123456@dropbox.com> ." http://HOST/acl/groups/42?sid=SID

**Example:** Set the member of a group, overwriting the existing ones:

# curl -X PUT -H "Content-Type: text/turtle" -d "<#group> a foaf:Group ; foaf:member <acct:123456@dropbox.com> ." http://HOST/acl/groups/42?sid=SID

**Example:** List the groups in the authentication realm scoped to the `sid:`

# curl http://HOST/acl/groups?sid=SID

## ACL API Examples Using jQuery

**Example:** Create an ACL rule using the `REST`ful API:

var ruleData = '<#rule> a acl:Authorization ; \

oplacl:hasAccessMode oplacl:Read ; \

acl:accessTo <urn:foobar> ; \

acl:agent <http://www.facebook.com/john.tester> ; \

oplacl:hasScope oplacl:PrivateGraphs .';

$.ajax('http://HOST/acl/rules?sid=' + encodeURIComponent('SID'), {

type: 'POST',

contentType: 'text/turtle',

data: ruleData,

dataType: 'text'

});

We use a jQuery `ajax` request to perform a `POST`. We do authentication via a URL parameter. The `dataType` should be set to `text` to prevent jQuery from trying to hopelessly detect our default `text/turtle` return type.

**Example:** Add a member to a group using the `REST`ful API:

var ruleData = '<#group> a foaf:Group ; \

foaf:member <http://www.facebook.com/john.tester> .';

$.ajax('http://HOST/acl/rules/42?sid=' + encodeURIComponent('SID'), {

type: 'PATCH',

contentType: 'text/turtle',

data: ruleData,

dataType: 'text'

});

As before authentication information is set via a URL parameter.