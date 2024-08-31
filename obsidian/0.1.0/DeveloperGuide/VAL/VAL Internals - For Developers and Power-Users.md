# Named Graphs Used Throughout VAL

VAL uses a set of private named graphs to store all kinds of configuration and user data. This includes ACL rules and the likes. The following sections give an overview of the graphs used in VAL.

## The VAL Configuration Graph

VAL uses one main configuration graph named `urn:virtuoso:val:config` (See also [VAL.DBA.val_config_graph_uri()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#af5427b8c92ded18a3237d00cb83e6795)).

This graph is typically filled manually or by UI.

## Graphs used in the VAL ACL System

VAL's own [The VAL ACL Rule and Group System](https://docs.openlinksw.com/valdocs/val_acl.html) uses a number of private graphs to store its data:

### VAL ACL Rule Graphs

VAL's ACL system uses one private graph for rules, one for groups, and one for restrictions. Each application realm defines its own set of rules, groups, and restrictions. Thus, each realm has its own set of these three private graphs. The following list shows the default graphs which can be customized as described in [Customizing the ACL Graphs](https://docs.openlinksw.com/valdocs/val_configuration.html#val_configuration_acl_graphs). (In the following examples `HOST` refers to the default hostname of the Virtuoso instance.)

- The graph that stores ACL rules consists of a prefix `[http://HOST/acl/graph/rules/](http://host/acl/graph/rules/)` and the URL-encoded realm URI (see also [VAL.DBA.val_acl_rule_graph()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a21952315f9ce1c577e1c0972ae6a1db5)).  
    **Example:** The rule graph for the default realm is `[http://HOST/acl/graph/rules/http%3A%2F%2Fwww.openlinksw.com%2Fontology%2Facl%23DefaultRealm](http://host/acl/graph/rules/http%3A%2F%2Fwww.openlinksw.com%2Fontology%2Facl%23DefaultRealm)`.
- The graph that stores ACL groups consists of a prefix `[http://HOST/acl/graph/groups/](http://host/acl/graph/groups/)` and the URL-encoded realm URI (see also [VAL.DBA.val_acl_group_graph()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a935d53cdc397308767d857e72478e64f)).  
    **Example:** The group graph for the default realm is `[http://HOST/acl/graph/groups/http%3A%2F%2Fwww.openlinksw.com%2Fontology%2Facl%23DefaultRealm](http://host/acl/graph/groups/http%3A%2F%2Fwww.openlinksw.com%2Fontology%2Facl%23DefaultRealm)`.
- The graph that stores ACL restrictions consists of a prefix `[http://HOST/acl/graph/restrictions/](http://host/acl/graph/restrictions/)` and the URL-encoded realm URI (see also [VAL.DBA.val_restrictions_graph()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a26dc228ed0bccde995e0fed880308b13)).  
    **Example:** The restrictions graph for the default realm is `[http://HOST/acl/graph/restrictions/http%3A%2F%2Fwww.openlinksw.com%2Fontology%2Facl%23DefaultRealm](http://host/acl/graph/restrictions/http%3A%2F%2Fwww.openlinksw.com%2Fontology%2Facl%23DefaultRealm)`.

### VAL ACL Scheme Graph

To ensure that nobody can tamper with default access modes and the like it is important that the Openlink ACL and restriction ontologies are stored in a private trusted graph.

VAL uses the ACL schema graph `urn:virtuoso:val:acl:schema` for this purpose. It is mandatory for both the [ACL](http://www.openlinksw.com/ontology/acl#) and the [restriction](http://www.openlinksw.com/ontology/restrictions#) ontologies to be loaded into this graph for the VAL ACL system to work properly.

Other applications also need to copy their specific ACL scope definitions into this graph.

See also

[VAL.DBA.get_acl_schema_graph](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga1c832c5509c57c7dcb4f1128ff656d8f "The VAL ACL Schema graph IRI.") ()

### VAL ACL Resource Ownership Graphs

VAL defines one resource ownership graph group for each scope. The graph consists of a prefix `urn:virtuoso:val:ownership:` and the URL-encoded scope URI (see also [VAL.DBA.ownership_graph_group](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga2bc430de1c302d6fff5d01b79e98454e "The URI of the graph group used to combine all resource ownership graphs.") ()).  
**Example:** The ownership graph group for the private graph scope is `urn:virtuoso:val:ownership:http%3A%2F%2Fwww.openlinksw.com%2Fontology%2Facl%23PrivateGraphsScope`.

## VAL owl:sameAs graph

VAL uses private graph `urn:virtuoso:val:online:accounts` (see also VAL.DBA.val_owl_sameas_graph()) to store `owl:sameAs` relations for all service ids which are considered to identify the same person. See also [VAL.DBA.update_user_online_mapping()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gacca9cce5aa606bba90e105a88f5d9c80).