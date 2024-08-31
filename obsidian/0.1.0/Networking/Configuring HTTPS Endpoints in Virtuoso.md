Virtuoso HTTPS Endpoints can be configured through the Virtuoso Conductor or by manually editing the Virtuoso configuration file.

The Certificate and Public Key upon which the SSL connections depend may be hosted within Virtuoso, or in the local File System. Note that if you want to change where the Certificate and Public Key are hosted (i.e., from Virtuoso to the File System, or vice versa), the Endpoint Listener should be stopped before the configuration is adjusted.

The instructions below presume that if you're manually editing the configuration file, you want to host the Certificate and Public Key in the filesystem. Likewise, if you're configuring the endpoint through the Conductor, it is assumed that you want to host the Certificate and Public Key within Virtuoso.  This can either be done via Virtuoso Conductor or Manually.

## Configuring HTTPS Endpoints [through the Virtuoso Conductor](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtSetupSSLVirtuoso)
### Virtuoso Certificate Authority Setup

The steps that follow guide you through the process of setting up your Virtuoso instance to issue CA-Authority-notarized X.509 certificates that include WebID watermarks.

- [Prerequisites](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso#Prerequisites)
- [Generating CA-Authority Certificate (.p12 or .pfx)](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso#Generating%20CA-Authority%20Certificate%20%28.p12%20or%20.pfx%29)

- [Manually Generating CA-Authority Certificate](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso#Manually%20Generating%20CA-Authority%20Certificate)
- [Importing CA-Authority Certificate](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso#Importing%20CA-Authority%20Certificate)

- [Generating SSL Key Using the Conductor UI](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso#Generating%20SSL%20Key%20Using%20the%20Conductor%20UI)
- [Setting Up Firefox](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso#Setting%20Up%20Firefox)
- [Related](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso#Related)

## Prerequisites

The following packages should be installed:

- [conductor_dav.vad](https://virtuoso.openlinksw.com/download/)

## Generating CA-Authority Certificate (.p12 or .pfx)

### Manually Generating CA-Authority Certificate

1. Go to the **`http://cname:port/conductor`** URL, enter the DBA user credentials.
2. Go to **System Admin** → **Security**  
      
    ![](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso/sca7.png)  
      
    
3. Fill in the form. For example:
    - **Country**: US
    - **State**: MA
    - **Organization**: Example Inc.
    - **Organization Unit**: Example
    - **Name**: Root CA
    - **e-mail**: dba@example.com  
          
        ![](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso/sca8.png)  
          
        
4. Click **Generate**.
5. The CA-Authority Certificate should be successfully generated:  
      
    ![](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso/sca9.png)  
      
    

### Importing CA-Authority Certificate

1. [Generate CA-Authority Certificate](http://id.myopenlink.net/certgen/) that:
    - has **`http://localhost:8890/dataspace/person/dba#this`** as WebID
    - is **Certification Authority (CA) Identity**
    - has **Self-Signed** Issuer
2. Go to the **`http://cname:port/conductor`** URL, enter the "dba" user credentials.
3. Go to **System Admin** → **User Accounts**.  
      
    ![](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso/sca0.png)  
      
    
4. For user **dba**, click **Edit**:  
      
    ![](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso/sca1.png)  
    ![](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso/sca2.png)  
      
    
5. In the presented form for **PKCS12 file**, click **Choose File** and select your CA Certificate; for example, with name **example.p12**:  
      
    ![](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso/sca3.png)  
      
    
6. Enter **Key Name** `id_rsa` and **Key Password** the password your CA Certificate has:  
      
    ![](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso/sca4.png)  
      
    
7. Click **Import Key**
8. On a successful import, the certificate should now be presented in the **Cryptographic Keys** list:  
      
    ![](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso/sca5.png)  
      
    
9. Click **Save**
10. Go to **System Admin** → **Security** → **Public Key Infrastructure**
11. The CA Certificate Details should be presented:  
      
    ![](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso/sca6.png)  
      
    

## Generating SSL Key Using the Conductor UI

_**Note** The following assumes the CA-Authority Certificate has been generated/imported already, as through the sections above._

1. Go to the **`http://cname:port/conductor`** URL, enter the DBA user credentials.  
      
    ![](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso/Picture02.png)  
      
    
2. Go to **System Admin** → **Security**.  
      
    ![](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso/Picture05.png)  
      
    
3. Click **Configure HTTPS Listeners**  
      
    ![](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso/Picture06.png)  
      
    
4. Edit the new listener, and click **Generate New**  
      
    ![](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso/Picture07.png)  
      
    
5. Click **Save**  
      
    ![](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso/Picture08.png)  
      
    

## Setting Up Firefox

1. In the **Preferences** dialog, open the **Advanced** tab, and click the **View certificates** button.
2. Click the **Add exception** button and enter the address of the HTTPS server you've just configured, i.e., **`https://virtuoso.example.com:4433/`**
3. Click **OK**, and confirm the exception.  
      
    ![](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLVirtuoso/Picture_2.png)



## MANUALLY Setting Up the Virtuoso HTTPS Listener using File System to host Certificate and Public Key

To enable the HTTPS listener, you will need a certificate. Existing certificates may not have Subject Alternate Name, so you may want to acquire (or [generate](https://vos.openlinksw.com/dataspace/owiki/wiki/VOS/VirtGenerateX509Cert)) a new one.

1. Move `newcert.pem`, `newkey.pem`, and `cacert.pem` into the server's working directory. In our test case, we put the keys in a '`keys`' sub-directory, and added the following lines to the `[HTTPServer]` section of the Virtuoso INI file (default, `virtuoso.ini`):  
    
      
    SSLPort                     = 4443
    SSLCertificate              = ./keys/newcert.pem
    SSLPrivateKey               = ./keys/newkey.pem
    X509ClientVerifyCAFile      = ./keys/cacert.pem
    X509ClientVerify            = 1
    X509ClientVerifyDepth       = 15
    
      
    
2. Also in the Virtuoso INI file, in the `[URIQA]` section, `DefaultHost` (set to `localhost:8890` below) must be edited to correspond to the DNS-resolvable host name ("CNAME") of the Virtuoso host, combined with the `ServerPort` as set in the `[HTTPServer]` section of the same INI file. Default settings are seen here:  
    
      
    [URIQA]
    DynamicLocal = 1
    DefaultHost  = localhost:8890
    
      
    For instance, if the CNAME of the host is `virtuoso.example.com`, and the `ServerPort` is `4321`, the `DefaultHost` should be set to `virtuoso.example.com:4321`  
    
      
    [URIQA]
    DynamicLocal = 1
    DefaultHost  = virtuoso.example.com:4321
    
      
    
3. Start the Virtuoso server, and look at the log file. Once HTTPS is up, you should see something like —  
    
      
    HTTPS Using X509 Client CA ....
    HTTPS/X509 server online at 4443
    
      
    

## Setting Up Firefox

1. In the **Preferences** dialog, open the **Advanced** tab, and the **Encryption** subtab; then, click the **View certificates** button.  
      
    ![](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLFileSystem/Picture_1.png)  
      
    
2. Click the **Add exception** button, and enter the address of the HTTPS server you've just configured, i.e. —  
    
      
    https://virtuoso.example.com:4443/
    
      
    
3. Click OK, and confirm the exception.  
      
    ![](https://vos.openlinksw.com/owiki/wiki/VOS/VirtSetupSSLFileSystem/Picture_2.png)  
      
    
4. Click to the **Your Certificates** tab, and import `mycert.p12`.