= '''Developer Documentation''' =
This section contains information about developer topics.  You may also be interested in [UserDocs User Documentation] and [DownloadIt downloads].

----
[[TOC(inline)]]
----

== __Design docs__ ==
 * [wiki:Architecture] -- a quick overview of the various components in Spacewalk
 * [wiki:JavaDesign] -- design of the Java web UI.
 * [wiki:NavigationSystem Navi] -- our navigation system -- understand our own home grown navigation system used throughout the app
 * [wiki:ListTag] -- used for creating lists within the java pages   
 * [wiki:PerlStack] -- understand how the pxt layer communicates with the perl modules and mod_perl
   * [wiki:PxtOverview] -- overview explaining the rationale for building PXT
   * [wiki:PxtForDummies] -- explains how to work with PXT
 * [wiki:AclDesign] -- detailed explanation of ACLs
 * Database
   * [wiki:DatabaseGuide Development Guide]
 * [http://www.redhat.com/spacewalk/documentation/javadoc/ JavaDoc] -- Documentation of Java code
 * [wiki:PythonDocumentation] -- Documentation of python code
 * [wiki:XmlrpcHandlers] -- understand how to deal with XMLRPC handlers
 * [wiki:UnitTests] -- how to run them
 * [wiki:CodeAnalysis] -- a document going through the java packages describing what they contain and what work is needed.
 * [https://www.ohloh.net/p/spacewalk/analyses/latest CodeAnalysis] -- Analyze of code on Ohloh.net
 * [wiki:TaskoMatic] -- Document outlining what taskomatic is and what each task is used for.
 * [wiki:CobblerIntegration] - How spacewalk and cobbler interact
 * [wiki:proxy Proxy] - How Proxy works
----
== __Working with the code__ ==
 * [wiki:GitGuide Git Guide] -- how to work with Git, the source control of choice for Spacewalk
 * [http://miroslav.suchy.cz/spacewalk/gitstat/ GitStat] -- boring statistics extracted from our git repo.
 * [wiki:DevelopmentWorkstationSetup Setting up the Development environment]
 * [wiki:EclipseSetup] -- How to get eclipse running to edit/compile/junit the spacewalk-java code.
 * [wiki:PatchProcess] -- how to go about creating a new patch and submitting it to the mailing list
 * [wiki:BugHandling] -- how to commit a fix and what to do with bugzillas.
 * [wiki:ChangingSchema] -- if you need to change the Spacewalk DB schema read this
 * [wiki:CodingConventions] -- coding style and conventions used in the project
 * [wiki:TracingaPage Tracing a page] -- Follow code flow from the webUI down to the DB layer
 * [wiki:AddingPagesOverview] -- Adding a page to the Java stack
 * [wiki:Branching] -- how branches are organized in the git repo.
 * [wiki:LocalIvyRepo] -- how to create a local ivy repository
 * [wiki:CustomSerializer] -- how to create a custom serializer
 * [wiki:LogDriverSetup] -- how to enable the log4j logdriver utility to see SQL output and params used
----
== __Releasing the code__ ==
 * [wiki:ReleaseProcess] -- Process for building RPMs
 * [http://miroslav.suchy.cz/spacewalk/packages-overview/ List of packages in releases] -- including packages already in Fedora. Contains version of each package for each distribution.
 * [http://koji.spacewalkproject.org/koji/ Koji] -- Current build status.
----
== __Artwork__ ==
 * [wiki:ArtAndDesignStuff Artwork and Design resources]
----
== __Misc__ ==
 * [wiki:BrainBox Brainstorming]
 * [wiki:ContributorList Contributor List]
 * [wiki:Projects Projects] - libraries, which may be useful for others as well and for which we are upstream.