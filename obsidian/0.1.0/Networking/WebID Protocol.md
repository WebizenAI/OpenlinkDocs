# WebID Protocol Support in OpenLink Data Spaces

- [What is the WebID](https://ods.openlinksw.com/wiki/ODS/VirtODSSecurityWebID#What%20is%20the%20WebID%20Protocol%3F)[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=VirtODSSecurityWebID) Protocol?
- [Why use the WebID](https://ods.openlinksw.com/wiki/ODS/VirtODSSecurityWebID#Why%20use%20the%20WebID%20Protocol%3F)[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=VirtODSSecurityWebID) Protocol?
- [How can I use the WebID](https://ods.openlinksw.com/wiki/ODS/VirtODSSecurityWebID#How%20can%20I%20use%20the%20WebID%20Protocol%3F)[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=VirtODSSecurityWebID) Protocol?

- [Prerequisites](https://ods.openlinksw.com/wiki/ODS/VirtODSSecurityWebID#Prerequisites)
- [Configure your ODS Account to use the WebID](https://ods.openlinksw.com/wiki/ODS/VirtODSSecurityWebID#Configure%20your%20ODS%20Account%20to%20use%20the%20WebID%20Protocol)[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=VirtODSSecurityWebID) Protocol
- [Test the setup](https://ods.openlinksw.com/wiki/ODS/VirtODSSecurityWebID#Test%20the%20setup)
- [WebID](https://ods.openlinksw.com/wiki/ODS/VirtODSSecurityWebID#WebID%20Protocol%20ACLs)[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=VirtODSSecurityWebID) Protocol ACLs
- [Setup ACL for ODS Applications](https://ods.openlinksw.com/wiki/ODS/VirtODSSecurityWebID#Setup%20ACL%20for%20ODS%20Applications)

- [Related](https://ods.openlinksw.com/wiki/ODS/VirtODSSecurityWebID#Related)

## What is the WebID Protocol?

The **WebID Protocol** is an authentication and authorization protocol that links a ''[Web ID](https://ods.openlinksw.com/wiki/VOS/GetAPersonalURIIn5MinutesOrLess)'' or "[Personal URI](https://ods.openlinksw.com/wiki/VOS/GetAPersonalURIIn5MinutesOrLess)" to a public key to create a global, decentralized, distributed, and secure authentication system that functions with existing browsers.

The WebID Protocol uses PKI standards — usually thought of as hierarchical trust management tools — [in a decentralized web-of-trust way](http://blogs.sun.com/bblfish/entry/foaf_ssl_pki_and_the). The web of trust is built using semantic web vocabularies (particularly [FOAF](http://www.foaf-project.org/)) published in RESTful manner to form Linked Data[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/LinkedData&parent=VirtODSSecurityWebID).

Based on well known existing standards, the WebID Protocol is currently in development, and is being discussed on the [FOAF protocols mailing list](http://lists.foaf-project.org/mailman/listinfo/foaf-protocols).

For the most recent description of the protocol, read the one-page _[WebID Protocol: Adding Security to Open Distributed Social Networks](http://blogs.sun.com/bblfish/entry/foaf_ssl_adding_security_to)._ For a more detailed explanation of how the authentication works, see _[WebID Protocol: Creating a Web of Trust without Key Signing Parties](http://blogs.sun.com/bblfish/entry/more_on_authorization_in_foaf)._

## Why use the WebID Protocol?

Automatic discovery of interpersonal trust relationships enables automatic application of appropriate permissions.

In other words, data owners can set fuzzy permissions like "only let my friends see this" or "only let my family edit this." Applications can discover the relationships between the data owner and the data requester/user, and permit (or disallow) any attempted actions, without needing the data owner to explicitly set permissions for each potential user.

One example might be a parent setting permissions on a photo gallery, to permit viewing only by "immediate family". The parent need not list each and every such relative specifically for this application -- and need not add new permissions for a new family member (whether by marriage, birth, or otherwise), though they **do** need to be added to the owner's FOAF. When a new user comes and asks to see the pictures, the gallery application would check the relationships declared by each person (the owner and the visitor), and if they matched up (in other words, the visitor could not get in simply by **claiming** a family relationship; the relationship must be confirmed by the owner's FOAF data), the pictures would be shown.

## How can I use the WebID Protocol?

### Prerequisites

- [Generate x.509 certificate](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtGenerateX509Cert).
- [Set up Virtuoso HTTPS](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSetupSSLFileSystem).

### Configure your ODS Account to use the WebID Protocol

1. Log in to your ODS account, and edit your profile.
2. Click to the Security Tab, and scroll to the bottom, where you will find the X.509 certificate entry area.
3. Copy & paste the PEM format of the certificate (i.e., the content of `mykey.pem`, from earlier).
4. Press "Save Certificate" button, and you are set.

### Test the setup

To test, we recommend [Virtuoso WebID Verification Proxy Service](http://id.myopenlink.net/ods/webid_demo.html):

1. Go to [Virtuoso WebID Verification Proxy Service](http://id.myopenlink.net/ods/webid_demo.html) Endpoint:
    - Note: Optionally you can hatch the "Check Certificate Expiration" check-box.  
          
        ![](https://ods.openlinksw.com/wiki/ODS/VirtODSSecurityWebID/vf1.png)  
          
        
2. Click the "Check" button.
3. Should be challenged to choose a certificate to present as identification. Select the certificate generated from above and click "Ok":  
      
    ![](https://ods.openlinksw.com/wiki/ODS/VirtODSSecurityWebID/vf2.png)  
      
    
4. Should be presented the extracted WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=VirtODSSecurityWebID) value, the subject, MD5, SHA1 and Timestamp in ISO 8601 format:  
      
    ![](https://ods.openlinksw.com/wiki/ODS/VirtODSSecurityWebID/vf3.png)  
      
    

### WebID Protocol ACLs

You can set WebID Protocol ACLs (Access Control Lists) through the [Virtuoso Authentication Server UI](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtAuthServerUI), for which there is [a tutorial](http://virtuoso.openlinksw.com/wiki/main/Main/VirtSPARQLSecurityWebID).


# Using Virtuoso's WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdpProxy) Identity Provider (IdP[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/IdP&parent=ODSWebIDIdpProxy)) Proxy Service with an X.509 certificate bearing an LDAP scheme WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdpProxy)

- [What?](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdpProxy#What%3F)
- [Why?](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdpProxy#Why%3F)
- [How?](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdpProxy#How%3F)

- [Example Using the Service Endpoint](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdpProxy#Example%20Using%20the%20Service%20Endpoint)

- [Prerequisites](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdpProxy#Prerequisites)
- [Steps](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdpProxy#Steps)

- [Examples Using cURL](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdpProxy#Examples%20Using%20cURL)

- [Prerequisites](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdpProxy#Prerequisites)

- [Using Your Own Virtuoso Instance](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdpProxy#Using%20Your%20Own%20Virtuoso%20Instance)
- [Using A Live Instance](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdpProxy#Using%20A%20Live%20Instance)

- [Example 1: Call the Service with Certificate](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdpProxy#Example%201%3A%20Call%20the%20Service%20with%20Certificate)
- [Example 2: Call the Service without Certificate](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdpProxy#Example%202%3A%20Call%20the%20Service%20without%20Certificate)

- [Related](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdpProxy#Related)

## What?

A callback supporting service that enables third parties verify WebIDs[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebIDs&parent=ODSWebIDIdpProxy) via RESTful interaction patterns.

## Why?

Most Web Developers and Users prefer to do plumbing as opposed to wholesale development in the course of web exploitation. Thus, federated services to which responsibilities can be delegated are always beneficial.

## How?

This verification service offers a user-friendly alternative to manually querying SPARQL endpoints; i.e., checking whether a WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdpProxy) and Public Key are related within a profile graph.

The service currently supports WebIDs[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebIDs&parent=ODSWebIDIdpProxy) based on the `ldap:`, `http:`, `mailto:`, `acct:` URI schemes. Other URI schemes will be added over time.

### Example Using the Service Endpoint

#### Prerequisites

If you want to use your own Virtuoso instance for this exercise, please ensure the following steps are performed:

1. Start Virtuoso server instance (locally, remote, EC2 AMI, etc. );
2. Configure an [HTTPS Listener](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSSetupSSL) for handling HTTPS requests from HTTP user agents (clients);
3. Install the [ODS Framework VAD package](https://virtuoso.openlinksw.com/download/);
4. Install the [HTML based Certificate Generator VAD package](https://virtuoso.openlinksw.com/download/);
5. Create an [X.509 Certificate](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSGenerateX509Certificate) with WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdpProxy) watermark. Otherwise, simply use the live certificate generation service at: [http://id.myopenlink.net/certgen/.](http://id.myopenlink.net/certgen/)

#### Steps

1. Access the service endpoint: `https://<Virtuoso host or IP address>[:<ssl-port>]/ods/webid_check.vsp`, e.g., [https://id.myopenlink.net:443/ods/webid_check.vsp](https://id.myopenlink.net/ods/webid_check.vsp)
2. The browser should prompt for identification. Select the certificate generated above, and click "OK".  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdpProxy/ldap2.png)  
      
    
3. The WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdpProxy) Identity Provider UI should be presented:  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdpProxy/ldap3.png)  
      
    
4. Enter a Requesting service endpoint, for example:  
    
      
    https://id.myopenlink.net/ods/
    
      
      
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdpProxy/ldap4.png)  
      
    
5. Click "Go".
6. When prompted for verification, again the certificate generated above and click "OK":  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdpProxy/ldap2.png)  
      
    
7. You should now be redirected to a log in page which has recognized the certificate's WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdpProxy), and a "WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdpProxy) Login" should be offered:  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdpProxy/ldap5.png)  
      
    
8. Click the "WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdpProxy) Login" button.
9. You should now be successfully logged in:  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdpProxy/ldap6.png)  
      
    

### Examples Using cURL

#### Prerequisites

##### Using Your Own Virtuoso Instance

If you want to use your own Virtuoso instance for this exercise, please ensure the following steps are performed:

1. Start Virtuoso server instance (locally, remote, EC2 AMI, etc. );
2. Configure an [HTTPS Listener](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSSetupSSL) for handling HTTPS requests from HTTP user agents (clients);
3. Install the [ODS Framework VAD package](https://virtuoso.openlinksw.com/download/);
4. Install the [HTML based Certificate Generator VAD package](https://virtuoso.openlinksw.com/download/);
5. Create an [X.509 Certificate](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSGenerateX509Certificate) with WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdpProxy) watermark. Otherwise, simply use the live certificate generation service at: [http://id.myopenlink.net/certgen/.](http://id.myopenlink.net/certgen/)
6. Using the service at: [http://id.myopenlink.net/certgen/,](http://id.myopenlink.net/certgen/,) export the generated X.509 Certificate and its associated private key to a local PKCS#12 (.p12 of .pfx) file system e.g., the file: "demo.p12" and password: "test"; or simply export to a PEM file.
7. Alternatively, you can achieve the same using OpenSSL[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OpenSSL&parent=ODSWebIDIdpProxy) utilities by executing the following from the command line:  
    
      
    openssl pkcs12 -in demo.p12 -out demo.pem -nodes
    
      
    

##### Using A Live Instance

If don't already have an X.509 certificate with a WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdpProxy) watermark, simply use the live certificate generation service at: [http://id.myopenlink.net/certgen/](http://id.myopenlink.net/certgen/) . You can also use this service to export your certificate in PEM and other formats.

#### Example 1: Call the Service with Certificate

1. Execute the following command:  
    
      
    $ curl -i -k --cert demo.pem  https://id.myopenlink.net/ods/webid_check.vsp?callback=http://id.myopenlink.net/myapp/
    Enter PEM pass phrase:
    HTTP/1.1 302 Found
    Server: Virtuoso/06.03.3131 (Linux) x86_64-generic-linux-glibc25-64  VDB
    Connection: Keep-Alive
    Content-Type: text/html; charset=UTF-8
    Date: Thu, 05 Jan 2012 16:08:13 GMT
    Accept-Ranges: bytes
    Location: http://id.myopenlink.net/myapp/?webid=http%3A%2F%2Fid.myopenlink.net%2Fdataspace%2Fperson%2Fdemo%23this&ts=2012-01-05T11%3A08%3A13.000004-05
    %3A00&signature=a17coYTjgrPnz%2FmEi9OVRwiTEa8%3D
    Content-Length: 0
    
      
    
2. In case of successful WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdpProxy) verification, the WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdpProxy) should be returned, as above:  
    
      
    webid=http%3A%2F%2Fid.myopenlink.net%2Fdataspace%2Fperson%2Fdemo%23this 
    
      
    
3. Additionally a timestamp in ISO 8601 format should be returned, as above:  
    
      
    ts=2012-01-05T11%3A08%3A13.000004-05
    
      
    

#### Example 2: Call the Service without Certificate

1. Execute the following command:  
    
      
    $ curl -i -k   https://id.myopenlink.net/ods/webid_check.vsp?callback=http://id.myopenlink.net/myapp/
    HTTP/1.1 302 Found
    Server: Virtuoso/06.03.3131 (Linux) x86_64-generic-linux-glibc25-64  VDB
    Connection: Keep-Alive
    Content-Type: text/html; charset=UTF-8
    Date: Thu, 05 Jan 2012 15:02:16 GMT
    Accept-Ranges: bytes
    Location: http://id.myopenlink.net/myapp/?error=noCert&ts=2012-01-05T10%3A02%3A16-05%3A00&signature=TLNskapgUg75%2FzJSRe154RloH%2FE%3D
    Content-Length: 0
    
      
    
2. The service returns "`error=..`" as it is in our example showing there is no certificate:  
    
      
    error=noCert

# Delegated WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) Verification Service

- [What?](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP#What%3F)
- [Why?](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP#Why%3F)
- [How?](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP#How%3F)

- [Examples of using the Web ID Verification Service Endpoint with requesting Web ID authentication Service Endpoint](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP#Examples%20of%20using%20the%20Web%20ID%20Verification%20Service%20Endpoint%20with%20requesting%20Web%20ID%20authentication%20Service%20Endpoint)

- [Prerequisites](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP#Prerequisites)
- [Example 1](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP#Example%201)
- [Example 2](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP#Example%202)

- [Examples Using cURL](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP#Examples%20Using%20cURL)

- [Prerequisites](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP#Prerequisites)
- [Example 1: Call the Web ID Verification Service with Certificate and Callback URL Parameters](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP#Example%201%3A%20Call%20the%20Web%20ID%20Verification%20Service%20with%20Certificate%20and%20Callback%20URL%20Parameters)
- [Example 2: Call the Web ID Verification Service without Certificate and Callback URL Parameters](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP#Example%202%3A%20Call%20the%20Web%20ID%20Verification%20Service%20without%20Certificate%20and%20Callback%20URL%20Parameters)

- [Client Using the Web ID Verification Service Sample Scenarios](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP#Client%20Using%20the%20Web%20ID%20Verification%20Service%20Sample%20Scenarios)

- [Virtuoso Server Pages (VSP) Example](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP#Virtuoso%20Server%20Pages%20%28VSP%29%20Example)
- [Javascript Example](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP#Javascript%20Example)
- [PHP Example](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP#PHP%20Example)

- [Related](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP#Related)

## What?

A delegated (proxy) service that provides WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) verification to 3rd party HTTP applications. This service currently uses WebIDs[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebIDs&parent=ODSWebIDIdP) based on the following URI schemes: `http:`, `ldap:`, `mailto:`, `acct:`. Other URI schemes will be added over time.

## Why?

WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) shouldn't require developers and end-users to build every layer of the technology stack en route to exploitation. This service provides a simple URL pattern for existing HTTP applications seeking to verify WebIDs[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebIDs&parent=ODSWebIDIdP) via the WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) verification protocol.

## How?

This service takes the following inputs via URL parameters:

- a callback URL (for your actual authentication service endpoint);
- optional X.509 certificate for the identity being verified by the calling service.

It returns the following payload via URL parameters:

- verified WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP);
- error: error code if verification fails;
- ts: timestamp in ISO 8601 format;
- RSA-SHA1 digest (digital signature) of the URL returned to the calling service.

### Examples of using the Web ID Verification Service Endpoint with requesting Web ID authentication Service Endpoint

These examples make use of the following endpoints:

1. [http://id.myopenlink.net/ods/webid_demo.html](http://id.myopenlink.net/ods/webid_demo.html) -- an authentication service that delegates WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) verification to a proxy service
2. [http://id.myopenlink.net/ods/webid_verify.vsp](http://id.myopenlink.net/ods/webid_verify.vsp) -- actual proxy (delegated) service.

#### Prerequisites

If you want to use your own Virtuoso instance for this exercise, please ensure the following steps are performed:

1. Start Virtuoso server instance (locally, remote, EC2 AMI, etc. );
2. Configure an [HTTPS Listener](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSSetupSSL) for handling HTTPS requests from HTTP user agents (clients);
3. Install the [ODS Framework VAD package](https://virtuoso.openlinksw.com/download/);
4. Install the [HTML based Certificate Generator VAD package](https://virtuoso.openlinksw.com/download/);
5. Create an [X.509 Certificate](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSGenerateX509Certificate) with WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) watermark. Otherwise, simply use the live certificate generation service at: [http://id.myopenlink.net/certgen/.](http://id.myopenlink.net/certgen/)

#### Example 1

1. Go to [http://id.myopenlink.net/ods/webid_verify.vsp](http://id.myopenlink.net/ods/webid_verify.vsp) :  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/http1.png)  
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/http2.png)  
      
    
2. Using the form presented, fill in the following:
    - "Requesting service endpoint:": [http://id.myopenlink.net/ods/webid_demo.html](http://id.myopenlink.net/ods/webid_demo.html)
    - Leave the X.509 certificate input area empty:  
          
        ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/http5.png)  
          
        ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/http6.png)
3. Click "Verify".
4. As result you should be redirected to the callback URL and in this case the verification will fail since it doesn't have an X.509 certificate to verify, but a new form is presented due to the effects of the callback URL of the calling service:  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/http7.png)
5. Click on the "Check" button and you will be challenged to presented an X.509 certificate, and if the certificate presented bears a WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) watermark in its Subject Alternative Name (SAN) slot, verification will be successful.  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/http8.png)  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/http9.png)

#### Example 2

1. Go to [http://id.myopenlink.net/ods/webid_verify.vsp](http://id.myopenlink.net/ods/webid_verify.vsp) :  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/http1.png)  
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/http2.png)  
      
    
2. Using the form presented, fill in the following:
    - "Requesting service endpoint:": [http://id.myopenlink.net/ods/webid_demo.html](http://id.myopenlink.net/ods/webid_demo.html)
    - Paste a base64 DER or PEM encoded representation of the X.509 certificate (that has a WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) watermark in its SAN slot) into the X.509 certificate input area:  
          
        ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/http3.png) ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/http3a.png)  
          
        
3. Click "Verify".
4. As result you should be redirected to the callback URL and in our case the verification is successful - the WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP), Subject, RSA-SHA1 digest (digital signature) of the callback URL returned, and timestamp in ISO 8601 format will be presented.  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/http4.png)  
      
    

### Examples Using cURL

#### Prerequisites

If you want to use your own Virtuoso instance for this exercise, please ensure the following steps are performed:

1. Start Virtuoso server instance (locally, remote, EC2 AMI, etc. );
2. Configure an [HTTPS Listener](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSSetupSSL) for handling HTTPS requests from HTTP user agents (clients);
3. Install the [ODS Framework VAD package](https://virtuoso.openlinksw.com/download/);
4. Install the [HTML based Certificate Generator VAD package](https://virtuoso.openlinksw.com/download/);
5. Create an [X.509 Certificate](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSGenerateX509Certificate) with WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) watermark. Otherwise, simply use the live certificate generation service at: [http://id.myopenlink.net/certgen/.](http://id.myopenlink.net/certgen/)
6. Using the service at: [http://id.myopenlink.net/certgen/,](http://id.myopenlink.net/certgen/,) export the generated X.509 Certificate and its associated private key to a local PKCS#12 (.p12 of .pfx) file system e.g., the file: "demo.p12" and password: "test"; or simply export to a PEM file.
7. Alternatively, you can achieve the same using OpenSSL[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OpenSSL&parent=ODSWebIDIdP) utilities by executing the following from the command line:  
    
      
    openssl pkcs12 -in demo.p12 -out demo.pem -nodes
    
      
    

#### Example 1: Call the Web ID Verification Service with Certificate and Callback URL Parameters

In this example the cURL command includes the "`-E`" parameter which provides the X.509 certificate required by the proxy verification service:

  

curl -i -k -E demo.pem:test https://id.myopenlink.net/ods/webid_verify.vsp?callback=http://id.myopenlink.net/ods/webid_demo.html

HTTP/1.1 302 Found
Server: Virtuoso/06.03.3131 (Linux) x86_64-generic-linux-glibc25-64  VDB
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8
Date: Mon, 06 Feb 2012 12:55:55 GMT
Accept-Ranges: bytes
Location: http://id.myopenlink.net/ods/webid_demo.html?webid=http%3A%2F%2Fid.myopenlink.net%2Fdataspace%2Fperson%2Fdemo%23this&ts=2012-02-06T07%3A55%3A55.000011-05%3A00&signature=vVhmk%2Fni1WN%2BEahDdnslPOd%2F8RCXdfdK1Syo4hDrIwCBf%2FDpGIMQjI%2FAhyIZW%2BsvV%2BKlWRBeFsDWyVZjRK6bkx2sC%2B4R4Pj1zH8539p7j8H0j8BLqBV9E3yhVvwTUhf4YdqVbXAzGBVwkuaxpfePWCjFhmvwAtkHH25Mo1wwvCE%3D
Content-Length: 0

1. In case of successful WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) verification, the WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) should be returned, as above:  
    
      
    webid=http%3A%2F%2Fid.myopenlink.net%2Fdataspace%2Fperson%2Fdemo%23this   
    
      
    
2. Additionally a timestamp in ISO 8601 format should be returned, as above:  
    
      
    ts=2012-02-06T07%3A55%3A55.000011-05%3A00
    
      
    

#### Example 2: Call the Web ID Verification Service without Certificate and Callback URL Parameters

In this example the cURL command excludes the "`-E`" parameter. Thus, an X.509 certificate isn't presented to the proxy verification service:

  

curl -i -k https://id.myopenlink.net/ods/webid_verify.vsp?callback=http://id.myopenlink.net/ods/webid_demo.html

HTTP/1.1 302 Found
Server: Virtuoso/06.03.3131 (Linux) x86_64-generic-linux-glibc25-64  VDB
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8
Date: Mon, 06 Feb 2012 13:02:28 GMT
Accept-Ranges: bytes
Location: http://id.myopenlink.net/ods/webid_demo.html?error=noCert&ts=2012-02-06T08%3A02%3A28-05%3A00&signature=Kp99KHmQwv8Ar7R4L5Iofh3ZO63uPUkZu%2FZiS%2FUz%2BF8pdXMQiS4Mjy5vH3WGkqCGLLrEJv1Rth%2BTfZ7TXohtwNrIveZR6jIymLYyacaTY70VZ6Em%2B6SbJxuE3mzfKlmEOeKGIZQkDQcn67PjI2TQ42830ybXjobDr9t9DoNZTHE%3D
Content-Length: 0

1. In case of any error, the service returns "`error=..`" as it is in our example showing there is no certificate to verify:  
    
      
    error=noCert  
    
      
    cURL showcases how the client of a WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) authentication client and proxy service can exchange messages using REST patterns via HTTP.

### Client Using the Web ID Verification Service Sample Scenarios

The following examples include Virtuoso PL (VSP), JavaScript[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/JavaScript&parent=ODSWebIDIdP), and PHP variants. Each has as part of their prototype (or call signature) an Address (a URL) that is used by the `webid_verify.vsp` service.

#### Virtuoso Server Pages (VSP) Example

This example presents a VSP client leveraging service with an X.509 Cert bearing a standard http: scheme URI re. its SAN hosted WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) watermark.

- View the code [here](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSWebIDIdPVSPEx1);
    - **Note**: The VSP pages can be tested/used both in case they are located in OS file system / or DAV. [See more details](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSWebIDIdPVSPModify).

Trying the service via **http**:

1. Access http://<cname>/ods/webid/webid_demo.vsp:  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/js14.png)  
      
    
2. Click the "Check" button.
3. As a result you should be challenged to present an certificate that has WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) watermark:  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/js15.png)  
      
    
4. Click "Ok".
5. As a result you should be redirected to a page with URL including the signature and timestamp REST pattern parameters, and in case of successful authentication, you should be presented the WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) extracted value and timestamp in ISO 8601 format:  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/js16.png)  
      
    

#### Javascript Example

This example presents a JavaScript[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/JavaScript&parent=ODSWebIDIdP) client leveraging service with an X.509 Cert bearing a standard http: scheme URI re. its SAN hosted WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) watermark.

- View the code [here](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSWebIDIdPJScriptEx1);
    - **Note**: The Javascript pages can be tested/used both in case they are located in OS file system / or DAV. [See more details](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSWebIDIdPJavascriptModify).

Trying the service via **http**:

1. Access http://<cname>/ods/webid/webid_demo.html :
    - Note: Optionally you can hatch "Check Certificate Expiration":  
          
        ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/js17.png)  
          
        
2. Click the "Check" button.
3. As a result you should be challenged to present an certificate that has WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) watermark:  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/js15.png)  
      
    
4. Click "Ok".
5. As a result you should be redirected to a page with URL including the signature and timestamp REST pattern parameters, and in case of successful authentication, you should be presented the WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) extracted value, Subject, MD5, SHA1 and timestamp in ISO 8601 format:  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/js18.png)  
      
    

#### PHP Example

This example presents a PHP client leveraging service with an X.509 Cert bearing a standard http: scheme URI re. its SAN hosted WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) watermark.

- View the code [here](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSWebIDIdPPHPEx1);
    - **Notes**: The PHP pages can be tested/used only when they are located in OS file system. [See more details](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSWebIDIdPPHPModify).

Trying the service via **http**:

1. Access http://<cname>/ods/webid/webid_demo.php :  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/js19.png)  
      
    
2. Click the "Check" button.
3. As a result you should be challenged to present an certificate that has WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) watermark:  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/js15.png)  
      
    
4. Click "Ok".
5. As a result you should be redirected to a page with URL including the signature and timestamp REST pattern parameters, and in case of successful authentication, you should be presented the WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSWebIDIdP) extracted value and timestamp in ISO 8601 format:  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSWebIDIdP/js20.png)