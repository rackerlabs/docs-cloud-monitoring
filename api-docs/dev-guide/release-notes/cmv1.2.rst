===============================================================
Cloud Monitoring release notes v1.2, May 10, 2012
===============================================================

These release notes correspond to the post-EAP release of Cloud
Monitoring.

**New Features**

-  **Test an Existing Check**

   Test execute an existing check. This allows you to execute a check
   like the traditional test check, but on a check that is already
   running. This will not actually execute the new check in the same
   check context, it executes in a new context.

-  **Alarm Templates**

   Get a list of alarm recipes with templating capabilities. This helps
   kick-start your thinking on all the possible ways to leverage this
   incredibly powerful part of the monitoring system. The link to the
   API documentation is here:

   `Alarm Examples API
   Documentation <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#document-api-operations/alarm-example-operations>`__

-  **Cascading Entity Deletion**

   Delete entities and now have it cascade to all of the associated
   checks and alarms in the system. This allows you to de-provision
   monitors quickly and easily without having to manually make the

-  **Type Checking on Alarms**

   Type check alarms so you receive alerts if you set up an incorrect
   alarm, or it isn't as expected. As a bonus the alarm also validates
   all the metrics you are checking are present, if they are not
   present, it automatically changes the alarm state to CRITICAL.

**Enhancements**

-  Fixed a defect in the networking partitioning logic that leads to
   more consistent operation.

-  Added more collector infrastructure in IAD.

-  Added a meta-data field on the check type.

**Resolved Issues**

-  Alarm states have a race condition. During replay it's possible to
   unintentionally store duplicates.

-  Fix missing version parameter in next href.

-  Fix banner match to be more consistent, be present but empty if it
   didn't match.

-  Removed the ability to use duplicate monitoring zones.

**Documentation**

-  Try some simple monitoring exercises in the Rackspace Cloud
   Monitoring Getting Started Guide at:

   http://docs.rackspace.com/cm/api/v1.0/cm-getting-started/content/Introduction.html.

-  Get reference information and examples for all endpoints in the
   Rackspace Cloud Monitoring Developers Guide at:

   https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#document-developer-guide.

**Talk to Us**

Do you have questions about Rackspace Cloud Monitoring? Would you like
to give us feedback on how we're doing?

-  Join us in our chat room at: Freenode IRC at #cloudmonitoring

   Or just click the following link:

   `Webchat <http://webchat.freenode.net?channels=cloudmonitoring&uio=d4>`__

-  You can also provide feedback using our feedback form:

   `Product Feedback
   Forum <http://feedback.rackspacecloud.com/forums/71021-product-feedback/category/41927-cloud-monitoring>`__

-  Get support here:

   `File a ticket
   here <https://manage.rackspacecloud.com/Tickets/YourTickets.do>`__
