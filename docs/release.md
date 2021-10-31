# Release Notes

## Teamstudio Usage Auditor 5.0.1

Teamstudio Usage Auditor 5.0.1 contains fixes and enhancements to improve the accuracy and reliability of Usage Auditor. The most significant updates include:
### Web Usage Activity
Usage Auditor 5.0.1 fixes an issue where certain server configurations failed to report web-browser activity. This release contains enhanced URL pattern matching that allows reporting of web activity regardless of the location of the server’s data directory.
### Trending
Usage Auditor 5.0.1 improves the accuracy of trending reports by generating these reports automatically when the usage data being imported switches from one month to the next. Previous versions relied on Trending being run as part of the nightly data import on a specific day of the month, which created the potential for missed months. This release also fixes an issue where, prior to Usage Auditor 5.0.1, calculations of trend data could become inaccurate after the second month of trending.
### Re-import Capability
Usage Auditor 5.0.1 can now re-generate Usage Activity reports from saved data when “Save Supporting Data” has been enabled for servers.

Re-importing clears all statistics in Usage Auditor, and then recreates the statistics based on the original activity data stored in CSV format.

Re-import can be used to apply fixes to the product to previously scanned data, as in the case of the Web Usage fix in 5.0.1. It also allows retroactive changes, such as switching between Common and Full User Name settings, or ignoring activity from certain users.

The Supporting Data view (available via View > Go To) contains documents with the CSV files that will be re-imported. Only data for periods when “Save Supporting Data” was enabled is available for re-import; however re-import is not affected by the 10 day limit (default) on server retention of activity data in the server’s log.nsf.

!!! note
    Usage statistics may change during re-import for a variety of reasons, including “Track DB Usage” being applied to the entire range of data, and changes to reporting behavior and bug fixes such as those listed below.

Backing up the Usage Auditor database prior to re-import is strongly recommended.

This feature is available via the Actions > Admin > Re-import from saved CSV data agent.

## Fixes and Enhancements
[TMS-458] - Fix issue where 5.0.0 fails to identify web usage for some server configurations
[TMS-421] - License key dialog now provides example License Number and Serial Key formats
[TMS-462] - Trending data is now generated in-line during activity import
[TMS-461] - Fix issue where trend data can become inaccurate after first 2 months of trends
[TMS-463] - Add ability to re-import usage statistics from saved "supporting files"
[TMS-465] - Fix issue where usage activity occurring in the same 100th of a second could be duplicated during re-import
[TMS-464] - Fix issue where 5.0.0 can incorrectly record "days used" due to case-sensitive db path matching
[TMS-581] - Fix issue where user lookup can fail to create a user and log an error "Item or match not found"

## Teamstudio Usage Auditor 5.0
This major feature release adds a number of significant enhancements:

* Improved performance and reliability of usage activity collection and reporting
* Scans can now be run on demand, up to the current time
* User statistics and tracking have been enhanced, user's total usage can now be viewed, and user tracking can be enabled/disabled on all/selected servers
* Redesigned User Interface improves presentation of usage statistics

### System Requirements 
Usage Auditor is supported on all all IBM-supported 32-bit configurations of Notes on running on Windows  Usage Auditor does not currently support 64-bit Domino installations; it is recommended that Usage Auditor be run on a client workstation.

### Prerequisites
Teamstudio Usage Auditor aggregates and reports on data collected by the IBM Domino server’s Activity Logging task. For more information, see the Usage Auditor online documentation topic [Installing Usage Auditor](installing.md).

### Upgrading from Prior Versions
For information on upgrading an existing installation, see the Usage Auditor online documentation topic [Installing Usage Auditor](installing.md).
