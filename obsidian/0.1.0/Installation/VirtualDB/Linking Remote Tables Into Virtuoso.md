https://docs.openlinksw.com/virtuoso/lnktabvirt/

### 3.3.4. Linking Remote Tables Into Virtuoso

A table on a remote datasource may be linked into the Virtuoso database so that it appears as a local table. Start a browser and point to Conductor, for ex. http://example.com:8890/conductor/. Go to tab "Database", then select "External Data Sources" and then "Sata Sources". Specify the remote datasource that you wish to link to Virtuoso. For example, click the link "connect" for DSN "VirtuosoDemoTest".

**Figure 3.17. Enter login name and password.**

![Enter login name and password.](https://docs.openlinksw.com/virtuoso/lnktabvirt/images/conndsn1a.png)

  

As result should be shown for DSN "VirtuosoDemoTest" the links "Link objects", "Change Credentials", "Disconnect". Click the "Link objects" link.

**Figure 3.18. Connected to datasource.**

![Connected to datasource.](https://docs.openlinksw.com/virtuoso/lnktabvirt/images/conndsn1b.png)

  

Pick the tables to be linked, and define the names to use.

**Figure 3.19. Define tables to link**

![Define tables to link](https://docs.openlinksw.com/virtuoso/lnktabvirt/images/rmtadd.png)