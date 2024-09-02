https://docs.openlinksw.com/virtuoso/qsmultihome/

### 3.4.2. Multi Homing

The term Multi Homing refers to the practice of maintaining more than one server on one machine, differentiated by their apparent host name. It is often desirable for companies sharing a web server to have their own domains, with web servers accessible as www.company1.com and www.company2.com, without requiring the user to know any extra path information.

[¶](https://docs.openlinksw.com/virtuoso/qsmultihome/#qsvirthostpl)

#### Creating Multiple Homes Programmatically

For an overview of Multi Homing, and how to configure it with PL, refer to the [Virtual Hosting and Multi Hosting](https://docs.openlinksw.com/virtuoso/virtdir/) section.

[¶](https://docs.openlinksw.com/virtuoso/qsmultihome/#qsvirthostui)

#### Setup in Administration Interface

This step by step example will define a virtual home for the URL http://www.ahelp.com/ to the server www.a.com and directory /departments/support/

1. Have a domain name allocated in the DNS for the ahelp.com that points to the same IP address of the a.com that is hosting a Virtuoso server.
    
2. From the Conductor UI go to Web Application Server/ Virtual Domains & Directories.
    
    **Figure 3.27. Http Hosts and Directories.**
    
    ![Http Hosts and Directories.](https://docs.openlinksw.com/virtuoso/qsmultihome/images/ui/virtdir1.png)
    
      
    
3. To add a new host definition, enter for "Port" 80, enter for "HTTP Host" www.ahelp.com and select the "Add" button.
    
    **Figure 3.28. Add new site**
    
    ![Add new site](https://docs.openlinksw.com/virtuoso/qsmultihome/images/ui/virthost2.png)
    
      
    
4. Click for the new defined site the "Edit" link in order to define the mapping between the virtual host and the actual listening host domain names.
    
    **Figure 3.29. New site mapping**
    
    ![New site mapping](https://docs.openlinksw.com/virtuoso/qsmultihome/images/ui/virthost3.png)
    
      
    
5. Click the "folder" icon for the new defined site and then click the "Edit" link for the Logical Path "/".
    
    **Figure 3.30. Set Logical Path**
    
    ![Set Logical Path](https://docs.openlinksw.com/virtuoso/qsmultihome/images/ui/virthost3a.png)
    
      
    
6. Enter details in the form to define the mapping. Most of the fields are optional. In this example, only the logical and physical paths and the default page name are required.
    
    **Figure 3.31. Mapping details**
    
    ![Mapping details](https://docs.openlinksw.com/virtuoso/qsmultihome/images/ui/virthost4.png)
    
      
    
7. The following URLs will then be equivalent:
    
    |   |
    |---|
    |http://www.ahelp.com/|
    |http://www.a.com/departments/support/index.html|