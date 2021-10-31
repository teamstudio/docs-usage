# Overview

## Configuration
Usage Auditor is configured by creating Server Configuration documents that define the target servers for usage collection, and contain additional settings that control the collection and reporting process.

Once Server Configurations have been created, scans can be run either manually or via scheduled agent to collect usage data.

For more information on configuration, see [Configuring Usage Auditor](configuring.md).
 
## Running Usage Auditor
Usage Auditor can be run manually, by clicking **Manual Scan** in the left-hand navigator of the Usage Auditor application, and choosing a time period. Usage Auditor will only record activity that is newer than the last recorded activity, so if all available activity is desired, choose that period for the first run. Re-running a period (such as Today) will add only new activity to the reports.

Manual scanning is helpful for getting started with a new installation, testing configurations, and troubleshooting.  
Once Usage Auditor is set up, local scheduled scanning can be enabled to update statistics daily.

For more information on scanning, see [Scanning Servers](scanning.md).
 
## Viewing results
Once Usage Auditor has been configured and data collected, you can browse the usage reports for Databases and Users in the Usage Auditor application. For an introduction to the statistics collected, see [Viewing Usage Statistics](viewing.md).
