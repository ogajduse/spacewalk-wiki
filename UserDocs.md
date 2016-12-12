= '''User Documentation''' =
In this section you can find user documentation for Spacewalk.  Are you a developer? You may also be interested in the [DeveloperDocs Developer Documentation] and [DownloadIt Source/RPM Download Information].

Is there documentation missing or you simply would like to see? Is there something you would like to understand better? Please feel free to let us know using the [https://fedorahosted.org/spacewalk/wiki#Communication mailing list] or look for us on #spacewalk on irc.freenode.net.

Do you know the answer to something and think others might find it useful? Feel free to add your own docs and/or additions, it is a wiki you know.

----
[[TOC(inline)]]
----
== __Getting Started__ ==
=== Introduction ===
  * [wiki:Preface Preface]
  * [wiki:Conventions Conventions]
=== Installation  ===
  * [wiki:HowToInstall How to install]
    * [wiki:HowToInstall#SettingupSpacewalkrepo Setting up Spacewalk repo]
    * [wiki:HowToInstall#Additionalrepospackages Additional repos & packages]
    * [wiki:HowToInstall#OraclePre-Requisites Oracle Pre-Requisites]
    * [wiki:HowToInstall#ConflictingPackages Conflicting Packages]
    * [wiki:HowToInstall#InstallingSpacewalk Installing Spacewalk]
    * [wiki:HowToInstall#ConfiguringSpacewalk Configuring Spacewalk]
    * [wiki:HowToInstall#ManagingSpacewalk Managing Spacewalk]
    * [wiki:HowToInstall#KnownIssues Known Issues]
  * [wiki:OracleXeSetup Oracle XE Setup] -- How to get Oracle XE running if you do not already have Oracle.
  * [http://www.redhat.com/f/pdf/rhn/satellite_redundancy.pdf Configuring redundant Satellites].
  * [http://wiki.woop.es/Instalacion_Spacewalk Spanish Translation]
=== Post-Installation Guides ===
  * [wiki:SpacewalkBackup Backup Spacewalk] -- How to backup a Spacewalk server
  * [wiki:CertCreation Entitlement Certs ] -- Create and activate your own certs for Spacewalk
  * [wiki:UploadFedoraContent Upload  Content] -- Upload RHEL, CENT, or Fedora content (or any other rpms)
  * [wiki:RegisteringClients Registering Clients] -- How to register Fedora / Cent OS clients to Spacewalk.
  * [wiki:OSADSetup How to install osad] -- How to use osad to force scheduled actions to run immediately on Spacewalk clients
  * [wiki:HowToInstallProxy How to install Proxy] -- How to download and install Spacewalk Proxy.
  * [http://www.redhat.com/docs/manuals/satellite/Red_Hat_Network_Satellite-5.2.0/html/Reference_Guide/s2-mon-rhnmd-sshd.html Implement monitoring via SSH] -- Instead of RHNMD/port 4545
  * [https://access.redhat.com/knowledge/docs/en-US/Red_Hat_Network_Satellite/5.5/html/Installation_Guide/sect-Installation_Guide-Maintenance-Implementing_PAM_Authentication.html Implement PAM (LDAP, Kerberos) authentication]  -- For the spacewalk web portal.
=== Core Guides ===
  * [wiki:MultiOrgGuide Multiple Organizations] -- A guide to setting up multiple organisations
  * [wiki:ConfigurationManagement General Configuration Management]
  * [wiki:ManagingRHELSystems Managing RHEL Systems]
  * [wiki:ManagingFedoraSystems Managing Fedora Systems]
    * [wiki:ManagingFedoraSystems#ChannelSetup Channel Setup]
    * [wiki:ManagingFedoraSystems#ProvisioningClients Provisioning]
    * [wiki:ManagingFedoraSystems#RegisteringClients Registering]
    * [wiki:ManagingFedoraSystems#PushingPackagestoClients Pushing Packages]
    * [wiki:ManagingFedoraSystems#ManagingClientConfigurations Fedora Specific Configuration Management]
    * [wiki:ManagingFedoraSystems#RelatedDocumentation Related Documentation]
  * [wiki:ManagingCentOSSystems Managing CentOS Systems] 
  * [wiki:ManagingSolarisSystems Managing Solaris Systems] -- Registering Solaris clients and uploading content.
    * [wiki:ManagingSolarisSystems#ChannelSetup Channel Setup]
    * [wiki:ManagingSolarisSystems#ProvisioningClients Provisioning]
    * [wiki:ManagingSolarisSystems#RegisteringClients Registering]
    * [wiki:ManagingSolarisSystems#PushingPackagestoClients Pushing Packages]
    * [wiki:ManagingSolarisSystems#ManagingClientConfigurations Solaris Specific Configuration Management]
    * [wiki:ManagingSolarisSystems#RelatedDocumentation Related Documentation]
  * [wiki:ManagingDebianSystems Managing Debian Systems]
----
== __General Documentation__ ==
=== Advanced Guides ===
  * [wiki:HowToKickstartCobbler How to Kickstart with Spacewalk and Cobbler] -- Spacewalk and Cobbler together: How to use the new integration released in Spacewalk 0.4
  * [wiki:Spacewalkonvm Spacewalk on Virtual Machine Procedure] -- A brain/screendump of installing a Fedora 10, kvm install of a spacewalk server (under construction!)
  * [wiki:AuditReviewing Using Spacewalk to review Linux audits] -- How to setup Spacewalk to search and review Linux audits
  * [wiki:spacecmd] -- command-line interface to Satellite and Spacewalk servers
  * [wiki:Deb_support_in_spacewalk Debian Support] -- Debian Support
  * [wiki:HowToUseCrashReporting Software Crash Reporting] -- How to use software crash reporting functionality in Spacewalk (Spacewalk & abrt)
=== Ongoing Maintenance and Administration ===
  * [wiki:HowToUpgrade How to upgrade] -- How to upgrade an existing Spacewalk installation.
  * [wiki:DebuggingProxy Debugging Proxy] -- Tip on solving problems with Spacewalk Proxy.
  * [wiki:SpacewalkHostnameRename Host name Rename] -- How to rename the server running spacewalk.
=== In-depth Guides ===
  * [wiki:OsadHowTo osad and osa-dispatcher] -- How does osad / osa-dispatcher / jabberd work
  * [http://www.redhat.com/docs/manuals/satellite/ Red Hat Network Satellite docs] -- These are the official docs for the production product.  Over time we will have some docs more closely related to upstream here.
  * [http://www.stud.fit.vutbr.cz/~xdurfi00/diplomka/xdurfi00.pdf Debian Support Thesis] which can also be downloaded [http://www.redhat.com/spacewalk/documentation/master-thesis-debian-support.pdf here].
=== Core API Reference ===
  * [wiki:ApiDocs Core API Guide] -- Learn how to use our XMLRPC API to control your Spacewalk server.
  * [wiki:SpacewalkApiPerlGuide API Guide for Perl] -- A user contributed guide to using the Spacewalk API in Perl.
  * [wiki:DeveloperDocs Developer documentation] -- Learn how to work on and build Spacewalk, and how Spacewalk is put together. 
----
== __Other Documentation__ ==
=== Up/Down-stream Documentation ===
  * The upstream, [http://www.redhat.com/docs/manuals/satellite/ Official Red Hat Network Satellite Documentation]
    * [http://www.redhat.com/docs/en-US/Red_Hat_Network_Satellite/5.3/Installation_Guide/html/index.html The official Red Hat Satellite Installation Section]
    * [http://www.redhat.com/docs/en-US/Red_Hat_Network_Satellite/5.3/Proxy_Installation_Guide/index.html The official Red Hat Proxy Installation Section]
    * [http://www.redhat.com/pdf/ISS_Best_Practices_Whitepaper.pdf ISS Best Practices Whitepaper]
  * The downstream, [http://centos.org/ CentOS] Project Documentation
    * [http://wiki.centos.org/HowTos/PackageManagement/Spacewalk The CentOS Project's Package Management/Spacewalk HowTo]
  * J. Tanner's notes about RHN Satellite
    * http://tannerjc.net/wiki/index.php?title=Satellite

=== Related Technology Resources ===
  * [http://www.rpm.org/ The RPM Homepage]
    * [http://en.wikipedia.org/wiki/RPM_Package_Manager Wikipedia article on RPM]
    * [http://docs.fedoraproject.org/drafts/rpm-guide-en/index.html The Fedora RPM guide]
  * [http://docs.fedoraproject.org/deployment-guide/f12/en-US/html/pt-pkg-management.html The Fedora 12 Deployment guide]
  * [http://yum.baseurl.org/ The YUM Homepage]
    * [http://en.wikipedia.org/wiki/Yellow_Dog_Updater_Modified Wikipedia article on YUM]
    * [http://prefetch.net/articles/yum.html Useful article about YUM]
----
== __Frequently Asked Questions__ ==
=== [wiki:SpacewalkFaq FAQ] ===
  * [wiki:SpacewalkFaq#General General]
  * [wiki:SpacewalkFaq#WhatisSpacewalk What Is Spacewalk?]
  * [wiki:SpacewalkFaq#HowlonghasSpacewalkbeenaround How long has Spacewalk been around?]
=== [wiki:SpacewalkFaq#Installation Installation] ===
  * [wiki:SpacewalkFaq#IsaSatelliteSpacewalkcertificaterequiredtouseSpacewalk Is a Satellite/Spacewalk certificate required to use Spacewalk?]
=== [wiki:SpacewalkFaq#SpacewalkArchitecture Architecture] ===
  * [wiki:SpacewalkFaq#WhydoyouuseOracleAnyplansforsupportingotherdatabases Any plans for supporting other databases?]
  * [wiki:SpacewalkFaq#WhatifIdonthaveOracle What if I don't have Oracle?]
  * [wiki:SpacewalkFaq#PerlPythonandJavaOHMY Perl, Python, and Java OH MY!]
  * [wiki:SpacewalkFaq#WhyaretheretwoXML-RPCAPIendpoints Why are there two XML-RPC API endpoints?]
  * [wiki:SpacewalkFaq#WhatlanguagescanIusetointeractwiththeXML-RPCAPIs What languages can I use to interact with the XML-RPC APIs?]
  * [wiki:SpacewalkFaq#WhatOSesaresupported What OSes are supported?]
=== [wiki:SpacewalkFaq#TheFuture The Future] ===
  * [wiki:SpacewalkFaq#WhataboutintegratingtechnologyX What about integrating technology X?]
  * [wiki:SpacewalkFaq#Whatkindofcommunitycontributionsareyouinterestedin What kind of community contributions are you interested in?]
----
== __Known Issues & Current Limitations__ ==
=== Installation Issues ===
=== GUI Issues ===
  * [wiki:KnownIssues/CertExpiring "Certificate Expiring" messages] -- What to do when such a message appears in the GUI.
=== Configuration Issues ===
  * [wiki:MultibyteSpacewalk Multibyte (UTF8) input limitations]
=== Networking Issues ===
  * [wiki:JabberAndOSAD Jabber & OSAD]
=== Database Issues ===
  * [wiki:OracleXeSetup#Troubleshooting Oracle XE] Issues
  * [wiki:PostgreSQL Postgresql] Support
  * [wiki:JabberDatabase Jabber Berkeley Database] Maintenance
----
== __Contact__ ==
 * [https://fedorahosted.org/spacewalk/wiki#Communication Communication]
 * [https://fedorahosted.org/spacewalk/#WanttoFileaBugRFE Bugzilla]
----
== __Appendices__ ==
=== Features ===
  * [wiki:BrainBox Feature Requests/BrainBox]
  * [https://fedorahosted.org/spacewalk/roadmap Road Map]
=== Installation Guides ===
  * [wiki:HowToInstall for 2.3]
  * [wiki:HowToInstall22 for 2.2]
  * [wiki:HowToInstall21 for 2.1]
  * [wiki:HowToInstall20 for 2.0]
  * [wiki:HowToInstall19 for 1.9]
  * [wiki:HowToInstall18 for 1.8]
  * [wiki:HowToInstall17 for 1.7]
  * [wiki:HowToInstall16 for 1.6]
  * [wiki:HowToInstall15 for 1.5]
  * [wiki:HowToInstall14 for 1.4]
  * [wiki:HowToInstall13 for 1.3]
  * [wiki:HowToInstall12 for 1.2]
  * [wiki:HowToInstall11 for 1.1]
  * [wiki:HowToInstall10 for 1.0]
  * [wiki:HowToInstall08 for 0.8]
  * [wiki:HowToInstall07 for 0.7]
=== Upgrade Notes ===
Upgrade guides, sequential, stepped upgrades are recommended to cover multiple update levels, i.e. to get from 0.6 to 0.8 please upgrade via 0.7 (and we recommend testing at each intermediate level as you proceed) rather than trying to go directly from 0.6 to 0.8. Jumping levels is deeply discouraged with the exception of version 0.9 which was never released.
  * [wiki:HowToUpgrade From 2.2 to 2.3]
  * [wiki:HowToUpgrade22 From 2.1 to 2.2]
  * [wiki:HowToUpgrade21 From 2.0 to 2.1]
  * [wiki:HowToUpgrade20 From 1.9 to 2.0]
  * [wiki:HowToUpgrade19 From 1.8 to 1.9]
  * [wiki:HowToUpgrade18 From 1.7 to 1.8]
  * [wiki:HowToUpgrade17 From 1.6 to 1.7]
  * [wiki:HowToUpgrade16 From 1.5 to 1.6]
  * [wiki:HowToUpgrade15 From 1.4 to 1.5]
  * [wiki:HowToUpgrade14 From 1.3 to 1.4]
  * [wiki:HowToUpgrade13 From 1.2 to 1.3]
  * [wiki:HowToUpgrade12 From 1.1 to 1.2]
  * [wiki:HowToUpgrade11 From 1.0 to 1.1]
  * [wiki:HowToUpgrade10 From 0.8 to 1.0]
  * [wiki:HowToUpgrade08 From 0.7 to 0.8]
  * [wiki:HowToUpgrade07 From 0.6 to 0.7]
  * [wiki:HowToUpgrade06 From 0.5 to 0.6]

If you are looking for instructions on how to upgrade the operating system underlying your Spacewalk without upgrading your Spacewalk, follow the instructions described in HowToUpgradeOperatingSystem.
=== Release Notes ===
Release notes for each version:
  * [wiki:ReleaseNotes23 for 2.3]
  * [wiki:ReleaseNotes22 for 2.2]
  * [wiki:ReleaseNotes21 for 2.1]
  * [wiki:ReleaseNotes20 for 2.0]
  * [wiki:ReleaseNotes19 for 1.9]
  * [wiki:ReleaseNotes18 for 1.8]
  * [wiki:ReleaseNotes17 for 1.7]
  * [wiki:ReleaseNotes16 for 1.6]
  * [wiki:ReleaseNotes15 for 1.5]
  * [wiki:ReleaseNotes14 for 1.4]
  * [wiki:ReleaseNotes13 for 1.3]
  * [wiki:ReleaseNotes12 for 1.2]
  * [wiki:ReleaseNotes11 for 1.1]
  * [wiki:ReleaseNotes10 for 1.0]
  * [wiki:ReleaseNotes08 for 0.8]
  * [wiki:ReleaseNotes07 for 0.7]
  * [wiki:ReleaseNotes06 for 0.6]
  * [wiki:ReleaseNotes05 for 0.5]
=== Wiki ===
  * [wiki:WikiSnippetsAndTemplates Snippets and Templates]
  * [wiki:WikiPageIndex Wiki Page Index]
  * [wiki:WikiMacroList Wiki Macro List]
  * [wiki:Meta-WikiPage Meta-Wiki Page]
     * [wiki:Meta-WikiPage#UserDocumentationRequests User Documentation Requests]
     * [wiki:Meta-WikiPage#DocumentationMarkedasWorkinProgressTodoList Documentation Marked as Work in Progress/Todo List]
     * [wiki:Meta-WikiPage#UserDocsRoadMap User Docs Road Map]
=== Licensing and Copyright ===
  * [source:/LICENSE License]
  * Copyright