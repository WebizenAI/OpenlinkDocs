# Weblog Publishing Platform

ODS-Weblog provides a sophisticated platform for editing and publishing of Weblogs.

## Feature Highlights

### Content Publishing Protocols Support

- Moveable Type
- Blogger (1.0 & 2.0)
- Meta Weblog
- Atom

### Content Syndication Formats

- RSS 1.0
- RSS 2.0 (including variations from Yahoo! and Apple)
- Atom
- OPML
- OCS
- SIOC
- FOAF
- XBEL

### Content Management

- CSS & (X)HTML based Page Templating
- WYSIWYG editor (includes Preview and Save-as-Draft functions)
- Archiving - by year, month, category
- Sophisticated Comment Engine - includes OpenID[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OpenID&parent=OdsBlog) support and transparent integration with NNTP
- Enclosures support for multimedia casting (Podcasts and Videocasts)
- Keyword-driven rules engine for automated content-categorization and tagging
- Automatically generated Linkblogs and Summary Pages (for outbound link automation)
- Search - Free Text, GData, SPARQL, XQuery, and XPath
- Automatic generation of syndication gems (ATOM, RSS 1.0, RSS 2.0, XBEL, OpenSearch[?](https://ods.openlinksw.com/dataspace/owiki/wiki/ODS/OpenSearch&parent=OdsBlog)) for all Search and Query result sets
- Microformats support - RDFa, eRDF, XFN, hReview, and others
- Mobile Blogging for Mobile phones acting as Blog clients

### 3rd Party Integration via web Services

- Automatic pinging of 3rd party services such as: weblogs.com, technorati.com, pingthesemanticweb.com, and others
- Import and Export integration with shard bookmarking services such as del.icio.us
- Automatic synchronization with third party (and other ODS Weblog instances) via rules-based upstreaming

### Security

- Community / Group authored blogs include oles- based security across various profile
- Access-control - Blog readership is controllable via Access Control Lists (ACLs)

# Weblog's Programmers Guide

- [Weblog Controllers](https://ods.openlinksw.com/wiki/ODS/OdsWeblogProgrammersGuide#Weblog%20Controllers)

- [Post new](https://ods.openlinksw.com/wiki/ODS/OdsWeblogProgrammersGuide#Post%20new)
- [Post edit](https://ods.openlinksw.com/wiki/ODS/OdsWeblogProgrammersGuide#Post%20edit)
- [Post delete](https://ods.openlinksw.com/wiki/ODS/OdsWeblogProgrammersGuide#Post%20delete)
- [Post get](https://ods.openlinksw.com/wiki/ODS/OdsWeblogProgrammersGuide#Post%20get)
- [Comment get](https://ods.openlinksw.com/wiki/ODS/OdsWeblogProgrammersGuide#Comment%20get)
- [Comment approve](https://ods.openlinksw.com/wiki/ODS/OdsWeblogProgrammersGuide#Comment%20approve)
- [Comment delete](https://ods.openlinksw.com/wiki/ODS/OdsWeblogProgrammersGuide#Comment%20delete)
- [Comment new](https://ods.openlinksw.com/wiki/ODS/OdsWeblogProgrammersGuide#Comment%20new)
- [Weblog get](https://ods.openlinksw.com/wiki/ODS/OdsWeblogProgrammersGuide#Weblog%20get)
- [Options set](https://ods.openlinksw.com/wiki/ODS/OdsWeblogProgrammersGuide#Options%20set)
- [Options get](https://ods.openlinksw.com/wiki/ODS/OdsWeblogProgrammersGuide#Options%20get)
- [Upstreaming set](https://ods.openlinksw.com/wiki/ODS/OdsWeblogProgrammersGuide#Upstreaming%20set)
- [Upstreaming get](https://ods.openlinksw.com/wiki/ODS/OdsWeblogProgrammersGuide#Upstreaming%20get)
- [Upstreaming remove](https://ods.openlinksw.com/wiki/ODS/OdsWeblogProgrammersGuide#Upstreaming%20remove)
- [Tagging set](https://ods.openlinksw.com/wiki/ODS/OdsWeblogProgrammersGuide#Tagging%20set)
- [Tagging retag](https://ods.openlinksw.com/wiki/ODS/OdsWeblogProgrammersGuide#Tagging%20retag)

## Weblog Controllers

### Post new

- **Description**: Creates new post
- **API name**: `ODS.ODS_API."weblog.post.new"`
- **Parameters**:
    - `inst_id`
    - `categories`
    - `date_created`
    - `description`
    - `enclosure`
    - `source`
    - `title`
    - `link`
    - `author`
    - `comments`
    - `allow_comments`
    - `allow_pings`
    - `convert_breaks`
    - `excerpt`
    - `tb_ping_urls`
    - `text_more`
    - `keywords`
    - `publish`

### Post edit

- **Description**: edits post
- **API name**: `ODS.ODS_API."weblog.post.edit"`
- **Parameters**:
    - `post_id`
    - `categories`
    - `date_created`
    - `description`
    - `enclosure`
    - `source`
    - `title`
    - `link`
    - `author`
    - `comments`
    - `allow_comments`
    - `allow_pings`
    - `convert_breaks`
    - `excerpt`
    - `tb_ping_urls`
    - `text_more`
    - `keywords`
    - `publish`

### Post delete

- **Description**: deletes post
- **API name**: `ODS.ODS_API."weblog.post.delete"`
- **Parameters**:
    - `post_id`

### Post get

- **Description**: gets post by given id
- **API name**: `ODS.ODS_API."weblog.post.get"`
- **Parameters**:
    - `post_id`

### Comment get

- **Description**: gets comment by given comment id
- **API name**: `ODS.ODS_API."weblog.comment.get"`
- **Parameters**:
    - `post_id`
    - `comment_id`

### Comment approve

- **Description**: approves comment
- **API name**: `ODS.ODS_API."weblog.comment.approve"`
- **Parameters**:
    - `post_id`
    - `comment_id`

### Comment delete

- **Description**: deletes comment
- **API name**: `ODS.ODS_API."weblog.comment.delete"`
- **Parameters**:
    - `post_id`
    - `comment_id`

### Comment new

- **Description**: creates new comment
- **API name**: `ODS.ODS_API."weblog.comment.new"`
- **Parameters**:
    - `post_id`
    - `name`
    - `title`
    - `email`
    - `url`
    - `text`

### Weblog get

- **Description**: gets weblog instance by given id
- **API name**: `ODS.ODS_API."weblog.get"`
- **Parameters**:
    - `inst_id`

### Options set

- **Description**: set options
- **API name**: `ODS.ODS_API."weblog.options.set"`
- **Parameters**:
    - `inst_id`
    - `options`

### Options get

- **Description**: get options
- **API name**: `ODS.ODS_API."weblog.options.get"`
- **Parameters**:
    - `inst_id`

### Upstreaming set

- **Description**: sets upstreaming
- **API name**: `ODS.ODS_API."weblog.upstreaming.set"`
- **Parameters**:
    - `inst_id`
    - `target_rpc_url`
    - `target_blog_id`
    - `target_protocol_id`
    - `target_uname`
    - `target_password`
    - `acl_allow`
    - `acl_deny`
    - `sync_interval`
    - `keep_remote`
    - `max_retries`
    - `max_retransmits`
    - `initialize_log`

### Upstreaming get

- **Description**: gets upstreaming
- **API name**: `ODS.ODS_API."weblog.upstreaming.get"`
- **Parameters**:
    - `job_id`

### Upstreaming remove

- **Description**: removes upstreaming
- **API name**: `ODS.ODS_API."weblog.upstreaming.remove"`
- **Parameters**:
    - `job_id`

### Tagging set

- **Description**: defines tagging set
- **API name**: `ODS.ODS_API."weblog.tagging.set"`
- **Parameters**:
    - `inst_id`
    - `flag`

### Tagging retag

- **Description**: retags tagging sets
- **API name**: `ODS.ODS_API."weblog.tagging.retag"`
- **Parameters**:
    - `inst_id`
    - `keep_existing_tags`