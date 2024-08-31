# Introduction

VAL supports a variety of authentication services via [VAL.DBA.thirdparty_authentication_url()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga6240c9d79e5a9816f7aa03cdbf73a170 "Create an authentication URL for any supported 3rd-party service.") and [VAL.DBA.digest_authentication()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga23ffe8209155d65fb7f44f1fc0213189). In addition [VAL.DBA.authentication_details_for_connection()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ae4565eb3fc3b48886af76de88fb72dd2) supports several means of authenticating.

The following gives an overview of these services and examples of the identifiers used.

# Supported 3rd Party Services

VAL supports a wide range of authentication methods and services. Authentication with any of those methods always yields a personal URI of some kind. This URI is referred to as a NetID, In other words: a NetID is any URI that identifies a person on the network.

The following list shows the different types of authentication services that can be used to authenticate via VAL. Each authentication session resolves to one unique service ID or NetID, i.e. a personal URI. Examples are included in the list.

|Service Type|Identifier used|NetID E|
|---|---|---|
|`facebook`|The profile URL|[http://www.facebook.com/sebastian.trug](http://www.facebook.com/sebastian.trug)|
|`twitter`|The profile URL|[http://twitter.com/tmptrueg](http://twitter.com/tmptrueg)|
|`linkedin`|The profile URL|[https://www.linkedin.com/in/trueg](https://www.linkedin.com/in/trueg)|
|`windowslive`|The profile URL|[http://profile.live.com/cid-7a6b1666d21a866b/](http://profile.live.com/cid-7a6b1666d21a866b/)|
|`google`|The Google Plus URL|[https://plus.google.com/100942621970840297012](https://plus.google.com/100942621970840297012)|
|`wordpress`|The main blog URL|[http://trueg.wordpress.com](http://trueg.wordpress.com/)|
|`disqus`|The profile URL|[http://disqus.com/strueg/](http://disqus.com/strueg/)|
|`instagram`|An acct: URL|acct:[176087504@instagram.com](https://docs.openlinksw.com/valdocs/val_services.html#)|
|`yahoo`|The profile URL|[http://profile.yahoo.com/S4KF6WXGWUBRV74G4TD6GOPCAE](http://profile.yahoo.com/S4KF6WXGWUBRV74G4TD6GOPCAE)|
|`tumblr`|The profile URL|[http://trueg.tumblr.com/](http://trueg.tumblr.com/)|
|`bitly`|The profile URL|[http://bitly.com/u/webods](http://bitly.com/u/webods)|
|`dropbox`|An acct: URL|acct:trueg@dropbox.com|
|`flickr`|The profile URL|[http://www.flickr.com/people/91384569](http://www.flickr.com/people/91384569)@N06/|
|`bitly`|The profile URL|[http://bitly.com/u/strueg](http://bitly.com/u/strueg)|
|`foursquare`|An acct: URL|acct:39809951@foursquare.com|
|`github`|The profile URL|[https://api.github.com/users/trueg](https://api.github.com/users/trueg)|
|`meetup`|The profile URL|[http://www.meetup.com/members/73346552](http://www.meetup.com/members/73346552)|
|`salesforce`|The profile URL|[https://login.salesforce.com/id/00Db0000000J2hSEAS/005b0000000QUONAA4](https://login.salesforce.com/id/00Db0000000J2hSEAS/005b0000000QUONAA4)|
|`boxnet`|An acct: URL|acct:189578964@box.com|
|`xing`|A profile URL|[https://www.xing.com/profile/Max_Mustermann](https://www.xing.com/profile/Max_Mustermann)|
|`beatport`|An acct: URL|acct:trueg@beatport.com|
|`amazon`|An acct: URL|acct:amzn1.account.AGTL7CUF4HT3FTBFX3JWF7QFGKFG@amazon.com|
|`soundcloud`|A profile URL|[http://soundcloud.com/user922973331](http://soundcloud.com/user922973331)|
|`webid`|The personal URI|[http://web.ods.openlinksw.com/dataspace/person/trueg#this](http://web.ods.openlinksw.com/dataspace/person/trueg#this)|
|`openid`|The OpenID URL||

# Supported Authentication Methods

## Session IDs

Authenticating via `authenticate.vsp` (which internally uses [VAL.DBA.thirdparty_authentication_url()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga6240c9d79e5a9816f7aa03cdbf73a170 "Create an authentication URL for any supported 3rd-party service."), and [VAL.DBA.digest_authentication()](https://docs.openlinksw.com/valdocs/group__val__auth__module__main.html#ga23ffe8209155d65fb7f44f1fc0213189)) results in a new session ID which is stored in a new cookie named `"sid"`. This cookie, as long as it is valid, can be used to authenticate to any endpoint using [VAL.DBA.authentication_details_for_connection()](https://docs.openlinksw.com/valdocs/namespaceVAL_1_1DBA.html#ae4565eb3fc3b48886af76de88fb72dd2).

Alternatively the session ID can be provided in a url parameter by the same name: `"sid"`.

## Basic PKI

In this authentication scenario, a standard X.509 client certificate is all that's required. VAL will use the certificate's fingerprint as the service ID.

**Example:** Given a certificate fingerprint `DC:18`:68:D3:4F:9A:08:71:38:4B:D8:B2:74:3E:BE:87 the service ID would be `cert:DC:18`:68:D3:4F:9A:08:71:38:4B:D8:B2:74:3E:BE:87.

VAL also supports a custom HTTP header `X-Application-Realm` which allows to set the application realm when authenticating. This is particular useful for API calls which have different results based on the realm. A typical example is the [VAL Public ACL HTTP API](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html).

## WebID+TLS

VAL supports authentication via [WebID+TLS](http://www.w3.org/wiki/WebID). If a client certificate is sent with the request that contains a valid WebID in its SAN field, then that WebID will be used as a valid service id.

VAL also supports a custom HTTP header `X-Application-Realm` which allows to set the application realm when authenticating. This is particular useful for API calls which have different results based on the realm. A typical example is the [VAL Public ACL HTTP API](https://docs.openlinksw.com/valdocs/group__val__acl__module__http__api.html).

## HTTP Authentication

VAL supports plain HTTP authentication for "real" SQL users of the Virtuoso instance. This is useful for tests and actions performed via curl and friends:

$ curl -u dba:dba -H "Accept:text/turtle" "http://HOST/acl/rules"

- Gener