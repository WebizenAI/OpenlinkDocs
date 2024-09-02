https://docs.openlinksw.com/virtuoso/ch-sampleapps/
# Chapter 4. Sample ODBC & JDBC Applications

**Abstract**

This chapter applies exclusively to the various commercial releases of Virtuoso. If you are working with the open source version, please refer to the instructions on the web site where you obtained it.

The OpenLink Virtuoso Installation provides sample applications to help you get quick and easy results from you installation. This chapter explains how to use these applications.

**Table of Contents**

4.1. [Binary & Source File Locations](https://docs.openlinksw.com/virtuoso/binsrcloc/)

4.1.1. [ODBC Demonstration Applications](https://docs.openlinksw.com/virtuoso/odbcdemos/)

4.1.2. [JDBC Demonstration Applications](https://docs.openlinksw.com/virtuoso/sampjdbcdemos/)

4.2. [Sample ODBC Applications](https://docs.openlinksw.com/virtuoso/sampleodbcapps/)

4.2.1. [Mac OS X](https://docs.openlinksw.com/virtuoso/macosxsamples/)

4.2.2. [Windows 95/98/NT/2000](https://docs.openlinksw.com/virtuoso/winodbcsamples/)

4.2.3. [Linux & UNIX](https://docs.openlinksw.com/virtuoso/unixodbcsamp/)

4.2.4. [MS DTC ODBC Sample Application](https://docs.openlinksw.com/virtuoso/msdtcsample/)

4.2.5. [MS DTC OLE DB Sample Application](https://docs.openlinksw.com/virtuoso/msdtcsample2/)

4.3. [Sample JDBC Applications & Applets](https://docs.openlinksw.com/virtuoso/jdbcdemos/)

4.3.1. [JDBCDemo Java Application](https://docs.openlinksw.com/virtuoso/jdbcdemo/)

4.3.2. [ScrollDemo2 Java Application](https://docs.openlinksw.com/virtuoso/scrolldemo2/)

4.3.3. [ScrollDemo2 Java Applet](https://docs.openlinksw.com/virtuoso/scrolldemo2applet/)

4.3.4. [JBench Application](https://docs.openlinksw.com/virtuoso/jbenchapplication/)

4.3.5. [JTA Demo Application](https://docs.openlinksw.com/virtuoso/jtademo/)

A number of sample applications are bundled with your Virtuoso installation for the following purposes:

|   |
|---|
|To simplifying the process of getting Virtuoso up and running|
|To accelerate the support case creation and resolution process|
|To demonstrate Virtuoso's unique product features highlighting the benefits it brings to your organization|
|To demonstrate application programming techniques that can used to aid and assist your ODBC and JDBC programmers|

Virtuoso's services are consumed primarily via ODBC and JDBC applications (OLE-DB applications connect to Virtuoso via ODBC Data Providers for OLE-DB), thus separate ODBC & JDBC sample applications (including source code) have been packaged and integrated into the Virtuoso installer. The current list of sample applications include:

- **C++ Demo.**  an ODBC based Interactive SQL processor written in C++.
    
- **ODBC Bench Test.**  a 32 Bit C++ program based on the industry standard TPC-A benchmark (we will be extending this program to include the TPC-C and TPC-D benchmarks also). This program helps you compare the performance of Virtuoso against other backend database engines as well as compare the performance of various ODBC Drivers connecting to any ODBC compliant backend database.
    
- **ODBCTEST.**  ODBC based Interactive SQL processor written in 'C' for Linux & UNIX
    

- **JDBCDemo.**  a JDBC sample application that demonstrates Virtuoso's SQL query.
    
- **ScrollDemo2.**  a JDBC 2.0 sample application that demonstrates Virtuoso's support of Scrollable Cursors and its ability to perform scrollable cursor operations across heterogeneous databases.
    
- **JBench.**  a Java and JDBC based adaptations of the industry standard TPC-A and TPC-C benchmarks. This program helps you compare the performance of Virtuoso against other backend database engines, it also helps you to compare the performance of various JDBC Drivers connecting to any JDBC compliant backend database.
    
- **JTADemo.**  a sample based on the TPC-A benchmark as well but implemented as a J2EE application which shows the use of XA distributed transactions as defined in JDBC 3.0 and JTA 1.0 specifications.

### 4.1.1. ODBC Demonstration Applications

Windows 95/98/NT/2000, Linux & UNIX:

The binary executables of these sample applications reside under the following directory structure:

<VIRTUOSO_INSTALLATION_DIRECTORY>\samples\odbc

The source code of some of these sample applications, when available, reside under the following directory structure, for example:

<VIRTUOSO_INSTALLATION_DIRECTORY>\samples\odbc\cppdemo


### 4.1.2. JDBC Demonstration Applications

Windows 95/98/NT/2000, Linux & UNIX:

The binary executables (Java class files), and sources for these sample applications reside under the following directory structure:

<VIRTUOSO_INSTALLATION_DIRECTORY>\samples\jdbc\<JDK_Version>\<Demo_name>