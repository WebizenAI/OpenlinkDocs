## Data Representation

This section covers how Virtuoso stores RDF triples. The IRI_ID built-in data type is introduced, along with the default table structures used for triple persistency. These details are mostly hidden from users of RDF, thus this section is not necessary reading for typical use of Virtuoso with RDF.


### 16.1.1. IRI_ID Type

The central notion of RDF is the IRI, or URI, which serves as the globally unique label of named nodes. The subject and predicate of a triple are always IRI's and the object may be an IRI or any other XML Schema scalar data type. In any case, an IRI is always distinct from any instance of any other data type.

Virtuoso supports a native IRI_ID data type, internally an unsigned 32 bit or unsigned 64 bit integer value. Small databases can use 32 bit values but if database becomes big then the administrator should execute `DB.DBA.RDF_64BIT_UPGRADE` () procedure that will switch to 64-bit values. This procedure takes time so if it is known in advance that the database will grow to billions of nodes then it could be convenient to upgrade it while it is empty. An IRI_ID is never equal to any instance of any other type.

Thus, the object column of a table storing triples can be declared as ANY and IRI values will be distinguishable without recourse to any extra flag and IRI's will naturally occupy their own contiguous segment in the ANY type collation sequence. Indices can be defined over such columns. An IRI_ID is never automatically cast into any other type nor any other type into IRI_ID.

The functions iri_id_num (in i IRI_ID) and iri_id_from_num (in n INT) convert between signed integers and IRI_ID's. The function isiri_id (in i any) returns nonzero if the argument is of type IRI_ID, zero otherwise.

The syntax for an IRI_ID literal is _#i<NNN>_ or _#ib<NNN>_ , where _<NNN>_ is up to 20 decimal digits. _#i12345_ is equal to _iri_id_from_num (12345)_ and _#ib12345_ is equal to _iri_id_from_num (12345) + min_64bit_bnode_iri_id ()_ .

When received by a SQL client application, the ODBC driver or interactive SQL will bind an IRI_ID to a character buffer, producing the _#i<NNN>_ syntax. When passing IRI_ID's from a client, one can pass an integer and use the iri_id_from_num () function in the statement to convert server side. A SQL client will normally not be exposed to IRI_ID's since the SPARQL implementation returns IRI's in their text form, not as internal id's. These will however be seen if reading the internal tables directly.

|   |   |
|---|---|
|![[Note]](https://docs.openlinksw.com/virtuoso/rdfiriidtype/images/note.png)|Note|
|Nobody, even DBA, should write directly to internal RDF tables, because some data from that tables are cached in a special way and cache is not automatically updated when content of tables has changed.|

_Example_

The following example demonstrates IRI type usage as Virtuoso PL function parameter:

```
SQL>create procedure vs_property_label (in _uri varchar)
  {
    declare res varchar;
    result_names (res);
    for (sparql define input:storage "" select distinct ?graph_rvr_fixed where { graph `iri(?:_uri)` { ?qmv virtrdf:qmGraphRange-rvrFixedValue ?graph_rvr_fixed}})
    do {
      result ("graph_rvr_fixed");
    }
  }
;
Done. -- 0 msec.

SQL>select vs_property_label('http://www.openlinksw.com/schemas/virtrdf#');
res
VARCHAR
_______________________________________________________________________________

http://demo.openlinksw.com/Northwind
http://demo.openlinksw.com/tpch
http://demo.openlinksw.com/tpcd
http://demo.openlinksw.com/bsbm
http://demo.openlinksw.com/tutorial/Northwind
http://demo.openlinksw.com/thalia
http://demo.openlinksw.com/tutorial_view
http://demo.openlinksw.com/ecrm
http://demo.openlinksw.com/sys
http://demo.openlinksw.com/Doc
http://demo.openlinksw.com/informix/stores_demo
http://demo.openlinksw.com/oraclehr
http://demo.openlinksw.com/db2sample
http://demo.openlinksw.com/ingrestut
http://demo.openlinksw.com/sybasepubs2
http://demo.openlinksw.com/MSPetShop#
http://demo.openlinksw.com/oracle#
http://demo.openlinksw.com/progress/isports
http://demo.openlinksw.com/wpl_v
http://demo.openlinksw.com/mw_v
http://demo.openlinksw.com/drupal_v
0

22 Rows. -- 241 msec.

```

### 16.1.2. RDF_BOX Type

While strings, numbers, dates and XML entities are "native" SQL datatypes, RDF literal with non-default type or language have no exact matches among standard SQL types. Virtuoso introduces a special data type called "RDF_BOX" in order to handle that cases. Instance of RDF_BOX consists of data type, language, the content (or beginning characters of a long content) and a possible reference to DB.DBA.RDF_OBJ table if the object is too long to be held in-line in some table or should be outlined for free-text indexing.

Usually applications do not need to access internals of an RDF boxes. This datatype is used in system tables but almost all SPARQL and RDF operations use standard SQL datatypes for arguments and return values.

### 16.1.3. RDF_QUAD and other tables
https://docs.openlinksw.com/virtuoso/rdfquadtables/ 

The main tables of the default RDF storage system are:

create table DB.DBA.RDF_QUAD (
  G IRI_ID,
  S IRI_ID,
  P IRI_ID,
  O any,
  primary key (G,S,P,O) );
create bitmap index RDF_QUAD_OGPS on DB.DBA.RDF_QUAD (O, G, P, S);

Each triple (more correctly, each quad) is represented by one row in RDF_QUAD. The columns represent the graph, subject, predicate and object. The IRI_ID type columns reference RDF_IRI, which translates the internal id to the external name of the IRI. The O column is of type ANY. If the O value is a non-string SQL scalar, such as a number or date or IRI, it is stored in its native binary representation. If it is a "very short" string (20 characters or less), it is also stored "as is". Long strings and RDF literal with non-default type or language are stored as RDF_BOX values. Instance of rdf_box consists of data type, language, the content (or beginning characters of a long content) and a possible reference to RDF_OBJ if the object is too long to be held in-line in this table or should be outlined for free-text indexing.

create table DB.DBA.RDF_PREFIX (
  RP_NAME varchar primary key,
  RP_ID int not null unique );
create table DB.DBA.RDF_IRI (
  RI_NAME varchar primary key,
  RI_ID IRI_ID not null unique );

These two tables store a mapping between internal IRI id's and their external string form. A memory-resident cache contains recently used IRIs to reduce access to this table. Function id_to_iri (in id IRI_ID) returns the IRI by its ID. Function iri_to_id (in iri varchar, in may_create_new_id) returns an IRI_ID for given string; if the string is not used before as an IRI then either NULL is returned or a new ID is allocated, depending on the second argument.

create table DB.DBA.RDF_OBJ (
  RO_ID integer primary key,
  RO_VAL varchar,
  RO_LONG long varchar,
  RO_DIGEST any
)
create index RO_VAL on DB.DBA.RDF_OBJ (RO_VAL)
create index RO_DIGEST on DB.DBA.RDF_OBJ (RO_DIGEST)
;

When an O value of RDF_QUAD is longer than a certain limit or should be free-text indexed, the value is stored in this table. Depending on the length of the value, it goes into the varchar or the long varchar column. The RO_ID is contained in rdf_box object that is stored in the O column. Still, the truncated value of O can be used for determining equality and range matching, even if < and > of closely matching values need to look at the real string in RDF_OBJ. When RO_LONG is used to store very long value, RO_VAL contains a simple checksum of the value, to accelerate search for identical values when the table is populated by new values.

create table DB.DBA.RDF_DATATYPE (
    RDT_IID IRI_ID not null primary key,
    RDT_TWOBYTE integer not null unique,
    RDT_QNAME varchar );

The XML Schema data type of a typed string O represented as 2 bytes in the O varchar value. This table maps this into the broader IRI space where the type URI is given an IRI number.

create table DB.DBA.RDF_LANGUAGE (
    RL_ID varchar not null primary key,
    RL_TWOBYTE integer not null unique );

The varchar representation of a O which is a string with language has a two byte field for language. This table maps the short integer language id to the real language name such as 'en', 'en-US' or 'x-any'.

_Note that unlike datatype names, language names are not URIs._

A short integer value can be used in both RDF_DATATYPE and RDF_LANGUAGE tables for two different purposes. E.g. an integer 257 is for 'unspecified datatype' as well as for 'unspecified language'.


### 16.1.4. Short, Long and SQL Values

When processing an O, the SPARQL implementation may have it in one of three internal formats, called "valmodes". The below cases apply for strings:

The short format is the format where an O is stored in RDF_QUAD.

The long value is similar to short one but an rdf_box object, that consists of six fields:

- short integer id of type referencing RDT_TWOBYTE, 257 if the type is not specified,
    
- the string as inlined in O or as stored in RO_VAL or RO_LONG,
    
- the RO_ID if the string is from RDF_OBJ (otherwise zero),
    
- the short integer id of language referencing RL_TWOBYTE, 257 if the language is not specified,
    
- flag whether the stored string value is complete or it is only the beginning that is inlined in O.
    

The SQL value is the string as a narrow string representing the UTF8 encoding of the value, stripped of data type and language tag.

The SQL form of an IRI is the string. The long and short forms are the IRI_ID referencing RU_IRI_ID of RDF_URL.

For all non-string, non-IRI types, the short, long and SQL values are the same SQL scalar of the appropriate native SQL type. A SQL host variable meant to receive an O should be of the ANY type.

The SPARQL implementation will usually translate results to the SQL format before returning them. Internally, it uses the shortest possible form suited to the operation. For equalities and joining, the short form is always good. For range comparisons, the long form is needed etc. For arithmetic, all three forms will do since the arguments are expected to be numbers which are stored as their binary selves in O, thus the O column unaltered and uncast will do as an argument of arithmetic or numeric comparison with, say, SQL literal constants.

### 16.1.5. Programatically resolving DB.DBA.RDF_QUAD.O to SQL

This section describes how to resolve programatically the internal representation of DB.DBA.RDF_QUAD.O to its SQL value.

When operating over RDF_QUAD table directly, in order to transform all values obtained from column O to the explicit SQL type in a programmatic way, should be used the following hints depending on the case:

- The SQL value can be extracted as
    
    ___ro2sq(O)_
    
    .
    
- The datatype can be extracted as
    
    _DB.DBA.RDF_DATATYPE_OF_OBJ (O)_
    
    if IRI_ID of the type is enough or
    
    ___ro2sq ( DB.DBA.RDF_DATATYPE_OF_OBJ(O))_
    
- The language can be extracted as
    
    _DB.DBA.RDF_LANGUAGE_OF_OBJ (O)_
    
    .
    

It could be helpful to be created an Linked Data View for a custom table with formats rdfdf:default or rdfdf:default-nullable for columns similar to O, and let SPARQL perform the rest.

To track SPARQL, use the following functions:
```
  
select sparql_to_sql_text ('query text here without a leading SPARQL keyword and trailing semicolon')
```

or

```
string_to_file ('filename.sql', sparql_to_sql_text ('query text'), -2);
```
So for example to track the following SPARQL query:
```
SPARQL define input:storage ""
select distinct ?graph_rvr_fixed
from <http://www.openlinksw.com/schemas/virtrdf#>
where { ?qmv virtrdf:qmGraphRange-rvrFixedValue ?graph_rvr_fixed }
```

execute

```
SQL>select sparql_to_sql_text('define input:storage "" select distinct ?graph_rvr_fixed from <http://www.openlinksw.com/schemas/virtrdf#> where { ?qmv virtrdf:qmGraphRange-rvrFixedValue ?graph_rvr_fixed }');
callret
VARCHAR
_______________________________________________________________________________

 SELECT  __ro2sq ("s-1-0_rbc"."graph_rvr_fixed") AS "graph_rvr_fixed" FROM (SELECT DISTINCT __rdf_sqlval_of_obj ( /*retval[*/ "s-1-1-t0"."O" /* graph_
rvr_fixed */ /*]retval*/ ) AS /*tmpl*/ "graph_rvr_fixed"
    FROM DB.DBA.RDF_QUAD AS "s-1-1-t0"
    WHERE /* field equal to URI ref */
        "s-1-1-t0"."G" = __i2idn ( /* UNAME as sqlval */ __box_flags_tweak ( 'http://www.openlinksw.com/schemas/virtrdf#' , 1))
        AND  /* field equal to URI ref */
        "s-1-1-t0"."P" = __i2idn ( /* UNAME as sqlval */ __box_flags_tweak ( 'http://www.openlinksw.com/schemas/virtrdf#qmGraphRange-rvrFixedValue' ,
1))
OPTION (QUIETCAST)) AS "s-1-0_rbc"

1 Rows. -- 321 msec.
```

or

```
SQL>string_to_file ('mytest.sql', sparql_to_sql_text ('define input:storage "" select distinct ?graph_rvr_fixed from <http://www.openlinksw.com/schemas/virtrdf#> where { ?qmv virtrdf:qmGraphRange-rvrFixedValue ?graph_rvr_fixed }'), -2);

As result will be created file with the given name, i.e. mytest.sql and its content should be:

 SELECT  __ro2sq ("s-1-0_rbc"."graph_rvr_fixed") AS "graph_rvr_fixed" FROM (SELECT DISTINCT __rdf_sqlval_of_obj ( /*retval[*/ "s-1-1-t0"."O" /* graph_rvr_fixed */ /*]retval*/ ) AS /*tmpl*/ "graph_rvr_fixed"
    FROM DB.DBA.RDF_QUAD AS "s-1-1-t0"
    WHERE /* field equal to URI ref */
        "s-1-1-t0"."G" = __i2idn ( /* UNAME as sqlval */ __box_flags_tweak ( 'http://www.openlinksw.com/schemas/virtrdf#' , 1))
        AND  /* field equal to URI ref */
        "s-1-1-t0"."P" = __i2idn ( /* UNAME as sqlval */ __box_flags_tweak ( 'http://www.openlinksw.com/schemas/virtrdf#qmGraphRange-rvrFixedValue' , 1))
OPTION (QUIETCAST)) AS "s-1-0_rbc"
```

### 16.1.6. Special Cases and XML Schema Compatibility

We note that since we store numbers as the equivalent SQL binary type, we do not preserve the distinction of byte, boolean etc. These all become integer. If preserving such detail is for some reason important, then storage as a typed string is possible but is not done at present for reasons of compactness and performance.

### 16.1.7. SQL Compiler Support - QUIETCAST option

The type cast behaviors of SQL and SPARQL are different. SQL will generally signal an error when an automatic cast fails. For example, a string can be compared to a date column if the string can be parsed as a date but otherwise the comparison should signal an error. In SPARQL, such situations are supposed to silently fail. Generally, SPARQL is much more relaxed with respect to data types.

These differences will be specially noticed if actual SQL data is processed with SPARQL via some sort of schema mapping translating references to triples into native tables and columns.

Also, even when dealing with the triple-oriented RDF_QUAD table, there are cases of joining between S and O such that the O can be a heterogeneous set of IRI's and other data whereas the S is always an IRI. The non-IRI to IRI comparison should not give cast errors but should silently fail. Also, in order to keep queries simple and easily optimizable, it should not be necessary to introduce extra predicates for testing if the O is n IRI before comparing with the S.

Due to these considerations, Virtuoso introduces a SQL statement option called QUIETCAST. When given in the OPTION clause of a SELECT, it switches to silent fail mode for automatic type casting.

The syntax is as follows:

```
SELECT ...
FROM .... OPTION (QUIETCAST)
```

This option is automatically added by the SPARQL to SQL translator. The scope is the enclosing procedure body.

### 16.1.8. Dynamic Renaming of Local IRI's

There are cases where it is desirable to have IRI's in RDF storage that will change to reflect a change of the host name of the containing store. This is specifically true of DAV resource metadata for local DAV resources. Such IRI's must be stored prefixed with `local:` .

If a user application makes statements with such a URI, then these statements will be returned with local: substituted with a prefix taken from the context as described below.

When returning IRI's from id's, this prefix is replaced by the Host header of the HTTP request and if not running with HTTP, with the DefaultHost from URIQA. This behavior is always in effect.

When converting strings to IRI id's, the `local:` prefix may or may not be introduced depending on ini file and other context factors. If [DynamicLocal](https://docs.openlinksw.com/virtuoso/dbadm/) defined in the [URIQA] section of the Virtuoso INI file is on and the host part of the IRI matches the Host header of the HTTP request in context or the DefaultHost if outside of HTTP context, then this is replaced with local: before looking up the IRI ID. Even if DynamicLocal is not on and the `local:` prefix occurs in the IRI string being translated to id, the translating the IRI_ID back to the IRI name will depend on the context as described above.

The effects of DynamicLocal = 1 can be very confusing since many names can refer to the exact same thing. For example, if the DefaultHost is dbpedia.org, `iri_to_id ('http://dbpedia.org/resource/Paris') = iri_to_id ('local:///resource/Paris)` is true and so is `'http://dbpedia.org/resource/Paris' = id_to_iri (iri_to_id ('local://resource/Paris'))` These hold in a SQL client context, i.e. also when connected through RDF frameworks like Jena or Sesame. When running a SPARQL protocol request, the Host: header influences the behavior, likewise when using web interactive SQL in Conductor. Also be careful when loading RDF files that may have URI's corresponding to the local host name.