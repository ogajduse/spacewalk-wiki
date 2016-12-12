[[TOC]]

= Contribute =

== Coding == #coding

Are you familiar with Python, Java or Perl? Look at some [https://bugzilla.redhat.com/buglist.cgi?query_format=advanced&bug_status=NEW&product=Spacewalk reported bugs] and 
pick up one. Assign it to yourself and start working on it. When you are done send us [PatchProcess a pull request].
Did not find anything interesting for you? Check [BrainBox brainbox] or come up with your own idea.

Did you write some useful script which uses [ApiDocs Spacewalk API]? Share it with the others!

== Testing == #testing

Just use Spacewalk and report any bugs you find.

Go through [https://bugzilla.redhat.com/buglist.cgi?bug_status=NEW&product=Spacewalk&query_format=advanced&order=bug_id&query_based_on= bug list] and test older bugs whether they are still valid. Sometimes bug is fixed as a side effect of other fix. You may find such case and close the bug as CURRENTRELEASE without any work!

== Documentation == #docs

A lot of Spacewalk programs or configuration files do not have a manual page. Do you want to write it?

We need general documentation of Spacewalk. You did not find documentation for the task you are currently doing? Just create a new wiki page and document what it is you did.
Some existing documentation is outdated and you may review it and update it.

Although we have some [http://www.redhat.com/spacewalk/documentation/ documentation], we still have wide areas undocumented. Just start reading code and document it. We use [http://epydoc.sourceforge.net/manual-docstring.html epydoc] style for python and Javadoc for Java. The documentation is inline in code. So send result as [PatchProcess a pull request]. This is the best start if you want to start coding, but you are not familiar with our code base.

== Help others == #mentor

Or you can just hang on [WikiStart#Communication IRC or mailing list] and try to answer questions others may have.

== Translations == #translate

Our translations live in Fedora's Zanata instance (as of 2014-DEC). We have two projects:

 * [https://fedora.zanata.org/project/view/spacewalk-other Spacewalk Backend] - for the python/client gettext translations
 * [https://fedora.zanata.org/project/view/spacewalk-frontend Spacewalk Web UI] - for the Java XLIFF translations

In each project, you'll see locked versions for each release of Spacewalk, and a '''{{{master}}}''' version. When a new release is prepared, a new version is cloned from '''{{{master}}}''' and locked.
Any translations can be added to the '''{{{master}}}''' version.

Feel free to pick a language and translate away!

== Money == #cash

We could not accept any money directly. But since Spacewalk is heavily sponsored by [http://www.redhat.com/ Red Hat], if you buy Red Hat Satellite, you directly support development of Spacewalk.