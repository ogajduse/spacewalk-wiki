
For up-to-date information about the PostgreSQL port, see [[PostgreSQL]]. This page is now obsolete.

----
# Introduction



Below is a collection of information related to the effort to remove Spacewalk's dependency on Oracle, support PostgreSQL, and ultimately be database agnostic. If you are interested in participating in this effort please feel free to review the projects and tasks below to find something that suits your abilities. If you find something you can assign the task to yourself. Help should be available if you require it on IRC and the mailing list.

All estimates are given in days.

The architecture we hope to achieve:

 * All database communication done via standardized SQL that will run against the major databases. 
 * Leverage Java Hibernate mappings whenever possible.
 * Migrate all stored procedures to Java application code. (unless absolutely necessary to keep for performance reasons)
 * If stored procedure was used in the Perl stack, migrate the affected pages to Java/JSP.
 * Implement an RPC API for the Python backend to call in place of the stored procedure. (NOTE: unclear if this will be required)

Most development of PostgreSQL specific code is underway in the *postgresql* branch in git. For information on how to checkout and work with this branch, see the GitGuide.
# Support Intallation of PostgreSQL Schema
 


Requires modifications to spacewalk-setup code to isolate any Oracle specific code and fork the execution path based on the selected database backend.

Current plan is to have PostgreSQL schema generated from Oracle schema using a simple type template system.


|  *Task*  |  *Estimate*  |  *Owner*  |  *Status*  |
| --- | --- | --- | --- |
|  Modify spacewalk-setup to support multiple databases  |  8  |  dgoodwin  |  ~70%  |
|  Generate PostgreSQL schema from templates  |  -  |  paji  |  done  |
# Port Stored Procedures to Java Application Code



After examining the advantages/disadvantages of migrating stored procedures straight to Java application code (that will theoretically run on multiple databases) it was decided the alternative (porting PL/SQL to PL/pgSQL and maintaining both versions) would be minimally less expensive (if we require strict unit testing of the new code). Considering that we would ultimately like to be database agnostic, the effort to reach the end goal could double and thus we chose to accept the overhead and proceed to obtain the architecture we want.

See also:
 * [StoredProcedureAnalysis](PathToPostgreSql_StoredProcedureAnalysis)

*TODO*: Add documentation for process involved with performing an actual migration of a stored proc. Link to a solid commit that demonstrates the whole process would also be nice.

Estimates below are based on the following:
 * <= 25 lines = small procedure = ~2 days
 * <= 75 lines = medium procedure = ~5 days
 * > 75 lines = large procedure = ~10 days


|  *Procedure*  |  *Lines*  |  *Estimate*  |  *Owner*  |  *Status*  |
| --- | --- | --- | --- | --- | --- |
|  is_user_org_admin  |  28  |  5  |  dgoodwin  |  done  |
|  lookup_channel_arch  |  15  |  2  |   |   |  |
|  name_join  |  23  |  2  |   |   |  |
|  rhn_install_org_satellites  |  25  |  2  |   |   |  |
|  rhnhistoryview_pkglist  |  42  |  5  |   |   |  |
|  lookup_package_nevra  |  36  |  5  |   |   |  |
|  rhn_synch_probe_state  |  27  |  5  |   |   |  |
|  new_user_postop  |  29  |  5  |   |   |  |
|  delete_errata  |  12  |  2  |   |   |  |
|  lookup_transaction_package  |  51  |  5  |   |   |  |
|  lookup_feature_type  |  16  |  2  |   |   |  |
|  lookup_config_info  |  29  |  5  |   |   |  |
|  lookup_cf_state  |  13  |  2  |   |   |  |
|  queue_server  |  28  |  5  |   |   |  |
|  lookup_server_arch  |  15  |  2  |   |   |  |
|  delete_server  |  181  |  10  |   |   |  |
|  lookup_sg_type  |  16  |  2  |   |   |  |
|  lookup_snapshot_invalid_reason  |  16  |  2  |   |   |  |
|  rhn_install_satellite  |  14  |  2  |   |   |  |
|  lookup_virt_sub_level  |  16  |  2  |   |   |  |
|  lookup_client_capability  |  20  |  2  |   |   |  |
|  lookup_package_provider  |  12  |  2  |   |   |  |
|  create_first_org  |  113  |  10  |   |   |  |
|  lookup_cve  |  20  |  2  |   |   |  |
|  delete_server_bulk  |  199  |  10  |   |   |  |
|  queue_errata  |  9  |  2  |   |   |  |
|  label_join  |  23  |  2  |   |   |  |
|  truncatecachequeue  |  4  |  2  |   |   |  |
|  lookup_package_name  |  23  |  2  |   |   |  |
|  rhn_clean_current_state  |  8  |  2  |  dgoodwin  |  done  |
|  lookup_package_key_type  |  12  |  2  |   |   |  |
|  lookup_tag_name  |  19  |  2  |   |   |  |
|  lookup_source_name  |  19  |  2  |   |   |  |
|  create_new_user  |  73  |  5  |   |   |  |
|  lookup_arch_type  |  13  |  2  |   |   |  |
|  id_join  |  23  |  2  |   |   |  |
|  create_new_org  |  98  |  10  |   |   |  |
|  rhn_prepare_install  |  39  |  5  |   |   |  |
|  create_pxt_session  |  16  |  2  |   |   |  |
|  lookup_first_matching_cf  |  35  |  5  |   |   |  |
|  channel_name_join  |  23  |  2  |   |   |  |
|  lookup_evr  |  21  |  2  |   |   |  |
|  lookup_package_arch  |  18  |  2  |   |   |  |
|  rhnhistoryview_erratalist  |  40  |  5  |   |   |  |
|  delete_channel  |  16  |  2  |   |   |  |
|  lookup_config_filename  |  20  |  2  |   |   |  |
|  lookup_package_delta  |  19  |  2  |   |   |  |
|  pxt_session_cleanup  |  25  |  2  |   |   |  |
|  does_user_have_role  |  26  |  5  |   |   |  |
|  lookup_package_capability  |  30  |  5  |   |   |  |
|  lookup_tag  |  20  |  2  |   |   |  |
|  lookup_erratafile_type  |  16  |  2  |   |   |  |
|  set_ks_session_history_message  |  35  |  5  |   |   |  |
|  is_user_applicant  |  28  |  5  |   |   |  |
|  rhn_server.system_service_level  |  16  |  2  |   |   |  |
|  rhn_server.can_change_base_channel  |  15  |  2  |   |   |  |
|  rhn_server.set_custom_value  |  26  |  5  |   |   |  |
|  rhn_server.bulk_set_custom_value  |  19  |  2  |   |   |  |
|  rhn_server.bulk_snapshot_tag  |  31  |  5  |   |   |  |
|  rhn_server.tag_delete  |  24  |  2  |   |   |  |
|  rhn_server.tag_snapshot  |  10  |  2  |   |   |  |
|  rhn_server.bulk_snapshot  |  12  |  2  |   |   |  |
|  rhn_server.snapshot_server  |  89  |  10  |   |   |  |
|  rhn_server.remove_action  |  62  |  5  |   |   |  |
|  rhn_server.check_user_access  |  27  |  5  |   |   |  |
|  rhn_server.can_server_consume_virt_slot  |  25  |  2  |   |   |  |
|  rhn_server.insert_into_servergroup  |  69  |  5  |   |   |  |
|  rhn_server.insert_into_servergroup_maybe  |  25  |  2  |   |   |  |
|  rhn_server.insert_set_into_servergroup  |  26  |  5  |   |   |  |
|  rhn_server.delete_from_servergroup  |  66  |  5  |   |   |  |
|  rhn_server.delete_set_from_servergroup  |  23  |  2  |   |   |  |
|  rhn_server.clear_servergroup  |  11  |  2  |   |   |  |
|  rhn_server.delete_from_org_servergroups  |  14  |  2  |   |   |  |
|  rhn_server.get_ip_address  |  22  |  2  |   |   |  |
|  rhn_org.find_server_group_by_type  |  9  |  2  |   |   |  |
|  rhn_org.delete_org  |  45  |  5  |   |   |  |
|  rhn_org.delete_user  |  120  |  10  |   |   |  |
|  rhn_exception.lookup_exception  |  13  |  2  |   |   |  |
|  rhn_exception.raise_exception  |  11  |  2  |   |   |  |
|  rhn_exception.raise_exception_val  |  13  |  2  |   |   |  |
|  rhn_package.canonical_name  |  12  |  2  |   |   |  |
|  rhn_package.channel_occupancy_string  |  16  |  2  |   |   |  |
|  rhn_bel.is_org_paid  |  10  |  2  |   |   |  |
|  rhn_bel.lookup_email_state  |  11  |  2  |   |   |  |
|  rhn_quota.recompute_org_quota_used  |  24  |  2  |   |   |  |
|  rhn_quota.get_org_for_config_content  |  14  |  2  |   |   |  |
|  rhn_quota.set_org_quota_total  |  20  |  2  |   |   |  |
|  rhn_quota.update_org_quota  |  8  |  2  |   |   |  |
|  rhn_user.check_role  |  18  |  2  |   |   |  |
|  rhn_user.check_role_implied  |  18  |  2  |   |   |  |
|  rhn_user.get_org_id  |  9  |  2  |   |   |  |
|  rhn_user.find_mailable_address  |  69  |  5  |   |   |  |
|  rhn_user.add_servergroup_perm  |  21  |  2  |   |   |  |
|  rhn_user.remove_servergroup_perm  |  18  |  2  |   |   |  |
|  rhn_user.add_to_usergroup  |  18  |  2  |   |   |  |
|  rhn_user.add_users_to_usergroups  |  13  |  2  |   |   |  |
|  rhn_user.remove_from_usergroup  |  23  |  2  |   |   |  |
|  rhn_user.remove_users_from_servergroups  |  14  |  2  |   |   |  |
|  rhn_entitlements.remove_org_entitlements  |  35  |  5  |   |   |  |
|  rhn_entitlements.entitlement_grants_service  |  26  |  5  |   |   |  |
|  rhn_entitlements.lookup_entitlement_group  |  19  |  2  |   |   |  |
|  rhn_entitlements.create_entitlement_group  |  19  |  2  |   |   |  |
|  rhn_entitlements.can_entitle_server  |  55  |  5  |   |   |  |
|  rhn_entitlements.can_switch_base  |  23  |  2  |   |   |  |
|  rhn_entitlements.find_compatible_sg  |  29  |  5  |   |   |  |
|  rhn_entitlements.entitle_server  |  45  |  5  |   |   |  |
|  rhn_entitlements.remove_server_entitlement  |  73  |  5  |   |   |  |
|  rhn_entitlements.unentitle_server  |  41  |  5  |   |   |  |
|  rhn_entitlements.repoll_virt_guest_entitlements  |  109  |  10  |   |   |  |


|  rhn_entitlements.get_server_entitlement  |  26  |  5  |   |   |  |
| --- | --- | --- | --- | --- | --- |
|  rhn_entitlements.modify_org_service  |  127  |  10  |   |   |  |
|  rhn_entitlements.set_customer_enterprise  |  5  |  2  |   |   |  |
|  rhn_entitlements.set_customer_provisioning  |  5  |  2  |   |   |  |
|  rhn_entitlements.set_customer_monitoring  |  5  |  2  |   |   |  |
|  rhn_entitlements.set_customer_nonlinux  |  5  |  2  |   |   |  |
|  rhn_entitlements.unset_customer_enterprise  |  5  |  2  |   |   |  |
|  rhn_entitlements.unset_customer_provisioning  |  5  |  2  |   |   |  |
|  rhn_entitlements.unset_customer_monitoring  |  5  |  2  |   |   |  |
|  rhn_entitlements.unset_customer_nonlinux  |  5  |  2  |   |   |  |
|  rhn_entitlements.prune_group  |  81  |  10  |   |   |  |
|  rhn_entitlements.assign_system_entitlement  |  85  |  10  |   |   |  |
|  rhn_entitlements.assign_channel_entitlement  |  62  |  5  |   |   |  |
|  rhn_entitlements.activate_system_entitlement  |  41  |  5  |   |   |  |
|  rhn_entitlements.activate_channel_entitlement  |  40  |  5  |   |   |  |
|  rhn_entitlements.set_group_count  |  58  |  5  |   |   |  |
|  rhn_entitlements.prune_family  |  56  |  5  |   |   |  |
|  rhn_entitlements.set_family_count  |  63  |  5  |   |   |  |
|  rhn_entitlements.entitle_last_modified_servers  |  36  |  5  |   |   |  |
|  rhn_entitlements.prune_everything  |  50  |  5  |   |   |  |
|  rhn_entitlements.subscribe_newest_servers  |  37  |  5  |   |   |  |
|  rhn_config.prune_org_configs  |  6  |  2  |   |   |  |
|  rhn_config.insert_revision  |  30  |  5  |   |   |  |
|  rhn_config.delete_revision  |  70  |  5  |   |   |  |
|  rhn_config.get_latest_revision  |  13  |  2  |   |   |  |
|  rhn_config.insert_file  |  20  |  2  |   |   |  |
|  rhn_config.delete_file  |  19  |  2  |   |   |  |
|  rhn_config.insert_channel  |  25  |  2  |   |   |  |
|  rhn_config.delete_channel  |  13  |  2  |   |   |  |
|  rhn_config_channel.action_diff_revision_status  |  45  |  5  |   |   |  |
|  rhn_config_channel.get_user_chan_access  |  47  |  5  |   |   |  |
|  rhn_config_channel.get_user_revision_access  |  16  |  2  |   |   |  |
|  rhn_config_channel.get_user_file_access  |  15  |  2  |   |   |  |
|  rhn_cache.update_perms_for_server  |  10  |  2  |   |   |  |
|  rhn_cache.update_perms_for_user  |  23  |  2  |   |   |  |
|  rhn_cache.update_perms_for_server_group  |  24  |  2  |   |   |  |
|  rhn_channel.get_license_path  |  14  |  2  |   |   |  |
|  rhn_channel.license_consent  |  15  |  2  |   |   |  |
|  rhn_channel.subscribe_server  |  98  |  10  |   |   |  |
|  rhn_channel.can_server_consume_virt_channl  |  25  |  2  |   |   |  |
|  rhn_channel.bulk_subscribe_server  |  7  |  2  |   |   |  |
|  rhn_channel.bulk_server_base_change  |  11  |  2  |   |   |  |
|  rhn_channel.bulk_server_basechange_from  |  42  |  5  |   |   |  |
|  rhn_channel.bulk_guess_server_base  |  19  |  2  |   |   |  |
|  rhn_channel.guess_server_base  |  16  |  2  |   |   |  |
|  rhn_channel.normalize_server_arch  |  15  |  2  |   |   |  |
|  rhn_channel.base_channel_for_release_arch  |  20  |  2  |   |   |  |
|  rhn_channel.base_channel_rel_archid  |  40  |  5  |   |   |  |
|  rhn_channel.bulk_guess_server_base_from  |  25  |  2  |   |   |  |
|  rhn_channel.clear_subscriptions  |  16  |  2  |   |   |  |
|  rhn_channel.unsubscribe_server  |  83  |  10  |   |   |  |
|  rhn_channel.bulk_unsubscribe_server  |  7  |  2  |   |   |  |
|  rhn_channel.family_for_channel  |  13  |  2  |   |   |  |
|  rhn_channel.available_family_subscriptions  |  33  |  5  |   |   |  |
|  rhn_channel.channel_family_current_members  |  22  |  2  |   |   |  |
|  rhn_channel.update_family_counts  |  10  |  2  |   |   |  |
|  rhn_channel.available_chan_subscriptions  |  11  |  2  |   |   |  |
|  rhn_channel.entitle_customer  |  27  |  5  |   |   |  |
|  rhn_channel.set_family_maxmembers  |  25  |  2  |   |   |  |
|  rhn_channel.unsubscribe_server_from_family  |  11  |  2  |   |   |  |
|  rhn_channel.get_org_id  |  9  |  2  |   |   |  |
|  rhn_channel.get_cfam_org_access  |  12  |  2  |   |   |  |
|  rhn_channel.get_org_access  |  17  |  2  |   |   |  |
|  rhn_channel.user_role_check_debug  |  35  |  5  |   |   |  |
|  rhn_channel.user_role_check  |  6  |  2  |   |   |  |
|  rhn_channel.loose_user_role_check  |  8  |  2  |   |   |  |
|  rhn_channel.direct_user_role_check  |  17  |  2  |   |   |  |
|  rhn_channel.org_channel_setting  |  17  |  2  |   |   |  |
|  rhn_channel.channel_priority  |  77  |  10  |   |   |  |
|  rhn_channel.delete_server_channels  |  34  |  5  |   |   |  |
|  rhn_channel.refresh_newest_package  |  17  |  2  |   |   |  |
|  rhn_channel.update_channel  |  27  |  5  |   |   |  |
|  rhn_channel.update_channels_by_package  |  11  |  2  |   |   |  |
|  rhn_channel.update_channels_by_errata  |  12  |  2  |   |   |  |
|  rpm.isdigit  |  10  |  2  |   |   |  |
|  rpm.isalpha  |  11  |  2  |   |   |  |
|  rpm.isalphanum  |  12  |  2  |   |   |  |
|  rpm.rpmstrcmp  |  109  |  10  |   |   |  |
|  rpm.vercmp  |  28  |  5  |   |   |  |
|  rpm.vercmpcounter  |  5  |  2  |   |   |  |
|  rpm.vercmpresetcounter  |  9  |  2  |   |   |  |
|  rhn_date_manip.get_reporting_period_start  |  17  |  2  |   |   |  |
|  rhn_date_manip.get_reporting_period_end  |  18  |  2  |   |   |  |

*Total Estimate*: 658 days
# Migrate Perl Pages Which Use Stored Procedures



Over 200 perl pages remain. The effort in eliminating them all would be too much additional overhead so the current plan is to identify which perl pages actually use stored procedures, and if the number is managable, port only these to application code.

TODO: Add similar table here listing perl pages that require porting.
# Replace Stored Procedure Usage In the Backend



Appears to be about 7 stored procedures used in the Python backend. (look for usage of rhnSQL.Function) 

If required, we may wish to port the procedures to application code, but expose them over an RPC API to the Python backend. See the [ThriftApiProposal](PathToPostgreSql_ThriftApiProposal).

However given the small number of procedures involved, other solutions may present themselves when the time comes.
# SQL Standardization



Examine the SQL in Hibernate and Datasource queries for anything that may be Oracle specific and remove it.
# Potential Hazards

### Custom Data Types




Spacewalk uses a custom data type EVR_T for rhnPackageEvr table. This EVR_T data type is mainly used for ordering. Look at [evr_t.sql](http://git.fedorahosted.org/git/spacewalk.git?p=spacewalk.git;a=blob_plain;f=schema/spacewalk/rhnsat/class/evr_t.sql;hb=HEAD) for the definition of this data type. While Postgres has the facility to create custom data type, it does not have a  'ORDER MEMBER FUNCTION' to dictate natural ordering for the custom data type. Here are some example queries that make use of the order member function in [Package_queries.xml](http://git.fedorahosted.org/git/spacewalk.git?p=spacewalk.git;a=blob_plain;f=java/code/src/com/redhat/rhn/common/db/datasource/xml/Package_queries.xml;hb=HEAD)...
 
    <mode name="system_latest_all_available_packages">
    ........
       SELECT  p.name_id name_id,
                     p.id,
                     p.evr_id,
                     max(pe.evr) evr,
          from ....
    .....
    </mode>
    
    <mode name="system_all_available_packages">
    ........
       SELECT  pn.name AS NAME,....
          from ....
          where ....
    ...     AND PE2.evr &gt;= full_list.evr)
    .....
    </mode>
or [System_queries.xml](http://git.fedorahosted.org/git/spacewalk.git?p=spacewalk.git;a=blob_plain;f=java/code/src/com/redhat/rhn/common/db/datasource/xml/System_queries.xml;hb=HEAD)

    <mode name="system_installed_packages">
    ...
    SELECT ...
      FROM ...
     WHERE ...
    ORDER BY PN.name, PE.evr
    ...
    </mode>

To make things a little worse, this EVR_T is used in DB table view definitions that rely on this magical ordering making it difficult to port in application code, for example [rhnChannelNewestPackageView.sql](http://git.fedorahosted.org/git/spacewalk.git?p=spacewalk.git;a=blob_plain;f=schema/spacewalk/rhnsat/views/rhnChannelNewestPackageView.sql;hb=HEAD)

    create or replace view
    rhnChannelNewestPackageView
    as
    ...
    where 
    ...
    and pe.evr = (select	max(sq_pe.evr)
    ...
PostgreSQL has a way to create  [User defined Aggregate Functions](http://www.postgresql.org/docs/8.3/interactive/sql-createaggregate.html) which has to be explored more and might work well for max, min,and order by have to be worked out... In this case custom methods like evr_max() and evr_min() will have to be created for both oracle and postgres and all the application quesries and view queries have to be replaced with this..
### Remove Synonyms



PostgreSQL does not have synonyms which are heavily used in the monitoring code.
### No Packages In PostgreSQL



NOTE: This does not appear to be an issue if we are replacing all stored procedures. Will omit this hudle from the tasks section for the time being.

80% of our Oracle stored procedures are in Package and Package Body. Postgres however does not have the concept of package bodies.. So sql queries with calls like rhn_config_channel.get_user_file_access will have issues.. A fix for this issue might be to define [Schema](http://www.postgresql.org/docs/8.3/interactive/ddl-schemas.html)  for each Package name space and define package functions and procedures in the schema .. For example in the case of rhn_config_channel.get_user_file_access, we will have  rhn_config_channel schema and get_user_file_access as a stored procedure in it.. Only issue here is that we will lose ability to store member variables in package body.. But the instances I checked there havent been many packages that have instance variables.
### Stored Procedures Referenced Within Schema Itself



There is a certain set of stored procedures within the schema that are referenced from *within* the database code directly. An example of this would be this usage of a stored procedure call within a view:


    create or replace view rhnUserChannel as
    select	cfp.user_id		user_id,
    	cfp.org_id		org_id,
    	cfm.channel_id		channel_id,
    	'manage'		role
    from	rhnChannelFamilyMembers	cfm,
    	rhnUserChannelFamilyPerms cfp
    where	cfp.channel_family_id = cfm.channel_family_id
    	and rhn_channel.user_role_check(cfm.channel_id,
    		cfp.user_id, 'manage') = 1
      ...

These stored procedures can not be extracted out into our RPC layer because they need to be called from within the schema itself.  The above need to be either:

 1.  Ported to PG/SQL
 1.  Inlined into the schema where the procedure is being called from (less desirable, and probably often quite nasty).


|  *Task*  |  *Estimate*  |  *Owner*  |  *Status*  |
| --- | --- | --- | --- | --- |
|  Replace EVR_T Class  |  15  |   |   |  |
|  Remove synonyms  |   |   |   |  |
|  Remove use of stored procedures within schema  |   |   |   |  |
# Links



  * [pgAdmin](http://www.pgadmin.org/): Looks like an exceptional GUI tool for PostgreSQL management.
  * http://www.pgadmin.org/docs/1.4/pg/plpgsql-porting.html: Some notes on migrating Oracle PL/SQL to PL/pgSQL.
  * [ora2pg](http://freshmeat.net/projects/ora2pg/): Migration tool.
  * http://www.pgcon.org/2008/schedule/attachments/41_oraport.pdf: Porting Oracle Applications to PostgreSQL