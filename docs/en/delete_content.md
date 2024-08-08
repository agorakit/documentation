# Deleting content
Deleting content on Agorakit follows a procedure that allows us to respond to various imperatives:

- everyone's right to delete his or her productions
- the right to change one's mind within a certain period of time
- the right to change one's mind for a certain period of time
- to keep collective contributions in the event of a participant's departure.


When content is deleted, it is marked as deleted in the database and no longer appears. An instance administrator can put deleted content back online by going to the "admin > retrieve content" menu.

Content marked as deleted is permanently deleted (physically) from the database after 30 days. It is no longer possible to recover content after this period.


# User account deletion
If a user decides to delete their account, they can choose to : 

- anonymize their content (all content is transferred to an anonymous user)
- request that all their content be deleted.

Discussions with comments are in all cases assigned to the anonymous user, so as not to lose the contributions of other users. 
It is not possible to individually delete a thread with comments.

A user who is the sole administrator of a group cannot leave the group.


# Restoring a deleted item
An instance administrator can restore any content deleted during the retention period (30 days by default). Simply go to `Admin > settings > recover content` and select the item(s) to be restored.

# Cleaning the database
If Agorakit is installed correctly (with recurring cron jobs), the database will be automatically cleaned to comply with the above.
The number of days of data retention before final deletion is configurable and set at 30 by default.