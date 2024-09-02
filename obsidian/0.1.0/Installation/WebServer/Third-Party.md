https://docs.openlinksw.com/virtuoso/qshostingplugs/
## 3.13. Third-Party Runtime Typing, Hosting & User Defined Types

All barriers are broken. If Virtuoso does not readily provide the data type that you require, then make your own. If you want a database trigger to test data against existing externally developed logic, then do that too. Virtuoso has been designed with open-design in mind giving ultimate flexibility. These are the systems current available (linked to the appropriate section of this documentation):

- Runtime Hosting
    
    support other environments and/or languages in-process with Virtuoso and utilizing Virtuoso storage methods such as DAV for replication and roll-out benefits.
    
    - [CLR](https://docs.openlinksw.com/virtuoso/rthclr/) & [Mono](https://docs.openlinksw.com/virtuoso/rthclrmono/)
        
    - [Java](https://docs.openlinksw.com/virtuoso/javaextvm/) & [Jakarta JSP](https://docs.openlinksw.com/virtuoso/rthjsp/)
        
    - [PHP](https://docs.openlinksw.com/virtuoso/servphpext/)
        
    
- [Plugins](https://docs.openlinksw.com/virtuoso/vseplugins/)
    
    enable support for other scripting langauges.
    
    - [Perl](https://docs.openlinksw.com/virtuoso/perlhosting/)
        
    - [Python](https://docs.openlinksw.com/virtuoso/pythonhosting/)
        
    - [Ruby](https://docs.openlinksw.com/virtuoso/rubyhosting/)
        
    
- [Extensibility](https://docs.openlinksw.com/virtuoso/cinterface/)
    
    the above features are applications of one or another of these interfaces, which are provided so that you have the potential to enhance Virtuoso further for more custom requirements.
    
    - [Virtuoso Server Extension Interface (VSEI)](https://docs.openlinksw.com/virtuoso/cinterface/)
        
    - [VSEI Plugins](https://docs.openlinksw.com/virtuoso/vseplugins/)
        
    - [User-Defined Types (UDT)](https://docs.openlinksw.com/virtuoso/ch-functions/)
        
    - [Hosted/Imported Assemblies/Classes](https://docs.openlinksw.com/virtuoso/createassembly/)
        
    
- Web/Service Exposure
    
    every part of Virtuoso can be view, interacted with or consumed by some third-party via a plethora of interfaces, to name a few:
    
    - [SOAP](https://docs.openlinksw.com/virtuoso/ch-functions/)
        
    - [WSDL](https://docs.openlinksw.com/virtuoso/wsdl/)
        
    - Static/Dynamic Web Content
        
    - XML/XSLT
        
        [XML Storage System](https://docs.openlinksw.com/virtuoso/xmlstoragesystem/)
        
        [XML RPC](https://docs.openlinksw.com/virtuoso/xmlrpc/)