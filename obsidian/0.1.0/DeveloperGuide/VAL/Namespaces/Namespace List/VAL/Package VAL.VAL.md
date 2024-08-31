|   |   |
|---|---|
|## Functions|   |
|acl.rule.|[delete](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga6fc68796871aceab36f663c9e580f83e) (varchar uri)|
||Delete an existing rule. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga6fc68796871aceab36f663c9e580f83e)|
||   |
|acl.rule.|[get](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga5f84db9b1b48866081dce9a481efd3fb) (varchar uri, varchar format=null)|
||   |
|acl.rule.|[list](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga4482c35b46473f3d5150478f3ed309c7) (varchar format=null)|
||List all existing rules in the current realm. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga4482c35b46473f3d5150478f3ed309c7)|
||   |
|acl.permissions.|[list](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga139024c82a319b2cd350e5dddc785d27) (varchar uri=null, varchar scope=null, varchar mode=null)|
||List permissions of the authenticated user for a given resource or scope. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga139024c82a319b2cd350e5dddc785d27)|
||   |
||[login](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga20284486a193239f08c9885596f01762) (varchar service)|
||Logs in a UI-less client, returning a session ID through a cookie `sid`. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga20284486a193239f08c9885596f01762)|
||   |
||[logout](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga45612b6dc47b262c761ee6bd98e866ce) ()|
||Logs out a UI-less client which logged in through [VAL.VAL.login](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga20284486a193239f08c9885596f01762 "Logs in a UI-less client, returning a session ID through a cookie sid."). [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#ga45612b6dc47b262c761ee6bd98e866ce)|
||   |
|acl.restriction.|[max](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html#ad1e54c4f4c793bdab5dc4e7c5aadf389) (varchar uri, varchar parameter=null)|
||   |
|acl.restriction.|[min](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html#a03c91a7180356723689492b3ef9bdc95) (varchar uri, varchar parameter=null)|
||   |
|acl.rule.|[new](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#gacb2dde6a02c97a7961971b710ff2ae39) (varchar ruleData=null, varchar format=null)|
||Create a new ACL rule. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#gacb2dde6a02c97a7961971b710ff2ae39)|
||   |
||[profile](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html#a40d4df5eade2340827df95835511aff4) ()|
||Fetch profile information for the authenticated person. [More...](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html#a40d4df5eade2340827df95835511aff4)|
||   |
|acl.restriction.|[update](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html#a21def3a7cea8a27781d4dbc17404a90c) (varchar uri, varchar restrictionData=null, varchar format=null)|
||   |
|acl.rule.|[update](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#gaa4823dd6df2da5874e34424b37f4f401) (varchar uri, varchar ruleData=null, varchar format=null, int overwrite=1)|
||Change an ACL rule's properties. [More...](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html#gaa4823dd6df2da5874e34424b37f4f401)|
||   |
||[val_headless_login_api_success_msg](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html#aacee5d2166ca0540cdaa2ea524397ff6) (varchar httpCode, varchar message)|
||   |
|acl.restriction.|[values](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html#adba527e9d3ad95865634ffc06f7c73b3) (varchar uri, varchar parameter=null)|
||   |

## Function Documentation

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html#ad1e54c4f4c793bdab5dc4e7c5aadf389) max()

|   |   |   |   |
|---|---|---|---|
|acl.restriction. VAL.VAL.max|(|varchar|_uri_,|
|||varchar|_parameter_ = `null`|
||)|||

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html#a03c91a7180356723689492b3ef9bdc95) min()

|   |   |   |   |
|---|---|---|---|
|acl.restriction. VAL.VAL.min|(|varchar|_uri_,|
|||varchar|_parameter_ = `null`|
||)|||

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html#a40d4df5eade2340827df95835511aff4) profile()

|   |   |   |   |   |
|---|---|---|---|---|
|VAL.VAL.profile|(||)||

Fetch profile information for the authenticated person.

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html#a21def3a7cea8a27781d4dbc17404a90c) update()

|   |   |   |   |
|---|---|---|---|
|acl.restriction. VAL.VAL.update|(|varchar|_uri_,|
|||varchar|_restrictionData_ = `null`,|
|||varchar|_format_ = `null`|
||)|||

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html#aacee5d2166ca0540cdaa2ea524397ff6) val_headless_login_api_success_msg()

|   |   |   |   |
|---|---|---|---|
|VAL.VAL.val_headless_login_api_success_msg|(|varchar|_httpCode_,|
|||varchar|_message_|
||)|||

## [◆](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1VAL.html#adba527e9d3ad95865634ffc06f7c73b3) values()

|   |   |   |   |
|---|---|---|---|
|acl.restriction. VAL.VAL.values|(|varchar|_uri_,|
|||varchar|_parameter_ = `null`|
||)|||