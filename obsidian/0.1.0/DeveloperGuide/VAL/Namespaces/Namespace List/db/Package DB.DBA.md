|   |   |
|---|---|
|## Functions|   |
||[DBEV_ACLS_ENABLED_FOR_SCOPE](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#a4c33f825bcbbd4f7115635112b0f6502) (varchar scope, varchar realm)|
||   |
||[DBEV_CHECK_CONNECTION_AUTHENTICATION](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#ab11662f0ac480f44e8e2f346c45155fc) (varchar uname)|
||Virtuoso callback for internal authentication. [More...](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#ab11662f0ac480f44e8e2f346c45155fc)|
||   |
||[DBEV_CHECK_CONNECTION_AUTHENTICATION_2](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#ab9c567d76433e1ac35180dc17ac28e53) (varchar uname, varchar agentIri, varchar realm=null)|
||Virtuoso callback for internal authentication. [More...](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#ab9c567d76433e1ac35180dc17ac28e53)|
||   |
||[DBEV_CHECK_PERMISSIONS](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#a8b44e54066d7da56710fd0d1d285df4f) (varchar resource, varchar scope, varchar clientIp=null, varchar agentIri=null, varchar realm=null)|
||Virtuoso callback for internal ACLs. [More...](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#a8b44e54066d7da56710fd0d1d285df4f)|
||   |
||[DBEV_GET_CONNECTION_RESTRICTION](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#a95673bc9b3d18556e19c3ec6a2ddb06c) (varchar resource, varchar parameter=null, decimal minValue, varchar minServiceId, decimal maxValue, varchar maxServiceId, varchar agentIri=null, varchar realm=null)|
||Virtuoso Hook proc: Get the min and max values of one restriction. [More...](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#a95673bc9b3d18556e19c3ec6a2ddb06c)|
||   |
||[DBEV_RES_CREATION_POST](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#ac5b7f4185d0471f8c84e382790e3715f) (varchar uri, varchar scope, varchar realm=null)|
||   |
||[DBEV_RESTRICTIONS](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#a60f938f6c112e6e3549070c27634e95b) (any keys, varchar agentIri=null, varchar realm=null)|
||Virtuoso callback for internal restrictions. [More...](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#a60f938f6c112e6e3549070c27634e95b)|
||   |

## Function Documentation

## [◆](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#a4c33f825bcbbd4f7115635112b0f6502) DBEV_ACLS_ENABLED_FOR_SCOPE()

|   |   |   |   |
|---|---|---|---|
|DB.DBA.DBEV_ACLS_ENABLED_FOR_SCOPE|(|varchar|_scope_,|
|||varchar|_realm_|
||)|||

## [◆](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#ab11662f0ac480f44e8e2f346c45155fc) DBEV_CHECK_CONNECTION_AUTHENTICATION()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|DB.DBA.DBEV_CHECK_CONNECTION_AUTHENTICATION|(|varchar|_uname_|)||

Virtuoso callback for internal authentication.

**[Deprecated:](https://docs.openlinksw.com/valdocs/deprecated.html#_deprecated000004)**

Use [DB.DBA.DBEV_CHECK_CONNECTION_AUTHENTICATION_2()](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#ab9c567d76433e1ac35180dc17ac28e53 "Virtuoso callback for internal authentication.") instead.

## [◆](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#ab9c567d76433e1ac35180dc17ac28e53) DBEV_CHECK_CONNECTION_AUTHENTICATION_2()

|   |   |   |   |
|---|---|---|---|
|DB.DBA.DBEV_CHECK_CONNECTION_AUTHENTICATION_2|(|varchar|_uname_,|
|||varchar|_agentIri_,|
|||varchar|_realm_ = `null`|
||)|||

Virtuoso callback for internal authentication.

Virtuoso for example uses this procedure to check external authentication in the DAV layer. This procedure simply checks if any of the VAL-supported auth information is available. If so, it will return `1` and set `uname` to the authenticated SQL user if and only if the authentication information could be mapped to such a user.

Since [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") also supports authentication via 3rd-party accounts that are not connected to any SQL user this procedure can also return `1` but leave `uname` to `null`.

See also

[DB.DBA.DBEV_CHECK_PERMISSIONS()](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#a8b44e54066d7da56710fd0d1d285df4f "Virtuoso callback for internal ACLs.")

## [◆](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#a8b44e54066d7da56710fd0d1d285df4f) DBEV_CHECK_PERMISSIONS()

|   |   |   |   |
|---|---|---|---|
|DB.DBA.DBEV_CHECK_PERMISSIONS|(|varchar|_resource_,|
|||varchar|_scope_,|
|||varchar|_clientIp_ = `null`,|
|||varchar|_agentIri_ = `null`,|
|||varchar|_realm_ = `null`|
||)|||

Virtuoso callback for internal ACLs.

Returns

A vector of access mode IRIs applicable to the authenticated user or anyone if there is no authentication information.

See also

[DB.DBA.DBEV_CHECK_CONNECTION_AUTHENTICATION()](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#ab11662f0ac480f44e8e2f346c45155fc "Virtuoso callback for internal authentication.")

## [◆](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#a95673bc9b3d18556e19c3ec6a2ddb06c) DBEV_GET_CONNECTION_RESTRICTION()

|   |   |   |   |
|---|---|---|---|
|DB.DBA.DBEV_GET_CONNECTION_RESTRICTION|(|varchar|_resource_,|
|||varchar|_parameter_ = `null`,|
|||decimal|_minValue_,|
|||varchar|_minServiceId_,|
|||decimal|_maxValue_,|
|||varchar|_maxServiceId_,|
|||varchar|_agentIri_ = `null`,|
|||varchar|_realm_ = `null`|
||)|||

Virtuoso Hook proc: Get the min and max values of one restriction.

Virtuoso allows the creation of procedure [DB.DBA.DBEV_GET_CONNECTION_RESTRICTION](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#a95673bc9b3d18556e19c3ec6a2ddb06c "Virtuoso Hook proc: Get the min and max values of one restriction.") to allow Virtuoso use of our restrictions engine.

Parameters

|   |   |   |
|---|---|---|
||resource|The resource for which a restriction should be checked.|
||parameter|The optional parameter which allows to split one `resource` into several restrictions.|
|[out]|minValue|Will be set to the min value of the restriction of `null` if no matching restriction had a min value.|
||minServiceId|Will be set to the service ID of the authenticated person which triggered the minimum restriction. If the restriction is based on an IP address then it will be `null`.|
|[out]|maxValue|Will be set to the max value of the restriction of `null` if no matching restriction had a max value.|
||maxServiceId|Will be set to the service ID of the authenticated person which triggered the maximum restriction. If the restriction is based on an IP address then it will be `null`.|
||agentIri|The optional IRI of the authenticated agent. If omitted [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") authentcation will be checked.|
||realm|The optional application realm which falls back to [VAL.DBA.get_default_realm()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gab4ad86ce5cd06213fa29ee6f2eab6292 "The default application realm.").|

Returns

`1` if restriction values have been found, `0` otherwise.

See also

[DB.DBA.DBEV_RESTRICTIONS()](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#a60f938f6c112e6e3549070c27634e95b "Virtuoso callback for internal restrictions.")

## [◆](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#ac5b7f4185d0471f8c84e382790e3715f) DBEV_RES_CREATION_POST()

|   |   |   |   |
|---|---|---|---|
|DB.DBA.DBEV_RES_CREATION_POST|(|varchar|_uri_,|
|||varchar|_scope_,|
|||varchar|_realm_ = `null`|
||)|||

Post-resource creation hook.

Once new resources have been created (typically DAV resources) via non-sql account authentication we need to create ACL rules to grant the authenticated person access to the newly created resource.

This is done in this hook.

## [◆](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#a60f938f6c112e6e3549070c27634e95b) DBEV_RESTRICTIONS()

|   |   |   |   |
|---|---|---|---|
|DB.DBA.DBEV_RESTRICTIONS|(|any|_keys_,|
|||varchar|_agentIri_ = `null`,|
|||varchar|_realm_ = `null`|
||)|||

Virtuoso callback for internal restrictions.

This callback can be used by Virtuoso to apply restrictions to any internal system. It is for example used by the HTTP engine to restrict the request rate or the max result content size.

Parameters

|   |   |
|---|---|
|keys|A vector which contains a map of restriction names to their type, ie. `min` or `max`. The restriction names will be prefixed with `urn:virtuoso:restrictions:` which is important when declaring the restriction rules.|
|agentIri|The optional IRI of the authenticated agent. If omitted [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL.html "SPARQL query callback which enforces VAL ACL rules.") authentcation will be checked.|
|realm|The optional application realm which falls back to [VAL.DBA.get_default_realm()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gab4ad86ce5cd06213fa29ee6f2eab6292 "The default application realm.").|

Returns

A vector which contains a map of restriction names to a vector of restriction type (`max` or `min`), the restriction value, and an optional serviceId of the authenticated person which triggered the restriction. If the latter is null then the restriction is assumed to be on an IP address level.

See also

[DB.DBA.DBEV_GET_CONNECTION_RESTRICTION()](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#a95673bc9b3d18556e19c3ec6a2ddb06c "Virtuoso Hook proc: Get the min and max values of one restriction.")

-