[[PageOutline]]


 *** THIS PAGE IN-PROGRESS ****

= Overview =

To support multiple databases, the spacewalk schema source is divided into ''common'', ''oracle'' specific and ''postgres'' specific as of 0.6.
In general, most of the tables, views and data (inserts) go into ''common''.  The triggers, stored procedures, packages, classes and types
will go in the DB specific directories.  The build uses [https://fedorahosted.org/releases/c/h/chameleon/ chameleon] and ''blend'' to convert the common parts of the schema and blend them
together with the specific parts into an installable file.

= How To =

=== Adding An Object ===

==== Tables ====

If the table is common for both oracle and postgres (and they almost always are), you want to:

 * cd schema/spacewalk/common/tables

Otherwise

 * cd schema/spacewalk(oracle|postgres)/tables

Then
 * Add your ''tablename''.sql file containing the DDL to create your table along with comments, constraints, indexes and sequences.
 * Update [https://fedorahosted.org/spacewalk/wiki/DatabaseGuide#Dependencies dependencies] as needed
 * If you need to define [https://fedorahosted.org/spacewalk/wiki/DatabaseGuide#Triggers triggers] for your table
 * If you need to prime your table with [https://fedorahosted.org/spacewalk/wiki/DatabaseGuide#Data data] at install
 * [https://fedorahosted.org/spacewalk/wiki/DatabaseGuide#BuildingInstalling Build] the schema(s) and verify.

To verify ''common'' table in oracle:

  cd schema/spacewalk/oracle/tables/common/''tablename''.sql  <--- transformed by chameleon, output here

To verify in ''common'' table  postgres:

  cd schema/spacewalk/postgres/tables/common/''tablename''.sql  <--- transformed by chameleon, output here

Notes:
 * No TABs please!
 * If you added in a database specific directory, don't forget to replicate these steps in __all__ for all other databases.
 * Do not create ''tablename''_trigger files in the /tables directory.  They now belong in /triggers
 * Do not create ''tablename''_data files in the /tables directory.  They now belong in /data
 * Do not define columns as NOT NULL using named ''column_name''_nn constraints.  Simply use the NOT NULL keyword.
 * To be ''common'', your table must be defined using the ''common'' DDL grammar and need to be loaded in all databases.

==== Data ====

If the table is common for both oracle and postgres (and they almost always are) and the data is loaded using simple insert
statements, you want to:

 * cd schema/spacewalk/common/data

Otherwise

 * cd schema/spacewalk(oracle|postgres)/data

Then
 * Add your ''tablename''.sql file containing the insert(s) SQL (named for table in which the data is inserted)
 * Update [https://fedorahosted.org/spacewalk/wiki/DatabaseGuide#Dependencies dependencies] as needed
 * [https://fedorahosted.org/spacewalk/wiki/DatabaseGuide#BuildingInstalling Build] the schema(s) and verify.

To verify ''common'' data insert in oracle:

  cd schema/spacewalk/oracle/data/common/''tablename''.sql  <--- transformed by chameleon, output here

To verify in ''common'' data insert  postgres:

  cd schema/spacewalk/postgres/data/common/''tablename''.sql  <--- transformed by chameleon, output here

Notes:
 * No TABs please!
 * If you added in a database specific directory, don't forget to replicate these steps in __all__ for all other databases.
 * Insert (select ...) cannot be handled by chameleon.
 * May contain sysdate, sequence (nextval) references, etc ..

==== Views ====

If the view is common for both oracle and postgres (and they almost always are), you want to:

 * cd schema/spacewalk/common/views

Otherwise

 * cd schema/spacewalk(oracle|postgres)/views
 
Then

 * Add your ''viewname''.sql file containing the DDL/SQL to create/replace your view.
 * Update [https://fedorahosted.org/spacewalk/wiki/DatabaseGuide#Dependencies dependencies] as needed
 * Test, no build required

Notes:
 * No TABs please!
 * If you added in a database specific directory, don't forget to __port__ and replicate these steps in __all__ for all other databases.
 * To be common, the view DDL/SQL and query must be compatible for all databases.
 * Common views are simply copied to (oracle|postgres)/views/common.

==== Classes & Types ====

These objects are always database specific and need to be created in database specific directories.

 * cd schema/spacewalk/oracle/class
 * Add your ''classname''.sql or ''typename''.sql file defining the class/type
 * Update [https://fedorahosted.org/spacewalk/wiki/DatabaseGuide#Dependencies dependencies] as needed
 * cd schema/spacewalk/postgres/class
 * Add your __ported__ ''classname''.sql or ''typename''.sql file defining the class/type
 * Update [https://fedorahosted.org/spacewalk/wiki/DatabaseGuide#Dependencies dependencies] as needed
 * Test, no build required

Notes:
 * No TABs please!

==== Stored Procedures & Functions ====

These objects are always database specific and need to be created in database specific directories.

 * cd schema/spacewalk/oracle/procs
 * Add your ''procedurename''.sql or ''functionname''.sql file in the /procs directory
 * Update [https://fedorahosted.org/spacewalk/wiki/DatabaseGuide#Dependencies dependencies] as needed
 * cd schema/spacewalk/postgres/procs
 * Add your __ported__ ''procedurename''.sql or ''functionname''.sql file defining the proc/function
 * Update [https://fedorahosted.org/spacewalk/wiki/DatabaseGuide#Dependencies dependencies] as needed
 * Test, no build required

Notes:
 * No TABs please!

==== Packages ====

These objects are always database specific and need to be created in database specific directories.

 * cd schema/spacewalk/oracle/packages
 * Add your ''packagename''.pks and ''packagename''.pkb or files defining the package header and body.
 * Update [https://fedorahosted.org/spacewalk/wiki/DatabaseGuide#Dependencies dependencies] as needed
 * cd schema/spacewalk/postgres/packages
 * Add your __ported__ ''packagename''.pks and ''packagename''.pkb or files defining the package header and body.
 * Update [https://fedorahosted.org/spacewalk/wiki/DatabaseGuide#Dependencies dependencies] as needed
 * Test, no build required

Notes:
 * No TABs please!
 * .pks files define package header
 * .pkb files define package body
 * .pkb (package body) files should __never__ be listed as dependency of other objects.
 * Packages are simulated using ''schemas'' in postgres

==== Triggers ====

These objects are always database specific and need to be created in database specific directories.

 * cd schema/spacewalk/oracle/triggers
 * Add your ''tablename''.sql file defining the triggers for a given table (named for table not trigger)
 * Update [https://fedorahosted.org/spacewalk/wiki/DatabaseGuide#Dependencies dependencies] as needed
 * cd schema/spacewalk/postgres/packages
 * Add your __ported__ ''tablename''.sql file defining the triggers for a given table (named for table not trigger).
 * Update [https://fedorahosted.org/spacewalk/wiki/DatabaseGuide#Dependencies dependencies] as needed
 * Test, no build required

Notes:
 * No TABs please!
 * Triggers __always__ loaded after tables, views, procedures and packages so not need to add dependencies.

==== Synonyms ====

These objects are oracle specific and need to be created in database specific directories.

 * cd schema/spacewalk/oracle/synonyms
 * Add your ''synonymname''.sql file defining the synonym.
 * Update [https://fedorahosted.org/spacewalk/wiki/DatabaseGuide#Dependencies dependencies] as needed
 * Test, no build required

Notes:
 * No TABs please!
 * Synonyms are always installed last and not referenced by other objects in the schema so no dependencies should be required.

=== Update An Object ===

TBD

=== Dependencies ===

Dependencies between database objects are defined in .deps files.  The dependency (.deps) files resemble GNU Make
dependency files - but they are not.  These files are processed by ''blend'' and conveniently have a similar syntax but there are
several differences:
 * Spaces not Tabs
 * Namespaces used to handle duplicate file names that are naturally scoped by directory.
 * Analysed for unused rules and unfound references.
 * All (.deps) files are processed not just those listed.
 * Named ''namespace''.deps instead of Makefile.deps to avoid confusion.  Eg: tables.deps, views.deps ...

Blend and (.deps) files have a concept of ''namespaces''.  Each ''root'' directory listed on the command line for
blend to process is considered a ''namespace'' which recursively includes all files and sub-directories.  Each .deps file
can list a ''path'' which defines the order in which unqualified references are resolved with (.) dot being the
current ''namespace''.  Support for both duplicate file names (in difference directories) and unqualified references
at the same time provides for natural file names and keeps the .deps files clean and readable.

For example:
  {{{
    path .
  }}}
Or
  {{{
  path . tables
  }}}
To resolve references first in the current ''namespace'' then within the tables ''namespace''.

For example, this (.deps) file contained within the ''tables'' namespace:
  {{{
    path . views
    ...
    tableA :: viewB
  }}}
Where 'viewB' would first be resolved as:
 1. tables/viewB
 1. views/viewB

This is compact and safe since names must be unique between tables and views.

Namespaces provides for deterministic resolution of unqualified references.  Optionally, references
may be qualified by ''namespace'' such as ''tables''/rhnChannel where ''tables'' is the namespace and rhnChannel is
the object.  References may be further qualified by file extension such as rhn_user.pks 

For example, this (.deps) file contained within the ''views'' namespace:
  {{{
    path . packages
    ...
    viewA :: procs/procA
  }}}

Would always resolve to a procedure named 'procA' because it has been qualified.

The object (flie) ordering is deterministic and sorted as follows:

 1. By directory listed to blend
 2. Alphabetically as listed in the directory.
 3. As defined by dependency.

Directory order (defined by DIRS in db Makefile):
    1. class
    1. types
    1. tables
    1. procs 
    1. packages 
    1. views 
    1. triggers
    1. data
    1. synonyms

Triggers, data and synonyms which are never referenced as dependencies really don't need (.deps) files
because the directory ordering is enough.

=== Building & Installing ===

Files found in schema/spacewalk/common/
 * tables
 * data

Are transformed from common -> specific using ''chameleon'' during the build and written into
the schema/spacewalk/<db>/*/common directories.  Then ''blend'' aggregates and
orders all of the (.sql, .pks, .pkb) files and generates a main.sql that may be used to install the schema.
  {{{
  cd schema/spacewalk/oracle
  make
  }}}
Or, to replace tablespace in Oracle Express:
  {{{
  cd schema/spacewalk/oracle
  make devel
  }}}
Or, to replace tablespace in Oracle Enterprise:
  {{{
  cd schema/spacewalk/oracle
  make devel TBS=data_tbs
  }}}

The ''devel'' target creates a devel.sql file that has the {{{[[tbs]]}}} macro replaced
with the appropriate tablespace name.

Then, for oracle using ''sqlplus'' load the ''devel'' schema.
  {{{
  SQL> @devel
  }}}

RPMs for '''chameleon''' can be found [https://fedorahosted.org/releases/c/h/chameleon/ here] until released into Fedora extras.

= Directory Structure =

== Common ==

 === /schema/spacewalk ===
Contains DDL files.

=== /schema/spacewalk/common ===
Common DDL/SQL (schema).

=== /schema/spacewalk/common/tables ===
Contains (.sql) files with DDL for ''common'' tables.  File names match the name of the table being created and may include
   * Table definition
   * Table / Column comments
   * Constraints
   * Indexes
   * sequences

=== /schema/spacewalk/common/views ===
Contains (.sql) files with DDL for ''common'' views.  File names match the name of view begin created and contain the DDL for creating or replacing the view.

=== /schema/spacewalk/common/data ===
Contains (.sql) files with SQL for inserting ''primer'' data into ''common'' tables.  File names match the name of table into which the data is inserted/updated.

== Oracle ^only^ ==

=== /schema/spacewalk/oracle/class ===
Contains '''oracle''' specific user defined types  (such as EVR_T) DDL files.  File names match the database type begin created.

=== /schema/spacewalk/oracle/types ===
Contains '''oracle''' specific user defined types.  File names match the database type begin created.

=== /schema/spacewalk/oracle/tables ===
Contains (.sql) files with DDL for '''oracle''' only tables.  File names match the name of the table being created and may include:
   * Table definition
   * Table / Column comments
   * Constraints
   * Indexes
   * sequences

=== /schema/spacewalk/oracle/tables/common ===
Populated at build ^''read-only''^

=== /schema/spacewalk/oracle/views ===
Contains (.sql) files with DDL for '''oracle''' views.  File names match the name of view begin created and contain the DDL for creating or replacing the view.

=== /schema/spacewalk/oracle/views/common ===
Populated at build ^''read-only''^

=== /schema/spacewalk/oracle/data ===
Contains (.sql) files with SQL for inserting ''primer'' data into '''oracle''' tables.  File names match the name of table into which the data is inserted/updated.

=== /schema/spacewalk/oracle/data/common ===
Populated at build ^''read-only''^

=== /schema/spacewalk/oracle/triggers ===
Contains (.sql) files with DDL for creating/replacing '''oracle''' triggers.  File names match the name of table on which the trigger is created/replaced.

=== /schema/spacewalk/oracle/procs ===
Contains (.sql) files with DDL for creating/replacing '''oracle''' stored procedures/functions.  File names match the name of procedure/function begin created.

=== /schema/spacewalk/oracle/packages ===
Contains (.pks|.pkb) files with DDL for creating/replacing '''oracle''' packages.  File names match the name of package begin created.
  .pks::
    Package Declaration (header)
  .pkb::
    Package Definition (body)

=== /schema/spacewalk/oracle/synonyms ===
Contains (.sql) files with DDL for creating/replacing '''oracle''' synonyms.  File names match the name of synonym begin created.

== PostgreSQL ^only^ ==

=== /schema/spacewalk/postgres/class ===
Contains '''postgres''' specific user defined types  (such as EVR_T) DDL files.  File names match the database type begin created.

=== /schema/spacewalk/postgres/types ===
Contains '''postgres''' specific user defined types.  File names match the database type begin created.

=== /schema/spacewalk/postgres/tables ===
Contains (.sql) files with DDL for '''postgres''' only tables.  File names match the name of the table being created and may include:
   * Table definition
   * Table / Column comments
   * Constraints
   * Indexes
   * sequences

=== /schema/spacewalk/postgres/tables/common ===
Populated at build ^''read-only''^

=== /schema/spacewalk/postgres/views ===
Contains (.sql) files with DDL for '''postgres''' views.  File names match the name of view begin created and contain the DDL for creating or replacing the view.

=== /schema/spacewalk/postgres/views/common ===
Populated at build ^''read-only''^

=== /schema/spacewalk/postgres/data ===
Contains (.sql) files with SQL for inserting ''primer'' data into '''postgres''' tables.  File names match the name of table into which the data is inserted/updated.

=== /schema/spacewalk/postgres/data/common ===
Populated at build ^''read-only''^

=== /schema/spacewalk/postgres/triggers ===
Contains (.sql) files with DDL for creating/replacing '''postgres''' triggers.  File names match the name of table on which the trigger is created/replaced.

=== /schema/spacewalk/postgres/procs ===
Contains (.sql) files with DDL for creating/replacing '''postgres''' stored procedures/functions.  File names match the name of procedure/function begin created.

=== /schema/spacewalk/postgres/packages ===
Contains (.pks|.pkb) files with DDL for creating/replacing '''postgres''' packages.  File names match the name of package begin created.
  .pks::
    Package Declaration (header)
  .pkb::
    Package Definition (body)

