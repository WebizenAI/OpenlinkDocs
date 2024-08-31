|   |   |
|---|---|
|## Functions|   |
||[VAL.DBA.add_ownership_graph](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga3eb4fcc5cff60079013beebdf58c9ae3) (varchar uri, varchar scope)|
||Add a resource ownership graph. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga3eb4fcc5cff60079013beebdf58c9ae3)|
||   |
||[VAL.DBA.add_resource_ownership](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga9ca7d11839530fd525f8e27b2f31cbc8) (varchar scope, varchar resource, varchar serviceId)|
||Add a resource ownership relation. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga9ca7d11839530fd525f8e27b2f31cbc8)|
||   |
||[VAL.DBA.check_acls_for_resource_basic](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gab6cf3963a149b67dcaa0fe6f84553f7d) (varchar serviceId, varchar resource=null, varchar realm, varchar mode=null, varchar scope=null, varchar sameAsGraph=null, int evalRecursiveRules=0)|
||Check Basic ACLs for a resource. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gab6cf3963a149b67dcaa0fe6f84553f7d)|
||   |
||[VAL.DBA.check_acls_for_resource_conditional](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga32a11e8482d82953d61ba58723939163) (varchar serviceId, varchar resource=null, varchar realm, varchar mode=null, varchar scope=null, varchar webidGraph=null, any certificate=null, varchar sameAsGraph=null, int evalRecursiveRules=0)|
||Check Conditional ACLs for a resource. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga32a11e8482d82953d61ba58723939163)|
||   |
||[VAL.DBA.check_acls_for_resource_ip_address](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga6fdbdf0af83dda6a465b71ee1035dc51) (varchar ipAddress, varchar resource=null, varchar realm, varchar mode=null, varchar scope=null, int evalRecursiveRules=0)|
||Check ACLs granting access to IP Addresses. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga6fdbdf0af83dda6a465b71ee1035dc51)|
||   |
||[VAL.DBA.check_acls_for_resource_public](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga7bd78e6bbeb0650cd410e15782ba5525) (varchar resource=null, varchar realm, varchar mode=null, varchar scope=null, int evalRecursiveRules=0)|
||Check Public ACLs for a resource. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga7bd78e6bbeb0650cd410e15782ba5525)|
||   |
||[VAL.DBA.check_resource_ownership](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gad799c6d8a25e07dd477590502d3b9731) (varchar serviceId, varchar resource, varchar scope, varchar sameAsGraph=null)|
||Check the ownership of a resource. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gad799c6d8a25e07dd477590502d3b9731)|
||   |
||[VAL.DBA.find_acl_permissions_basic](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gae69de59e6668f5462635a0e6074f55de) (varchar serviceId, varchar resource=null, varchar realm, varchar mode=null, varchar scope=null, varchar sameAsGraph=null, int evalRecursiveRules=0)|
||   |
||[VAL.DBA.find_acl_permissions_conditional](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gaf744e6431b91b7bdf9a9d9b85551c4af) (varchar serviceId, varchar resource=null, varchar realm, varchar mode=null, varchar scope=null, varchar webidGraph=null, any certificate=null, varchar sameAsGraph=null, int evalRecursiveRules=0)|
||   |
||[VAL.DBA.find_acl_permissions_ip_address](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga7212b4d513c2139d886f52c215ac27d5) (varchar ipAddress, varchar resource=null, varchar realm, varchar mode=null, varchar scope=null, int evalRecursiveRules=0)|
||   |
||[VAL.DBA.find_acl_permissions_public](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga28a729c0fa13d584023bb7aeac4d8687) (varchar resource=null, varchar realm, varchar mode=null, varchar scope=null, int evalRecursiveRules=0)|
||   |
||[VAL.DBA.find_restrictions_basic](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gae37e1bf2ef9317f32005cceee2824a84) (varchar serviceId, varchar resource, varchar realm, decimal minValue, decimal maxValue, varchar parameter=null, varchar sameAsGraph=null)|
||Find the restriction values from basic rules. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gae37e1bf2ef9317f32005cceee2824a84)|
||   |
||[VAL.DBA.find_restrictions_conditional](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gace67df8f7d7eb4882d21bc1f22050413) (varchar serviceId, varchar resource, varchar realm, varchar webidGraph=null, any certificate=null, decimal minValue, decimal maxValue, varchar parameter=null, varchar sameAsGraph=null)|
||Find the restriction values from conditional rules. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gace67df8f7d7eb4882d21bc1f22050413)|
||   |
||[VAL.DBA.find_restrictions_ip_address](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga9c992448ca7ff789e767206d1d72bc41) (varchar ipAddress, varchar resource, varchar realm, decimal minValue, decimal maxValue, varchar parameter=null)|
||Find the restriction values from IP Address based rules. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga9c992448ca7ff789e767206d1d72bc41)|
||   |
||[VAL.DBA.find_restrictions_public](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gae9dbe8048d87a1ac43cf187ed824201f) (varchar resource, varchar realm, decimal minValue, decimal maxValue, varchar parameter=null)|
||Find the restriction values from public rules. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gae9dbe8048d87a1ac43cf187ed824201f)|
||   |
||[VAL.DBA.get_acl_schema_graph](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga1c832c5509c57c7dcb4f1128ff656d8f) ()|
||The VAL ACL Schema graph IRI. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga1c832c5509c57c7dcb4f1128ff656d8f)|
||   |
||[VAL.DBA.get_dav_scope](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gabf8e31f7ee7b8babb2432ee54ce4a387) ()|
||The IRI of the DAV ACL rule scope. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gabf8e31f7ee7b8babb2432ee54ce4a387)|
||   |
||[VAL.DBA.get_owned_graphs](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gaa84c6ea7e257e469fed362afa0f995dd) (varchar serviceId)|
||Get the graphs owned by a given service id. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gaa84c6ea7e257e469fed362afa0f995dd)|
||   |
||[VAL.DBA.get_query_scope](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gad7d45951926e95727372402cd3e97b51) ()|
||The IRI of the Query ACL rule scope. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gad7d45951926e95727372402cd3e97b51)|
||   |
||[VAL.DBA.get_resource_owner](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gac425bf8c6cf3d2a6e005090cf0505f63) (varchar resource, varchar scope)|
||Get the owner of a resource. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gac425bf8c6cf3d2a6e005090cf0505f63)|
||   |
||[VAL.DBA.get_restrictions_scope](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gac79d434a51dc8ad154f8952f42983124) ()|
||The IRI of the Restrictions ACL rule scope. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gac79d434a51dc8ad154f8952f42983124)|
||   |
||[VAL.DBA.get_sparql_scope](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga27e327bb4de4c515266db21601600c0b) ()|
||The IRI of the Private named graphs ACL rule scope. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga27e327bb4de4c515266db21601600c0b)|
||   |
||[VAL.DBA.ownership_graph_group](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga2bc430de1c302d6fff5d01b79e98454e) (varchar scope)|
||The URI of the graph group used to combine all resource ownership graphs. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga2bc430de1c302d6fff5d01b79e98454e)|
||   |
||[VAL.DBA.remove_ownership_graph](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gaa0dfb4fcb31b5bb3a6f51d9e5d6269da) (varchar uri, varchar scope)|
||Remove a resource ownership graph. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gaa0dfb4fcb31b5bb3a6f51d9e5d6269da)|
||   |
||[VAL.DBA.set_resource_ownership](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga39324e0e0cf5fcaf259dac362357b92c) (varchar scope, varchar resource, varchar serviceId)|
||Set the owner of a resource in a given scope. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga39324e0e0cf5fcaf259dac362357b92c)|
||   |
||[VAL.DBA.sparql_graph_ownership_graph](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga52fe4f6da197f74fa77f9faf02414363) ()|
||Graph containing the ownership relations for named graphs. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga52fe4f6da197f74fa77f9faf02414363)|
||   |

## Detailed Description

The procedures in the utility API can be used in applications to enforce the ACL rules and to maintain [Resource Ownership](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_ownership). Most notably VAL.DBA.val_prepare_sparql_permissions_for_query() needs to be called before each SPARQL query to ensure proper permissions.

In contrast to the procedures in [VAL Internal ACL API](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html) the usage of these procedures is encouraged and often necessary.

## Function Documentation

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga3eb4fcc5cff60079013beebdf58c9ae3) add_ownership_graph()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.add_ownership_graph|(|varchar|_uri_,|
|||varchar|_scope_|
||)|||

Add a resource ownership graph.

[VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) uses the ownership definitions in all ownershop graphs to determine if a user is allowed to create ACL rules for a resource.

This procedure allows to add a named graph for [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) to search. This graph should contain triples like

<http://www.facebook.com/foobar> foaf:made <urn:someresource> .

This would allow the authenticated user `[http://www.facebook.com/foobar](http://www.facebook.com/foobar)` to create ACL rules for resource `urn:someresource`.

Be aware that the SPARQL ownership is handled by [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) via [VAL.DBA.add_graph_ownership()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ab5856e17c84a9224f4cbb58b3d7b5923) and [VAL.DBA.remove_graph_ownership()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a22ecd911ad04cde5ea46b6a12e55828f).

Also VAL provides convinience procedures like [VAL.DBA.set_resource_ownership](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga39324e0e0cf5fcaf259dac362357b92c "Set the owner of a resource in a given scope.") () to avoid the need for clients to define their own ownership graphs.

See also

[VAL.DBA.remove_ownership_graph()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gaa0dfb4fcb31b5bb3a6f51d9e5d6269da "Remove a resource ownership graph.")

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga9ca7d11839530fd525f8e27b2f31cbc8) add_resource_ownership()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.add_resource_ownership|(|varchar|_scope_,|
|||varchar|_resource_,|
|||varchar|_serviceId_|
||)|||

Add a resource ownership relation.

Instead of defining an ownership graph manually and adding it via [VAL.DBA.add_ownership_graph()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga3eb4fcc5cff60079013beebdf58c9ae3 "Add a resource ownership graph.") one can simply use [VAL.DBA.add_resource_ownership()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga9ca7d11839530fd525f8e27b2f31cbc8 "Add a resource ownership relation."), [VAL.DBA.set_resource_ownership()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga39324e0e0cf5fcaf259dac362357b92c "Set the owner of a resource in a given scope."), and [VAL.DBA.remove_resource_ownership()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a8fd5031bf4c4a047ab41caf266d73535) to simplify things and let VAL handle the rest.

This procedure will try to add a new ownership relation. In contrast to [VAL.DBA.set_resource_ownership()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga39324e0e0cf5fcaf259dac362357b92c "Set the owner of a resource in a given scope.") it will not overwrite existing ownership but throw a signal instead.

See also

[VAL.DBA.set_resource_ownership()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga39324e0e0cf5fcaf259dac362357b92c "Set the owner of a resource in a given scope."), [VAL.DBA.remove_resource_ownership()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a8fd5031bf4c4a047ab41caf266d73535)

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gab6cf3963a149b67dcaa0fe6f84553f7d) check_acls_for_resource_basic()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.check_acls_for_resource_basic|(|varchar|_serviceId_,|
|||varchar|_resource_ = `null`,|
|||varchar|_realm_,|
|||varchar|_mode_ = `null`,|
|||varchar|_scope_ = `null`,|
|||varchar|_sameAsGraph_ = `null`,|
|||int|_evalRecursiveRules_ = `0`|
||)|||

Check Basic ACLs for a resource.

Checks basic ACL rules for access to one or more resources. This includes rules which grant access to a person or a static group. Conditional groups are handled by [VAL.DBA.check_acls_for_resource_conditional()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga32a11e8482d82953d61ba58723939163 "Check Conditional ACLs for a resource.").

In general it is recommended to use [VAL.DBA.check_acls_for_resource()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9a2351c047a02b3ce8457e49c804e3d8 "Find permissions for resources as set by ACL rules in a certain realm.") instead.

Parameters

|   |   |
|---|---|
|serviceId|The service id which access is requested for.|
|resource|The optional resource to request access to. If not given all resources `serviceId` has access to are returned.|
|realm|The application realm in which permissions should be checked.|
|mode|The optional access mode to check for. If not given all granted access modes are returned.|
|scope|The optional scope of the queried rules. A scope defines the type of resource.|
|sameAsGraph|This is the graph from which [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) will read owl:sameAs triples to determine which service URIs denote the same person. This defaults to VAL.DBA.val_owl_sameas_graph () which is based on account mappings in VAL.DBA.VAL_USER_ONLINE_ACCOUNTS.|
|evalRecursiveRules|If `1` then recursive rules will be evaluated for scopes other than `DAV`. See [Recursion Based On Relations](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_recursive_rules_haspart) for details on how the rules are evaluated.|

Returns

A vector which contains key/value pairs mapping resources to a list of the granted access modes. The access modes are represented by URIs as stored in the ACLs

See also

[VAL.DBA.check_acls_for_resource()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9a2351c047a02b3ce8457e49c804e3d8 "Find permissions for resources as set by ACL rules in a certain realm."), [VAL.DBA.check_acls_for_resource_public()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga7bd78e6bbeb0650cd410e15782ba5525 "Check Public ACLs for a resource."), [VAL.DBA.check_acls_for_resource_conditional()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga32a11e8482d82953d61ba58723939163 "Check Conditional ACLs for a resource.")

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga32a11e8482d82953d61ba58723939163) check_acls_for_resource_conditional()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.check_acls_for_resource_conditional|(|varchar|_serviceId_,|
|||varchar|_resource_ = `null`,|
|||varchar|_realm_,|
|||varchar|_mode_ = `null`,|
|||varchar|_scope_ = `null`,|
|||varchar|_webidGraph_ = `null`,|
|||any|_certificate_ = `null`,|
|||varchar|_sameAsGraph_ = `null`,|
|||int|_evalRecursiveRules_ = `0`|
||)|||

Check Conditional ACLs for a resource.

Checks conditional ACL rules for access to one or more resources. This includes rules which grant access to a conditional group. Conditional groups are handled by [VAL.DBA.check_acls_for_resource_basic()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gab6cf3963a149b67dcaa0fe6f84553f7d "Check Basic ACLs for a resource.").

In general it is recommended to use [VAL.DBA.check_acls_for_resource()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9a2351c047a02b3ce8457e49c804e3d8 "Find permissions for resources as set by ACL rules in a certain realm.") instead.

Parameters

|   |   |
|---|---|
|serviceId|The service id which access is requested for.|
|resource|The optional resource to request access to. If not given all resources `serviceId` has access to are returned.|
|realm|The application realm in which permissions should be checked.|
|mode|The optional access mode to check for. If not given all granted access modes are returned.|
|scope|The optional scope of the queried rules. A scope defines the type of resource.|
|webidGraph|The optional named graph which contains the triples imported from the WebID profile if `certificate` contains an embedded WebID.|
|certificate|The optional client certificate used for authentication.|
|sameAsGraph|This is the graph from which [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) will read owl:sameAs triples to determine which service URIs denote the same person. This defaults to VAL.DBA.val_owl_sameas_graph () which is based on account mappings in VAL.DBA.VAL_USER_ONLINE_ACCOUNTS.|
|evalRecursiveRules|If `1` then recursive rules will be evaluated for scopes other than `DAV`. See [Recursion Based On Relations](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_recursive_rules_haspart) for details on how the rules are evaluated.|

Returns

A vector which contains key/value pairs mapping resources to a list of the granted access modes. The access modes are represented by URIs as stored in the ACLs

See also

[VAL.DBA.check_acls_for_resource()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9a2351c047a02b3ce8457e49c804e3d8 "Find permissions for resources as set by ACL rules in a certain realm."), [VAL.DBA.check_acls_for_resource_public()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga7bd78e6bbeb0650cd410e15782ba5525 "Check Public ACLs for a resource."), [VAL.DBA.check_acls_for_resource_basic()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gab6cf3963a149b67dcaa0fe6f84553f7d "Check Basic ACLs for a resource.")

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga6fdbdf0af83dda6a465b71ee1035dc51) check_acls_for_resource_ip_address()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.check_acls_for_resource_ip_address|(|varchar|_ipAddress_,|
|||varchar|_resource_ = `null`,|
|||varchar|_realm_,|
|||varchar|_mode_ = `null`,|
|||varchar|_scope_ = `null`,|
|||int|_evalRecursiveRules_ = `0`|
||)|||

Check ACLs granting access to IP Addresses.

Checks ACL rules for access to one or more resources. ACLs which grant access for service ids are handled by [VAL.DBA.check_acls_for_resource()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9a2351c047a02b3ce8457e49c804e3d8 "Find permissions for resources as set by ACL rules in a certain realm.").

Parameters

|   |   |
|---|---|
|ipAddress|The IP address which access is requested for.|
|resource|The optional resource to request access to. If not given all resources `serviceId` has access to are returned.|
|realm|The application realm in which permissions should be checked.|
|mode|The optional access mode to check for. If not given all granted access modes are returned.|
|scope|The optional scope of the queried rules. A scope defines the type of resource.|
|evalRecursiveRules|If `1` then recursive rules will be evaluated for scopes other than `DAV`. See [Recursion Based On Relations](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_recursive_rules_haspart) for details on how the rules are evaluated.|

Returns

A vector which contains key/value pairs mapping resources to a list of the granted access modes. The access modes are represented by URIs as stored in the ACLs

See also

[VAL.DBA.check_acls_for_resource()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9a2351c047a02b3ce8457e49c804e3d8 "Find permissions for resources as set by ACL rules in a certain realm."), [VAL.DBA.check_acls_for_resource_public()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga7bd78e6bbeb0650cd410e15782ba5525 "Check Public ACLs for a resource."), [VAL.DBA.check_acls_for_resource_conditional()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga32a11e8482d82953d61ba58723939163 "Check Conditional ACLs for a resource.")

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga7bd78e6bbeb0650cd410e15782ba5525) check_acls_for_resource_public()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.check_acls_for_resource_public|(|varchar|_resource_ = `null`,|
|||varchar|_realm_,|
|||varchar|_mode_ = `null`,|
|||varchar|_scope_ = `null`,|
|||int|_evalRecursiveRules_ = `0`|
||)|||

Check Public ACLs for a resource.

Checks public ACL rules for access to one or more resources. This means rules that grant access to `foaf:Agent`. Basic rules are handled by [VAL.DBA.check_acls_for_resource_basic()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gab6cf3963a149b67dcaa0fe6f84553f7d "Check Basic ACLs for a resource."), conditional groups are handled by [VAL.DBA.check_acls_for_resource_conditional()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga32a11e8482d82953d61ba58723939163 "Check Conditional ACLs for a resource.").

In general it is recommended to use [VAL.DBA.check_acls_for_resource()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9a2351c047a02b3ce8457e49c804e3d8 "Find permissions for resources as set by ACL rules in a certain realm.") instead.

Parameters

|   |   |
|---|---|
|resource|The optional resource to request access to. If not given all resources `serviceId` has access to are returned.|
|realm|The application realm in which permissions should be checked.|
|mode|The optional access mode to check for. If not given all granted access modes are returned.|
|scope|The optional scope of the queried rules. A scope defines the type of resource.|
|evalRecursiveRules|If `1` then recursive rules will be evaluated for scopes other than `DAV`. See [Recursion Based On Relations](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_recursive_rules_haspart) for details on how the rules are evaluated.|

Returns

A vector which contains key/value pairs mapping resources to a list of the granted access modes. The access modes are represented by URIs as stored in the ACLs

See also

[VAL.DBA.check_acls_for_resource()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9a2351c047a02b3ce8457e49c804e3d8 "Find permissions for resources as set by ACL rules in a certain realm."), [VAL.DBA.check_acls_for_resource_basic()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gab6cf3963a149b67dcaa0fe6f84553f7d "Check Basic ACLs for a resource."), [VAL.DBA.check_acls_for_resource_conditional()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga32a11e8482d82953d61ba58723939163 "Check Conditional ACLs for a resource.")

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gad799c6d8a25e07dd477590502d3b9731) check_resource_ownership()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.check_resource_ownership|(|varchar|_serviceId_,|
|||varchar|_resource_,|
|||varchar|_scope_,|
|||varchar|_sameAsGraph_ = `null`|
||)|||

Check the ownership of a resource.

Check if the given `serviceId` does own the given `resource` in the given `scope`. If `scope` is not `null` then specific ownership is tested. That means specific scopes can have their own way of defining ownership. A typical example is DAV which is checked via the permissions of the resource.

Returns

`1` in case `serviceId` does own `resource`, `0` otherwise.

See also

[VAL.DBA.add_ownership_graph()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga3eb4fcc5cff60079013beebdf58c9ae3 "Add a resource ownership graph.")

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gae69de59e6668f5462635a0e6074f55de) find_acl_permissions_basic()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.find_acl_permissions_basic|(|varchar|_serviceId_,|
|||varchar|_resource_ = `null`,|
|||varchar|_realm_,|
|||varchar|_mode_ = `null`,|
|||varchar|_scope_ = `null`,|
|||varchar|_sameAsGraph_ = `null`,|
|||int|_evalRecursiveRules_ = `0`|
||)|||

Find all permissions a given `serviceId` has on a given `resource` (or any resource if omitted) in the given application `realm`. If `mode` is specified, only that mode is verified and returned. This procedure only checks basic rules, ie. such rules that grant permissions to a person or a static group.

This procedure creates a result set. As such it is suitable for queries and can be used as follows:

for (select _resource, _mode

from VAL.DBA.find_acl_permissions_basic (s, res, rlm, m)(_resource varchar, _mode varchar) x

where s = myServiceId and

res = myResource and

rlm = myRealm and

m = myMode) do {

do_something_with_permissions (_resource, _mode);

}

See also

[VAL.DBA.check_acls_for_resource_basic()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gab6cf3963a149b67dcaa0fe6f84553f7d "Check Basic ACLs for a resource."), [VAL.DBA.find_acl_permissions_public()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga28a729c0fa13d584023bb7aeac4d8687), [VAL.DBA.find_acl_permissions_conditional()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gaf744e6431b91b7bdf9a9d9b85551c4af)

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gaf744e6431b91b7bdf9a9d9b85551c4af) find_acl_permissions_conditional()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.find_acl_permissions_conditional|(|varchar|_serviceId_,|
|||varchar|_resource_ = `null`,|
|||varchar|_realm_,|
|||varchar|_mode_ = `null`,|
|||varchar|_scope_ = `null`,|
|||varchar|_webidGraph_ = `null`,|
|||any|_certificate_ = `null`,|
|||varchar|_sameAsGraph_ = `null`,|
|||int|_evalRecursiveRules_ = `0`|
||)|||

Find all permissions a given `serviceId` has on a given `resource` (or any resource if omitted) in the given application `realm`. If `mode` is specified, only that mode is verified and returned. This procedure only checks conditional rules, ie. such rules that grant permissions to a conditional group.

This procedure creates a result set. As such it is suitable for queries and can be used as follows:

for (select _resource, _mode

from VAL.DBA.find_acl_permissions_conditional (s, res, rlm, m, wg, c)(_resource varchar, _mode varchar) x

where s = myServiceId and

res = myResource and

rlm = myRealm and

m = myMode and

wg = myWebidGraph and

c = myCertificate) do {

do_something_with_permissions (_resource, _mode);

}

See also

[VAL.DBA.check_acls_for_resource_conditional()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga32a11e8482d82953d61ba58723939163 "Check Conditional ACLs for a resource."), [VAL.DBA.find_acl_permissions_public()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga28a729c0fa13d584023bb7aeac4d8687), [VAL.DBA.find_acl_permissions_basic()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gae69de59e6668f5462635a0e6074f55de)

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga7212b4d513c2139d886f52c215ac27d5) find_acl_permissions_ip_address()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.find_acl_permissions_ip_address|(|varchar|_ipAddress_,|
|||varchar|_resource_ = `null`,|
|||varchar|_realm_,|
|||varchar|_mode_ = `null`,|
|||varchar|_scope_ = `null`,|
|||int|_evalRecursiveRules_ = `0`|
||)|||

Find all permissions a given `ipAddress` has on a given `resource` (or any resource if omitted) in the given application `realm`. If `mode` is specified, only that mode is verified and returned.

This procedure creates a result set. As such it is suitable for queries and can be used as follows:

for (select _resource, _mode

from VAL.DBA.find_acl_permissions_ip_address (ip, res, rlm, m)(_resource varchar, _mode varchar) x

where ip = myIpAddress and

res = myResource and

rlm = myRealm and

m = myMode) do {

do_something_with_permissions (_resource, _mode);

}

See also

[VAL.DBA.check_acls_for_resource_ip_address()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga6fdbdf0af83dda6a465b71ee1035dc51 "Check ACLs granting access to IP Addresses."), [VAL.DBA.find_acl_permissions_public()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga28a729c0fa13d584023bb7aeac4d8687), [VAL.DBA.find_acl_permissions_basic()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gae69de59e6668f5462635a0e6074f55de), [VAL.DBA.find_acl_permissions_conditional()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gaf744e6431b91b7bdf9a9d9b85551c4af)

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga28a729c0fa13d584023bb7aeac4d8687) find_acl_permissions_public()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.find_acl_permissions_public|(|varchar|_resource_ = `null`,|
|||varchar|_realm_,|
|||varchar|_mode_ = `null`,|
|||varchar|_scope_ = `null`,|
|||int|_evalRecursiveRules_ = `0`|
||)|||

Find all permissions granted by public rules on a given `resource` (or any resource if omitted) in the given application `realm`. If `mode` is specified, only that mode is verified and returned. This procedure only checks public rules, ie. such rules that grant permissions to `foaf:Agent`.

This procedure creates a result set. As such it is suitable for queries and can be used as follows:

for (select _resource, _mode

from VAL.DBA.find_acl_permissions_public (s, res, rlm, m)(_resource varchar, _mode varchar) x

where s = myServiceId and

res = myResource and

rlm = myRealm and

m = myMode) do {

do_something_with_permissions (_resource, _mode);

}

See also

[VAL.DBA.check_acls_for_resource_public()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga7bd78e6bbeb0650cd410e15782ba5525 "Check Public ACLs for a resource."), [VAL.DBA.find_acl_permissions_basic()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gae69de59e6668f5462635a0e6074f55de), [VAL.DBA.find_acl_permissions_conditional()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gaf744e6431b91b7bdf9a9d9b85551c4af)

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gae37e1bf2ef9317f32005cceee2824a84) find_restrictions_basic()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.find_restrictions_basic|(|varchar|_serviceId_,|
|||varchar|_resource_,|
|||varchar|_realm_,|
|||decimal|_minValue_,|
|||decimal|_maxValue_,|
|||varchar|_parameter_ = `null`,|
|||varchar|_sameAsGraph_ = `null`|
||)|||

Find the restriction values from basic rules.

This procedure will find the least restrictive values from all basic rules in the given `realm` for the given `resource`. This includes restrictions scoped to individuals and static groups.

`sameAsGraph` is the graph from which [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) will read owl:sameAs triples to determine which service URIs denote the same person. This defaults to VAL.DBA.val_owl_sameas_graph () which is based on account mappings in VAL.DBA.VAL_USER_ONLINE_ACCOUNTS.

Typically one would use [VAL.DBA.find_restrictions()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gab7485fb9ae3ba202e9e27b6741a21901 "Find the restriction values for a given resource.") instead.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gace67df8f7d7eb4882d21bc1f22050413) find_restrictions_conditional()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.find_restrictions_conditional|(|varchar|_serviceId_,|
|||varchar|_resource_,|
|||varchar|_realm_,|
|||varchar|_webidGraph_ = `null`,|
|||any|_certificate_ = `null`,|
|||decimal|_minValue_,|
|||decimal|_maxValue_,|
|||varchar|_parameter_ = `null`,|
|||varchar|_sameAsGraph_ = `null`|
||)|||

Find the restriction values from conditional rules.

This procedure will find the least restrictive values from all conditional rules in the given `realm` for the given `resource`. This means restrictions scoped to conditional groups.

`sameAsGraph` is the graph from which [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) will read owl:sameAs triples to determine which service URIs denote the same person. This defaults to VAL.DBA.val_owl_sameas_graph () which is based on account mappings in VAL.DBA.VAL_USER_ONLINE_ACCOUNTS.

Typically one would use [VAL.DBA.find_restrictions()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gab7485fb9ae3ba202e9e27b6741a21901 "Find the restriction values for a given resource.") instead.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga9c992448ca7ff789e767206d1d72bc41) find_restrictions_ip_address()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.find_restrictions_ip_address|(|varchar|_ipAddress_,|
|||varchar|_resource_,|
|||varchar|_realm_,|
|||decimal|_minValue_,|
|||decimal|_maxValue_,|
|||varchar|_parameter_ = `null`|
||)|||

Find the restriction values from IP Address based rules.

This procedure will find the least restrictive values from all IP Address based rules in the given `realm` for the given `resource`.

Typically one would use [VAL.DBA.find_restrictions()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gab7485fb9ae3ba202e9e27b6741a21901 "Find the restriction values for a given resource.") instead.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gae9dbe8048d87a1ac43cf187ed824201f) find_restrictions_public()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.find_restrictions_public|(|varchar|_resource_,|
|||varchar|_realm_,|
|||decimal|_minValue_,|
|||decimal|_maxValue_,|
|||varchar|_parameter_ = `null`|
||)|||

Find the restriction values from public rules.

This procedure will find the least restrictive values from all public rules in the given `realm` for the given `resource`.

Typically one would use [VAL.DBA.find_restrictions()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gab7485fb9ae3ba202e9e27b6741a21901 "Find the restriction values for a given resource.") instead.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga1c832c5509c57c7dcb4f1128ff656d8f) get_acl_schema_graph()

|   |   |   |   |   |
|---|---|---|---|---|
|VAL.DBA.get_acl_schema_graph|(||)||

The VAL ACL Schema graph IRI.

To ensure that nobody can tamper with default access modes and the like it is important that the Openlink ACL and restriction ontologies are stored in a private trusted graph.

VAL uses the ACL schema graph `urn:virtuoso:val:acl:schema` for this purpose. It is mandatory for both the [ACL](http://www.openlinksw.com/ontology/acl#) and the [restriction](http://www.openlinksw.com/ontology/restrictions#) ontologies to be loaded into this graph for the VAL ACL system to work properly.

Returns

The IRI of the VAL ACL schema graph.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_ACL`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_ACL` role:

grant VAL_ACL to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gabf8e31f7ee7b8babb2432ee54ce4a387) get_dav_scope()

|   |   |   |   |   |
|---|---|---|---|---|
|VAL.DBA.get_dav_scope|(||)||

The IRI of the DAV ACL rule scope.

This scope is special as [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) contains special ownership handling for DAV resources and collections. See [DAV ACL Rules](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_dav) for details.

Returns

The IRI of the DAV resource scope: `oplacl:Dav`.

See also

[Rule Scopes](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_rule_scopes)

Special SQL Execute Permissions

This procedure can be executed by role `VAL_ACL`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_ACL` role:

grant VAL_ACL to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gaa84c6ea7e257e469fed362afa0f995dd) get_owned_graphs()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.get_owned_graphs|(|varchar|_serviceId_|)||

Get the graphs owned by a given service id.

[VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) manages the ownership relations for named graphs. This procedure lists all graphs which have been set as owned by the given person.

Returns

a vector of graph IRIs.

See also

[VAL.DBA.set_graph_ownership()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a1b330f04d1153b55f8bcb1aa55bf5df4), [VAL.DBA.add_graph_ownership()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ab5856e17c84a9224f4cbb58b3d7b5923), [VAL.DBA.remove_graph_ownership()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a22ecd911ad04cde5ea46b6a12e55828f)

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gad7d45951926e95727372402cd3e97b51) get_query_scope()

|   |   |   |   |   |
|---|---|---|---|---|
|VAL.DBA.get_query_scope|(||)||

The IRI of the Query ACL rule scope.

This is used to group ACL rules which grant permission to execute SQL or SPARQL expressions in general. Applicable resources are:

- `urn:virtuoso:access:sql` - Grants read and/or write access for SQL expressions.
- `urn:virtuoso:access:sparql` - Grants read, write, and sponge permissions for SPARQL in general. Access to specific graphs is handled via rules in the sparql scope.

See also

[Rule Scopes](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_rule_scopes), [VAL.DBA.get_sparql_scope()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga27e327bb4de4c515266db21601600c0b "The IRI of the Private named graphs ACL rule scope.")

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gac425bf8c6cf3d2a6e005090cf0505f63) get_resource_owner()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.get_resource_owner|(|varchar|_resource_,|
|||varchar|_scope_|
||)|||

Get the owner of a resource.

This procedure checks resource ownership graphs and handles DAV as a special case.

Returns

The service URI of the owner of the given `resource` or `null` if none could be found.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_ACL`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_ACL` role:

grant VAL_ACL to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gac79d434a51dc8ad154f8952f42983124) get_restrictions_scope()

|   |   |   |   |   |
|---|---|---|---|---|
|VAL.DBA.get_restrictions_scope|(||)||

The IRI of the Restrictions ACL rule scope.

This scope is only used for permissions for restriction creation. By default only `dba` can create restrictions on any resource. ACL rules creates in this scope allow to grant the right to create restrictions to others.

Returns

The IRI of the restrictions scope: `oplres:Restrictions`.

See also

[Rule Scopes](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_rule_scopes)

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga27e327bb4de4c515266db21601600c0b) get_sparql_scope()

|   |   |   |   |   |
|---|---|---|---|---|
|VAL.DBA.get_sparql_scope|(||)||

The IRI of the Private named graphs ACL rule scope.

See also

[Rule Scopes](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_rule_scopes)

Special SQL Execute Permissions

This procedure can be executed by role `VAL_ACL`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_ACL` role:

grant VAL_ACL to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga2bc430de1c302d6fff5d01b79e98454e) ownership_graph_group()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.ownership_graph_group|(|varchar|_scope_|)||

The URI of the graph group used to combine all resource ownership graphs.

Resource ownership is managed in several graphs. Applications can simply register their own ownership graphs via [VAL.DBA.add_ownership_graph()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga3eb4fcc5cff60079013beebdf58c9ae3 "Add a resource ownership graph.") for the ACL system to pick up the information within.

This graph group combines all the ownership graphs for one scope, ie. it can be used to query all ownership graphs at once.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gaa0dfb4fcb31b5bb3a6f51d9e5d6269da) remove_ownership_graph()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.remove_ownership_graph|(|varchar|_uri_,|
|||varchar|_scope_|
||)|||

Remove a resource ownership graph.

[VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) uses the ownership definitions in all ownershop graphs to determine if a user is allowed to create ACL rules for a resource.

This procedure allows to remove a named graph for [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) not to search anymore.

See also

[VAL.DBA.add_ownership_graph()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga3eb4fcc5cff60079013beebdf58c9ae3 "Add a resource ownership graph.")

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga39324e0e0cf5fcaf259dac362357b92c) set_resource_ownership()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.set_resource_ownership|(|varchar|_scope_,|
|||varchar|_resource_,|
|||varchar|_serviceId_|
||)|||

Set the owner of a resource in a given scope.

Instead of defining an ownership graph manually and adding it via [VAL.DBA.add_ownership_graph()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga3eb4fcc5cff60079013beebdf58c9ae3 "Add a resource ownership graph.") one can simply use [VAL.DBA.add_resource_ownership()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga9ca7d11839530fd525f8e27b2f31cbc8 "Add a resource ownership relation."), [VAL.DBA.set_resource_ownership()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga39324e0e0cf5fcaf259dac362357b92c "Set the owner of a resource in a given scope."), and [VAL.DBA.remove_resource_ownership()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a8fd5031bf4c4a047ab41caf266d73535) to simplify things and let VAL handle the rest.

Parameters

|   |   |
|---|---|
|scope|The ACL scope for which the ownership should hold.|
|resource|The resource which should be defined as being owned by the given service id.|
|serviceId|The owner of the given `resource`.|

See also

[VAL.DBA.add_ownership_graph()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga3eb4fcc5cff60079013beebdf58c9ae3 "Add a resource ownership graph.")  
[VAL.DBA.remove_ownership_graph()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gaa0dfb4fcb31b5bb3a6f51d9e5d6269da "Remove a resource ownership graph.")  
[VAL.DBA.set_graph_ownership()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a1b330f04d1153b55f8bcb1aa55bf5df4)

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga52fe4f6da197f74fa77f9faf02414363) sparql_graph_ownership_graph()

|   |   |   |   |   |
|---|---|---|---|---|
|VAL.DBA.sparql_graph_ownership_graph|(||)||

Graph containing the ownership relations for named graphs.

[VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) manages the ownership relations for named graphs. It maintains all ownership relations in this graph. Clients should only depend on [VAL.DBA.add_graph_ownership()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ab5856e17c84a9224f4cbb58b3d7b5923), [VAL.DBA.set_graph_ownership()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a1b330f04d1153b55f8bcb1aa55bf5df4), and [VAL.DBA.remove_graph_ownership()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a22ecd911ad04cde5ea46b6a12e55828f) to avoid problems with mapping ACLs to Virtuoso's internal graph security system.