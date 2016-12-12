[[TOC]]
= '''Spacewalk''' =
== __Latest News__ ==
[[Image(https://fedorahosted.org/spacewalk/attachment/wiki/ReleaseNotes26/26release.png?format=raw)]]
[[BR]]
=== '''Spacewalk 2.6''' was released on November 29th, 2016: ===
 * [HowToInstall Download and Install]
 * [wiki:ReleaseNotes26 Release Notes]

== __Introduction__ ==
[http://spacewalk.redhat.com/ Spacewalk] is an open source Linux systems management solution.  It allows you to:
 * Inventory your systems (hardware and software information)
 * Install and update software on your systems
 * Collect and distribute your custom software packages into manageable groups
 * Provision (Kickstart) your systems
 * Manage and deploy configuration files to your systems
 * Provision virtual guests
 * Start/stop/configure virtual guests

Spacewalk is the upstream project for the source of [http://www.redhat.com/red_hat_network/ Red Hat Satellite]. Spacewalk works with RHEL, Fedora, and other RHEL derivative distributions like CentOS, Scientific Linux, etc. Limited support for managing [wiki:RegisteringClients#Debian Debian] machines is also available. We are working on getting Spacewalk packages included in Fedora.

This wiki is primarily focused on the usage and development of Spacewalk. For a higher-level overview of Spacewalk, what it does, and for a full gallery of screenshots, please visit the [http://spacewalk.redhat.com/ Spacewalk website at redhat.com].

== __Content__ ==
The main subsections of this wiki;
 * [wiki:UserDocs User Documentation]: Learn more about how to set up and use Spacewalk
 * [wiki:DeveloperDocs Developer Documentation]: Learn how to work on and build Spacewalk, and how Spacewalk is put together.
 * [wiki:SpacewalkFaq FAQs]: Answers to your questions.
 * [wiki:Contribute How to Contribute]: Do you want to help us? Start here.
 * [wiki:DownloadIt Downloads (Source and RPMs)]: Find out how to check out the source code and get RPM releases.
 * [https://fedorahosted.org/spacewalk/roadmap Roadmap]: What are the plans for the future of Spacewalk.
 * [wiki:ReleaseProcess Release Process]: What is the process for releasing Spacewalk.
 * [wiki:BrainBox Brainbox]: Some ideas that might end up in the roadmap. Just a page to collect them.
 * [wiki:Features Features]: An index page of ideas that have graduated from the [wiki:BrainBox] to become features.

== __Communication__ ==
There are several ways to get in touch with Spacewalk developers and users:
 * Announcement list (Moderated): spacewalk-announce-list@redhat.com [https://www.redhat.com/mailman/listinfo/spacewalk-announce-list (signup)] [https://www.redhat.com/archives/spacewalk-announce-list/ (archives)]
 * User list: spacewalk-list@redhat.com [https://www.redhat.com/mailman/listinfo/spacewalk-list (signup)] [https://www.redhat.com/archives/spacewalk-list/ (archives)]
 * Developer list: spacewalk-devel@redhat.com [https://www.redhat.com/mailman/listinfo/spacewalk-devel (signup)] [https://www.redhat.com/archives/spacewalk-devel/ (archives)]
 * IRC: #spacewalk & #spacewalk-devel on [http://freenode.net/ (irc.freenode.net)]
 * Let us know about your [wiki:Installations]

== __Community__ ==
[[Image(http://farm4.static.flickr.com/3257/2594729312_4c72913c2c_m.jpg)]]

View photos from the [http://www.flickr.com/photos/mairin/sets/72157605713726653/ Spacewalk Campground] at the [http://redhat.com/summit 2008 Red Hat Summit].

[https://plus.google.com/111907808094365263361/posts G+ (Google plus)]

[https://www.facebook.com/groups/108094892955/ Facebook Spacewalk Group]
== __Need To Edit This Wiki?__ ==
You don't need to ask to be in the spacewalk account system group, that's only for commit access, see the [wiki:PatchProcess Patch Process]. To get started simply;
 * [http://admin.fedoraproject.org/accounts Get a Fedora account]: Come back and start editing.

== __Want to File a Bug/RFE?__ ==
 * [https://bugzilla.redhat.com/enter_bug.cgi?product=Spacewalk Enter a bug here]: Check if the issue already has bugzilla filed at bugzilla.redhat.com.
 * [https://bugzilla.redhat.com/query.cgi?product=Spacewalk Search for bugs here]: If it has, feel free to add yourself to Cc list of that bugzilla and add comments with more details, logs, etc.
 * [https://bugzilla.redhat.com/enter_bug.cgi?product=Spacewalk Report a new bug]: If it has not, then please report it here with all the detail you can muster.
 * [https://bugzilla.redhat.com/createaccount.cgi Get a Bugzilla account]: You will need an account in bugzilla to add comments or file new bugzillas.