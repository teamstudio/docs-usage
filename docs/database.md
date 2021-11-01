# Database Usage Statistics

Teamstudio Usage Auditor reports the following categories of usage:

* Overall applications usage
* User-specific usage
* Agent-specific statistics
<figure markdown="1">
  ![Database Statistics](img/database.png)
</figure>
 
At each level, the total activity counts and last access dates are shown. For more detail on how activity counts are collected, see [Scanning Servers](scanning.md).

The Database document also shows information on the number of Unique Users, User Days, and if appropriate the last date on which the Users table was reset.

The Users table may be reset from time to time on Database documents for applications with a large number of users. This occurs because of size limits in Notes documents, and also affects the Unique Users count. For more information on User table resets, see below.

## Status Indicators
Usage Auditor displays visual indicators in views when certain situations have occurred during data collection and reporting:

* **!** - A single exclamation point indicates that the server was unavailable at the time of the last scan. A warning message also appears in the database document. This indicator will be cleared on the next successful scan.
* **!!** - Double exclamation points indicate that an error occurred processing statistics for the specific database. Error information is listed in the database document.
* **+** - A plus sign following the Unique Users columns indicates that the database document has been **reset** or marked **ignore**, and the actual count may be higher than indicated in the view. See the section that follows for more information in Unique Users and Resets.
 
## User Usage, Unique Users, and Resets
Usage Auditor’s focus is providing insight into the usage patterns of Domino applications to support IT decision making processes, for example, identifying unused or lightly used applications for retirement, or high use applications that require prioritization.

To provide a simple, consolidated view of databases statistics, and allow for a large number of servers and applications to be reported on in a single Usage Auditor instance, application statistics are maintained in a single document.

As a result, a limited number of user statistics can be recorded at the database level, due to the fact that Notes supports a maximum of 64K of “summary data” per document.

When the table of users stored in the Database document nears this limit it either resets the table, or ignores (stops collecting) user activity for the database, depending on the configuration options for the server being scanned.
 
## Resets
If the configuration specifies that the User table should be reset when the limit is hit, Usage Auditor will clear the table of all values, and begin tracking users again, starting with the an entry for the user’s name whose addition necessitated the reset.

If a Database document has been reset, the date of the reset is listed in the summary information.

## Ignore
If the configuration specifies that user activity should be ignored after the limit is hit, the Database document will be marked as being “ignored” and user level tracking will cease. The User table will not be updated and will be hidden. Database level counts will continue to be updated while the document is ignored, and the document can be filtered from Database views.

Databases can be manually marked as **Ignore** via **Actions > Mark selected as ‘Ignore’** action. This is useful for preventing tracking on applications, and filtering those applications from Database views.

## Unique Counts
Note that Unique Users counts are affected by reset/ignore events since they are calculated based on the User table.

When a database document has been reset, the Unique User count will reset as well, however the database document will also display the Unique User count prior to the reset. The database views will show the higher of the two counts, followed by a plus (**+**) sign, to indicate that the total unique count may be higher.

If a database is marked Ignore, either manually, or by hitting the user table limit, Unique Users will no longer be tracked; A plus (**+**) sign will be displayed following the Unique Count in views to indicate that the total unique count may be higher.

For information on configuring servers to Ignore or Reset when this limit is hit, see the section on **Cutoff Action** in [Configuring Usage Auditor](configuring.md).
 
## Removing User Activity
When database documents are selected, user activity for specific users can be removed via the **Actions > Remove User...** action. This action is helpful when you have chosen not to track a particular user's activity at the database level, and wish to remove that user's activity from database documents that include the user. For more information on disabling user tracking, see [User Usage Statistics](user.md).

When a user is removed from selected database documents, the user's activity counts are removed from the total Web Activity, Notes Activity, and Unique User counts. Other statistics, such as Total Days Used, cannot be accurately adjusted after the fact, and remain unchanged.
