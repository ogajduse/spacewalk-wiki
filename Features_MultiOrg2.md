= Background =

The multiple organization support feature in Spacewalk allows you to partition your Spacewalk server into different organizations that each have their own set of entitlements, systems, and content that other organizations on the Spacewalk server cannot access.

What is in Spacewalk right now is a first cut of this feature. There are a number of improvements that should be made to the feature to make it more usable. The following pages will track the requirements, specifications and details for the next phase of Multiple Organizations:

 * [wiki:Features/MultiOrg2/Requirements Requirements] to be implemented
 * [wiki:Features/MultiOrg2/Specification Specification] - High Level design
 * [wiki:Features/MultiOrg2/TrustRelationships Trust relationships] between organizations will enable content sharing and system migration - if you don't have a trust relationship with a given org, you can't see any of the content it shares with you nor can you migrate systems to it or can systems from it be migrated to your organization.
 * [wiki:Features/MultiOrg2/ContentSharing Content Sharing] between organizations
 * [wiki:Features/MultiOrg2/SystemMigration System Migration] between organizations will be implemented as a script that will be run by the root user on the server itself. However, the webui will help you identify which systems have been migrated to your organization.

== Web UI Overview ==
Here's a sitemap of the Web UI showing new/modified pages for this feature:

[[Image(multiorg-sitemap.png)]]

== Directory of Web UI Mockups ==
 * '''Mockup A1''': attachment:wiki:Features/MultiOrg2/SystemMigration:overview-widget-migrated.png
 * '''Mockup B1''': attachment:wiki:Features/MultiOrg2/TrustRelationships:org-mytrusts.png
 * '''Mockup B2''': attachment:wiki:Features/MultiOrg2/TrustRelationships:org-extorg-details.png
 * '''Mockup B3''': attachment:wiki:Features/MultiOrg2/TrustRelationships:org-extorg-channelsconsumed.png
 * '''Mockup B4''': attachment:wiki:Features/MultiOrg2/TrustRelationships:org-extorg-channelsprovided.png
 * ''There is no mockup B5.''
 * '''Mockup B6''': attachment:wiki:Features/MultiOrg2/ContentSharing:channel-details-consumer.png
 * '''Mockup C1''': attachment:wiki:Features/MultiOrg2/SystemMigration:systems-list-migrated.png
 * '''Mockup D1''': attachment:wiki:Features/MultiOrg2/ContentSharing:channel-details-sharing.png
 * '''Mockup D2''': attachment:wiki:Features/MultiOrg2/ContentSharing:channel-details-orgs_privateconfirm.png
 * '''Mockup D3''': attachment:wiki:Features/MultiOrg2/ContentSharing:channel-details-orgs_protectedconfirm.png
 * '''Mockup D4''': attachment:wiki:Features/MultiOrg2/ContentSharing:channel-details-orgs.png
 * '''Mockup D5''': attachment:wiki:Features/MultiOrg2/ContentSharing:channel-details-orgs_removalconfirm.png
 * '''Mockup E1''': attachment:wiki:Features/MultiOrg2/ContentSharing:channels-list-new-filters.2.png
 * '''Mockup F1''': attachment:wiki:Features/MultiOrg2/TrustRelationships:orgs-list.png
 * '''Mockup F2''': attachment:wiki:Features/MultiOrg2/TrustRelationships:org-trust-tab.png
 * '''Mockup F3''': attachment:wiki:Features/MultiOrg2/TrustRelationships:org-trust-tab-confirm.png

== Channel Sharing Model ==

[[Image(channel-sharing_multiorg2.png)]] 