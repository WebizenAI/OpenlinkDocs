|   |   |
|---|---|
|## Functions|   |
||[acl_group_addCondition](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga44fa7f391b254fc3864530fd14054299) (varchar serviceId, varchar name, varchar criteria=null, varchar comparator=null, varchar value=null, varchar query=null, varchar property=null, any object=null, varchar realm, varchar ipAddressPattern=null)|
||Add a condition to an existing conditional group. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga44fa7f391b254fc3864530fd14054299)|
||   |
||[acl_group_list](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga882fcbb1bed39eb3240cb7394ac1cdd1) (varchar serviceId, varchar type=null, integer details=0, varchar format, varchar realm)|
||   |
||[acl_group_new](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga2ee524dea4975b5b7ed5c576a450df6b) (varchar serviceId, varchar name, varchar comment=null, varchar type="static", any members=null, varchar realm)|
||Create a new group. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga2ee524dea4975b5b7ed5c576a450df6b)|
||   |
||[acl_group_remove](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga77d2b86ff04300b90518e82002055d06) (varchar serviceId, varchar name, varchar realm)|
||Remove an existing group. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga77d2b86ff04300b90518e82002055d06)|
||   |
||[acl_group_removeCondition](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga84d7e302aac40d561b3d4c0c0f5d63da) (varchar serviceId, varchar uri, varchar realm)|
||Remove a condition from a conditional group. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga84d7e302aac40d561b3d4c0c0f5d63da)|
||   |
||[acl_group_removeConditions](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga6b7dddaf1c69e050d1c78ea408ffddb1) (varchar serviceId, varchar name, varchar criteria=null, varchar comparator=null, varchar value=null, varchar query=null, varchar realm)|
||   |
||[acl_group_update](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9df164506e7346ea73e53070797efca8) (varchar serviceId, varchar name, varchar newName, varchar newComment, any addMembers, any removeMembers, integer overwrite=0, varchar realm)|
||Update an existing group. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9df164506e7346ea73e53070797efca8)|
||   |
||[acl_iri](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a80cbd62a277cd2098fbc7f357574f0f3) (varchar s)|
||   |
||[acl_rule_get](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gadf3270ae9fb676c854e7f5734364ec54) (varchar serviceId, any iris, varchar format, varchar realm)|
||   |
||[acl_rule_list](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gaeeff50189ea328b61f58851b641bbbb2) (varchar serviceId, varchar subject=null, integer recursive=null, varchar agent=null, varchar agentClass=null, any access=null, varchar realm=null, integer details=0, varchar format=null, varchar scope=null, varchar label=null)|
||   |
||[acl_rule_new](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga133dcb304ad818701bb953c73b4ce739) (varchar serviceId, varchar subject=null, integer recursive=0, varchar agent=null, varchar agentClass=null, any access, varchar realm, varchar name=null, varchar comment=null, varchar scope=null, varchar label=null)|
||Create a new ACL rule. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga133dcb304ad818701bb953c73b4ce739)|
||   |
||[acl_rule_remove](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga964cbf944626fe27d9672ceee7c0a4a4) (varchar serviceId, varchar uri, varchar realm)|
||   |
||[acl_rule_update](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga27bf0ee497590179a0557bb59d495a19) (varchar serviceId, varchar uri, varchar subject=null, integer recursive=null, varchar agent=null, varchar agentClass=null, any access=null, integer overwrite=0, varchar realm, varchar name=null, varchar comment=null, varchar scope=null, varchar label=null)|
||   |
||[acls_enabled_for_scope](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gaf81eb3387fa574373af0282bf772a4a4) (varchar scope, varchar realm=null, int fallbackValue=0)|
||Checks if ACL rule evaluation is enabled for a given scope. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gaf81eb3387fa574373af0282bf772a4a4)|
||   |
||[add_default_vdirs](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a51b888c6f038d276fdf0e235ec356b50) ()|
||   |
||[add_graph_ownership](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ab5856e17c84a9224f4cbb58b3d7b5923) (varchar serviceId, varchar graphIri)|
||   |
||[add_ownership_graph](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga3eb4fcc5cff60079013beebdf58c9ae3) (varchar uri, varchar scope)|
||Add a resource ownership graph. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga3eb4fcc5cff60079013beebdf58c9ae3)|
||   |
||[add_resource_ownership](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga9ca7d11839530fd525f8e27b2f31cbc8) (varchar scope, varchar resource, varchar serviceId)|
||Add a resource ownership relation. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga9ca7d11839530fd525f8e27b2f31cbc8)|
||   |
||[add_same_as_relation](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a729ab2d639aac64165a925734e24d555) (varchar serviceId1, varchar serviceId2)|
||Mark two service ids as being the same. [More...](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a729ab2d639aac64165a925734e24d555)|
||   |
||[add_sid_to_url](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga756d433a798321a35d033b62c881b6ad) (varchar url, varchar service=null, varchar serviceId=null, varchar realm=null, varchar sidParamName="sid", varchar cookieSidName="sid", any options=null, varchar sid=null)|
||   |
||[authentication_details_for_connection](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ae4565eb3fc3b48886af76de88fb72dd2) (varchar sid, varchar serviceId, varchar uname, int isRealUser, varchar realm=null, varchar sidParamName="sid", any cert=null, varchar webidGraph=null)|
||   |
||[authentication_service_icon_path](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ac7fb85c78443249751357372a0e6deb8) (varchar service, integer size)|
||   |
||[build_acl_rule_sparql_pattern](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a56222251025e6d9e019b3cccc4c2b83d) (varchar usrIri, varchar ruleGraph, varchar subject=null, integer recursive=null, varchar agent=null, varchar agentClass=null, any access=null, varchar realm=null, varchar name=null, varchar comment=null, varchar scope=null, varchar label=null, int readOnly=0)|
||   |
||[build_restriction_sparql_pattern](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a4a56db38b461010838a17e5c90d338a9) (varchar name=null, varchar comment=null, varchar resource=null, varchar agent=null, varchar agentClass=null, decimal minValue=null, decimal maxValue=null, varchar realm, varchar parameter=null, varchar serviceId=null, varchar label=null)|
||   |
||[check_access_mode_for_resource](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga02d2eab7b4a0c696c72ec6c064ebe982) (varchar serviceId, varchar ipAddress=null, varchar resource, varchar realm, varchar mode, varchar scope, varchar webidGraph=null, any certificate=null, varchar sameAsGraph=null, int honorScopeState=0, int evalRecursiveRules=0)|
||Convinience procedure to check for a specific mode on one resource. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga02d2eab7b4a0c696c72ec6c064ebe982)|
||   |
||[check_acl_group_condition](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#abca54b2da7c1850502f380ed725d2176) (varchar serviceId, varchar criteria, varchar compPattern, varchar value, varchar query, varchar property, varchar object, varchar maker, any cert=null, varchar webidGraph=null, varchar sameAsGraph=null)|
||   |
||[check_acls_for_named_graph](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga0941b8fe50d5a3c1b51b13a00945f090) (varchar serviceId, varchar uname=null, varchar ipAddress=null, varchar graphUri, varchar realm=null, varchar webidGraph=null, any certificate=null, varchar sameAsGraph=null, int honorScopeState=0, int includeVirtuosoSecurity=1)|
||Check access for a given user and named graph. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga0941b8fe50d5a3c1b51b13a00945f090)|
||   |
||[check_acls_for_resource](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9a2351c047a02b3ce8457e49c804e3d8) (varchar serviceId, varchar ipAddress=null, varchar resource=null, varchar realm, varchar mode=null, varchar scope=null, varchar webidGraph=null, any certificate=null, varchar sameAsGraph=null, int honorScopeState=0, int evalRecursiveRules=0)|
||Find permissions for resources as set by ACL rules in a certain realm. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9a2351c047a02b3ce8457e49c804e3d8)|
||   |
||[check_acls_for_resource_basic](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gab6cf3963a149b67dcaa0fe6f84553f7d) (varchar serviceId, varchar resource=null, varchar realm, varchar mode=null, varchar scope=null, varchar sameAsGraph=null, int evalRecursiveRules=0)|
||Check Basic ACLs for a resource. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gab6cf3963a149b67dcaa0fe6f84553f7d)|
||   |
||[check_acls_for_resource_conditional](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga32a11e8482d82953d61ba58723939163) (varchar serviceId, varchar resource=null, varchar realm, varchar mode=null, varchar scope=null, varchar webidGraph=null, any certificate=null, varchar sameAsGraph=null, int evalRecursiveRules=0)|
||Check Conditional ACLs for a resource. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga32a11e8482d82953d61ba58723939163)|
||   |
||[check_acls_for_resource_ip_address](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga6fdbdf0af83dda6a465b71ee1035dc51) (varchar ipAddress, varchar resource=null, varchar realm, varchar mode=null, varchar scope=null, int evalRecursiveRules=0)|
||Check ACLs granting access to IP Addresses. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga6fdbdf0af83dda6a465b71ee1035dc51)|
||   |
||[check_acls_for_resource_public](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga7bd78e6bbeb0650cd410e15782ba5525) (varchar resource=null, varchar realm, varchar mode=null, varchar scope=null, int evalRecursiveRules=0)|
||Check Public ACLs for a resource. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga7bd78e6bbeb0650cd410e15782ba5525)|
||   |
||[check_conditional_group_membership](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a153d9eec2de8ff905930ee2c55efa12d) (varchar groupIri, varchar serviceId, varchar owner, varchar realm, varchar webidGraph=null, any certificate=null, varchar sameAsGraph=null)|
||Check if a given serviceId is part of a given conditional group. [More...](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a153d9eec2de8ff905930ee2c55efa12d)|
||   |
||[check_resource_ownership](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gad799c6d8a25e07dd477590502d3b9731) (varchar serviceId, varchar resource, varchar scope, varchar sameAsGraph=null)|
||Check the ownership of a resource. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gad799c6d8a25e07dd477590502d3b9731)|
||   |
||[clear_graph_acl_cache](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a07bca037fbbb0e7bb66fbaf1d15e5e58) (varchar serviceId=null, varchar realm=null, int forced=0)|
||Clear the named graph ACL cache for a given service id and realm. [More...](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a07bca037fbbb0e7bb66fbaf1d15e5e58)|
||   |
||[count_acl_rules_for_resource](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gabbe236f4cfd9c8cc782fbdfacdbe14b0) (varchar resource, varchar scope, varchar realm=null)|
||Count the number of ACL rules for a given resource. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gabbe236f4cfd9c8cc782fbdfacdbe14b0)|
||   |
||[create_acl_group_condition_uri](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#aa64fc514d73d77606d9f7ebe70b17806) (varchar serviceId)|
||   |
||[create_acl_group_uri](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#add3cb2cc62101a83cf9b03b62ba6ed0f) (varchar serviceId)|
||   |
||[create_acl_rule_uri](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ae039e74c758f1792d3b48f17057e1009) (varchar serviceId)|
||   |
||[create_login_page_url](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gaca0ee199741126f9b1fda4e52ab3b143) (varchar url, varchar deniedService=null, varchar deniedServiceId=null, varchar realm=null)|
||   |
||[create_restriction_uri](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a63565efe9f4230d13588fa77711cbf3c) ()|
||   |
||[create_val_vhosts](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a59db7e5873c813d54fdd85fd1ed03c01) (varchar vhost, varchar lhost, integer ssl=0, varchar httpsCert=null, varchar httpsKey=null, int httpsVerify=null, int httpsCvDepth=null)|
||Create the necessary virtual hosts for using [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) authentication on the given endpoint. [More...](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a59db7e5873c813d54fdd85fd1ed03c01)|
||   |
||[dav_resource_owner_by_url](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a78326aa784b6473d9670a82c2cd039ac) (varchar url, integer resOwnerId, varchar resOwnerUName, varchar resOwnerName, varchar resOwnerEmail)|
||   |
||[dav_resource_owner_get_service_accounts](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a8e5466663cf86ba2e4ed1491611173e6) (integer resOwnerId)|
||   |
||[default_smtp_server](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga5f68f8a4e9d8d4ccb6541b7565b8c4ab) ()|
||Reads the default smpt server from the Virtuoso configuration. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga5f68f8a4e9d8d4ccb6541b7565b8c4ab)|
||   |
||[digest_authentication](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga23ffe8209155d65fb7f44f1fc0213189) (varchar uname, varchar nonce, varchar pwdHash)|
||   |
||[email_address_for_service_id](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga0e3510e9b6a77b33558bd6d78814afc3) (varchar serviceId)|
||Find an email address for the given service id. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga0e3510e9b6a77b33558bd6d78814afc3)|
||   |
||[ensure_control_permissions_on_res](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ad1c16930cf73d813deee5fb3fb824207) (varchar serviceId, varchar resource, any access, varchar realm, varchar scope)|
||   |
||[exec_sparql](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a5410c1f6661f413c60393d9baf8ebe2e) (varchar query, any params=null, integer useCache=0)|
||   |
||[exec_sparql_with_format](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ac7aa12a4dc7a94592a7479122160d4fd) (varchar query, varchar format, integer useCache=0)|
||   |
||[exec_sql](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#af1901bfd9a7dff48b7f870ea7537fbc2) (varchar query, any params=null, int useCache=1)|
||   |
||[extract_acl_group_conditions_from_blob](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#adbd15697515501e0573f5b72d9d2c1e4) (varchar ruleData, varchar format)|
||   |
||[extract_acl_groups_from_blob](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a60115dd2dda50733e86cff68e3689095) (varchar groupData, varchar format)|
||   |
||[extract_acl_rules_from_blob](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a4a1cb2505a1dd4cd5cad2d7ace54ca75) (varchar ruleData, varchar format)|
||   |
||[extract_restrictions_from_blob](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a47c9fe6679dd9c5915182c140d2257ba) (varchar restData, varchar format)|
||   |
||[find_acl_permissions_basic](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gae69de59e6668f5462635a0e6074f55de) (varchar serviceId, varchar resource=null, varchar realm, varchar mode=null, varchar scope=null, varchar sameAsGraph=null, int evalRecursiveRules=0)|
||   |
||[find_acl_permissions_conditional](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gaf744e6431b91b7bdf9a9d9b85551c4af) (varchar serviceId, varchar resource=null, varchar realm, varchar mode=null, varchar scope=null, varchar webidGraph=null, any certificate=null, varchar sameAsGraph=null, int evalRecursiveRules=0)|
||   |
||[find_acl_permissions_ip_address](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga7212b4d513c2139d886f52c215ac27d5) (varchar ipAddress, varchar resource=null, varchar realm, varchar mode=null, varchar scope=null, int evalRecursiveRules=0)|
||   |
||[find_acl_permissions_public](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga28a729c0fa13d584023bb7aeac4d8687) (varchar resource=null, varchar realm, varchar mode=null, varchar scope=null, int evalRecursiveRules=0)|
||   |
||[find_group_by_name_or_iri](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a1bc0341ed8847ccab926826ad901b4eb) (varchar serviceId, varchar name, varchar realm)|
||   |
||[find_group_condition_by_iri](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#abbad5a0d29b33c8a857c94e7ab7b98ad) (varchar serviceId, varchar uri, varchar realm)|
||   |
||[find_oauth_session_for_service](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ad50528e12eeca63bda928b64e14c5875) (varchar serviceId, varchar service, varchar requiredScope=null)|
||   |
||[find_restriction_by_iri](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#afb2ca347af28fd4bf404b3f77b17c06d) (varchar serviceId, varchar uri, varchar realm)|
||   |
||[find_restrictions](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gab7485fb9ae3ba202e9e27b6741a21901) (varchar serviceId=null, varchar ipAddress=null, varchar resource, varchar realm, varchar webidGraph=null, any certificate=null, decimal minValue, decimal maxValue, varchar parameter=null, varchar sameAsGraph=null)|
||Find the restriction values for a given resource. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gab7485fb9ae3ba202e9e27b6741a21901)|
||   |
||[find_restrictions_basic](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gae37e1bf2ef9317f32005cceee2824a84) (varchar serviceId, varchar resource, varchar realm, decimal minValue, decimal maxValue, varchar parameter=null, varchar sameAsGraph=null)|
||Find the restriction values from basic rules. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gae37e1bf2ef9317f32005cceee2824a84)|
||   |
||[find_restrictions_conditional](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gace67df8f7d7eb4882d21bc1f22050413) (varchar serviceId, varchar resource, varchar realm, varchar webidGraph=null, any certificate=null, decimal minValue, decimal maxValue, varchar parameter=null, varchar sameAsGraph=null)|
||Find the restriction values from conditional rules. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gace67df8f7d7eb4882d21bc1f22050413)|
||   |
||[find_restrictions_ip_address](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga9c992448ca7ff789e767206d1d72bc41) (varchar ipAddress, varchar resource, varchar realm, decimal minValue, decimal maxValue, varchar parameter=null)|
||Find the restriction values from IP Address based rules. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga9c992448ca7ff789e767206d1d72bc41)|
||   |
||[find_restrictions_max](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gad3f57510dc6b58c3ab7a8aa548d92ec3) (varchar serviceId, varchar ipAddress=null, varchar resource, varchar realm=null, varchar webidGraph=null, any certificate=null, varchar parameter=null, varchar sameAsGraph=null)|
||Get the maximum restriction value for a given resource. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gad3f57510dc6b58c3ab7a8aa548d92ec3)|
||   |
||[find_restrictions_min](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga945480c6422506359ba72652b1b6e35e) (varchar serviceId, varchar ipAddress=null, varchar resource, varchar realm=null, varchar webidGraph=null, any certificate=null, varchar parameter=null, varchar sameAsGraph=null)|
||Get the minimum restriction value for a given resource. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga945480c6422506359ba72652b1b6e35e)|
||   |
||[find_restrictions_public](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gae9dbe8048d87a1ac43cf187ed824201f) (varchar resource, varchar realm, decimal minValue, decimal maxValue, varchar parameter=null)|
||Find the restriction values from public rules. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gae9dbe8048d87a1ac43cf187ed824201f)|
||   |
||[find_rule_by_iri](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a0b3dc7fca2eed90f881b4c92a8dedf2b) (varchar serviceId, varchar uri, varchar realm)|
||   |
||[foaf_iri](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a20513d457dadbbfb610ea787eb9a0609) (varchar s)|
||   |
||[get_accept_mime_type](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#af08e4cab7d81bfb0455d339d5d9ac660) (varchar format=null)|
||   |
||[get_acl_schema_graph](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga1c832c5509c57c7dcb4f1128ff656d8f) ()|
||The VAL ACL Schema graph IRI. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga1c832c5509c57c7dcb4f1128ff656d8f)|
||   |
||[get_applicable_access_for_scope](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga6321049570d5aea012c2f21facef80df) (varchar scope)|
||Get the list of applicable access modes for a given scope. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga6321049570d5aea012c2f21facef80df)|
||   |
||[get_authentication_details_for_connection](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga745878ab820820c45f26d15217824cfa) (varchar sid, varchar serviceId, varchar uname, int isRealUser, varchar realm=null, varchar sidParamName="sid", any cert, varchar webidGraph=null)|
||Checks for existing authentication information in the current connection. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga745878ab820820c45f26d15217824cfa)|
||   |
||[get_connection_realm](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gaad46a43c72959c862b8dc40015eafbce) (varchar fallback=null)|
||Get the realm for the current http connection. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gaad46a43c72959c862b8dc40015eafbce)|
||   |
||[get_content_mime_type](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a93314a06fe48b843174131f523404ab5) ()|
||   |
||[get_dav_scope](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gabf8e31f7ee7b8babb2432ee54ce4a387) ()|
||The IRI of the DAV ACL rule scope. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gabf8e31f7ee7b8babb2432ee54ce4a387)|
||   |
||[get_default_access_for_scope](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga0c9da57d48c38613d17f593917d2e3ce) (varchar scope)|
||Get the list of default access modes for a given scope. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga0c9da57d48c38613d17f593917d2e3ce)|
||   |
||[get_default_realm](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gab4ad86ce5cd06213fa29ee6f2eab6292) ()|
||The default application realm. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gab4ad86ce5cd06213fa29ee6f2eab6292)|
||   |
||[get_owned_graphs](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gaa84c6ea7e257e469fed362afa0f995dd) (varchar serviceId)|
||Get the graphs owned by a given service id. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gaa84c6ea7e257e469fed362afa0f995dd)|
||   |
||[get_ownership_graph_uri](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a2deb0615620db4b32bab170404f21d4e) (varchar scope)|
||   |
||[get_profile_graph_uri](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a39d6bc88bf5dc5006826dd8aaba34571) (varchar serviceId)|
||The graph URI for a given service id. [More...](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a39d6bc88bf5dc5006826dd8aaba34571)|
||   |
||[get_profile_name](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gaca32625bec8fc5666c905918997e3c96) (varchar serviceId)|
||Get the full name for the given profile URI. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gaca32625bec8fc5666c905918997e3c96)|
||   |
||[get_profile_url](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga43385dfc887ccad03701cfc9f4a143c0) (varchar serviceId, varchar service=null)|
||Get a profile URL for a given service ID. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga43385dfc887ccad03701cfc9f4a143c0)|
||   |
||[get_query_scope](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gad7d45951926e95727372402cd3e97b51) ()|
||The IRI of the Query ACL rule scope. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gad7d45951926e95727372402cd3e97b51)|
||   |
||[get_realm_config_value](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a5fe7d8d5130a3b518690550fabd1a8dc) (varchar realm, varchar property)|
||Convinience procedure to get a config value from the given realm. [More...](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a5fe7d8d5130a3b518690550fabd1a8dc)|
||   |
||[get_resource_owner](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gac425bf8c6cf3d2a6e005090cf0505f63) (varchar resource, varchar scope)|
||Get the owner of a resource. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gac425bf8c6cf3d2a6e005090cf0505f63)|
||   |
||[get_restrictions_scope](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gac79d434a51dc8ad154f8952f42983124) ()|
||The IRI of the Restrictions ACL rule scope. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gac79d434a51dc8ad154f8952f42983124)|
||   |
||[get_service_client_key](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a02a504c9b2b974ed1272b2cfb81bb514) (varchar service, any clientId)|
||Get the key and secret for the given service API. [More...](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a02a504c9b2b974ed1272b2cfb81bb514)|
||   |
||[get_sparql_html_footer](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ab24b9081a253bacacd7895a97c439b1b) (varchar pageUrl)|
||   |
||[get_sparql_permissions](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gae955138972efdcf37bc1d50cc61f70c6) (varchar serviceId, varchar uname=null, varchar ipAddress=null, varchar realm=null, varchar webidGraph=null, any certificate=null, varchar sameAsGraph=null)|
||Check the generic SPARQL permissions for the given authentication information. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gae955138972efdcf37bc1d50cc61f70c6)|
||   |
||[get_sparql_permissions_for_sql_user](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a32f10cd2a5aa21a7e959b37999c4fb46) (varchar uname)|
||   |
||[get_sparql_scope](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga27e327bb4de4c515266db21601600c0b) ()|
||The IRI of the Private named graphs ACL rule scope. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga27e327bb4de4c515266db21601600c0b)|
||   |
||[http_to_https_uri](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga1fb3e8864649b678769092c6b52f72a3) (varchar uri, int checkForVhost=0)|
||Convert an HTTP URI into its HTTPS counterpart. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga1fb3e8864649b678769092c6b52f72a3)|
||   |
||[is_admin_user](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga6d55cc950a8e04c8e1372dad15521922) (varchar uname)|
||Check if a given SQL user is `dba` or in the admin group (role) [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga6d55cc950a8e04c8e1372dad15521922)|
||   |
||[load_triples_into_tmp_graph](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ab36c1eda059016c1488105dcd6f00a82) (varchar data, varchar format)|
||   |
||[logout](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga3b4ad3ebbecda2375698fff095d64f77) (varchar sid=null, varchar sidParamName="sid")|
||Clear authentication information. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga3b4ad3ebbecda2375698fff095d64f77)|
||   |
||[new_user_session](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga4f5af9c98b75233c21a7edd7715ecc41) (varchar uname, varchar realm=null, int checkDeactivated=0, any options=null)|
||   |
||[normalize_dav_path](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a610f1d8c9e7ba6240263074b04df8ef0) (varchar url)|
||Normalizes the path in a DAV url. [More...](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a610f1d8c9e7ba6240263074b04df8ef0)|
||   |
||[normalize_host](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a3bf0e2f98eecbb7725d8ca34994016f0) (varchar vhost, varchar lhost)|
||   |
||[normalize_vhost_and_lhost](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a4649a1a33ec7df84d108d1ffa46026bc) (varchar vhost, varchar lhost)|
||   |
||[oauth_refresh_token](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#gae780b9ab20c441bb27991994762821ae) (varchar service=null, varchar serviceId=null, int force=0, varchar oauthSid=null, varchar scope=null)|
||Refresh an OAuth access token based on service type and service id. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#gae780b9ab20c441bb27991994762821ae)|
||   |
||[oplacl_iri](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a0b23bb541e4472a74389670ea2885731) (varchar s)|
||   |
||[oplres_iri](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a0da24d0bc5ad932dc7ca7e20c31bee3f) (varchar s)|
||   |
||[ownership_graph_group](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga2bc430de1c302d6fff5d01b79e98454e) (varchar scope)|
||The URI of the graph group used to combine all resource ownership graphs. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga2bc430de1c302d6fff5d01b79e98454e)|
||   |
||[prepare_sql_params](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#aed8531c00be3b6f82b15826d5f59080b) (varchar _sql, any _sqlParams, any _params)|
||   |
||[rdfs_iri](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#abf17951c324d3e2f35c48bc6c5cdeb79) (varchar s)|
||   |
||[remove_graph_ownership](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a22ecd911ad04cde5ea46b6a12e55828f) (varchar serviceId, varchar graphIri)|
||   |
||[remove_ownership_graph](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gaa0dfb4fcb31b5bb3a6f51d9e5d6269da) (varchar uri, varchar scope)|
||Remove a resource ownership graph. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gaa0dfb4fcb31b5bb3a6f51d9e5d6269da)|
||   |
||[remove_resource_ownership](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a8fd5031bf4c4a047ab41caf266d73535) (varchar scope, varchar resource, varchar serviceId)|
||   |
||[remove_user_online_mapping](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga6d85d15c62b79c533cd103f3d12936dd) (varchar service, varchar serviceId)|
||   |
||[request_login_nonce](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#gac3fc7b80455871fa062e721f81b3cf0f) ()|
||   |
||[restriction_delete](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9126f9b2b90bbb3b44dcceab02632e33) (varchar uri, varchar realm=null, varchar serviceId=null)|
||Delete a restriction. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#ga9126f9b2b90bbb3b44dcceab02632e33)|
||   |
||[restriction_get](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gac97f9e10fd321c6577e739dd2e1a831b) (any iris, varchar format, varchar realm, varchar serviceId=null)|
||Get the details one or more restrictions. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gac97f9e10fd321c6577e739dd2e1a831b)|
||   |
||[restriction_list](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gae46864a9dc688ecccc7bd27824a71114) (varchar name=null, varchar comment=null, varchar resource=null, varchar agent=null, varchar agentClass=null, decimal minValue=null, decimal maxValue=null, varchar realm, integer details=0, varchar format=null, varchar parameter=null, varchar serviceId=null, varchar label=null)|
||List restrictions defined in a realm. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gae46864a9dc688ecccc7bd27824a71114)|
||   |
||[restriction_new](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gad3bc16f9b48d640a799f787cbd562109) (varchar name=null, varchar comment=null, varchar resource, varchar agent=null, varchar agentClass=null, decimal minValue=null, decimal maxValue=null, varchar realm=null, varchar parameter=null, varchar serviceId=null, varchar label=null)|
||Create a new ACL restriction. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gad3bc16f9b48d640a799f787cbd562109)|
||   |
||[restriction_update](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gaa4a919690984e55fda88b812135330c7) (varchar uri, varchar name=null, varchar comment=null, varchar resource=null, varchar agent=null, varchar agentClass=null, decimal minValue=null, decimal maxValue=null, varchar realm, varchar parameter=null, varchar serviceId=null, varchar label=null)|
||Update properties of an existing restriction. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__internal__api.html#gaa4a919690984e55fda88b812135330c7)|
||   |
||[send_notification_email](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ac8c3b94adee13f1aaebf76121b5b738b) (varchar recipient, varchar subject, varchar text)|
||Send a notification email to some email address from the system. [More...](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ac8c3b94adee13f1aaebf76121b5b738b)|
||   |
||[service_from_profile_uri](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga722e71c1b7f33de735cfa323083d5b65) (varchar url)|
||Extract service name from online account URI. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga722e71c1b7f33de735cfa323083d5b65)|
||   |
||[service_id_to_sql_user](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a0c00892e53521c6054f811bb94ab4123) (varchar serviceId)|
||Try to find a connected SQL account for a given serviceId. [More...](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a0c00892e53521c6054f811bb94ab4123)|
||   |
||[session_id_for_connection](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gaebc0aebc4bcbbb9933bf3f0a0d4bbe6d) (varchar sid, varchar serviceId, varchar realm=null, varchar sidParamName="sid")|
||   |
||[set_graph_context_query](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#abafa69c7b8088a0d78012038dc2b2d32) (varchar serviceId, varchar realm=null, any certificate=null, varchar webidGraph=null)|
||Set the required connection settings for the read-only graph security system. [More...](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#abafa69c7b8088a0d78012038dc2b2d32)|
||   |
||[set_graph_ownership](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a1b330f04d1153b55f8bcb1aa55bf5df4) (varchar serviceId, varchar graphIri)|
||   |
||[set_keyword](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ad2348c477b8cf61229fb5626a034c7df) (varchar name, any params, any value)|
||   |
||[set_resource_ownership](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga39324e0e0cf5fcaf259dac362357b92c) (varchar scope, varchar resource, varchar serviceId)|
||Set the owner of a resource in a given scope. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga39324e0e0cf5fcaf259dac362357b92c)|
||   |
||[setup_val_host](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a5677b0a2e39c8d6c92bc5683a331047c) (varchar httpVHost, varchar httpLHost, varchar httpsVHost, varchar httpsLHost, varchar httpsCert, varchar httpsKey)|
||Setup a [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) host. [More...](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a5677b0a2e39c8d6c92bc5683a331047c)|
||   |
||[smtp_server_available](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga882a0ac491ca06f6514220b72f608bd2) ()|
||Check if a valid SMTP server has been configured. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga882a0ac491ca06f6514220b72f608bd2)|
||   |
||[sparql_access_modes_to_bitmask](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#acbc77ee86753709b37a4f2aa205e1875) (any modes)|
||   |
||[sparql_graph_ownership_graph](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga52fe4f6da197f74fa77f9faf02414363) ()|
||Graph containing the ownership relations for named graphs. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga52fe4f6da197f74fa77f9faf02414363)|
||   |
||[thirdparty_authentication_default_callback](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a70bcb8306e4d6000da135bb30a22b20a) (varchar url, any opts, varchar service, varchar serviceId, any profile, any oauthInfo, varchar oauthSid)|
||Default callback procedure for [VAL.DBA.thirdparty_authentication_url](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga6240c9d79e5a9816f7aa03cdbf73a170 "Create an authentication URL for any supported 3rd-party service."). [More...](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a70bcb8306e4d6000da135bb30a22b20a)|
||   |
||[thirdparty_authentication_default_error_callback](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#afcb2a9b1e7b77f6286dad53a9953ba2e) (varchar url, any opts, varchar service, any _sqlState, any _sqlMessage)|
||   |
||[thirdparty_authentication_url](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga6240c9d79e5a9816f7aa03cdbf73a170) (varchar service, varchar data, varchar callback, varchar successProc=null, varchar errorProc=null, any params=null, varchar scope="basic", varchar clientIp=null, varchar realm=null)|
||Create an authentication URL for any supported 3rd-party service. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga6240c9d79e5a9816f7aa03cdbf73a170)|
||   |
||[thirdparty_callback](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#aae548a70d5c0aa191b0f0547cf98f0e8) (varchar state)|
||   |
||[thirdparty_service_labels](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ad44f48c6401a9d2c8c031fcce2927282) ()|
||A simple map of all supported third-party authentication services and their labels. [More...](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ad44f48c6401a9d2c8c031fcce2927282)|
||   |
||[thirdparty_services](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga94fd59580131de16c4c19e48cc60ef1d) ()|
||A simple map of all supported third-party authentication services, their labels, and oauth apikey urls. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga94fd59580131de16c4c19e48cc60ef1d)|
||   |
||[thirdparty_supported_services](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga81b14cfb51604d9f8e5c95f480a2babd) ()|
||A simple map of all the supported authentication services that can be used in thirdparty_authentication_url. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga81b14cfb51604d9f8e5c95f480a2babd)|
||   |
||[update_graph_acl_cache](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a4c30616174cc981ea5fbbffe5bc9a024) (varchar serviceId, varchar realm=null, any certificate=null, varchar webidGraph=null, int forced=0)|
||Update the named graph ACL cache VAL.DBA.VAL_GRAPH_ACL_CACHE. [More...](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a4c30616174cc981ea5fbbffe5bc9a024)|
||   |
||[update_user_online_mapping](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#gacca9cce5aa606bba90e105a88f5d9c80) (varchar service=null, varchar serviceId, varchar oauthSid=null, any uname)|
||   |
||[user_personal_uri](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga9a2e2f961dfa1e26ee0b420990781d17) (varchar uname)|
||An SQL user's personal URI. [More...](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga9a2e2f961dfa1e26ee0b420990781d17)|
||   |
||[username_for_online_account](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga354775a43d1d1d75abbfa7b205a66210) (varchar service=null, varchar serviceId, any cert=null, varchar webidGraph=null, varchar realm=null)|
||   |
||[val_acl_group_graph](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a935d53cdc397308767d857e72478e64f) (varchar realm, int createGraph=0)|
||   |
||[val_acl_rule_graph](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a21952315f9ce1c577e1c0972ae6a1db5) (varchar realm, int createGraph=0)|
||   |
||[val_config_graph_uri](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#af5427b8c92ded18a3237d00cb83e6795) ()|
||   |
||[val_get_certificate_info](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a174a2775ade00100de7674731aa1a323) (int detail, any cert)|
||   |
||[val_restrictions_graph](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a26dc228ed0bccde995e0fed880308b13) (varchar realm=null, int createGraph=0)|
||   |
||[vector_intersect](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a02cee1a4263ad4dc6c1ff2edc9a24e8b) (any v1, any v2)|
||   |
||[vector_merge](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a54ab7fec2df037018468f31c16bd3ce0) (any v1, any v2)|
||   |

## Function Documentation

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a80cbd62a277cd2098fbc7f357574f0f3) acl_iri()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.acl_iri|(|varchar|_s_|)||

Create a ACL URI. The procedure simply appends the given `s` to the acl namespace.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_ACL`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_ACL` role:

grant VAL_ACL to myuser;

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a51b888c6f038d276fdf0e235ec356b50) add_default_vdirs()

|   |   |   |   |   |
|---|---|---|---|---|
|VAL.DBA.add_default_vdirs|(||)||

Configure the default [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) vhosts

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ab5856e17c84a9224f4cbb58b3d7b5923) add_graph_ownership()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.add_graph_ownership|(|varchar|_serviceId_,|
|||varchar|_graphIri_|
||)|||

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a729ab2d639aac64165a925734e24d555) add_same_as_relation()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.add_same_as_relation|(|varchar|_serviceId1_,|
|||varchar|_serviceId2_|
||)|||

Mark two service ids as being the same.

VAL supports `owl:sameAs` relations for ACL rules and the like. This procedure allows to mark two service ids as being "the same". An `owl:sameAs` relation will be added to VAL's sameAs graph and optionally an entry will be added to VAL_USER_ONLINE_ACCOUNTS if applicable.

Caution: only ever call this procedure if you are certain that the two accounts are the same. This is typically the case if the user authenticated with one service while working with a session connected to the other.

See also

VAL.DBA.val_owl_sameas_graph()

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ae4565eb3fc3b48886af76de88fb72dd2) authentication_details_for_connection()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.authentication_details_for_connection|(|varchar|_sid_,|
|||varchar|_serviceId_,|
|||varchar|_uname_,|
|||int|_isRealUser_,|
|||varchar|_realm_ = `null`,|
|||varchar|_sidParamName_ = `"sid"`,|
|||any|_cert_ = `null`,|
|||varchar|_webidGraph_ = `null`|
||)|||

**[Deprecated:](https://docs.openlinksw.com/valdocs/deprecated.html#_deprecated000001)**

Use [VAL.DBA.get_authentication_details_for_connection()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga745878ab820820c45f26d15217824cfa "Checks for existing authentication information in the current connection.") instead.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ac7fb85c78443249751357372a0e6deb8) authentication_service_icon_path()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.authentication_service_icon_path|(|varchar|_service_,|
|||integer|_size_|
||)|||

Creates the path to an image that can be used to create a login button for the given service type. It uses the images provided by [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html).

**Example:**

If service type `facebook` and size \ 24 are given the following path is returned:

/val/img/social24/facebook.png

If no specific images does exist either `ods.png` or `unknown.png` are used, depending on whether the given `service` is an ODS instance added via ODS' [admin.oauth.odshosts.new()](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#gacb2dde6a02c97a7961971b710ff2ae39 "Create a new ACL rule.") API or not.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a56222251025e6d9e019b3cccc4c2b83d) build_acl_rule_sparql_pattern()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.build_acl_rule_sparql_pattern|(|varchar|_usrIri_,|
|||varchar|_ruleGraph_,|
|||varchar|_subject_ = `null`,|
|||integer|_recursive_ = `null`,|
|||varchar|_agent_ = `null`,|
|||varchar|_agentClass_ = `null`,|
|||any|_access_ = `null`,|
|||varchar|_realm_ = `null`,|
|||varchar|_name_ = `null`,|
|||varchar|_comment_ = `null`,|
|||varchar|_scope_ = `null`,|
|||varchar|_label_ = `null`,|
|||int|_readOnly_ = `0`|
||)|||

This is an internal helper function to avoid code duplication in acl.rule.*

It creates a SPARQL pattern which selects the ACL rules as indicated by the paramters.

Also it improves input parameters by replacing empty strings with null values for easier processing.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a4a56db38b461010838a17e5c90d338a9) build_restriction_sparql_pattern()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.build_restriction_sparql_pattern|(|varchar|_name_ = `null`,|
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

Build a SPARQL pattern to query or insert restrictions.

This procedure is used internally by the ACL restrictions system and should normally never be called in another context.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#abca54b2da7c1850502f380ed725d2176) check_acl_group_condition()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.check_acl_group_condition|(|varchar|_serviceId_,|
|||varchar|_criteria_,|
|||varchar|_compPattern_,|
|||varchar|_value_,|
|||varchar|_query_,|
|||varchar|_property_,|
|||varchar|_object_,|
|||varchar|_maker_,|
|||any|_cert_ = `null`,|
|||varchar|_webidGraph_ = `null`,|
|||varchar|_sameAsGraph_ = `null`|
||)|||

Check an ACL group condition.

Internal procedure used by [VAL.DBA.find_acl_permissions_conditional()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gaf744e6431b91b7bdf9a9d9b85551c4af).

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a153d9eec2de8ff905930ee2c55efa12d) check_conditional_group_membership()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.check_conditional_group_membership|(|varchar|_groupIri_,|
|||varchar|_serviceId_,|
|||varchar|_owner_,|
|||varchar|_realm_,|
|||varchar|_webidGraph_ = `null`,|
|||any|_certificate_ = `null`,|
|||varchar|_sameAsGraph_ = `null`|
||)|||

Check if a given serviceId is part of a given conditional group.

Parameters

|   |   |
|---|---|
|groupIri|The IRI of the conditional group.|
|serviceId|The IRI of the person to check for group membership.|
|owner|The owner of the rule for which this test is relevant. This is used in check_acl_group_condition to set the graph permissions, only graph readable by the rule owner are used for evaluation of conditions.|
|realm|The application realm.|
|webidGraph|The graph in which the WebID profile is cached.|
|certificate|The client certificate in case of WebID authentication.|
|sameAsGraph|This is the graph from which [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) will read owl:sameAs triples to determine which service URIs denote the same person. This defaults to VAL.DBA.val_owl_sameas_graph () which is based on account mappings in VAL.DBA.VAL_USER_ONLINE_ACCOUNTS.|

Returns

`1` if `serviceId` is part of group `groupIri`, `0` otherwise.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a07bca037fbbb0e7bb66fbaf1d15e5e58) clear_graph_acl_cache()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.clear_graph_acl_cache|(|varchar|_serviceId_ = `null`,|
|||varchar|_realm_ = `null`,|
|||int|_forced_ = `0`|
||)|||

Clear the named graph ACL cache for a given service id and realm.

Parameters

|   |   |
|---|---|
|serviceId|The service id (personal uri) of the grantee to clear the cache for. If `null` then the cache will be cleared for all service ids.|
|realm|The realm in which to clear the cache. Falls back to the default realm oplacl:DefaultRealm.|

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#aa64fc514d73d77606d9f7ebe70b17806) create_acl_group_condition_uri()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.create_acl_group_condition_uri|(|varchar|_serviceId_|)||

Internal helper procedure. Do not use outside of VAL!

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#add3cb2cc62101a83cf9b03b62ba6ed0f) create_acl_group_uri()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.create_acl_group_uri|(|varchar|_serviceId_|)||

Internal helper procedure. Do not use outside of VAL!

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ae039e74c758f1792d3b48f17057e1009) create_acl_rule_uri()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.create_acl_rule_uri|(|varchar|_serviceId_|)||

Internal helper procedure. Do not use outside of VAL!

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a63565efe9f4230d13588fa77711cbf3c) create_restriction_uri()

|   |   |   |   |   |
|---|---|---|---|---|
|VAL.DBA.create_restriction_uri|(||)||

Internal helper procedure. Do not use outside of VAL!

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a59db7e5873c813d54fdd85fd1ed03c01) create_val_vhosts()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.create_val_vhosts|(|varchar|_vhost_,|
|||varchar|_lhost_,|
|||integer|_ssl_ = `0`,|
|||varchar|_httpsCert_ = `null`,|
|||varchar|_httpsKey_ = `null`,|
|||int|_httpsVerify_ = `null`,|
|||int|_httpsCvDepth_ = `null`|
||)|||

Create the necessary virtual hosts for using [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) authentication on the given endpoint.

This procedure will setup the required vhosts for /val and /val/api. The former is used to expose the [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) images and the 40x_page for /DAV. The latter only hosts the [thirdparty_callback()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#aae548a70d5c0aa191b0f0547cf98f0e8) function which is required for OAuth and OpenID authentication. In the case of an SSL vhost client certificates will be disabled on the host.

A typical configuration would be as follows:

VAL.DBA.create_val_vhosts ('mysite.com:443', 'mysite.com:443', 1, 'db:https_key_mysite_com', 'db:https_key_mysite_com');

Parameters

|   |   |
|---|---|
|vhost|The virtual host name that the browser presents as Host: entry in the request headers. i.e. Name-based virtual hosting. The default value is taken from the Virtuoso INI file.|
|lhost|The address of the network interface the Virtuoso HTTP server uses to listen and accept connections. The default value is taken from the Virtuoso INI file.|
|ssl|`1` if the host to configure is SSL-secured. If this is set to `null` then the values are determined automatically based on the the first vdir found for the listener.|
|httpsCert|The name of the https certificate to use for the SSL endpoint. If this is set to `null` then the value is determined automatically based on the the first vdir found for the listener.|
|httpsKey|The name of the https key to use for the SSL endpoint. Often the same as `httpsCert`. If this is set to `null` then the value is determined automatically based on the the first vdir found for the listener.|
|httpsVerify|The `https_verify` value for the SSL listener. If this is set to `null` then the value is determined automatically based on the the first vdir found for the listener.|
|httpsCvDepth|The `https_cv_depth` value for the SSL listener. If this is set to `null` then the value is determined automatically based on the the first vdir found for the listener.|

**Typically this procedure is not called directly but via [VAL.DBA.setup_val_host()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a5677b0a2e39c8d6c92bc5683a331047c "Setup a VAL host.").**

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a78326aa784b6473d9670a82c2cd039ac) dav_resource_owner_by_url()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.dav_resource_owner_by_url|(|varchar|_url_,|
|||integer|_resOwnerId_,|
|||varchar|_resOwnerUName_,|
|||varchar|_resOwnerName_,|
|||varchar|_resOwnerEmail_|
||)|||

Determine the owner of any DAV resource by URL.

Returns

`1` on success, `0` if the resource could not be found.

**[Deprecated:](https://docs.openlinksw.com/valdocs/deprecated.html#_deprecated000003)**

Use [VAL.DBA.get_resource_owner()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gac425bf8c6cf3d2a6e005090cf0505f63 "Get the owner of a resource.") instead.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a8e5466663cf86ba2e4ed1491611173e6) dav_resource_owner_get_service_accounts()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.dav_resource_owner_get_service_accounts|(|integer|_resOwnerId_|)||

Get the owner's service accounts which have a profile url

param resOwnerId The ID of the account

Returns

`vector` of vectors with NAME, URL

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ad1c16930cf73d813deee5fb3fb824207) ensure_control_permissions_on_res()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.ensure_control_permissions_on_res|(|varchar|_serviceId_,|
|||varchar|_resource_,|
|||any|_access_,|
|||varchar|_realm_,|
|||varchar|_scope_|
||)|||

Checks if the given `serviceId` owns a given `resource` or has permission to grant the given `access` rights to anyone. Throws a signal if not.

Internal procedure. Do not use outside of [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html).

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a5410c1f6661f413c60393d9baf8ebe2e) exec_sparql()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.exec_sparql|(|varchar|_query_,|
|||any|_params_ = `null`,|
|||integer|_useCache_ = `0`|
||)|||

Execute a sparql query via exec() and thow the signal in case of an error.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ac7aa12a4dc7a94592a7479122160d4fd) exec_sparql_with_format()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.exec_sparql_with_format|(|varchar|_query_,|
|||varchar|_format_,|
|||integer|_useCache_ = `0`|
||)|||

Execute a `describe` or `construct` query, using the given result format.

Throws a signal on error.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#af1901bfd9a7dff48b7f870ea7537fbc2) exec_sql()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.exec_sql|(|varchar|_query_,|
|||any|_params_ = `null`,|
|||int|_useCache_ = `1`|
||)|||

Execute a SQL query via exec() and thow the signal in case of an error.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#adbd15697515501e0573f5b72d9d2c1e4) extract_acl_group_conditions_from_blob()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.extract_acl_group_conditions_from_blob|(|varchar|_ruleData_,|
|||varchar|_format_|
||)|||

Reads the given `ruleData` and extract all the ACL group conditions given within.

Returns

A vector of vectors, each containing a condition where each condition contains: query or criteria, comparator, and value

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a60115dd2dda50733e86cff68e3689095) extract_acl_groups_from_blob()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.extract_acl_groups_from_blob|(|varchar|_groupData_,|
|||varchar|_format_|
||)|||

Reads the given `ruleData` and extract all the ACL groups given within.

Returns

A vector of vectors, each containing name, comment, type (oplacl:ConditionalGroup or null), vector or members, vector of conditions where each condition contains: type, query or criteria or ip pattern, comparator, and value

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a4a1cb2505a1dd4cd5cad2d7ace54ca75) extract_acl_rules_from_blob()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.extract_acl_rules_from_blob|(|varchar|_ruleData_,|
|||varchar|_format_|
||)|||

Reads the given `ruleData` and extract all the ACL rules given within.

Returns

A vector of vectors, each containing

- subject
- recursive (0 or 1)
- agent
- agentClass
- access vector (containing uris like oplacl:Read or oplacl:GrantWrite)
- name
- comment
- scope

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a47c9fe6679dd9c5915182c140d2257ba) extract_restrictions_from_blob()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.extract_restrictions_from_blob|(|varchar|_restData_,|
|||varchar|_format_|
||)|||

Extract a set of restriction objects from a blob of data.

Returns

A vector of vectors, each representing one restriction consisting of:

- name
- comment
- resource
- agent
- agent class
- min value
- max value
- restricted parameter
- label

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a1bc0341ed8847ccab926826ad901b4eb) find_group_by_name_or_iri()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.find_group_by_name_or_iri|(|varchar|_serviceId_,|
|||varchar|_name_,|
|||varchar|_realm_|
||)|||

This is a helper function which only exists to avoid code duplication in acl.group.*

It finds a group in a given named graph by name or IRI. If the group is not found an error is signaled.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#abbad5a0d29b33c8a857c94e7ab7b98ad) find_group_condition_by_iri()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.find_group_condition_by_iri|(|varchar|_serviceId_,|
|||varchar|_uri_,|
|||varchar|_realm_|
||)|||

This is a helper function which only exists to avoid code duplication in acl.group.*

It finds a group condition by IRI. If the group is not found an error is signaled.

Returns

the uri of the group the condition belongs to.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ad50528e12eeca63bda928b64e14c5875) find_oauth_session_for_service()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.find_oauth_session_for_service|(|varchar|_serviceId_,|
|||varchar|_service_,|
|||varchar|_requiredScope_ = `null`|
||)|||

Get an OAuth session id (OAUTH..CLI_SESSIONS:CS_SID) for the given serviceId and the given service and scope. The service can be any of the VAL-supported OAuth services.

The serviceId doe not have to be for the given service, as long as a owl:sameAs relation exists.

Parameters

|   |   |
|---|---|
|serviceId|The authenticated person in need of an OAuth session for service `service`.|
|service|The service for which an OAUth session is required.|
|requiredScope|The scope of the required OAuth session. If `null` any session can be used.|

Returns

The OAuth session ID or `null` if no session matching the request could be found.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#afb2ca347af28fd4bf404b3f77b17c06d) find_restriction_by_iri()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.find_restriction_by_iri|(|varchar|_serviceId_,|
|||varchar|_uri_,|
|||varchar|_realm_|
||)|||

Check if a given restriction exists. If `serviceId` is given and is not the personal uri of `dba`, then the `foaf:maker` of the restriction is also checked.

Throws a signal in case the restriction is not found.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a0b3dc7fca2eed90f881b4c92a8dedf2b) find_rule_by_iri()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.find_rule_by_iri|(|varchar|_serviceId_,|
|||varchar|_uri_,|
|||varchar|_realm_|
||)|||

This is a helper function which only exists to avoid code duplication in acl_rule*

It finds a rule for a given service uri and IRI. If the rule is not found an error is signaled.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a20513d457dadbbfb610ea787eb9a0609) foaf_iri()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.foaf_iri|(|varchar|_s_|)||

Create a foaf URI. The procedure simply appends the given `s` to the foaf namespace.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_ACL`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_ACL` role:

grant VAL_ACL to myuser;

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#af08e4cab7d81bfb0455d339d5d9ac660) get_accept_mime_type()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.get_accept_mime_type|(|varchar|_format_ = `null`|)||

Get the mime type requested by the client from the request headers. Falling back to turtle and allowing to override with a parameter.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a93314a06fe48b843174131f523404ab5) get_content_mime_type()

|   |   |   |   |   |
|---|---|---|---|---|
|VAL.DBA.get_content_mime_type|(||)||

Get the mime type of the content provided by the client from the request headers.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a2deb0615620db4b32bab170404f21d4e) get_ownership_graph_uri()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.get_ownership_graph_uri|(|varchar|_scope_|)||

Internal procedure which returns the URI of the graph used to store ownership relations maintained by VAL itself via [VAL.DBA.set_resource_ownership()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#ga39324e0e0cf5fcaf259dac362357b92c "Set the owner of a resource in a given scope.") and friends.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a39d6bc88bf5dc5006826dd8aaba34571) get_profile_graph_uri()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.get_profile_graph_uri|(|varchar|_serviceId_|)||

The graph URI for a given service id.

VAL does store certain profile details for all users that authenticated at some point via VAL. These details are stored in a private graph which only the person in question has read access to (see also VAL.DBA.store_profile_details()).

Since the Sponger already uses the service id itself as graph URI we use our own internal graph based on the service id and a `urn` prefix.

Returns

The profile graph URI or `null` if `serviceId` is `null` or empty.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a5fe7d8d5130a3b518690550fabd1a8dc) get_realm_config_value()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.get_realm_config_value|(|varchar|_realm_,|
|||varchar|_property_|
||)|||

Convinience procedure to get a config value from the given realm.

VAL typically stores configuration by application realm. This means that most configuration settings are tied to the realm URI within the private configuration graph ([VAL.DBA.val_config_graph_uri()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#af5427b8c92ded18a3237d00cb83e6795)).

This procedure simply returns the configured value for the given property or `null` if there is none.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a02a504c9b2b974ed1272b2cfb81bb514) get_service_client_key()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.get_service_client_key|(|varchar|_service_,|
|||any|_clientId_|
||)|||

Get the key and secret for the given service API.

This procedure reads client id and secret from OAUTH.DBA.APP_REG.

Parameters

|   |   |
|---|---|
|service|The name of the service.|
|clientId[out]|A vector containing the client ID and secret on success.|

Returns

On success `1` is returned, `0` otherwise.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ab24b9081a253bacacd7895a97c439b1b) get_sparql_html_footer()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.get_sparql_html_footer|(|varchar|_pageUrl_|)||

Reads the HTML footer configured for the given web page and returns its contents or `null` if none was configured.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a32f10cd2a5aa21a7e959b37999c4fb46) get_sparql_permissions_for_sql_user()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.get_sparql_permissions_for_sql_user|(|varchar|_uname_|)||

Find the SPARQL permissions for a given user. This refers to the system permissions which are defined by the three roles `SPARQL_SELECT`, `SPARQL_SPONGE`, and `SPARQL_UPDATE`.

Returns

A bitmask as follow:

- `1` for Read
- `2` for Write (returns 7 as write includes read and sponge)
- `4` for Sponge (returns 5 as sponge includes read)

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ab36c1eda059016c1488105dcd6f00a82) load_triples_into_tmp_graph()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.load_triples_into_tmp_graph|(|varchar|_data_,|
|||varchar|_format_|
||)|||

Load the triples in `data` into a tmp graph and return the graph IRI.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a610f1d8c9e7ba6240263074b04df8ef0) normalize_dav_path()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.normalize_dav_path|(|varchar|_url_|)||

Normalizes the path in a DAV url.

Virtuoso allows to create different virtual dirs which point to different locations in the DAV system. This procedure allows to determine the actual DAV path (`/DAV/`...) of the resource in question.

Supported are both http(s) URLs and the special `dav:/` urls which are used to create access-protocol-independant ACL rules on dav resources.

**Example:**

Given a virtual dir `/test` which points to `/DAV/test/foo` the following values for `url` would all return the same path:

- `[http://HOST/test/bar.txt](http://host/test/bar.txt)`
- `[http://HOST/DAV/test/foo/bar.txt](http://host/DAV/test/foo/bar.txt)`
- `dav:/DAV/test/foo/bar`.txt All three would result in the normalized path `/DAV/test/foo/bar`.txt which can be used for internal DAV operations.

Returns

The normalized path of the DAV resource to which `url` refers, or, if the given `url` could not be mapped to any virtual dir, the path from the `url` is returned.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a3bf0e2f98eecbb7725d8ca34994016f0) normalize_host()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.normalize_host|(|varchar|_vhost_,|
|||varchar|_lhost_|
||)|||

Normalizes a vhost value in the same way VHOST_DEFINE does but also replaces _ini_ and _sslini_ with default values from the config.

Returns

The VD in the form HOST:PORT.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a4649a1a33ec7df84d108d1ffa46026bc) normalize_vhost_and_lhost()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.normalize_vhost_and_lhost|(|varchar|_vhost_,|
|||varchar|_lhost_|
||)|||

Normalizes vhost and lhost values the same way VHOST_DEFINE does. Running vhost and lhost values through this procedure will allow a lookup in HTTP_PATH.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a0b23bb541e4472a74389670ea2885731) oplacl_iri()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.oplacl_iri|(|varchar|_s_|)||

Create an OPLACL URI. The procedure simply appends the given `s` to the oplacl namespace.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_ACL`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_ACL` role:

grant VAL_ACL to myuser;

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a0da24d0bc5ad932dc7ca7e20c31bee3f) oplres_iri()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.oplres_iri|(|varchar|_s_|)||

Create an OPLRES URI. The procedure simply appends the given `s` to the oplres namespace.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#aed8531c00be3b6f82b15826d5f59080b) prepare_sql_params()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.prepare_sql_params|(|varchar|__sql_,|
|||any|__sqlParams_,|
|||any|__params_|
||)|||

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#abf17951c324d3e2f35c48bc6c5cdeb79) rdfs_iri()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.rdfs_iri|(|varchar|_s_|)||

Create a RDFS URI. The procedure simply appends the given `s` to the RDFS namespace.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a22ecd911ad04cde5ea46b6a12e55828f) remove_graph_ownership()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.remove_graph_ownership|(|varchar|_serviceId_,|
|||varchar|_graphIri_|
||)|||

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a8fd5031bf4c4a047ab41caf266d73535) remove_resource_ownership()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.remove_resource_ownership|(|varchar|_scope_,|
|||varchar|_resource_,|
|||varchar|_serviceId_|
||)|||

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ac8c3b94adee13f1aaebf76121b5b738b) send_notification_email()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.send_notification_email|(|varchar|_recipient_,|
|||varchar|_subject_,|
|||varchar|_text_|
||)|||

Send a notification email to some email address from the system.

The email will be sent from an address that can be supplied in the vad config page. However, if one is not supplied the it will use "noreply@HOST" where HOST matches the value of http_host() stripped of the port.

This proc will signal an error if email sending fails.

Parameters

|   |   |
|---|---|
|recipient|The email address to send to, like [foo@bar.com](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#)|
|subject|The subject of the email.|
|text|The contents of the email.|

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a0c00892e53521c6054f811bb94ab4123) service_id_to_sql_user()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.service_id_to_sql_user|(|varchar|_serviceId_|)||

Try to find a connected SQL account for a given serviceId.

Returns

The name of the SQL account or `null` if none was found.

Special SQL Execute Permissions

This procedure can be executed by role `VAL_AUTH`. This means that applications running as a SQL user different from `dba` can use the API by being granted the `VAL_AUTH` role:

grant VAL_AUTH to myuser;

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#abafa69c7b8088a0d78012038dc2b2d32) set_graph_context_query()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.set_graph_context_query|(|varchar|_serviceId_,|
|||varchar|_realm_ = `null`,|
|||any|_certificate_ = `null`,|
|||varchar|_webidGraph_ = `null`|
||)|||

Set the required connection settings for the read-only graph security system.

Virtuoso has a secondary graph security system which improves the performance for read-only queries considerably as compared to the graph security callback system (see also DB.DBA.SPARQL_GS_APP_CALLBACK_VAL_SPARQL_PERMS()). The idea is that one query returns the list of graphs a person has access to. This list is then cached and reused on the next query, even between connections.

Warning

Since conditional groups can be arbitrary and [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) has no way of knowing when the membership changes, it is up to the application or the administrator to invalidate the cache whenever ACLs change.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a1b330f04d1153b55f8bcb1aa55bf5df4) set_graph_ownership()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.set_graph_ownership|(|varchar|_serviceId_,|
|||varchar|_graphIri_|
||)|||

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ad2348c477b8cf61229fb5626a034c7df) set_keyword()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.set_keyword|(|varchar|_name_,|
|||any|_params_,|
|||any|_value_|
||)|||

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a5677b0a2e39c8d6c92bc5683a331047c) setup_val_host()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.setup_val_host|(|varchar|_httpVHost_,|
|||varchar|_httpLHost_,|
|||varchar|_httpsVHost_,|
|||varchar|_httpsLHost_,|
|||varchar|_httpsCert_,|
|||varchar|_httpsKey_|
||)|||

Setup a [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) host.

This procedure is used to setup an SSL-protected [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) installation. For this to work properly [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) needs to be able to map an http vhost to its https counterpart.

Without this setup WebID and OAuth services that require an https callback (like Box.com) will not work.

**Example:**

VAL.DBA.setup_val_host('*ini*', '*ini*', 'web.ods.openlinksw.com', ':443', 'db:https_key_web_ods', 'db:https_key_web_ods');

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#acbc77ee86753709b37a4f2aa205e1875) sparql_access_modes_to_bitmask()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.sparql_access_modes_to_bitmask|(|any|_modes_|)||

Create a bitmask from a vector of mode uris.

- `1` for Read
- `2` for Write (returns 7 as write includes read and sponge)
- `4` for Sponge (returns 5 as sponge includes read)

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a70bcb8306e4d6000da135bb30a22b20a) thirdparty_authentication_default_callback()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.thirdparty_authentication_default_callback|(|varchar|_url_,|
|||any|_opts_,|
|||varchar|_service_,|
|||varchar|_serviceId_,|
|||any|_profile_,|
|||any|_oauthInfo_,|
|||varchar|_oauthSid_|
||)|||

Default callback procedure for [VAL.DBA.thirdparty_authentication_url](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga6240c9d79e5a9816f7aa03cdbf73a170 "Create an authentication URL for any supported 3rd-party service.").

This callback procedure will create a session id and return the original url after setting a sid cookie. The session id can be mapped to the serviceId by querying VSPX_SESSION.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#afcb2a9b1e7b77f6286dad53a9953ba2e) thirdparty_authentication_default_error_callback()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.thirdparty_authentication_default_error_callback|(|varchar|_url_,|
|||any|_opts_,|
|||varchar|_service_,|
|||any|__sqlState_,|
|||any|__sqlMessage_|
||)|||

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#aae548a70d5c0aa191b0f0547cf98f0e8) thirdparty_callback()

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|VAL.DBA.thirdparty_callback|(|varchar|_state_|)||

Generic OAuth and OpenID callback. This procedure is exported as a public SOAP/HTTP call. It handles the results from the 3rd-party services and then continues on with the callback procedure as provided to [VAL.DBA.thirdparty_authentication_url()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga6240c9d79e5a9816f7aa03cdbf73a170 "Create an authentication URL for any supported 3rd-party service.").

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ad44f48c6401a9d2c8c031fcce2927282) thirdparty_service_labels()

|   |   |   |   |   |
|---|---|---|---|---|
|VAL.DBA.thirdparty_service_labels|(||)||

A simple map of all supported third-party authentication services and their labels.

**[Deprecated:](https://docs.openlinksw.com/valdocs/deprecated.html#_deprecated000002)**

Please use [VAL.DBA.thirdparty_services()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga94fd59580131de16c4c19e48cc60ef1d "A simple map of all supported third-party authentication services, their labels, and oauth apikey url...") instead.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a4c30616174cc981ea5fbbffe5bc9a024) update_graph_acl_cache()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.update_graph_acl_cache|(|varchar|_serviceId_,|
|||varchar|_realm_ = `null`,|
|||any|_certificate_ = `null`,|
|||varchar|_webidGraph_ = `null`,|
|||int|_forced_ = `0`|
||)|||

Update the named graph ACL cache VAL.DBA.VAL_GRAPH_ACL_CACHE.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a935d53cdc397308767d857e72478e64f) val_acl_group_graph()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.val_acl_group_graph|(|varchar|_realm_,|
|||int|_createGraph_ = `0`|
||)|||

Get the graph the groups are stored in for the given user.

Parameters

|   |   |
|---|---|
|realm|The application realm for which groups should be stored.|
|serviceId|The service id of the user or `null` for querying all groups.|

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a21952315f9ce1c577e1c0972ae6a1db5) val_acl_rule_graph()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.val_acl_rule_graph|(|varchar|_realm_,|
|||int|_createGraph_ = `0`|
||)|||

Get the graph the acl rules are stored in for the given user.

Parameters

|   |   |
|---|---|
|realm|The application realm for which rules should be stored.|
|serviceId|The service id of the user or `null` for querying all rules.|

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#af5427b8c92ded18a3237d00cb83e6795) val_config_graph_uri()

|   |   |   |   |   |
|---|---|---|---|---|
|VAL.DBA.val_config_graph_uri|(||)||

The graph which contains the [VAL](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html) configuration.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a174a2775ade00100de7674731aa1a323) val_get_certificate_info()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.val_get_certificate_info|(|int|_detail_,|
|||any|_cert_|
||)|||

A simple replacement for get_certificate_info which will return `null` if the given `cert` is `null`.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a26dc228ed0bccde995e0fed880308b13) val_restrictions_graph()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.val_restrictions_graph|(|varchar|_realm_ = `null`,|
|||int|_createGraph_ = `0`|
||)|||

Get the graph the restrictions are stored in.

Parameters

|   |   |
|---|---|
|realm|The application realm for which restrictions should be stored. Leave `null` for system restrictions.|

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a02cee1a4263ad4dc6c1ff2edc9a24e8b) vector_intersect()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.vector_intersect|(|any|_v1_,|
|||any|_v2_|
||)|||

Create the intersection of two vectors.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a54ab7fec2df037018468f31c16bd3ce0) vector_merge()

|   |   |   |   |
|---|---|---|---|
|VAL.DBA.vector_merge|(|any|_v1_,|
|||any|_v2_|
||)|||

Merge v2 into v1, eliminating duplicates.