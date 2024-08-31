# Certificate Authority and Issuer Setup Guide

The following step-by-step guide walks you through the processing of configuring your ODS instance for issuing CA-Authority notarized X.509 certificates for ODS instance users.

## Certificate Authority Setup

1. Install the [ODS Framework](https://virtuoso.openlinksw.com/download/) and [Virtuoso Conductor](https://virtuoso.openlinksw.com/download/) VAD packages.
2. [Bind your Virtuoso HTTPS Listener](http://virtuoso.openlinksw.com/dataspace/dav/wiki/Main/VirtSetupSSLVirtuoso) to host a CA-Authority certificate.

## ODS Endpoint Configuration

_**Note:** If the `DefaultHost` setting value in the Virtuoso INI file is changed, the ODS VAD package must be re-installed before the steps below will succeed._

1. Go to **Conductor** -> **System Admin** -> **Security** -> **Public Key Infrastructure** -> **Configure HTTPS Listeners**.  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSPkiSetup/Picture08.png)  
      
    
2. Click **Configure ODS Endpoints**  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSPkiSetup/Picture09.png)  
      
    
3. Click **Create New Endpoint**
4. Enter the home path for ODS, and save:  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSPkiSetup/Picture10.png)  
      
    
5. The new endpoint should now appear in the Endpoints list:  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSPkiSetup/Picture11.png)  
      
    
6. Go to the HTTPS site, e.g., **`https://<cname>:<port>/ods/`**; in our example, **`https://localhost:4433/ods/`**.
    1. If Firefox is used, it will complain that the certificate is not valid, so we must register the site's certificate.  
          
        ![](https://ods.openlinksw.com/wiki/ODS/ODSPkiSetup/Picture12.png)  
          
        
    2. To add an exception to the Firefox certificate manager, drill down to **Firefox Tools** -> **Options** -> **View Certificates** -> **Servers** -> **Add Exception**.  
          
        ![](https://ods.openlinksw.com/wiki/ODS/ODSPkiSetup/Picture13.png)  
          
        
    3. Confirm exception.  
          
        ![](https://ods.openlinksw.com/wiki/ODS/ODSPkiSetup/Picture14.png)  
          
        
7. Return to the ODS site, and register new user.  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSPkiSetup/Picture15.png)  
      
    
8. [Generate an X.509 Certificate for the new user](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/ODSGenerateX509Certificate).
9. Log out from ODS and refresh browser to simulate opening the ODS site.
10. Go to `https://<cname>:<ssl-port>/ods/`. The browser will ask for a certificate; select the one you generated in the steps above.  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSPkiSetup/Picture21.png)  
      
    
11. ODS presents your card, and asks whether to login with that certificate. Confirm it.  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSPkiSetup/Picture22.png)  
      
    
12. You should now be logged in to ODS via WebID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/WebID&parent=ODSPkiSetup) Protocol.  
      
    ![](https://ods.openlinksw.com/wiki/ODS/ODSPkiSetup/Picture23.png)