
### 4.2.1. Mac OS X

[¶](https://docs.openlinksw.com/virtuoso/macosxsamples/#odbctestmac)

#### ODBCTEST:

This is a simple 'C' based and ODBC compliant Interactive SQL processor.

1. Open a Terminal session, and start ODBCTEST by executing the following command:
    
    /Library/iodbc/bin/odbctest
    
2. At the SQL command prompt enter "?" for a list of ODBC DSNs on your machine or enter a valid ODBC Connect String. If you have a DSN named "Marketing" you would enter:
    
    DSN=Marketing;UID=username;PWD=password
    
    Note: If there is no password, you must include a semicolon at the end:
    
    DSN=Marketing;UID=sa;PWD=;
    
3. Any valid SQL or ODBC command may be executed through this interface. The following example shows a connection to Microsoft SQL Server 2000, making a simple query against the sample Northwind database:
    
    [localhost:~] openlink% /Library/iodbc/bin/odbctest
    iODBC Demonstration program
    This program shows an interactive SQL processor
    
    Enter ODBC connect string (? shows list, or DSN=...): DSN=user_tthib_sql2k
    
    SQL>select au_lname, au_fname, state from authors where au_id < '333-33-3333'
    au_lname                                |au_fname            |state
    ----------------------------------------+--------------------+-----
    White                                   |Johnson             |CA
    Green                                   |Marjorie            |CA
    Carson                                  |Cheryl              |CA
    O'Leary                                 |Michael             |CA
    Straight                                |Dean                |CA
     5 row(s) fetched.
    
    SQL>quit
    Again (y/n) ? n
    
    Have a nice day.
    [localhost:~] openlink%

https://docs.openlinksw.com/virtuoso/macosxsamples/

### 4.2.2. Windows 95/98/NT/2000

[¶](https://docs.openlinksw.com/virtuoso/winodbcsamples/#cppdemo32)

#### C++ Demo

1. Go to the Virtuoso "Start Menu" item, then click on the "C++ Demo 32 Bit" menu item.
    
    **Figure 4.1. C++ Demo**
    
    ![C++ Demo](https://docs.openlinksw.com/virtuoso/winodbcsamples/images/sampl001.gif)
    
      
    
2. Follow the Environment->Open Connection menu path. Selecting the "Open Connection" menu item results in the ODBC Driver Manager presenting you with a list of ODBC DSNs on your machine as depicted by the screen capture below:
    
    **Figure 4.2. C++ Demo**
    
    ![C++ Demo](https://docs.openlinksw.com/virtuoso/winodbcsamples/images/sampl004.gif)
    
      
    
3. Select the ODBC DSN that you want to be connecting to, in this case "Local Virtuoso Demo" has been chosen since this will connect you to a sample Virtuoso database that has been populated with data.
    
4. You are then presented with a Login Dialog by the Virtuoso driver for ODBC, enter a valid user name and password (default being user: demo and password: demo) into the appropriate fields.
    
    **Figure 4.3. C++ Demo**
    
    ![C++ Demo](https://docs.openlinksw.com/virtuoso/winodbcsamples/images/sampl003.gif)
    
      
    
5. At this point you will be connected to the Virtuoso demonstration database, you can now use the SQL-->Execute SQL menu path to open up the Interactive SQL input dialog. Enter a valid SQL statement (see example in screen shot) and then click on the "OK" button.
    
    **Figure 4.4. C++ Demo**
    
    ![C++ Demo](https://docs.openlinksw.com/virtuoso/winodbcsamples/images/sampl006.gif)
    
      
    
6. You will be presented with the results of your query.
    
    **Figure 4.5. C++ Demo**
    
    ![C++ Demo](https://docs.openlinksw.com/virtuoso/winodbcsamples/images/sampl007.gif)
    
      
    
7. You exit this demo by following the Environment-->Close Connection menu path.
    

[¶](https://docs.openlinksw.com/virtuoso/winodbcsamples/#odbcbench32)

#### ODBC Bench Test 32

1. Go to the Virtuoso "Start Menu" item, then click on the "ODBC Bench Test 32 Bit" menu item. You will be presented with the "Bench Test" interface.
    
    **Figure 4.6. ODBC Bench**
    
    ![ODBC Bench](https://docs.openlinksw.com/virtuoso/winodbcsamples/images/sampl008.gif)
    
      
    
2. Follow the File-Connect menu path which initializes the ODBC Driver Manager which in turn presents you with a list of ODBC DSN's installed on your machine. Select the DSN that you want to benchmark, remember that by benchmarking a DSN you are benchmarking the ODBC Driver that serves the DSN in question and the backend database engine that serves the ODBC Driver. Choose the "Local Virtuoso Demo" DSN if you want to benchmark Virtuoso.
    
    **Figure 4.7. ODBC Bench**
    
    ![ODBC Bench](https://docs.openlinksw.com/virtuoso/winodbcsamples/images/sampl009.gif)
    
      
    
3. You will then be presented with a Login Dialog by the Virtuoso driver for ODBC, enter a valid user name and password (default being user: demo and password: demo for the Demo database) into the appropriate fields.
    
    **Figure 4.8. ODBC Bench**
    
    ![ODBC Bench](https://docs.openlinksw.com/virtuoso/winodbcsamples/images/sampl010.gif)
    
      
    
4. Now follow the Bench-->Load Tables menu path and you will be presented with a dialog that enables you to configure key elements of your benchmark. Click the "Execute" button to commence the process of setting up your database for the benchmark tests.
    
    **Figure 4.9. ODBC Bench**
    
    ![ODBC Bench](https://docs.openlinksw.com/virtuoso/winodbcsamples/images/sampl011.gif)
    
      
    
5. As the process of loading data occurs, all the way up to completion, the benchmark program will provide status information into the benchmark output pane as shown below:
    
    **Figure 4.10. ODBC Bench**
    
    ![ODBC Bench](https://docs.openlinksw.com/virtuoso/winodbcsamples/images/sampl012.gif)
    
      
    
6. Now that all the benchmark data has been loaded into your database, follow the Bench-->Run Benchmark menu path and then configure your actual benchmark session parameters:
    
    These benchmark parameters fall into 3 categories, Timing Options, SQL Options, and Execution Options.
    
    **Figure 4.11. ODBC Bench**
    
    ![ODBC Bench](https://docs.openlinksw.com/virtuoso/winodbcsamples/images/sampl013.gif)
    
      
    
    _Timing Options:_ These setting allow you to configure the duration related aspects of this benchmark program
    
    Minutes - this is the duration of each benchmark run
    
    Runs - this controls how many iterations of the benchmarks you actually run (the default is one benchmark iteration with a duration of 5 minutes)
    
    _SQL Options:_ These setting allow you to configure how your benchmark's SQL instructions are actually handled.
    
    ExecDirect with SQL Text - this means that no form of repetitive SQL execution optimization is being applied (SQL statements are prepared and executed repetitively)
    
    Prepare/Execute Bound Params - this means that the Parameter Binding SQL execution optimization is being applied (SQL is prepared once but executed many times without the overhead of re-preparing statements prior to execution)
    
    Use Stored Procedures - this means that the Stored Procedure SQL optimization is being applied (benchmark instructions are stored within database being benchmarked)
    
    _Execution Options:_ These setting allow you to configure the tone of your benchmark, for instance it could have Transaction scoping and a mix of record retrieval queries, or it could simply be input and update intensive with a minimal amount of record retrieval queries (the case when the 100 row query checkbox is unchecked a typical OLTP scenario)
    
    Asynchronous - execute the benchmark instructions asynchronously
    
    Use Transactions - make the benchmark use transaction control (instructions are scoped to transaction blocks)
    
    Do 100 row Query - perform a simulation of a 100 record retrieval as part of the benchmark activity.
    

1. Click on the "Run All" button if you would like all the different benchmark type combinations to be performed.
    
2. When benchmark run complete benchmark data is written to the benchmark program's output pane.
    
    **Figure 4.12. ODBC Bench**
    
    ![ODBC Bench](https://docs.openlinksw.com/virtuoso/winodbcsamples/images/sampl014.gif)
    
      
    
    The key pieces of benchmark data that you need to look out for are:
    
    _Total Transactions:_ total number of transactions completed during the benchmark run
    
    _Transactions Per Second_ number of transaction completed per second for the benchmark run
    
    Information from this benchmark is automatically written to an Excel format CSV (the file odbcbnch.csv) which makes it easy for you to graph and pivot data collated from several benchmark runs. A later version of this demo will actually write the benchmark data into an ODBC DSN that you provide thereby offering even more flexibility and accessibility to benchmark data.

### 4.2.3. Linux & UNIX

[¶](https://docs.openlinksw.com/virtuoso/unixodbcsamp/#odbctestnix)

#### ODBCTEST:

This is a simple 'C' based and ODBC compliant Interactive SQL processor.

1. Run the script virtuoso-enterprise.sh to set up your environment:
    
    . virtuoso-enterprise.sh
    
2. Start ODBCTEST by executing the following command:
    
    odbctest
    
3. At the SQL command prompt enter "?" for a list of ODBC DSNs on your machine or enter a valid ODBC Connect String. If you have a DSN named "Marketing" you would enter:
    
    DSN=Marketing;UID=username;PWD=password
    
    Note: If there is no password, you must include a semicolon at the end:
    
    DSN=Marketing;UID=sa;PWD=;
    
4. Any valid SQL or ODBC command may be executed through this interface. The following example shows a connection to Microsoft SQL Server 2000, making a simple query against the sample Northwind database:
    
    [localhost:~] openlink% odbctest
    iODBC Demonstration program
    This program shows an interactive SQL processor
    
    Enter ODBC connect string (? shows list, or DSN=...): DSN=test_sql2k
    
    SQL>select au_lname, au_fname, state from authors where au_id < '333-33-3333'
    au_lname                                |au_fname            |state
    ----------------------------------------+--------------------+-----
    White                                   |Johnson             |CA
    Green                                   |Marjorie            |CA
    Carson                                  |Cheryl              |CA
    O'Leary                                 |Michael             |CA
    Straight                                |Dean                |CA
     5 row(s) fetched.
    
    SQL>quit
    Again (y/n) ? n
    
    Have a nice day.
    [localhost:~] openlink%


### 4.2.4. MS DTC ODBC Sample Application

The MS DTC demo is located in the

<VIRTUOSO_INSTALLATION_DIRECTORY>\samples\odbc\MSDTCdemo1

folder. This demo shows usage of distributed transactions driven by MS DTC through the ODBC API.

[¶](https://docs.openlinksw.com/virtuoso/msdtcsample/#msdtcdemo1setup)

#### Setup

The sample works with two instances of Virtuoso server. The running MS DTC service is needed. The servers must be started with MS DTC support (see Virtuoso documentation).

First of all, edit the virt.odbc file. By default this file contains two connection strings of local Virtuoso servers running on port 1111 and port 1112, Each line begins with connection string to appropriate Virtuoso server. Initially this file contains the following lines:

1111 dba dba 00.sql
1112 dba dba 01.sql 
	             

where 1111, 1112 are ports of two Virtuoso servers. "dba dba" - user and password.

[¶](https://docs.openlinksw.com/virtuoso/msdtcsample/#msdtcdemo1init)

#### Initialization

Start

 mtstest.exe +load 

in the

<VIRTUOSO_INSTALLATION_DIRECTORY>\samples\odbc\MSDTCdemo1

folder. This must check whether all needed servers are running, create and initialize tables, procedures, etc.

[¶](https://docs.openlinksw.com/virtuoso/msdtcsample/#msdtcdemo1start)

#### Test

Run the command in the demo's working directory:

 
mtstest.exe   +exec N
mtstest.exe   +exec 0
	         

where N - is a number of test iterations. The second command checks logical consistency of the tables.

[¶](https://docs.openlinksw.com/virtuoso/msdtcsample/#msdtcdemo1description)

#### Description

The demo source is

start.c

file in the

<VIRTUOSO_INSTALLATION_DIRECTORY>\samples\odbc\MSDTCdemo1

directory. Several highlights of the most significant parts of code are presented below:

  ITransactionDispenser *disp;
  ITransaction *transaction;

  ...
  HRESULT hr =
      DtcGetTransactionManagerC (0, 0, &IID_ITransactionDispenser, 0, 0, 0,
      &, disp);
	         

The code above creates Dispenser object which represents the local instance of MS DTC. If MS DTC is not available

DtcGetTransactionManagerC

fails. The Dispenser is needed to create distributed transaction objects later.

Begin new distributed transaction:

disp->lpVtbl->BeginTransaction (disp, 0, ISOLATIONLEVEL_ISOLATED,
      0, 0, &transaction);	             
	         

Enlist connection in the transaction:

SQLSetConnectOption (hdbc, SQL_COPT_SS_ENLIST_IN_DTC,
      (DWORD) transaction);
	         

And, finally, commit the transaction:

transaction->lpVtbl->Commit (tran, 0, 0, 0);


### 4.2.5. MS DTC OLE DB Sample Application

The MS DTC OLE DB demo is located in the

<VIRTUOSO_INSTALLATION_DIRECTORY>\samples\odbc\MSDTCdemo2

folder. This demo shows usage of distributed transactions driven by MS DTC through OLE DB.

[¶](https://docs.openlinksw.com/virtuoso/msdtcsample2/#msdtcdemo2setup)

#### Setup

The sample works with two instances of Virtuoso server. Running MS DTC service is needed. The servers must be started with MS DTC support (see Virtuoso documentation).

The test needs two Virtuoso server instances running on ports 1111 and 1112

[¶](https://docs.openlinksw.com/virtuoso/msdtcsample2/#msdtcdemostart)

#### Run

Run the command in the demo's working directory:

 
voledbtest.exe
	         

[¶](https://docs.openlinksw.com/virtuoso/msdtcsample2/#msdtcdemodescription)

#### Description

The demo source is

voledbtest.cs

file in the

<VIRTUOSO_INSTALLATION_DIRECTORY>\samples\odbc\MSDTCdemo

directory. Several highlights of the most significant parts of code are presented below:

[TransactionAttribute(TransactionOption.Required)]	             
  	         

It is significant to set this attribute of class to enable automatic transaction initialization.

Create connections to appropriate servers:

string strConn = "Provider=VIRTOLEDB;Data Source=" + dsn1 
    + ";User Id=dba;Password=dba;Initial Catalog=Demo;Prompt=NoPrompt;";
string strConn2 = "Provider=VIRTOLEDB;Data Source=" + dsn2 + 
    ";User Id=dba;Password=dba;Initial Catalog=Demo;Prompt=NoPrompt;";
obj_conn = new OleDbConnection(strConn);
obj_conn2 = new OleDbConnection(strConn2);
	         

And, finally, execute the SQL code in the context of distributed transaction:

OleDbCommand sqlc = new OleDbCommand ("ODBC_BENCHMARK(" + idx + ",1,1,12.00,\'noone\')");
sqlc.Connection = obj_conn;
sqlc.ExecuteNonQuery();
sqlc = new OleDbCommand ("ODBC_BENCHMARK(" + idx + ",1,1,-12.00,\'noone\')");
sqlc.Connection = obj_conn2;
sqlc.ExecuteNonQuery();