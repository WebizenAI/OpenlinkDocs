#### Summary of VAD Operations

The following is what the dba needs to know about [[Installation/VAD Packages]].

A VAD package is installed from a file with the db..vad_install SQL function. The first argument is the file path, which must be in a location that the server process can open, i.e. it is in the DirsAllowed list in the virtuoso.ini file. The second argument is 0, meaning that we are installing from a file.

SQL> vad_install ('conductor_dav.vad', 0);

is an example. If the package installation fails, the server exits and will have to be restarted. No effects of a failed installation will remain in the database after restart. Contact the supplier of the VAD package for further instructions.

To know what is installed, do:

SQL> vad_list_packages ();

VAD package installations are not recorded in the transaction log. Thus, if there is a backup followed by archived transaction logs produced if CheckpointAuditTrail is on in virtuoso.ini, the VAD install must be performed before replaying any logs that were made after the VAD installation. The package installation must be just in the right place in the replay sequence. In practice it is simplest to make an incremental backup after installing and packages, see backup_online () or the section on backing up.

For any further information, including how to make VAD packages, see the rest of this chapter.

[¶](https://docs.openlinksw.com/virtuoso/vaddistr/#vadpackcomposition)

### [VadPacker](https://github.com/openlink/vadpacker) 
vadpacker is a small python tool which allows to create Virtuoso VAD packages from a sticker
file template. This template can contain variables and resource tags which use file globbing.
#### VAD Package Composition

A VAD package has no developer tie-ins; it is built in a development environment from source code that can be managed and versioned in the developers system of preference.

The VAD package is described by an XML structure called the 'VAD Sticker'. The VAD sticker describes items to deploy, procedures to execute at install and uninstall time and all conditions to be checked to ensure correct installation. The VAD Sticker consists of the following:

- VAD package meta data
    
    - Names of package, developer, copyright holder etc.
        
    - Version number of package, build date, build number, build type (e.g. sort of optimization performed).
        
    - Dependency information: minimal/maximal allowed version numbers of Virtuoso server and depending VAD packages. Every required package may include hint-text that may help the administrator determine (a) why the dependent package is required, and (b) how to obtain the required package.
        
    - Information regarding known conflicts between packages; conflicting package names and version number, with optional troubleshooting hints.
        
    - Ability to uninstall, a flag and list of reasons why it may be impossible to uninstall the package.
        
    - Custom configuration data to be placed in the VAD Registry
        
    
- Locations of SQL files containing main and installation code:
    
    - Pre-install code, used to check application-specific installation preconditions.
        
    - Application specific table and view definitions.
        
    - Application specific stored procedure and trigger definitions.
        
    - Post-install (initialization) code, such as initial contents of tables.
        
    - Pre-uninstall code, used to check that it is safe to uninstall a package.
        
    - Post-uninstall code, used for removal of cached resources unusable or meaningless without the package.
        
    
- Locations of Resources:
    
    - Documentation files.
        
    - Samples data for demonstration or package sanity check.
        
    - VSP/VSPX pages, related graphics, Java scripts, stylesheets, other web content.
        
    - XML docs, XSLT sheets, DTDs and Schemas.
        
    

[¶](https://docs.openlinksw.com/virtuoso/vaddistr/#vadpackversion)

#### Package Versioning

All required packages should be listed in the VAD sticker. Known conflict may be listed in either of the conflicting VAD packages stickers, hence VAD stickers of all installed packages should be checked.

Later versions of a package may be installed replacing earlier versions of the same package. This however can be prohibited by listing either version (or limit) as a known conflict in either VAD package sticker in the usual way. Furthermore, it is possible to prevent re-installation of a package by stating that it conflicts with itself. This provides some security against exploits involving attempts to upgrade, downgrade or re-install a package, in the hope that the administrator may corrupt the existing installation by installing new packages and working through installing their dependencies.

Packages may differ in language and encoding of documentation and resource files, even though the version number remains the same. If a package is sensitive to internationalization issues, the developer should either assign different names to various localizations of the package, or divide it into kernel package for any language-independent parts and set of language-specific packages, with some dependency between them.

[¶](https://docs.openlinksw.com/virtuoso/vaddistr/#vadprocessres)

#### Processing of Resources

During creation of a VAD package, the "location" mentioned above may be name of a file in file system or URI or DAV path. Upon package-time, URIs will be resolved and resources under them will be copied into the package. The resulting sticker will thus contain the location of resource within the package, the resource itself, and the target location.

All SQL files have a specific order of loading. Tables, views etc. must be defined before being referenced.

[¶](https://docs.openlinksw.com/virtuoso/vaddistr/#vadunsupportfeat)

#### Unsupported Features of VAD

The VAD specification explicitly does not define the following:

**Method of development or environment.**  There are no specific restrictions for the schema or Virtuoso/PL code of the package. The VAD system does not make assumptions on the method of software development.

**Method of source code control or versioning.**  Version numbers used in the sticker have nothing common with tag labels in a developers versioning system. Procedures edited directly within the database using a web interface or CASE tools should be exported to a file for inclusion in a VAD package. If the application developer uses some script to export such code, this script is not usually part of sticker or the resulting package.

**Shipping/Deployment the VAD package from vendor to user.**  VAD provides no methods for downloading dependent packages, or check for package updates etc.

**Concurrent running of multiple versions of the same VAD package on a single server.**  There can be no guarantee that pre- or post-installation checks will provide valid results if more than one VAD is being processed at the same time. VAD does however guarantee that a package installation will be either entirely successful or entirely rolled back.

**Installation or maintenance of non-Virtuoso hosted components.**  Unlike Virtuoso-based packages, these components are usually operating system specific, they may require some complex tuning, and their usage from within Virtuoso applications may even require changes in virtuoso.ini configuration file. VAD packages may contain test calls in pre-installation SQL procedures to check that required external executables are available and provide the functionality required.

**Data migration.**  Some installations may require several days to complete migration/conversion of stored data. Whilst it may be possible to provide a restricted service during such time, VAD contains no tools to simplify such a process, this is left to the administrator or developer. VAD completes its work right after the execution of the post-installation code.

**Synchronous installation of a package on all hosts of a distributed system or cluster.**  VAD has no standardized metadata regarding replication issues, hence package-specific code may be required. Similarly, if a cluster uses "round-robin" or a "director" loading management system and the server should be stopped for VAD installation, the administrator should explicitly inform the cluster manager about this event.

[¶](https://docs.openlinksw.com/virtuoso/vaddistr/#vadsecurity)

#### Security

Since VAD packages are run by an administrator as the database DBA user, care must be taken to ensure the package comes from a safe source. Any new package installed may violate the security regulations of the target database and may even inflict damage to files under the web-root of the Virtuoso Server or in directories specified in the "DirsAllowed" parameter of the virtuoso.ini. If the virtuoso.ini parameter "AllowOsCalls" is enabled then the installation procedures of the package may call operating executables. It is the responsibility of the database administrator to control this via the "AllowOsCalls", "SafeExecutables" and "DbaExecutables" parameters of the virtuoso.ini.

VAD packages do not offer any automatic protection against unauthorized modifications. Although ever VAD package contains a checksum, its purpose is to guard against data transfer errors, it may not be sufficient to detect unwanted modification.

[¶](https://docs.openlinksw.com/virtuoso/vaddistr/#vadbuildingvadpacks)

#### Building VAD Packages

Initially, the VAD sticker and resources may reside in the file system, DAV directory and or other locations available through the `DB.DBA.HTTP_URI_GET()` function.

The VAD creation operation parses the VAD sticker's XML description and constructs the VAD file by calling [`DB.DBA.VAD_PACK`](https://docs.openlinksw.com/virtuoso/fn_vad_pack/) .

This function reads the VAD sticker identified by the _`sticker_uri`_ which contains the `vad:package` root element. Then the resources identified in the sticker are retrieved. All resource URIs are interpreted in the context of the _`base_uri_of_resources`_ and are parsed and checked to be syntactically correct. Resources are appended to generated package that will be stored at the _`package_uri`_ . [`DB.DBA.VAD_PACK`](https://docs.openlinksw.com/virtuoso/fn_vad_pack/) returns a human readable log of error and warning messages, it will signal errors if any resource or database objects are unavailable at build time.

By convention, VAD package files have the extension '.vad'.

[¶](https://docs.openlinksw.com/virtuoso/vaddistr/#vadutils)

#### VAD Utilities

An optional VAD package named VADutils provides various tools for capturing changes made in the database after some point in time. The result of a capture consists of:

- Database object additions whose names match given patterns (e.g. all tables and procedures within a particular catalog/qualifier).
    
- Resource additions under particular locations.
    
- Post-install local customizations of selected packages.
    

The capture results may be useful for the following purposes:

- Archival of changes for replaying later.
    
- Creating a special package of the changes for applying against a fresh installation of the package.
    
- Creating a new complete package containing both the original and changes that will be included in the package sticker.
    

These mechanisms provide good support for centralized development and custom deployment methodology. If a site is localized to contain local links, graphics, custom layout and such, then VAD capabilities offer help to the developer to define the specific overlay of customizations over another VAD package. When the underlying VAD package is updated the local customizations will be overwritten. Being saved in a VAD package, customizations can be reapplied over the updated base package.

[¶](https://docs.openlinksw.com/virtuoso/vaddistr/#vadadminrspnslts)

#### VAD Administrator Responsibilities

VAD package installation, upgrade and uninstallation requires a temporary break of service. The package checks may be performed on the fly if it can be guaranteed that the resources being inspected will not be altered by any users. The package check is a read-only process and operates solely within the VAD Registry using read-only functions.

All VAD operations are logged in the server event log. All completed operations are reflected in the `DB.DBA.VAD_HISTORY` system table.

The optional VADutils package provides some additional administrative tools, mostly for troubleshooting. These include special installation and de-installation functions that can ignore error signals, and provide an interactive editor for the VAD Registry etc.

All operations described below require DBA access to the database.

Check if a VAD package may be installed by calling [`DB.DBA.VAD_CHECK_INSTALLABILITY`](https://docs.openlinksw.com/virtuoso/fn_vad_check_installability/) .

Checks the presence and correct versions of required packages and of the Virtuoso platform. It does not executes any pre-install Virtuoso/PL code from the package, so there's no guarantee that installation will be successful if the check found no error. If _`package_uri`_ is DAV path, _`is_dav=1`_ , else _`is_dav=0`_ .

Perform VAD Package Installation by calling [`DB.DBA.VAD_INSTALL`](https://docs.openlinksw.com/virtuoso/fn_vad_install/) .

If _`package_uri`_ is DAV path, _`is_dav=1`_ , else _`is_dav=0`_ .

The administrator performs the following operations when installing:

- Invoke the install procedure from the web user interface or interactive SQL. This will perform the following:
    
    - Install documentation files.
        
    - Check for version and prerequisite package compatibility.
        
    - Disconnect SQL users and terminate web processing.
        
    - Make a database checkpoint.
        
    - Run the pre-install SQL script.
        
    - Load SQL code in the VAD package, in the order specified by the developer.
        
    - Copy web resources (VSP, VSPX, XSLT, etc.) into their designated places in WebDAV or file system Web root.
        
    - Run any post-install SQL code.
        
    
- If the installation was successful, the server will come back on-line.
    
- If the installation was unsuccessful, e.g., mid-install failure due to running out of disk space, or some other serious unrecoverable database error, the Virtuoso server will exit. The administrator should consult the Virtuoso log file to see what caused the failure. The installation can be completely undone manually by halting the server (if not already stopped), and removing the transaction log file (.trx). Upon Virtuoso restart, the server will continue from the last checkpoint, made prior to install, as if the installation never took place.
    

The return value of the [`DB.DBA.VAD_INSTALL()`](https://docs.openlinksw.com/virtuoso/fn_vad_install/) function is usually a sum of messages from pre- and post-installation procedures of the package. It should normally contain at least the following:

- any errors and/or warnings encountered.
    
- created users and catalogs/qualifiers
    
- root VSP page for accessing the application, if applicable.
    
- path to installed documentation files.
    
- performance optimization hints.
    

The VAD packages should be tested to install on an empty Virtuoso database, after any required VAD packages. Installing a package on an empty server is useful for determining that no other procedures or components were missed. Since the application would normally run on the development machine where the VAD package was built, it can be easy to overlook some components. The completeness of the source archive of the application and its independence from any ad hoc SQL objects is important, this is the only way the package can be reliably versioned, tracked or uninstalled.

Check if a VAD package may be uninstalled by calling [`DB.DBA.VAD_CHECK_UNINSTALLABILITY`](https://docs.openlinksw.com/virtuoso/fn_vad_check_uninstallability/)

Performs a preliminary read-only checks to see whether the package given can be uninstalled. This does not execute any pre-uninstall Virtuoso/PL code from within the package at this stage. Hence, the success of this function does not guarantee that uninstallation will be successful.

Perform VAD Package Uninstallation by calling [`DB.DBA.VAD_UNINSTALL`](https://docs.openlinksw.com/virtuoso/fn_vad_uninstall/) .

The administrator will perform the following operations for the uninstallation process:

- Invoke the uninstall procedure from the web user interface or interactive SQL. This will initiate the following:
    
    - Check that no other packages are using the package to be uninstalled.
        
    - disconnect SQL users and terminate web processing.
        
    - Make a database checkpoint.
        
    - Run the pre-uninstall SQL script.
        
    - Remove web resources installed by the package (all VSP , VSPX, XSLT, etc files) in WebDAV or the filesystem under the web root.
        
    - Drop all SQL procedures and data. This is performed in reverse order to the install.
        
    - Run any post-uninstall SQL code.
        
    - Remove documentation files explicitly marked as removable. Usually documentation would not be deleted as part of package uninstallation in case it is needed e.g. if a set of documents is distributed as VAD package)
        
    
- If uninstallation was successful the server will come back on-line.
    
- If uninstallation was unsuccessful, the server will exit. Uninstallation could fail due to lack of disk space or some other serious unrecoverable database error. The failed uninstallation attempt can be manually reversed by halting the server (if not already) and deleting the transaction log file (.trx). Upon server restart Virtuoso will continue from the last checkpoint, made prior to uninstallation, as if the uninstallation was never attempted. The administrator should consult the log file for clues to the failure.
    

Check the state of VAD package installation by calling [`DB.DBA.VAD_CHECK`](https://docs.openlinksw.com/virtuoso/fn_vad_check/) .

This checks to see if the elements of the package are as they are defined in the original distribution. A list of differing elements is returned. Differences revealed may not indicate a corruption, such changes could have been made intentionally by another package, possibly a later version or upgrade that added some columns to tables, and some resources may be customized by the user post-installation.

This will check for the prior existence of tables, views etc owned by other applications that are not compatible with this application. Any such schema objects found are listed, the installation will not continue. These may be dropped by the DBA to help the installation to succeed. Some such elements may not be part of some other package, hence no package uninstall would be available leading the DBA to drop them with the appropriate SQL commands.

To enable automatic vads updates on server startup, set the VADInstallDir parameter in the [[Parameters] ini section](https://docs.openlinksw.com/virtuoso/dbadm/) with path the folder containg the vads files.

[¶](https://docs.openlinksw.com/virtuoso/vaddistr/#vadpackageoverlap)

#### Package Overlap

Each package contains full definitions of all tables and indices. Upon installing the following outcomes can occur:

- If a table already exists with the same primary key as the new definition, additional columns are added to the table. If the primary keys differ, the installation automatically fails. Note that a pre-install SQL script can be defined to explicitly alter tables if consecutive versions of an application use different primary keys.
    
- Existing indexes are left untouched. New indices are added as specified in the package. If indices should be modified or dropped, the pre-install script is a reasonable place for dropping these.
    

Thus the same SQL schema can be loaded twice without ill effect.

The post install script should be used to populate tables and such. Inserts should be executed using the insert soft statement so that attempts to insert duplicate are silently ignored without causing the installation to fail. The post install script can perform any application level data format changes.

Packages should define their own distinct catalog or qualifier. They should not overwrite another package unless upgrading a prior version. Sometimes a package will require the use of another package's tables. This should be achieved via grants issued in a pre-install script. A schema element such as a table, view or procedure will always have at most one owner package even though it may be referenced or even modified with additional columns by another package installed later. These elements will only be dropped when the owner package is dropped. Tables created ad-hoc from interactive SQL do not have any owner package.

[¶](https://docs.openlinksw.com/virtuoso/vaddistr/#vadsticker)

#### VAD Sticker

The VAD Sticker contains meta-data and descriptions of resources contained, or to be contained, within a VAD package. Like any XML documents, the target VAD package sticker can be sourced from more than one source file, which can aid maintenance and development.

[¶](https://docs.openlinksw.com/virtuoso/vaddistr/#vadstickerdtd)

##### VAD Sticker DTD

The namespace vad, used below, represents the URI `http://example.com/urn/vad` .

The top level element of a VAD Sticker is <sticker>. It must contain a <caption> element and may contain <dependencies>, <procedures>, <ddls> and <resources> elements.

<!--<<top>>-->

<!ENTITY % vad.source_sticker "INCLUDE">
<!ENTITY % vad.package_sticker "IGNORE">
<!ENTITY % vad.ecm.group_content "(dependencies | procedures | ddls | resources | registry)" >
<![%vad.source_sticker;[
  <!ENTITY % vad.ecm.sticker "(caption, (group | %vad.ecm.group_content;)*)">
  <!ELEMENT group ((group | %vad.ecm.group_content;)*) >
  ]]>
<![%vad.package_sticker;[
  <!ENTITY % vad.ecm.sticker "(caption, %vad.ecm.group_content;)">
  ]]>
<!ELEMENT sticker %vad.ecm.sticker; >
<!ATTLIST sticker
  version     NMTOKEN #REQUIRED
  xml:lang    CDATA   #REQUIRED
  >
    <!--<</top>>-->

    <!--<<caption>>-->

<!ELEMENT caption (name, version)>
<!ELEMENT name ((prop)*)>
<!ATTLIST name
  package NMTOKEN #REQUIRED
  >
<!ELEMENT version ((prop)*)>
<!ATTLIST version
  package NMTOKEN #REQUIRED
  >
<!ELEMENT prop EMPTY>
<!ATTLIST prop
  name NMTOKEN #REQUIRED
  value CDATA #REQUIRED
  >
    <!--<</caption>>-->

The caption contains one name and one version element. These elements have a package attribute for keeping requisites used by VAD procedures. Other prop-s are for keeping admin-readable info, but they will not affect the installer's behavior. Typical names of properties here are Vendor, Copyright, Release+Date, Build, Language, Encoding, but any (even non-unique) names are acceptable.

Sticker's elements for dependencies

<!--<<dependencies>>-->

<!ELEMENT dependencies ((require | allow | conflict)*) >
<!ATTLIST dependencies>
<!ENTITY % vad.ecm.version_list "((version | versions_earlier | versions_later)*)">
<!ELEMENT require (name, %vad.ecm.version_list;) >
<!ELEMENT allow (name, %vad.ecm.version_list;) >
<!ELEMENT conflict (name, %vad.ecm.version_list;) >
<!ATTLIST require
  group NMTOKEN #IMPLIED
  >
<!ELEMENT versions_earlier ((prop)*)>
<!ATTLIST versions_earlier
  package NMTOKEN #REQUIRED
  >
<!ELEMENT versions_later ((prop)*)>
<!ATTLIST versions_later
  package NMTOKEN #REQUIRED
  >
    <!--<</dependencies>>-->

Element dependencies contains an list of packages related to given one. For every version or range of versions of every package, developer may specify whether the given version is required for the package, or allowed but not required, or will cause some sort of troubles.

More precisely, to find information about some particular version of a package, the list of children of dependencies element will be scanned from top to bottom. If the first matching record is in conflict group, not in require or allow, then installation is impossible. From other side, there must be at least one installed package for every require section.

Element require may be labeled with optional group attribute. As an exception from common rule, there must be at least one installed package for every group of require sections with identical name. E.g. If an installation of package B requires either of two interchangeable packages A1 and A2, sticker should contain a pair of nodes in the same group:

<require group="G">
  <name package="A1">...</name>
</require>

...

<require group="G">
  <name package="A2">...</name>
</require>

|   |   |
|---|---|
|![[Note]](https://docs.openlinksw.com/virtuoso/vaddistr/images/note.png)|Note:|
|There are no methods to specify that exactly one package, either A1 or A2, should be installed. It must be done by placing proper conflict descriptions in stickers of A1 and/or A2, but not in the sticker of B.|

Sticker's elements for procedures

<!--<<procedures>>-->

<!ELEMENT procedures ((sql)*)>
<!ATTLIST procedures
  uninstallation (supported | prohibited) #REQUIRED
  >
<![%vad.source_sticker;[
  <!ENTITY % vad.sql.include "include CDATA #IMPLIED">
  ]]>
<![%vad.package_sticker;[
  <!ENTITY % vad.sql.include "">
  ]]>
<!ELEMENT sql (#PCDATA)>
<!ATTLIST sql
  purpose (install-check | pre-install | post-install | uninstall-check | pre-uninstall | post-uninstall) #REQUIRED
  %vad.sql.include;
  >
    <!--<</procedures>>-->

Element procedures contains an list of Virtuoso/PL fragments, and every fragment is tagged by one of four values of the purpose attribute. At every stage of install or uninstall VAD procedure, a whole list of procedures will be scanned from the beginning to the end, and all procedures of appropriate sort will be executed in the same order as they are listed. In source sticker files, include attribute may be used to insert text of some external file instead of having SQL code written inside the element.

Sticker's elements for ddls

<!--<<ddls>>-->

<!ELEMENT ddls ((sql)*)>
<!ATTLIST ddls
  >
    <!--<</ddls>>-->

Element ddls is very similar to procedures and contains an list of Virtuoso/PL fragments to create schemas etc.

Sticker's elements for resources

<!--<<resources>>-->

<!ELEMENT resources ((file | location)*)>
<!ATTLIST resources >
<![%vad.source_sticker;[
  <!ENTITY % vad.file.source_uri "source_uri CDATA #IMPLIED">
  ]]>
<![%vad.package_sticker;[
  <!ENTITY % vad.file.source_uri "">
  ]]>
<!ELEMENT file EMPTY>
<!ATTLIST file
  type (doc | http | dav | code | special) #REQUIRED
  source (http) "http"
  target_uri CDATA #REQUIRED
  makepath (yes | no | abort) "abort"
  overwrite (yes | no | abort | equal | expected) "equal"
  package_id CDATA #IMPLIED
  location IDREF #IMPLIED
  dav_owner CDATA #IMPLIED
  dav_grp CDATA #IMPLIED
  dav_perm CDATA #IMPLIED
  %vad.file.source_uri;
  >
<!ELEMENT location ((prop)*) >
<!ATTLIST location
  id ID #REQUIRED
  default_target_uri CDATA #REQUIRED
  >
    <!--<</resources>>-->

Element resources lists all files to be copied onto target box. For every file, source and target URIs should be specified, and suggested behavior for cases when a directory should be created or file should be overwritten. Target URI may be relative to one of roots: for documentation, web-resources, DAV, SQL code (it's where virtuoso.ini is located) and one of special locations, additionally specified by location elements. (Installer may query administrator to allow changing of locations' roots; in such case, information from location's properties will be shown to the administrator.) By default, the value of _`package_id`_ is a space delimited list of type, location ID (if any) and target URI.

|   |
|---|
|dav_owner - DAV owner for file (used if type="dav", ignored if "filesystem");|
|dav_grp - DAV group for file (used if type="dav", ignored if "filesystem");|
|dav_perm - DAV permissions for file (used if type="dav", ignored if "filesystem").|

**Example 6.10. VAD installable file descriptions**

To install files into DAV:

<file type="dav" source="http" target_uri="yacutia/yacutia_style.css" dav_owner='dav' dav_grp='administrators' dav_perm='111101101N' makepath="yes"/>
<file type="dav" source="http" target_uri="yacutia/yacutia_vdir_style.css"  dav_owner='dav' dav_grp='administrators' dav_perm='111101101N' makepath="yes"/>

To install files into file system:

<file type="http" source="http" target_uri="yacutia/yacutia_style.css" makepath="yes"/>
<file type="http" source="http" target_uri="yacutia/yacutia_vdir_style.css" makepath="yes"/>

  

Sticker's elements for registry

<!--<<registry>>-->

      <!ELEMENT registry ((record)*)>
      <!ATTLIST registry >
      <!ELEMENT record ANY>
      <!ATTLIST record
        key CDATA #REQUIRED
        type (STRING | INTEGER | KEY | URL | XML) #REQUIRED
        overwrite (yes | no | abort | equal | expected) "equal"
        >
    <!--<</registry>>-->

Element registry lists all branches to be defined in the VAD Registry. Every record element contain data of one record. The first children of record element (either a text or an element) will be serialized and stored as a value of _`DB.DBA.VAD_REGISTRY.R_VALUE`_ cell. To prevent errors, it is recommended to keep comments to the data outside the record element: being in the wrong place inside, they may be stored in the registry instead of actually needed data.

**Example 6.11. Sample Stickers**

A package that contains only some commonly useful ("exported") functions, one table for internal purposes, a small sample VSP application, and small set of documentation files.

<?xml version="1.0" encoding="ASCII" ?>
<!DOCTYPE sticker SYSTEM "vad_sticker.dtd">
<sticker version="1.0.010505A" xml:lang="en-UK">
 <!-- Name and version; common data about the package -->

 <caption>
  <name package="rdf_lib">
   <prop name="Title" value="RDF Support Library" />
   <prop name="Developer" value="OpenLink Software" />
   <prop name="Copyright" value="(C) 2020 OpenLink Software" />
   <prop name="Download" value="http://example.com/virtuoso/rdf_lib/download" />
  </name>
  <version package="3.14">
   <prop name="Release+Date" value="2003-05-05" />
   <prop name="Build" value="Release, optimized" />
  </version>
 </caption>
 <!-- This package requires no other packages,
but it conflicts with package virtodp of versions
from 1.00 to 2.17, inclusive -->

 <dependencies>
  <allow>
   <name package="virtodp"></name>
   <versions_earlier package="1.00"></versions_earlier>
  </allow>
  <conflict>
   <name package="virtodp">
    <prop name="Title" value="Virtuoso ODP Sample" />
   </name>
   <versions_earlier package="2.17">
    <prop name="Date" value="2001-01-26" />
    <prop name="Comment"
	  value="An incompatible version of RDF library is included in some old versions of virtodp " />
   </versions_earlier>
  </conflict>
 </dependencies>
 <!-- There are no installation procedures, other than DDLs -->

 <procedures uninstallation="supported"></procedures>
 <!-- There are some procedures, which may be re-applying and (maybe) reverted automatically -->

 <ddls>
  <sql purpose="pre-install">
   "DB"."DBA"."VAD_CREATE_TABLE" ('DB', 'DBA', 'RDF_SCHEDULED_IMPORTS',
      'ID integer,
	   URI varchar,
	   CALLBACK varchar,
	   VERSION varchar,
	   REPORT long varchar,
	   primary key (ID)');
  </sql>
  <sql purpose="post-install">
   "DB"."DBA"."VAD_LOAD_RESOURCE" ('rdf_functions');
  </sql>
 </ddls>
 <!-- Resources include... -->

 <resources>
  <!-- ...documentation, ... -->

  <file type="doc" target_uri="rdf_lib/1.1/intro.dxt" />
  <file type="doc" target_uri="rdf_lib/1.1/interface.dxt" />
  <file type="doc" target_uri="rdf_lib/1.1/implementation.dxt" />
  <file type="doc" target_uri="rdf_lib/1.1/sample_app.dxt" />
  <!-- ...the file of commonly-useful functions, ... -->

  <file package_id="rdf_functions"
    type="code" target_uri="rdf_lib/1.1/rdf_lib.sql" />
  <!-- ...pages of the sample application, named rdf_edit, ... -->

  <file type="http" target_uri="rdf_lib/rdf_edit/default.htm" />
  <file type="http" target_uri="rdf_lib/rdf_edit/browse.vsp" />
  <file type="http" target_uri="rdf_lib/rdf_edit/edit.vsp" />
  <!-- ...a DAV resource with sample RDF data, ... -->

  <file type="dav" target_uri="rdf_lib/sample_odp_structure.rdf" />
  <!-- ...two files of sample application's functions. -->

  <file type="code" target_uri="rdf_lib/1.1/rdf_edit/content_level.sql" />
  <file type="code" target_uri="rdf_lib/1.1/rdf_edit/view_level.sql" />
 </resources>
 <!-- There are no application-specific registry items in this package -->

</sticker>