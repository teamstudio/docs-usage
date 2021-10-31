# Scanning Servers

## Manual Scans
Usage Auditor can be run manually, by clicking **Scan Now** in the left-hand navigator of the Usage Auditor application. Usage Auditor will scan for activity since the last time a scan was run; or all available activity if a scan has not yet been run.

Usage Auditor scans all enabled target servers. See [Configuring Usage Auditor](configuring.md) for details.

Manual scanning is helpful for getting started with a new installation, testing configurations, and troubleshooting. 
 
## Scheduled Scanning
Once Usage Auditor is set up, local scheduled scanning can be enabled to update statistics daily.

To enable scheduled scanning on a workstation with a Notes client installed, the Notes client preference "Enable scheduled local agents" must be set.

The scheduled scan can be enabled via the **Agent Settings** action in the **Admin -> Configuration** view.

Once the schedule has been enabled and a scan time chosen, saving this document will attempt to enable the **Scheduler** agent, which will initiate the scan process.

Enabling logging in the scheduling settings is helpful to confirm that the locally scheduled agent is running, but should be disabled once scheduled runs are established to reduce the number of log documents created.

## Data Collection
Teamstudio Usage Auditor uses information collected by IBM Domino Activity Logging to keep track of usage and provide an overview of the level of usage for each application on each monitored server.

Domino’s Activity Logging records information as “events” related to certain activities, such as opening a Notes session, opening a database, and so on.

Usage Auditor tracks running totals for events related to Notes Client, HTTP (web browser), and Agent access to applications. The event data for these types of events isn’t homogenous; a single event does not necessarily represent a single database-open action, or a single document read or written, nor are the counts generated identical between access methods.

The goal of Usage Auditor is to provide insight into which applications are used heavily and by whom. Usage Auditor does not attempt to interpret these events; it reports on event counts. As a result, a single database-open action may generate multiple hit counts, and Notes access will likely produce fewer counts than web access due to the nature of HTTP requests and how Domino tracks them.  The summary information generated from this process provides an accurate picture of the relative usage of applications within each access type.