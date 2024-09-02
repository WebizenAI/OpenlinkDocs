https://docs.openlinksw.com/virtuoso/qsnntp/
## 3.10. NNTP

Virtuoso supports the Network News Transfer Protocol used by Internet newsgroup forums. NNTP servers manage the global network of collected newsgroup postings and represent a vast repository of targeted information archives. As an NNTP aggregator, Virtuoso enables integration of multiple news forums around the world. All news content in Virtuoso is dynamically indexed to provide keyword searches, enabling rapid transformation of disparate text data into information. Virtuoso also acts as an NNTP server, enabling creation of new Internet and Intranet News Forums to leverage the global knowledge base into eBusiness Intelligence.

### 3.10.1. NNTP Server Setup

[¶](https://docs.openlinksw.com/virtuoso/qsnntpservsetup/#qsnntport)

#### Enable Server

Before the NNTP server can be used, it has to be enabled to listen on the NNTP port. This change is made in the configuration file.

For more details, refer to [Enable NNTP Server](https://docs.openlinksw.com/virtuoso/newssrvenable/) section.

[¶](https://docs.openlinksw.com/virtuoso/qsnntpservsetup/#qsnntadd)

#### Create/Attach News Groups

The definition of news groups is held in system tables.

For more details on inserting news groups by SQL command, refer to [Add Groups to NNTP Server](https://docs.openlinksw.com/virtuoso/newssrvadm/) section. See also the [Conductor News Server and Newsgroups Administration](https://docs.openlinksw.com/virtuoso/newssrvadm/) section, to setup the groups in the Visual Server Administration Interface.

[¶](https://docs.openlinksw.com/virtuoso/qsnntpservsetup/#qsnntlimit)

#### Limit Groups

This is an optional step, appropriate if a news group is to be limited for internal use only, or by a group of IP addresses. This is achieved by creating an Access Control List (ACL) in the DB.DBA.NEWS_ACL table. If no ACL is defined, then all groups are public readable and writable.

For table details, refer to [NNTP Server Tables](https://docs.openlinksw.com/virtuoso/newssrvtables/) section.

### 3.10.2. Local & Remote Groups

News groups may be Local such that they are the only instance, or a master instance of a group. Remote groups are ones that are replicated from other news servers.

See the [Conductor News Server and Newsgroups Administration](https://docs.openlinksw.com/virtuoso/newssrvadm/) section, to setup the groups in the Visual Server Administration Interface.

### 3.10.3. NNTP Client Setup

Virtuoso can make a client connection to an external news server to receive newsgroup postings.

For more details, refer to the [NNTP Client](https://docs.openlinksw.com/virtuoso/nntpclient/) section.

###   19.4.1. NNTP Client

[¶](https://docs.openlinksw.com/virtuoso/nntpclient/#fn_nntp_get_dedup)

#### nntp_get_dedup

For detailed description and example use of the function, see [nntp_get](https://docs.openlinksw.com/virtuoso/fn_nntp_get/) in the [Functions Reference Guide](https://docs.openlinksw.com/virtuoso/ch-functions/).