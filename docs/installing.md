# Installing Teamstudio Usage

## System Requirements
Teamstudio Usage installs onto a workstation. There is no server component, although you will need to ensure that each server is configured correctly as described below.

## Workstation Requirements
Teamstudio Usage requires a 64 bit version of Windows. Supported versions are

|Product|Version|
|---|---|
|Windows 10|1607+|
|Windows 11|All versions|

In order to scan servers, you also need

* A Notes client install, version 8.5 or higher (version 10 or higher strongly recommended). Both 32 and 64 bit Notes client versions are supported
* A Notes ID with the necessary permissions to access the servers being scanned

## Server Requirements
### ACL
For each server that you will scan, the ID that you plan to use with Teamstudio Usage needs to have reader or above access to

* catalog.nsf
* log.nsf
* names.nsf

### Activity Logging
Domino servers do not collect detailed usage information by default. This needs to be enabled on every server that you will scan.

Activity Logging can be enabled on the *Server Configuration* document in the Domino Directory database. Teamstudio Usage reads the following activity streams:

* Domino.Notes.Database
* Domino.AGENT
* Domino.HTTP

<figure markdown="1">
  ![Activity Logging](img/activitylogging.png)
</figure>

If you have already enabled Activity Logging for the activity streams above, Usage will pick up any activity information that has already been stored during its first scan. Otherwise, activity information will be available from the point when Activity Logging was enabled.

## Installation

Once you have a workstation that meets the requirements, and have configured each server appropriately, you can download and install the latest version of Teamstudio Usage from [teamstudio.com](https://www.teamstudio.com/downloads). The installer will install the program files and you can then proceed to launch the program and enter your license details. You can then continue to [Configuration](configuration.md).
