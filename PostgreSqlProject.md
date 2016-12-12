
For up-to-date information about the PostgreSQL port, see [wiki:PostgreSQL]. This page is now obsolete.

----

= PostgreSQL Project =

== Overview ==

This project is focused on modifying Spacewalk to support both Oracle and PostgreSQL databases.

The minimum supported version of Oracle is Oracle 10g.

Targeted version of PostgreSQL is 8.1+

=== Communication ===

 * Developer list: spacewalk-devel@redhat.com [https://www.redhat.com/mailman/listinfo/spacewalk-devel (signup)]
 * IRC: #spacewalk-devel on [http://freenode.net/ (irc.freenode.net)]
 * [wiki:GitGuide git repo]: branch "pgsql" ''( last merged ''from'' master: 06-22-09 by jortel )''
    {{{
    git branch --track pgsql origin/pgsql
    git checkout pgsql
    }}}

 

=== Contacts ===

||'''Name'''||'''Email'''||'''IRC nick'''|| git ||'''Role/Responsibilities'''||
||Todd Sanders||mailto:tsanders@redhat.com||tsanders|| Y || ||
||Jeff Ortel||mailto:jortel@redhat.com||jortel|| Y || Technical Lead ||
||Devan Goodwin||mailto:dgoodwin@redhat.com||dgoodwin|| Y || ||
||Greg De Koenigsberg||mailto:gdk@redhat.com||gregdek||N||Community Guy||

=== Planning ===

[wiki:"PostgreSQL Development Plan" Project Plan]

[wiki:"PostgreSQL Test Plan" Test Plan]

[wiki:PostgresTechnicalApproach Technical Approach]

=== Tracking ===

'''What's happening this week ...'''^03/30/09^

 * Getting perl stack connecting/working with postgres (dgoodwin)
 * Refactoring ''/schema'' directory into:  (jortel)
    * common parts (done)
    * forked '''oracle''' parts (done)
    * forked '''postgres''' parts 
 * Get build, install & packaging working with refactored directory (jortel).
   * oracle build working.
   * postgres build working but:
      * syntax problems in many of the procs
      * missing 119 trigger files.


|| Tables & Indexes || 100% || [wiki:PgportTables Details] || ||
|| Data (inserts) || 100% ||  || ||
|| Views || 100% || [wiki:PgportViews Details] || ||
|| Triggers || 50% || [wiki:PgportTriggers Details] || 119 missing
|| Procedures || 80% || [wiki:PgportProcedures Details] || 13/57 loaded by EDB || 
|| Packages || 70% || || Also needs .pks created.||
|| Application infrastructure || 30% || [wiki:PostgresAppInfrastructure Details] ||
|| Query tagging || 75% || [wiki:PgportQueries Details]||
|| Query migration:java || 0%|| ||
|| Query migration:python || 0%|| ||
|| Query migration:perl || 0%|| ||

[PostgresBranchReview Branch Review]

[PostgresIssues Project Issues]

[PostgresTasks Project Tasks]

[PostgresMeetingNotes Meeting Notes]

[PostgresWorklog Worklog] - What problems are being encountered in the "pgsql" branch and how they're being solved.

[PostgresDevelopmentNotes Development Notes] - Notes on how to actually work with the as of yet unreleased PostgreSQL code in the pgsql git branch.

[PostgresTestNotes Testing Notes] - Notes on current testing activities

=== Resources ===

Orafce: Oracle support functions http://pgfoundry.org/projects/orafce/

Ora2pg: Convert Oracle DDL to Postgres http://freshmeat.net/projects/ora2pg/

=== Porting Documentation ===

Porting Oracle Applications to PostgreSQL http://developer.postgresql.org/~petere/oraport.pdf

EnterpriseDB Oracle Compatibility Developer's Guide http://www.enterprisedb.com/downloads/docs/EnterpriseDB_OraCompat_8.3_v2.7.pdf

Migrating Oracle PL/SQL to PL/pgSQL http://www.pgadmin.org/docs/1.4/pg/plpgsql-porting.html

=== Porting Guidelines ===

[PostgresPortingGuidelines Postgres Porting guidelines] Here are the initial guidelines on how to move ahead with this porting effort. This will be posted, discussed and finalized on the developer mailing list too, so please follow it up there.

=== References ===
[PathToPostgreSql early research]