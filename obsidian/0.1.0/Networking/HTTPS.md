# Guide for Setting Up the Virtuoso HTTPS Listener using File System to host Certificate and Public Key

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