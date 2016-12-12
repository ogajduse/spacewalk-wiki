= Script based reporting: Specification =

See [wiki:Features/ScriptBasedReporting] for the overall status of the feature.

== Overview ==

This feature is being added because of user feedback.

== Requirements ==

=== Content of the feature ===

 * Canned, but open source, scripts for some key, highly desired reports
 * Entitlement / subscriptions report
 * Inventory report
 * Software / errata report
 * FISMA (federally mandated) report
 * Event reporting

=== Detailed Requirements ===

 * Scripted subscription and entitlement canned report
 * Scripted inventory canned report
 * Scripted Basic FISMA Report
 * Report on events applied to a system (bugzilla 156311) (should have)

See [wiki:Features/ScriptBasedReporting/Requirements] for complete requirement document.

== Other Feature Impact ==

None.

== Proposed Implementation ==

As the content of the first two reports is nicely described, the proposal is to start with these two, find the appropriate values in the database and create the SQL select commands to retrieve the data, together with the formatting and output.

Since whatever data the API approach will output will have to be generated by SQL queries similar/same to what the direct SQL script would use, we shall start with the direct SQL approach for the first two reports, aim for finishing those two as direct SQL in Spacewalk 0.6.

The other two queries will require more investigation WRT the content of the reports.

The script which will do the formatting should have command line options of specifying if multiple values for given entity (for example, list of software channels for given system) should be presented within single value in one CSV output, in one row, or if the row should be repeated for each of these values. We propose adding systemid value to the reports to make it possible to relate multiple rows of single system, if multivalued values cause the entity to be presented on multiple rows.

The reports will be canned, no user customization of the content of the reports is supported, besides the above-mentioned multivalue presentation. 

=== Known Issues ===

The current Spacewalk database schema has no auditing capabilities. If registered system is deleted from Spacewalk server, the records are actually deleted from the database, making it impossible to show reports for entities that were present on server but are not present anymore. So for example, if system is registered to the server the whole year, and deleted one day before the reporting scripts will be run, it won't show in the report. This problem won't be addressed within this feature.

=== Future Enhancements ===

It is assumed that nicer output presentation (HTML, PDF), while possible, will be provided by different tools in the future, so it is not part of this feature and of the proposal.

== Mockups ==

None.

== Tasks ==

 * Command line script
 * First two reports
 * Add the reports as API calls, modify the script
 * Work on the third report
 * Work on the fourth report

== Test Notes ==

Run queries on various servers populated with various data and check that they match the requirements.

== Risks/Concerns ==

None.