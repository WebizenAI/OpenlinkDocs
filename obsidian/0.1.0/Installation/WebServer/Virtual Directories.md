https://docs.openlinksw.com/virtuoso/qsvirtdir/

### 3.4.1. Virtual Directories

The term virtual directory applies to the mechanism to hide the physical location of a Web resource under different path which user agents use to retrieve it. This mechanism in virtuoso is a part of host definition.

This method is useful when one server has to keep many Web sites. Using a redirect mechanism is not a universal way to do this. It is better to define virtual hosts and paths to the directory entries which contain Web pages.

[¶](https://docs.openlinksw.com/virtuoso/qsvirtdir/#qsvirtdirpl)

#### Creating Virtual Directories Programmatically

For an overview of virtual directories, and how to configure them in PL, refer to the [Virtual Directories Section](https://docs.openlinksw.com/virtuoso/virtdir/) .

[¶](https://docs.openlinksw.com/virtuoso/qsvirtdir/#qsvirtdirui)

#### Setup in Administration Interface

This step by step example will define a virtual directory /help that will point to the directory /departments/support/

1. From the Conductor UI go to Web Application Server/ Virtual Domains & Directories.
    
    **Figure 3.22. Http Hosts and Directories**
    
    ![Http Hosts and Directories](https://docs.openlinksw.com/virtuoso/qsvirtdir/images/ui/virtdir1.png)
    
      
    
2. Open the "folder" icon for your {Default Web Site}.
    
    **Figure 3.23. Edit URL mappings**
    
    ![Edit URL mappings](https://docs.openlinksw.com/virtuoso/qsvirtdir/images/ui/virtdir2.png)
    
      
    
3. Click the link "New Directory" to add a new virtual directory.
    
    **Figure 3.24. Add virtual directory**
    
    ![Add virtual directory](https://docs.openlinksw.com/virtuoso/qsvirtdir/images/ui/virtdir3.png)
    
      
    
4. Select for "Type" File system, as this mapping example will be from one directory to another, and click "Next".
    
    **Figure 3.25. Use File system template**
    
    ![Use File system template](https://docs.openlinksw.com/virtuoso/qsvirtdir/images/ui/virtdir4.png)
    
      
    
5. Enter details in the form to define the mapping. Most of the fields are optional. In this example, only the logical and physical paths and the default page name are required. Click finally the button "Save Changes".
    
    **Figure 3.26. Mapping details**
    
    ![Mapping details](https://docs.openlinksw.com/virtuoso/qsvirtdir/images/ui/virtdir5.png)
    
      
    
6. The following URLs will then be equivalent:
    
    |   |
    |---|
    |http://example.com:8890/help|
    |http://example.com:8890/departments/support/index.html|