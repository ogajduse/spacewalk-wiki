# How to use software crash reporting in Spacewalk

## Overview




If you're using / have installed *abrt* ([[http://abrt.readthedocs.org/]]) on your systems registered to Spacewalk, you may take advantage
of the software crash reporting functionality provided by Spacewalk.

Software crash reporting functionality was introduced first in Spacewalk 1.8 and extended later in Spacewalk 1.9 and Spacewalk 2.0.

This functionality allows:

* your registered clients to automatically report software crashes captured by abrt directly to the Spacewalk server
* you to process the captured crashes in a centralized way
  * ability to see the software crashes that occurred on a system
  * ability to manipulate directly with the crash files captured with the crash (further processing, reporting a bug)
  * adding custom notes to a particular crash
  * ability to group similar software crashes across multiple systems in an organization
  * creating crash reports with _spacewalk-report_
## Quick start



To use the software crash reporting functionality:

1. Install _spacewalk-abrt_ package (part of Spacewalk client repository) on your client system(s). This package will install _abrt_ as its dependency. Note: neither abrt nor spacewalk-abrt are available for RHEL-5 / CentOS-5.

2. Wait for a software crash to occur or trigger a crash manually:

    $ sleep 60 &
    $ kill -s SEGV %1
    [1]+  Segmentation fault      sleep 60

3. In your webui, navigate to:

        Systems -> [desired system] -> Software -> Software Crashes

to see the list of software crashes that occurred on the registered system. Click on the particular crash to see the crash details and crash files captured for this crash report.

4. Use the following API calls to manipulate with the reported software crashes:

    system.crash.getLastReportDate()
    system.crash.getUniqueCrashCount()
    system.crash.getTotalCrashCount()
    system.crash.listSystemCrashes()
    system.crash.listSystemCrashFiles()
    system.crash.deleteCrash()
    system.crash.getCrashFileUrl()
    system.crash.getCrashFile()

Consult the API documentation for further details.
## Advanced Usage

### Crash Notes




Spacewalk 2.0 supports custom crash notes (adding / viewing / removing).

To manipulate with the crash notes in the webui, navigate to

    Systems -> [desired system] -> Software -> Software Crashes -> [desired software crash] -> Crash Notes

To manipulate with the crash notes using the API, use the following calls:

    system.crash.createCrashNote()
    system.crash.deleteCrashNote()
    system.crash.getCrashNotesForCrash()
### Similar Software Crashes



Spacewalk 2.0 allows you to see identical / similar software crashes across multiple systems in your organization.

ABRT assigns every software crash a UUID. Crashes with identical UUID may potentially indicate similar or identical software crashes.

To see the overview of software crashes that occurred in your organization grouped by their UUID, navigate to

    Systems -> Software Crash Overview

You can similarly use the following API calls to see similar / identical software crashes in your organization:

    system.crash.getCrashOverview()
    system.crash.getCrashesByUuid()
### Organization Configuration



Spacewalk allows you to configure the following crash-related settings in your organization:

* turn the crash reporting on / off
* turn the crash file upload on / off
* crash file upload size limit, i.e. the size of a single crash file that can be uploaded with every crash report 

To configure these settings in webui, navigate to:

    Admin -> | [your organization] | -> Configuration

You can also use the following API calls to configure your organization:

    org.getCrashFileSizeLimit()
    org.setCrashFileSizeLimit()
    org.isCrashReportingEnabled()
    org.setCrashReporting()
    org.isCrashfileUploadEnabled()
    org.setCrashfileUpload()
### Reporting



Spacewalk allows you to use the following crash-related reports with the _spacewalk-report_ tool:

    system-crash-count
    system-crash-details
### Unpackaged Software



If you wish to capture crashes of a software that is not packaged in RPM format (for example Adobe Reader installed from a tar.gz), you need to configure abrt to process crashes from unpackaged software:

    # grep ProcessUnpackaged /etc/abrt/abrt-action-save-package-data.conf 
    ProcessUnpackaged = yes
## Further details

### Client




The _spacewalk-abrt_ package has two important components:
1. configuration file for abrt: /etc/libreport/events.d/spacewalk.conf
2. spacewalk-abrt utility: /usr/bin/spacewalk-abrt

spacewalk-abrt package contains the following _libreport_ configuration file:


    $ cat /etc/libreport/events.d/spacewalk.conf
    
    # To be run when a new software crash occurs
    EVENT=notify
            /usr/bin/spacewalk-abrt --report $DUMP_DIR
    
    # To be run when abrt detects duplicate of already existing crash
    EVENT=notify-dup
            /usr/bin/spacewalk-abrt --update-count $DUMP_DIR
    

This configuration file instructs abrt daemon to:

* Use /usr/bin/spacewalk-abrt utility to automatically report every new crash that occurs on the system to your Spacewalk server. This is done in a fully automated fashion and ordinarilly does not require any human intervention.
* Use /usr/bin/spacewalk-abrt utility to inform the Spacewalk server an existing crash occurred again (i.e. it reports the updated crash count for an existing crash)

Should you ever need to report a crash manually, use the spacewalk-abrt utility, executed from your client system:

    # spacewalk-abrt --help
    Usage: spacewalk-abrt [options]
      Commands:
        Specify one of the commands below
    
        --report=REPORT     Upload content of the specified problem directory
        --update-count=UPDATE_COUNT
                            Update crash count for the specified problem directory
        --sync              Synchronize missing problem directories

Use --report option to report a single crash:

    # abrt-cli list
    @0
    Directory:      /var/tmp/abrt/ccpp-2013-02-28-15:48:50-8820
    count:          2
    executable:     /usr/bin/python2.7
    package:        python-2.7.3-13.fc16
    time:           Thu 28 Feb 2013 03:48:50 PM CET
    uid:            0
    
    @1
    Directory:      /var/tmp/abrt/oops-2013-02-27-14:16:03-8107-1
    count:          3
    package:        kernel
    time:           Wed 27 Feb 2013 02:16:03 PM CET
    
    @2
    Directory:      /var/tmp/abrt/ccpp-2013-02-13-14:44:49-10924
    count:          20
    executable:     /usr/bin/sleep
    package:        coreutils-8.17-7.fc16
    time:           Wed 13 Feb 2013 02:44:49 PM CET
    uid:            0
    
    @3
    Directory:      /var/tmp/abrt/libreport-2012-09-26-13:55:57-21857
    executable:     /sbin/firstboot
    package:        firstboot-18.3-1.fc16.x86_64
    time:           Wed 26 Sep 2012 07:55:57 PM CEST
    uid:            0
    # spacewalk-abrt --report /var/tmp/abrt/ccpp-2013-02-28-15:48:50-8820

Use --sync option to report all crashes that occurred on your system:

    # spacewalk-abrt --sync
### Server

#### Crash files




The crash files captured by abrt will be uploaded to your Spacewalk server for every crash report. These files can be downloaded from webui or via API. On your Spacewalk server, these crash files will be physically stored
on the file system under:

    /var/satellite/systems/$org_id/$system_id/crashes/$crash_name/