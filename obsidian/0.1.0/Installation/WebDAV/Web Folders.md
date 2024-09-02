https://docs.openlinksw.com/virtuoso/qswebfolders/

### 3.5.1. Web Folders

Microsoft Windows has a notion of a Web Folder. This is how Windows connects to a WebDAV store which can then be traversed like any other file system. Files can be copied and moved to and from the DAV using normal drag-and-drop methods.

1. To create a Web Folder open the _Windows Explorer_ and navigate to _My Network Places_ .
    
    **Figure 3.32. My Network Places**
    
    ![My Network Places](https://docs.openlinksw.com/virtuoso/qswebfolders/images/ui/qs-dav001.png)
    
      
    
2. You will find an icon or option to _Add Network Place_ which when double-clicked will lead you to the wizard.
    
    **Figure 3.33. Web Folder Wizard**
    
    ![Web Folder Wizard](https://docs.openlinksw.com/virtuoso/qswebfolders/images/ui/qs-dav002.png)
    
      
    
3. The first screen encourages you to type the location of the network place, for connecting to a Virtuoso DAV you will need to know the server location and port number. If you installed Virtuoso on to your local machine taking default options then you would probably be typing:
    
    http://example.com:8889/DAV/
    
    **Figure 3.34. WebDAV location**
    
    ![WebDAV location](https://docs.openlinksw.com/virtuoso/qswebfolders/images/ui/qs-dav003.png)
    
      
    
4. You will then be asked for authentication information which will require a username and a password. If defaults are taken then this would simply be dav and dav for both.
    
    **Figure 3.35. WebDAV authentication**
    
    ![WebDAV authentication](https://docs.openlinksw.com/virtuoso/qswebfolders/images/ui/qs-dav004.png)
    
      
    
5. To complete the creation of a Web Folder you be asked to supply a name for the network place.
    
    **Figure 3.36. Name of your WebDAV Web Folder**
    
    ![Name of your WebDAV Web Folder](https://docs.openlinksw.com/virtuoso/qswebfolders/images/ui/qs-dav005.png)
    
      
    
6. Once provided Explorer will automatically open a new Window over looking the new location.
    
    **Figure 3.37. Files contained in your DAV**
    
    ![Files contained in your DAV](https://docs.openlinksw.com/virtuoso/qswebfolders/images/ui/qs-dav006.png)
    
      
    
7. You can find your new Web Folder again from My Network Places where the link will be saved.