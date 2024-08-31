Member [DB::DBA.DBEV_CHECK_CONNECTION_AUTHENTICATION](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#ab11662f0ac480f44e8e2f346c45155fc) (varchar uname)

Use [DB.DBA.DBEV_CHECK_CONNECTION_AUTHENTICATION_2()](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html#ab9c567d76433e1ac35180dc17ac28e53 "Virtuoso callback for internal authentication.") instead.

Member [VAL::DBA.authentication_details_for_connection](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ae4565eb3fc3b48886af76de88fb72dd2) (varchar sid, varchar serviceId, varchar uname, int isRealUser, varchar realm=null, varchar sidParamName="sid", any cert=null, varchar webidGraph=null)

Use [VAL.DBA.get_authentication_details_for_connection()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga745878ab820820c45f26d15217824cfa "Checks for existing authentication information in the current connection.") instead.

Member [VAL::DBA.dav_resource_owner_by_url](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#a78326aa784b6473d9670a82c2cd039ac) (varchar url, integer resOwnerId, varchar resOwnerUName, varchar resOwnerName, varchar resOwnerEmail)

Use [VAL.DBA.get_resource_owner()](https://docs.openlinksw.com/valdocs/group__val__acl__module__utility__api.html#gac425bf8c6cf3d2a6e005090cf0505f63 "Get the owner of a resource.") instead.

Member [VAL::DBA.thirdparty_service_labels](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ad44f48c6401a9d2c8c031fcce2927282) ()

Please use [VAL.DBA.thirdparty_services()](https://docs.openlinksw.com/valdocs/group__val__auth__module__tools.html#ga94fd59580131de16c4c19e48cc60ef1d "A simple map of all supported third-party authentication services, their labels, and oauth apikey url...") instead.