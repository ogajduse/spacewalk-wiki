[wiki:PostgreSqlProject Main Project Page]

= Project Plan =

This is s ''straw man'' for the project plan and needs more work.
 
== Planning - phase 1 ==

''<add detail here>''

["PostgreSQL Development Plan"]

["PostgreSQL Tasks/Track"]

=== Knowledge Transfer ===

''<add detail here>''

==== Overview ====

''<add detail here>''

==== Datamodel Review ====

''<add detail here>''

=== Analysis ===

''<add detail here>''

==== Sample (populated) Database (oracle & postgres) ====
       
''<add detail here>''

==== Schema ====

''<add detail here>''

==== Views ====

''<add detail here>''

==== Queries ====

''<add detail here>''

==== Stored Procedures ====

''<add detail here>''

=== Identify Risks ===

''<add detail here>''

=== Infrastructure ===

''<add detail here>''

==== Communication ====

''<add detail here>''

==== Source Control ====

''<add detail here>''

=== Packaging Plan ===

''<add detail here>''

=== Technical (migration) Approach ===

''<add detail here>''

[wiki:PostgresTechnicalApproach Technical Approach]

=== Assemble Team ===

  * Bruce Momjian mailto:bruce@momjian.us
  * George Williams mailto:george.williams@enterprisedb.com
  * Gurjeet Singh mailto:gurjeet.singh@enterprisedb.com
  * Vikram Rai mailto:vikram.singh@enterprisedb.com
  * Tushar Ahuja mailto:tushar.ahuja@enterprisedb.com


=== Test Plan ===

''<add detail here>''

["PostgreSQL Test Plan"]

==== Functional Test Plan ====

''<add detail here>''

==== Query / Stored Procedure ''( Level )'' ====

''<add detail here>''

==== System ''( Level )'' ====

''<add detail here>''

==== Performance Test Plan ====

''<add detail here>''

=== Test Environment ===

''<add detail here>''

=== Identify Gaps In Automated Testing ===

''<add detail here>''

=== Data Migration Plan ===

''<add detail here>''

==== Oracle -> Postgres ====

''<add detail here>''

==== Postgres -> Oracle ====

''<add detail here>''

=== Schema Upgrade Plan ===

''How do we do this for multiple databases?''

== Implementation - phase 2 ==

=== Git Setup ===
 
Cleanup or drop and recreate the postgres branch.

''<add detail here>''

=== Create PG Schema & Sample Database ===

''<add detail here>''

=== Compatibility Libraries ===

''<add detail here>''
 * orafce
 * other?

==== Back porting ====

''<add detail here>''

==== Packaging ====

''<add detail here>''

=== Development Packages ===

''<add detail here>''
 * spacewalk-schema.rpm
 * spacewalk-setup.rpm
 * ...

=== Spacewalk Database Infrastructure ===

Modify Spacewalk infrastructure to support multiple databases.
 * Drivers
 * Installer
 * DB Wrappers 
   * Java Stack
   * Python Stack
   * Perl Stack
 * db-control scripts

''<add detail here>''

=== Refine/Tune Postgres Schema ===

''<add detail here>''

=== Tag Queries ===

''<add detail here>''

=== Isolate Development Branch from Master ===

Stop pulling from master.

''<add detail here>''

=== Migrate Queries ===

''<add detail here>''

=== Migrate Stored Procedures ===

Create postgres function of Oracle stored procedures.

''<add detail here>''

== Testing - phase 3 ==

=== Functional Regression Test''(Automated Testing)'' ===

''<add detail here>''

=== Query/Stored Procedure Performance Testing ===

''<add detail here>''

=== Client ''driven'' Performance Testing ===

   ''<add detail here>''