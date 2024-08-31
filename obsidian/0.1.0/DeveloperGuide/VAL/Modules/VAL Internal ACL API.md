|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ## Functions |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.acl_group_addCondition](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga44fa7f391b254fc3864530fd14054299) (varchar serviceId, varchar name, varchar criteria=null, varchar comparator=null, varchar value=null, varchar query=null, varchar property=null, any object=null, varchar realm, varchar ipAddressPattern=null)                                                                  |
|              | Add a condition to an existing conditional group. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga44fa7f391b254fc3864530fd14054299)                                                                                                                                                                                                                                                       |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.acl_group_list](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga882fcbb1bed39eb3240cb7394ac1cdd1) (varchar serviceId, varchar type=null, integer details=0, varchar format, varchar realm)                                                                                                                                                                                                 |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.acl_group_new](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga2ee524dea4975b5b7ed5c576a450df6b) (varchar serviceId, varchar name, varchar comment=null, varchar type="static", any members=null, varchar realm)                                                                                                                                                                           |
|              | Create a new group. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga2ee524dea4975b5b7ed5c576a450df6b)                                                                                                                                                                                                                                                                                     |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.acl_group_remove](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga77d2b86ff04300b90518e82002055d06) (varchar serviceId, varchar name, varchar realm)                                                                                                                                                                                                                                       |
|              | Remove an existing group. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga77d2b86ff04300b90518e82002055d06)                                                                                                                                                                                                                                                                               |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.acl_group_removeCondition](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga84d7e302aac40d561b3d4c0c0f5d63da) (varchar serviceId, varchar uri, varchar realm)                                                                                                                                                                                                                               |
|              | Remove a condition from a conditional group. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga84d7e302aac40d561b3d4c0c0f5d63da)                                                                                                                                                                                                                                                            |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.acl_group_removeConditions](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga6b7dddaf1c69e050d1c78ea408ffddb1) (varchar serviceId, varchar name, varchar criteria=null, varchar comparator=null, varchar value=null, varchar query=null, varchar realm)                                                                                                                                     |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.acl_group_update](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9df164506e7346ea73e53070797efca8) (varchar serviceId, varchar name, varchar newName, varchar newComment, any addMembers, any removeMembers, integer overwrite=0, varchar realm)                                                                                                                                          |
|              | Update an existing group. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9df164506e7346ea73e53070797efca8)                                                                                                                                                                                                                                                                               |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.acl_rule_get](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gadf3270ae9fb676c854e7f5734364ec54) (varchar serviceId, any iris, varchar format, varchar realm)                                                                                                                                                                                                                               |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.acl_rule_list](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gaeeff50189ea328b61f58851b641bbbb2) (varchar serviceId, varchar subject=null, integer recursive=null, varchar agent=null, varchar agentClass=null, any access=null, varchar realm=null, integer details=0, varchar format=null, varchar scope=null, varchar label=null)                                                       |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.acl_rule_new](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga133dcb304ad818701bb953c73b4ce739) (varchar serviceId, varchar subject=null, integer recursive=0, varchar agent=null, varchar agentClass=null, any access, varchar realm, varchar name=null, varchar comment=null, varchar scope=null, varchar label=null)                                                                    |
|              | Create a new ACL rule. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga133dcb304ad818701bb953c73b4ce739)                                                                                                                                                                                                                                                                                  |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.acl_rule_remove](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga964cbf944626fe27d9672ceee7c0a4a4) (varchar serviceId, varchar uri, varchar realm)                                                                                                                                                                                                                                         |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.acl_rule_update](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga27bf0ee497590179a0557bb59d495a19) (varchar serviceId, varchar uri, varchar subject=null, integer recursive=null, varchar agent=null, varchar agentClass=null, any access=null, integer overwrite=0, varchar realm, varchar name=null, varchar comment=null, varchar scope=null, varchar label=null)                       |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.acls_enabled_for_scope](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gaf81eb3387fa574373af0282bf772a4a4) (varchar scope, varchar realm=null, int fallbackValue=0)                                                                                                                                                                                                                         |
|              | Checks if ACL rule evaluation is enabled for a given scope. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gaf81eb3387fa574373af0282bf772a4a4)                                                                                                                                                                                                                                             |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.check_access_mode_for_resource](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga02d2eab7b4a0c696c72ec6c064ebe982) (varchar serviceId, varchar ipAddress=null, varchar resource, varchar realm, varchar mode, varchar scope, varchar webidGraph=null, any certificate=null, varchar sameAsGraph=null, int honorScopeState=0, int evalRecursiveRules=0)                                      |
|              | Convinience procedure to check for a specific mode on one resource. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga02d2eab7b4a0c696c72ec6c064ebe982)                                                                                                                                                                                                                                     |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.check_acls_for_named_graph](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga0941b8fe50d5a3c1b51b13a00945f090) (varchar serviceId, varchar uname=null, varchar ipAddress=null, varchar graphUri, varchar realm=null, varchar webidGraph=null, any certificate=null, varchar sameAsGraph=null, int honorScopeState=0, int includeVirtuosoSecurity=1)                                         |
|              | Check access for a given user and named graph. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga0941b8fe50d5a3c1b51b13a00945f090)                                                                                                                                                                                                                                                          |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.check_acls_for_resource](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9a2351c047a02b3ce8457e49c804e3d8) (varchar serviceId, varchar ipAddress=null, varchar resource=null, varchar realm, varchar mode=null, varchar scope=null, varchar webidGraph=null, any certificate=null, varchar sameAsGraph=null, int honorScopeState=0, int evalRecursiveRules=0)                              |
|              | Find permissions for resources as set by ACL rules in a certain realm. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9a2351c047a02b3ce8457e49c804e3d8)                                                                                                                                                                                                                                  |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.count_acl_rules_for_resource](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gabbe236f4cfd9c8cc782fbdfacdbe14b0) (varchar resource, varchar scope, varchar realm=null)                                                                                                                                                                                                                      |
|              | Count the number of ACL rules for a given resource. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gabbe236f4cfd9c8cc782fbdfacdbe14b0)                                                                                                                                                                                                                                                     |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.find_restrictions](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gab7485fb9ae3ba202e9e27b6741a21901) (varchar serviceId=null, varchar ipAddress=null, varchar resource, varchar realm, varchar webidGraph=null, any certificate=null, decimal minValue, decimal maxValue, varchar parameter=null, varchar sameAsGraph=null)                                                                |
|              | Find the restriction values for a given resource. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gab7485fb9ae3ba202e9e27b6741a21901)                                                                                                                                                                                                                                                       |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.find_restrictions_max](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gad3f57510dc6b58c3ab7a8aa548d92ec3) (varchar serviceId, varchar ipAddress=null, varchar resource, varchar realm=null, varchar webidGraph=null, any certificate=null, varchar parameter=null, varchar sameAsGraph=null)                                                                                                |
|              | Get the maximum restriction value for a given resource. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gad3f57510dc6b58c3ab7a8aa548d92ec3)                                                                                                                                                                                                                                                 |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.find_restrictions_min](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga945480c6422506359ba72652b1b6e35e) (varchar serviceId, varchar ipAddress=null, varchar resource, varchar realm=null, varchar webidGraph=null, any certificate=null, varchar parameter=null, varchar sameAsGraph=null)                                                                                                |
|              | Get the minimum restriction value for a given resource. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga945480c6422506359ba72652b1b6e35e)                                                                                                                                                                                                                                                 |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.get_applicable_access_for_scope](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga6321049570d5aea012c2f21facef80df) (varchar scope)                                                                                                                                                                                                                                                         |
|              | Get the list of applicable access modes for a given scope. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga6321049570d5aea012c2f21facef80df)                                                                                                                                                                                                                                              |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.get_default_access_for_scope](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga0c9da57d48c38613d17f593917d2e3ce) (varchar scope)                                                                                                                                                                                                                                                            |
|              | Get the list of default access modes for a given scope. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga0c9da57d48c38613d17f593917d2e3ce)                                                                                                                                                                                                                                                 |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.get_sparql_permissions](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gae955138972efdcf37bc1d50cc61f70c6) (varchar serviceId, varchar uname=null, varchar ipAddress=null, varchar realm=null, varchar webidGraph=null, any certificate=null, varchar sameAsGraph=null)                                                                                                                     |
|              | Check the generic SPARQL permissions for the given authentication information. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gae955138972efdcf37bc1d50cc61f70c6)                                                                                                                                                                                                                          |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.restriction_delete](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9126f9b2b90bbb3b44dcceab02632e33) (varchar uri, varchar realm=null, varchar serviceId=null)                                                                                                                                                                                                                            |
|              | Delete a restriction. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9126f9b2b90bbb3b44dcceab02632e33)                                                                                                                                                                                                                                                                                   |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.restriction_get](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gac97f9e10fd321c6577e739dd2e1a831b) (any iris, varchar format, varchar realm, varchar serviceId=null)                                                                                                                                                                                                                       |
|              | Get the details one or more restrictions. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gac97f9e10fd321c6577e739dd2e1a831b)                                                                                                                                                                                                                                                               |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.restriction_list](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gae46864a9dc688ecccc7bd27824a71114) (varchar name=null, varchar comment=null, varchar resource=null, varchar agent=null, varchar agentClass=null, decimal minValue=null, decimal maxValue=null, varchar realm, integer details=0, varchar format=null, varchar parameter=null, varchar serviceId=null, varchar label=null) |
|              | List restrictions defined in a realm. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gae46864a9dc688ecccc7bd27824a71114)                                                                                                                                                                                                                                                                   |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.restriction_new](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gad3bc16f9b48d640a799f787cbd562109) (varchar name=null, varchar comment=null, varchar resource, varchar agent=null, varchar agentClass=null, decimal minValue=null, decimal maxValue=null, varchar realm=null, varchar parameter=null, varchar serviceId=null, varchar label=null)                                          |
|              | Create a new ACL restriction. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gad3bc16f9b48d640a799f787cbd562109)                                                                                                                                                                                                                                                                           |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|              | [VAL.DBA.restriction_update](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gaa4a919690984e55fda88b812135330c7) (varchar uri, varchar name=null, varchar comment=null, varchar resource=null, varchar agent=null, varchar agentClass=null, decimal minValue=null, decimal maxValue=null, varchar realm, varchar parameter=null, varchar serviceId=null, varchar label=null)                          |
|              | Update properties of an existing restriction. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gaa4a919690984e55fda88b812135330c7)                                                                                                                                                                                                                                                           |
|              |                                                                                                                                                                                                                                                                                                                                                                                                                                       |

## Detailed Description

Warning

Please do not use the internal ACL API if you could also use [The RESTful ACL API](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#val_acl_restful_api) or [VAL Public ACL HTTP API](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html)!

The internal ACL API allows vsp-based applications to manage ACL rules. However, this should only be used if the HTTP API is for some reason not sufficient.

## Function Documentation

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga44fa7f391b254fc3864530fd14054299) acl_group_addCondition()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.acl_group_addCondition|(|varchar|_serviceId_,|
|||varchar|_name_,|
|||varchar|_criteria_ = `null`,|
|||varchar|_comparator_ = `null`,|
|||varchar|_value_ = `null`,|
|||varchar|_query_ = `null`,|
|||varchar|_property_ = `null`,|
|||any|_object_ = `null`,|
|||varchar|_realm_,|
|||varchar|_ipAddressPattern_ = `null`|
||)|||

Add a condition to an existing conditional group.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga882fcbb1bed39eb3240cb7394ac1cdd1) acl_group_list()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.acl_group_list|(|varchar|_serviceId_,|
|||varchar|_type_ = `null`,|
|||integer|_details_ = `0`,|
|||varchar|_format_,|
|||varchar|_realm_|
||)|||

List all groups by the given `serviceId` in the given `realm`. If `details` is `0` then only the URIs are returned.

Returns

If `format` is given a serialized set of triples is returned, otherwise a [VAL.DBA.exec_sparql()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a5410c1f6661f413c60393d9baf8ebe2e) result is returned instead.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga2ee524dea4975b5b7ed5c576a450df6b) acl_group_new()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.acl_group_new|(|varchar|_serviceId_,|
|||varchar|_name_,|
|||varchar|_comment_ = `null`,|
|||varchar|_type_ = `"static"`,|
|||any|_members_ = `null`,|
|||varchar|_realm_|
||)|||

Create a new group.

Two kinds of groups are supported: `static` and `conditional` groups. The former simply contains of an unsorted list of persons. The latter can have arbitrarily complex conditions which decide if a certain person (identified by their WebID) is part of the group. This means that it might be impossible to list all members of a conditional group if the conditions include unknown persons (for example if a conditional group is defined to include all persons of a certain type).

Parameters

|   |   |
|---|---|
|serviceId|The service id to which to scope the group.|
|name|The name of the group. This is unique to the `serviceId` and `realm`.|
|comment|An optional comment to describe the group.|
|type|The type of the group. This is either `static` or `conditional`.|
|members|An optional list of members to fill a static group.|
|realm|The application realm in which the group should be created.|

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga77d2b86ff04300b90518e82002055d06) acl_group_remove()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.acl_group_remove|(|varchar|_serviceId_,|
|||varchar|_name_,|
|||varchar|_realm_|
||)|||

Remove an existing group.

Removes the group identified by `name` (URI or group name). Both `serviceId` and `realm` have to match the group's properties. Otherwise an error is signaled.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga84d7e302aac40d561b3d4c0c0f5d63da) acl_group_removeCondition()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.acl_group_removeCondition|(|varchar|_serviceId_,|
|||varchar|_uri_,|
|||varchar|_realm_|
||)|||

Remove a condition from a conditional group.

The `serviceId` and the `realm` need to match the corresponding properties of the condition identified by `uri`.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga6b7dddaf1c69e050d1c78ea408ffddb1) acl_group_removeConditions()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.acl_group_removeConditions|(|varchar|_serviceId_,|
|||varchar|_name_,|
|||varchar|_criteria_ = `null`,|
|||varchar|_comparator_ = `null`,|
|||varchar|_value_ = `null`,|
|||varchar|_query_ = `null`,|
|||varchar|_realm_|
||)|||

Remove all group conditions which match a set of properties.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9df164506e7346ea73e53070797efca8) acl_group_update()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.acl_group_update|(|varchar|_serviceId_,|
|||varchar|_name_,|
|||varchar|_newName_,|
|||varchar|_newComment_,|
|||any|_addMembers_,|
|||any|_removeMembers_,|
|||integer|_overwrite_ = `0`,|
|||varchar|_realm_|
||)|||

Update an existing group.

This function allows to change the basic details of any group except for its type. The group has to be created via [VAL.DBA.acl_group_new()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga2ee524dea4975b5b7ed5c576a450df6b "Create a new group.") before.

Parameters

|   |   |
|---|---|
|serviceId|The service id the group is scoped to. Has to match the group's properties.|
|name|The name or the IRI of the group to change.|
|newName|The optional new name of the group. This name cannot be used by another group already.|
|newComment|The optional new comment of the group.|
|addMembers|An optional vector of URIs which indicate the new members to add to the group.|
|removeMembers|An optional vector of URIs which indicate the members to remove from the group. If `overwrite` is `1` `removeMember` is ignored.|
|overwrite|If `1` the existing members of the given group are replaced by the ones specified in `addMembers`.|
|realm|The application realm the group is scoped to. Has to match the group's properties.|

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gadf3270ae9fb676c854e7f5734364ec54) acl_rule_get()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.acl_rule_get|(|varchar|_serviceId_,|
|||any|_iris_,|
|||varchar|_format_,|
|||varchar|_realm_|
||)|||

Get the details of one or more specific rules. Both `serviceId` and `realm` have to match the rule's properties. Otherwise an error is signaled. `iris` can be a single IRI or a vector of IRIs.

Returns

If `format` is given a serialized set of triples is returned, otherwise a [VAL.DBA.exec_sparql()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a5410c1f6661f413c60393d9baf8ebe2e) result is returned instead.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gaeeff50189ea328b61f58851b641bbbb2) acl_rule_list()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.acl_rule_list|(|varchar|_serviceId_,|
|||varchar|_subject_ = `null`,|
|||integer|_recursive_ = `null`,|
|||varchar|_agent_ = `null`,|
|||varchar|_agentClass_ = `null`,|
|||any|_access_ = `null`,|
|||varchar|_realm_ = `null`,|
|||integer|_details_ = `0`,|
|||varchar|_format_ = `null`,|
|||varchar|_scope_ = `null`,|
|||varchar|_label_ = `null`|
||)|||

Lists ACL rules which meet the criteria provided as parameters.

Returns

If `format` is given a serialized set of triples is returned, otherwise a [VAL.DBA.exec_sparql()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a5410c1f6661f413c60393d9baf8ebe2e) result is returned instead.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga133dcb304ad818701bb953c73b4ce739) acl_rule_new()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.acl_rule_new|(|varchar|_serviceId_,|
|||varchar|_subject_ = `null`,|
|||integer|_recursive_ = `0`,|
|||varchar|_agent_ = `null`,|
|||varchar|_agentClass_ = `null`,|
|||any|_access_,|
|||varchar|_realm_,|
|||varchar|_name_ = `null`,|
|||varchar|_comment_ = `null`,|
|||varchar|_scope_ = `null`,|
|||varchar|_label_ = `null`|
||)|||

Create a new ACL rule.

Typically clients should rather use the public HTTP API [VAL.VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html)."acl.rule.new"().

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga964cbf944626fe27d9672ceee7c0a4a4) acl_rule_remove()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.acl_rule_remove|(|varchar|_serviceId_,|
|||varchar|_uri_,|
|||varchar|_realm_|
||)|||

Remove one rule identified by the given `uri`. Both `serviceId` and `realm` have to match the rule's properties. Otherwise an error is signaled.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga27bf0ee497590179a0557bb59d495a19) acl_rule_update()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.acl_rule_update|(|varchar|_serviceId_,|
|||varchar|_uri_,|
|||varchar|_subject_ = `null`,|
|||integer|_recursive_ = `null`,|
|||varchar|_agent_ = `null`,|
|||varchar|_agentClass_ = `null`,|
|||any|_access_ = `null`,|
|||integer|_overwrite_ = `0`,|
|||varchar|_realm_,|
|||varchar|_name_ = `null`,|
|||varchar|_comment_ = `null`,|
|||varchar|_scope_ = `null`,|
|||varchar|_label_ = `null`|
||)|||

Changing the realm of a rule is not allowed! Remove and create new instead.

Parameters

|   |   |
|---|---|
|overwrite|If set to 1 the given access values will replace the existing ones intead of being added on top.|

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gaf81eb3387fa574373af0282bf772a4a4) acls_enabled_for_scope()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.acls_enabled_for_scope|(|varchar|_scope_,|
|||varchar|_realm_ = `null`,|
|||int|_fallbackValue_ = `0`|
||)|||

Checks if ACL rule evaluation is enabled for a given scope.

Rule evaluation for a certain scope can be disabled by setting `oplacl:aclRulesEnabled` to `false` for the scope in question.

This value, however, is not enforced by [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html)'s main API ([VAL.DBA.check_acls_for_resource()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9a2351c047a02b3ce8457e49c804e3d8 "Find permissions for resources as set by ACL rules in a certain realm.") and friends). This procedure is provided to simplify this check for applications.

Parameters

|   |   |
|---|---|
|scope|The URI of the scope to be checked.|
|realm|The optional realm in which the scope should be checked. Falls back to the default realm ([VAL.DBA.get_default_realm()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gab4ad86ce5cd06213fa29ee6f2eab6292 "The default application realm."))|
|fallbackValue|This will be used as a return value if the scope has neither been enabled or disabled.|

Returns

`1` if ACL evaluation has been enabled, `0` otherwise. It defaults to `fallbackValue` or `0` if no value is stored with the scope.

See also

[VAL.DBA.get_acl_schema_graph()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga1c832c5509c57c7dcb4f1128ff656d8f "The VAL ACL Schema graph IRI."), [VAL.DBA.get_default_access_for_scope()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga0c9da57d48c38613d17f593917d2e3ce "Get the list of default access modes for a given scope."), [Rule Scopes](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_rule_scopes)

Special SQL Execute Permissions

This procedure can be executed by role `VAL_ACL`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_ACL` role:

grant VAL_ACL to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga02d2eab7b4a0c696c72ec6c064ebe982) check_access_mode_for_resource()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.check_access_mode_for_resource|(|varchar|_serviceId_,|
|||varchar|_ipAddress_ = `null`,|
|||varchar|_resource_,|
|||varchar|_realm_,|
|||varchar|_mode_,|
|||varchar|_scope_,|
|||varchar|_webidGraph_ = `null`,|
|||any|_certificate_ = `null`,|
|||varchar|_sameAsGraph_ = `null`,|
|||int|_honorScopeState_ = `0`,|
|||int|_evalRecursiveRules_ = `0`|
||)|||

Convinience procedure to check for a specific mode on one resource.

This procedure is basically the same as [VAL.DBA.check_acls_for_resource()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9a2351c047a02b3ce8457e49c804e3d8 "Find permissions for resources as set by ACL rules in a certain realm."), except that it can only be used to check one specific mode on one resource. As such, it only exists to simplify code.

Returns

`1` if the given requested access `mode` is in fact granted for the given `resource`, `scope`, and `realm`.

See also

[VAL.DBA.check_acls_for_resource()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9a2351c047a02b3ce8457e49c804e3d8 "Find permissions for resources as set by ACL rules in a certain realm.")

Special SQL Execute Permissions

This procedure can be executed by role `VAL_ACL`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_ACL` role:

grant VAL_ACL to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga0941b8fe50d5a3c1b51b13a00945f090) check_acls_for_named_graph()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.check_acls_for_named_graph|(|varchar|_serviceId_,|
|||varchar|_uname_ = `null`,|
|||varchar|_ipAddress_ = `null`,|
|||varchar|_graphUri_,|
|||varchar|_realm_ = `null`,|
|||varchar|_webidGraph_ = `null`,|
|||any|_certificate_ = `null`,|
|||varchar|_sameAsGraph_ = `null`,|
|||int|_honorScopeState_ = `0`,|
|||int|_includeVirtuosoSecurity_ = `1`|
||)|||

Check access for a given user and named graph.

Virtuoso has an internal security system for named graphs which defines access on the SQL user level. This procedure allows to check this security system in addition to the VAL ACL rules. In addition named graph ownership is checked. Compare [VAL.DBA.set_graph_ownership()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a1b330f04d1153b55f8bcb1aa55bf5df4) and friends.

Be aware that this procedure does not check the general SPARQL ACLs, meaning rules in the oplacl:Query scope.

This procedure is close to [VAL.DBA.check_acls_for_resource()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9a2351c047a02b3ce8457e49c804e3d8 "Find permissions for resources as set by ACL rules in a certain realm."), except that it only checks named graph ACLs and can optionally check the Virtuoso graph security.

Parameters

|   |   |
|---|---|
|serviceId|The service id which access is requested for.|
|ipAddress|The optional IP address for which access is requested. Rules are checked for both, meaning that only those resources are considered accessible for which rules exist that grant access to both `serviceId` and `ipAddress`. Use [VAL.DBA.check_acls_for_resource_ip_address()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga6fdbdf0af83dda6a465b71ee1035dc51 "Check ACLs granting access to IP Addresses.") to check only IP address specific rules.|
|graphUri|The uri of the named graph for which access permissions should be checked.|
|realm|The application realm in which permissions should be checked. Defaults to oplacl:DefaultRealm.|
|webidGraph|The optional named graph which contains the triples imported from the WebID profile if `certificate` contains an embedded WebID.|
|certificate|The optional client certificate used for authentication.|
|sameAsGraph|This is the graph from which [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) will read owl:sameAs triples to determine which service URIs denote the same person. This defaults to VAL.DBA.val_owl_sameas_graph () which is based on account mappings in VAL.DBA.VAL_USER_ONLINE_ACCOUNTS.|
|honorScopeState|If `1` then ACLs will only be checked for enabled scopes. If the scope in question is disabled, then its default modes are returned. See also [val_acl_rule_graph](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a21952315f9ce1c577e1c0972ae6a1db5).|
|includeVirtuosoSecurity|If `1` then the internal Virtuoso graph security will be taken into account also. That means permissions set via DB.DBA.RDF_GRAPH_USER_PERMS_SET() and friends as well as default permissions for world and private graphs.|

Returns

A bitmap describing the access mode for `graphUri`, following the model of Virtuoso's internal named graph security:

- Bit 1 (integer `1`) for read access
- Bit 2 (integer `2`) for write access
- Bit 3 (integer `4`) for sponge access

Special SQL Execute Permissions

This procedure can be executed by role `VAL_ACL`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_ACL` role:

grant VAL_ACL to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9a2351c047a02b3ce8457e49c804e3d8) check_acls_for_resource()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.check_acls_for_resource|(|varchar|_serviceId_,|
|||varchar|_ipAddress_ = `null`,|
|||varchar|_resource_ = `null`,|
|||varchar|_realm_,|
|||varchar|_mode_ = `null`,|
|||varchar|_scope_ = `null`,|
|||varchar|_webidGraph_ = `null`,|
|||any|_certificate_ = `null`,|
|||varchar|_sameAsGraph_ = `null`,|
|||int|_honorScopeState_ = `0`,|
|||int|_evalRecursiveRules_ = `0`|
||)|||

Find permissions for resources as set by ACL rules in a certain realm.

Checks ACL rules for access to one or more resources. This includes all rules, basic and conditional. When checking access to named graphs [VAL.DBA.check_acls_for_named_graph()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga0941b8fe50d5a3c1b51b13a00945f090 "Check access for a given user and named graph.") might be the more convinient choice as it can also check Virtuoso's internal graph security.

Parameters

|   |   |
|---|---|
|serviceId|The service id which access is requested for.|
|ipAddress|The optional IP address for which access is requested. Rules are checked for both, meaning that only those resources are considered accessible for which rules exist that grant access to both `serviceId` and `ipAddress`. Use [VAL.DBA.check_acls_for_resource_ip_address()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga6fdbdf0af83dda6a465b71ee1035dc51 "Check ACLs granting access to IP Addresses.") to check only IP address specific rules.|
|resource|The optional resource to request access to. If not given all resources `serviceId` has access to are returned.|
|realm|The application realm in which permissions should be checked.|
|mode|The optional access mode to check for. If not given all granted access modes are returned.|
|scope|The optional scope of the queried rules. A scope defines the type of resource.|
|webidGraph|The optional named graph which contains the triples imported from the WebID profile if `certificate` contains an embedded WebID.|
|certificate|The optional client certificate used for authentication.|
|sameAsGraph|This is the graph from which [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) will read owl:sameAs triples to determine which service URIs denote the same person. This defaults to VAL.DBA.val_owl_sameas_graph () which is based on account mappings in VAL.DBA.VAL_USER_ONLINE_ACCOUNTS.|
|honorScopeState|If `1` then ACLs will only be checked for enabled scopes. If the scope in question is disabled, then its default modes are returned. See also [val_acl_rule_graph](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a21952315f9ce1c577e1c0972ae6a1db5).|
|evalRecursiveRules|If `1` then recursive rules will be evaluated for scopes other than `DAV`. See [Recursion Based On Relations](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_recursive_rules_haspart) for details on how the rules are evaluated.|

Returns

A vector which contains key/value pairs mapping resources to a list of the granted access modes. The access modes are represented by URIs as stored in the ACLs

See also

[VAL.DBA.check_acls_for_resource_public()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga7bd78e6bbeb0650cd410e15782ba5525 "Check Public ACLs for a resource.")  
[VAL.DBA.check_acls_for_resource_basic()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gab6cf3963a149b67dcaa0fe6f84553f7d "Check Basic ACLs for a resource.")  
[VAL.DBA.check_acls_for_resource_conditional()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga32a11e8482d82953d61ba58723939163 "Check Conditional ACLs for a resource.")  
[VAL.DBA.check_acls_for_resource_ip_address()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga6fdbdf0af83dda6a465b71ee1035dc51 "Check ACLs granting access to IP Addresses.")  
[VAL.DBA.check_access_mode_for_resource()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga02d2eab7b4a0c696c72ec6c064ebe982 "Convinience procedure to check for a specific mode on one resource.")

Special SQL Execute Permissions

This procedure can be executed by role `VAL_ACL`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_ACL` role:

grant VAL_ACL to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gabbe236f4cfd9c8cc782fbdfacdbe14b0) count_acl_rules_for_resource()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.count_acl_rules_for_resource|(|varchar|_resource_,|
|||varchar|_scope_,|
|||varchar|_realm_ = `null`|
||)|||

Count the number of ACL rules for a given resource.

In certain situations it is good to know if any rule have been created at all. This is when the count can be checked for `0`.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gab7485fb9ae3ba202e9e27b6741a21901) find_restrictions()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.find_restrictions|(|varchar|_serviceId_ = `null`,|
|||varchar|_ipAddress_ = `null`,|
|||varchar|_resource_,|
|||varchar|_realm_,|
|||varchar|_webidGraph_ = `null`,|
|||any|_certificate_ = `null`,|
|||decimal|_minValue_,|
|||decimal|_maxValue_,|
|||varchar|_parameter_ = `null`,|
|||varchar|_sameAsGraph_ = `null`|
||)|||

Find the restriction values for a given resource.

This procedure will find the least restrictive values from all rules in the given `realm` for the given `resource`.

Parameters

|   |   |   |
|---|---|---|
||serviceId|The optional authenticated person. If `null` then only public rules will be evaluated which results in restriction values scoped to everyone.|
||ipAddress|The optional IP address from which the client is connecting. If given, restrictions for IP Address patterns are also taken into account.|
||resource|The resource for which restriction values should be found.|
||realm|The application realm in which to look for the restrictions. Each realm has its own distinct set of restrictions.|
||webidGraph|The optional (typically temporary) graph in which the authenticated user's WebID profile has been stored. This only applies to WebID authentication, if left `null` then the profile will be loaded into a tmp graph and cleared after completion.|
||certificate|The optional client certificate used for authentication. If `null` the current connection's client certificate is checked.|
|[out]|minValue|Will be set to the least restrictive minimum value from all defined restrictions or `null` if no applicable restriction can be found.|
|[out]|maxValue|Will be set to the least restrictive maximum value from all defined restrictions or `null` if no applicable restriction can be found.|
||parameter|The optional restriction parameter which allows to "divide" one resource into different restrictions. This is typically used if the resource IRI is fixed and one wants to define several restrictions for one resource.|
||sameAsGraph|This is the graph from which [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) will read owl:sameAs triples to determine which service URIs denote the same person. This defaults to VAL.DBA.val_owl_sameas_graph () which is based on account mappings in VAL.DBA.VAL_USER_ONLINE_ACCOUNTS.|

Throws a signal in case of an error.

See also

[VAL.DBA.restriction_new()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gad3bc16f9b48d640a799f787cbd562109 "Create a new ACL restriction."), [VAL.DBA.restriction_list()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gae46864a9dc688ecccc7bd27824a71114 "List restrictions defined in a realm.")

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gad3f57510dc6b58c3ab7a8aa548d92ec3) find_restrictions_max()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.find_restrictions_max|(|varchar|_serviceId_,|
|||varchar|_ipAddress_ = `null`,|
|||varchar|_resource_,|
|||varchar|_realm_ = `null`,|
|||varchar|_webidGraph_ = `null`,|
|||any|_certificate_ = `null`,|
|||varchar|_parameter_ = `null`,|
|||varchar|_sameAsGraph_ = `null`|
||)|||

Get the maximum restriction value for a given resource.

This is a convinience procedure which allows to get the maximum restriction value without the need for `out` parameters. See [VAL.DBA.find_restrictions()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gab7485fb9ae3ba202e9e27b6741a21901 "Find the restriction values for a given resource.") for details on the input parameters.

Returns

The least restrictive maximum value or `null` if no applicable restriction can be found.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga945480c6422506359ba72652b1b6e35e) find_restrictions_min()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.find_restrictions_min|(|varchar|_serviceId_,|
|||varchar|_ipAddress_ = `null`,|
|||varchar|_resource_,|
|||varchar|_realm_ = `null`,|
|||varchar|_webidGraph_ = `null`,|
|||any|_certificate_ = `null`,|
|||varchar|_parameter_ = `null`,|
|||varchar|_sameAsGraph_ = `null`|
||)|||

Get the minimum restriction value for a given resource.

This is a convinience procedure which allows to get the minimum restriction value without the need for `out` parameters. See [VAL.DBA.find_restrictions()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gab7485fb9ae3ba202e9e27b6741a21901 "Find the restriction values for a given resource.") for details on the input parameters.

Returns

The least restrictive minimum value or `null` if no applicable restriction can be found.

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga6321049570d5aea012c2f21facef80df) get_applicable_access_for_scope()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.get_applicable_access_for_scope|(|varchar|_scope_|)||

Get the list of applicable access modes for a given scope.

See also

[VAL.DBA.acls_enabled_for_scope()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gaf81eb3387fa574373af0282bf772a4a4 "Checks if ACL rule evaluation is enabled for a given scope."), [Rule Scopes](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_rule_scopes)

Special SQL Execute Permissions

This procedure can be executed by role `VAL_ACL`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_ACL` role:

grant VAL_ACL to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga0c9da57d48c38613d17f593917d2e3ce) get_default_access_for_scope()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.get_default_access_for_scope|(|varchar|_scope_|)||

Get the list of default access modes for a given scope.

Clients using [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html)'s ACL system can support enabling and disabling of ACL evaluation through the used ACL scope. Procedures like [VAL.DBA.check_access_mode_for_resource()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga02d2eab7b4a0c696c72ec6c064ebe982 "Convinience procedure to check for a specific mode on one resource.") have a parameter which enforces the check of the state of the given scope. If disabled the default set of modes is returned via this procedure.

Parameters

|   |   |
|---|---|
|scope|The ACL scope for which the default modes should be returned. Default modes are defined in the ACL schema graph `urn:virtuoso:val:acl:schema`. This information is either loaded by the instance admin or by the client itself.|

See also

[VAL.DBA.get_acl_schema_graph()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga1c832c5509c57c7dcb4f1128ff656d8f "The VAL ACL Schema graph IRI."), [VAL.DBA.acls_enabled_for_scope()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gaf81eb3387fa574373af0282bf772a4a4 "Checks if ACL rule evaluation is enabled for a given scope."), [Rule Scopes](https://docs.openlinksw.com/valdocs/val_acl.html#val_acl_rule_scopes)

Special SQL Execute Permissions

This procedure can be executed by role `VAL_ACL`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_ACL` role:

grant VAL_ACL to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gae955138972efdcf37bc1d50cc61f70c6) get_sparql_permissions()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.get_sparql_permissions|(|varchar|_serviceId_,|
|||varchar|_uname_ = `null`,|
|||varchar|_ipAddress_ = `null`,|
|||varchar|_realm_ = `null`,|
|||varchar|_webidGraph_ = `null`,|
|||any|_certificate_ = `null`,|
|||varchar|_sameAsGraph_ = `null`|
||)|||

Check the generic SPARQL permissions for the given authentication information.

This procedure will check whether the provided person is allowed to use SPARQL.

Parameters

|   |   |
|---|---|
|serviceId|The service id which access is requested for.|
|ipAddress|The optional IP address for which access is requested. Rules are checked for both, meaning that only those resources are considered accessible for which rules exist that grant access to both `serviceId` and `ipAddress`. Use [VAL.DBA.check_acls_for_resource_ip_address()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga6fdbdf0af83dda6a465b71ee1035dc51 "Check ACLs granting access to IP Addresses.") to check only IP address specific rules.|
|realm|The application realm in which permissions should be checked. Defaults to oplacl:DefaultRealm.|
|webidGraph|The optional named graph which contains the triples imported from the WebID profile if `certificate` contains an embedded WebID.|
|certificate|The optional client certificate used for authentication.|
|sameAsGraph|This is the graph from which [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) will read owl:sameAs triples to determine which service URIs denote the same person. This defaults to VAL.DBA.val_owl_sameas_graph () which is based on account mappings in VAL.DBA.VAL_USER_ONLINE_ACCOUNTS.|

Returns

A bitmap describing the access mode generic SPARQL access, following the model of Virtuoso's internal named graph security:

- Bit 1 (integer `1`) for read access
- Bit 2 (integer `2`) for write access
- Bit 3 (integer `4`) for sponge access

Special SQL Execute Permissions

This procedure can be executed by role `VAL_ACL`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_ACL` role:

grant VAL_ACL to myuser;

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9126f9b2b90bbb3b44dcceab02632e33) restriction_delete()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.restriction_delete|(|varchar|_uri_,|
|||varchar|_realm_ = `null`,|
|||varchar|_serviceId_ = `null`|
||)|||

Delete a restriction.

Parameters

|   |   |
|---|---|
|uri|The IRI of the restriction to delete.|
|realm|The IRI of the realm in which the restriction lives. Deletion will only succeed if the given restriction is actually defined in the given `realm`.|
|serviceId|The optional creator of the restriction. If given then [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) will make sure that this particular person was actually the creator of the restriction to delete.|

Throws a signal in case of an error. This includes a realm mismatch.

See also

[VAL.DBA.restriction_new()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gad3bc16f9b48d640a799f787cbd562109 "Create a new ACL restriction."), [VAL.DBA.restriction_update()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gaa4a919690984e55fda88b812135330c7 "Update properties of an existing restriction.")

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gac97f9e10fd321c6577e739dd2e1a831b) restriction_get()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.restriction_get|(|any|_iris_,|
|||varchar|_format_,|
|||varchar|_realm_,|
|||varchar|_serviceId_ = `null`|
||)|||

Get the details one or more restrictions.

A restriction is very similar to an ACL rule, except that instead of granting access modes, it does set value restrictions for a given resource.

For details see [VAL.DBA.restriction_new()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gad3bc16f9b48d640a799f787cbd562109 "Create a new ACL restriction.").

Parameters

|   |   |
|---|---|
|iris|A vector of restriction IRIs.|
|format|The format in which to serialize the triple data. If `null` a vector (result of an exec() call) is returned. Otherwise a string.|
|realm|The IRI of the realm for which restrictions should be listed.|
|serviceId|The optional serviceId. If given then only restrictions created by that person are returned.|

Throws a signal in case of an error. This includes a realm mismatch.

See also

[VAL.DBA.restriction_list()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gae46864a9dc688ecccc7bd27824a71114 "List restrictions defined in a realm.")

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gae46864a9dc688ecccc7bd27824a71114) restriction_list()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.restriction_list|(|varchar|_name_ = `null`,|
|||varchar|_comment_ = `null`,|
|||varchar|_resource_ = `null`,|
|||varchar|_agent_ = `null`,|
|||varchar|_agentClass_ = `null`,|
|||decimal|_minValue_ = `null`,|
|||decimal|_maxValue_ = `null`,|
|||varchar|_realm_,|
|||integer|_details_ = `0`,|
|||varchar|_format_ = `null`,|
|||varchar|_parameter_ = `null`,|
|||varchar|_serviceId_ = `null`,|
|||varchar|_label_ = `null`|
||)|||

List restrictions defined in a realm.

A restriction is very similar to an ACL rule, except that instead of granting access modes, it does set value restrictions for a given resource.

For details see [VAL.DBA.restriction_new()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gad3bc16f9b48d640a799f787cbd562109 "Create a new ACL restriction.").

Parameters

|   |   |
|---|---|
|name|The optional name (foaf:name) to filter.|
|comment|The optional descriptive comment to filter.|
|resource|The optional IRI of the resource the restrictions apply to.|
|agent|The optional agent IRI (individual or group) the restrictions apply to. Only one of `agent` and `agentClass` can be set.|
|agentClass|The optional class of agents the restrictions apply to. Currently only `foaf:Agent` is supported which refers to everyone.|
|minValue|The optional minimum value connected to the restrictions.|
|maxValue|The optional maximum value connected to the restrictions.|
|realm|The IRI of the realm for which restrictions should be listed.|
|details|If `0` only the restriction IRIs will be listed, otherwise all their properties are included.|
|format|The format in which to serialize the triple data. If `null` a vector (result of an exec() call) is returned. Otherwise a string.|
|serviceId|The optional serviceId which will restrict the list of restrictions to those created by `serviceId`.|
|label|The optional label to filter.|

Throws a signal in the case of an error.

See also

[VAL.DBA.restriction_get()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gac97f9e10fd321c6577e739dd2e1a831b "Get the details one or more restrictions.")

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gad3bc16f9b48d640a799f787cbd562109) restriction_new()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.restriction_new|(|varchar|_name_ = `null`,|
|||varchar|_comment_ = `null`,|
|||varchar|_resource_,|
|||varchar|_agent_ = `null`,|
|||varchar|_agentClass_ = `null`,|
|||decimal|_minValue_ = `null`,|
|||decimal|_maxValue_ = `null`,|
|||varchar|_realm_ = `null`,|
|||varchar|_parameter_ = `null`,|
|||varchar|_serviceId_ = `null`,|
|||varchar|_label_ = `null`|
||)|||

Create a new ACL restriction.

A restriction is very similar to an ACL rule, except that instead of granting access modes, it does set value restrictions for a given resource.

New restrictions are stored in a private graph which depends on the `realm`. See [VAL.DBA.val_restrictions_graph()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a26dc228ed0bccde995e0fed880308b13) on how it is built.

Parameters

|   |   |
|---|---|
|name|The optional name (foaf:name) for the new restriction.|
|comment|The optional comment for the new restriction.|
|resource|The IRI of the resource the restriction applies to. This resource is client-specific, the restriction system does not assume anything about it.|
|agent|The optional agent IRI (individual or group) the restriction applies to. Only one of `agent` and `agentClass` can be set.|
|agentClass|The optional class of agents the restriction applies to. Currently only|
|foaf:Agent|is supported which refers to everyone.|
|minValue|The optional minimum value connected to this restriction.|
|maxValue|The optional maximum value connected to this restriction.|
|realm|The IRI of the realm the restriction should be stored in. Each realm has its own set of restrictions (and groups and acl rules).|
|parameter|The optional restriction parameter which allows to "divide" one resource into different restrictions. This is typically used if the resource IRI is fixed and one wants to define several restrictions for one resource.|
|serviceId|The optional creator of the restriction. If given then [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) will make sure that this particular person has the right to create restrictions on the given resource.|
|label|The optional label for the new restriction.|

Throws a signal in case of an error. This includes missing or invalid input parameters.

See also

[VAL.DBA.restriction_delete()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9126f9b2b90bbb3b44dcceab02632e33 "Delete a restriction."), [VAL.DBA.restriction_update()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gaa4a919690984e55fda88b812135330c7 "Update properties of an existing restriction."), [VAL.DBA.find_restrictions()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gab7485fb9ae3ba202e9e27b6741a21901 "Find the restriction values for a given resource.")

## [◆](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gaa4a919690984e55fda88b812135330c7) restriction_update()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.restriction_update|(|varchar|_uri_,|
|||varchar|_name_ = `null`,|
|||varchar|_comment_ = `null`,|
|||varchar|_resource_ = `null`,|
|||varchar|_agent_ = `null`,|
|||varchar|_agentClass_ = `null`,|
|||decimal|_minValue_ = `null`,|
|||decimal|_maxValue_ = `null`,|
|||varchar|_realm_,|
|||varchar|_parameter_ = `null`,|
|||varchar|_serviceId_ = `null`,|
|||varchar|_label_ = `null`|
||)|||

Update properties of an existing restriction.

A restriction is very similar to an ACL rule, except that instead of granting access modes, it does set value restrictions for a given resource.

For details see [VAL.DBA.restriction_new()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gad3bc16f9b48d640a799f787cbd562109 "Create a new ACL restriction.").

Parameters

|   |   |
|---|---|
|uri|The IRI of the restriction to modify.|
|name|The optional new name (foaf:name).|
|comment|The optional new descriptive comment.|
|resource|The optional IRI of the new resource the restriction applies to. This resource is client-specific, the restriction system does not assume anything about it.|
|agent|The optional new agent IRI (individual or group) the restriction applies to. Only one of `agent` and `agentClass` can be set.|
|agentClass|The optional new class of agents the restriction applies to. Currently only|
|foaf:Agent|is supported which refers to everyone.|
|minValue|The optional new minimum value connected to this restriction.|
|maxValue|The optional new maximum value connected to this restriction.|
|realm|The IRI of the realm the restriction is stored in. The udpate will only succeed if the given restriction is actually defined in the given `realm`.|
|parameter|The optional restriction parameter which allows to "divide" one resource into different restrictions. This is typically used if the resource IRI is fixed and one wants to define several restrictions for one resource.|
|serviceId|The optional creator of the restriction. If given then [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) will make sure that this particular person was actually the creator of the restriction to update.|
|label|The optional new label.|

Throws a signal in case of an error. This includes a realm mismatch.

See also

[VAL.DBA.restriction_new()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gad3bc16f9b48d640a799f787cbd562109 "Create a new ACL restriction."), [VAL.DBA.restriction_delete()](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9126f9b2b90bbb3b44dcceab02632e33 "Delete a restriction.")