=================================================================
Cloud Monitoring release notes v1.1, March 28, 2012 
=================================================================


These release notes correspond to the EAP for Rackspace Cloud
Monitoring.

**New Features**

-  **Test Notifications**

   Test execute a notification. This makes it easy to execute test
   checks and verify that you'll receive the payload. We also added the
   ability to test existing notifications as well.

-  **JSONP Support**

   Support for JSONP for retrieval in the API. This gives you the tools
   to access the API from the browser directly.

-  **Rate Limiting Exposed**

   We now expose rate limiting and the time window of the rate limiting
   to you through headers. This helps us with transparency and lets you
   know when you're getting close to reaching your account rate limits.

-  **Email Notifications**

   We added email as a notification type so you can receive email on
   your alerts.

**Enhancements**

-  Renamed "Alarm History" to "Alarm Notification History."

-  Now support a key-value hash to facilitate multiple body matches.

-  Added previous state to webhook payload.

-  Audits now expose the tenantId.

-  Added HTTP CORS headers so you can now do cross domain requests.

-  Unified the notification history log and the alarm change log.

-  Improved support dealing with time ordered mixed results.

-  Improved type checking for the alarm subsystem.

-  Added detection for missing metrics and automatically output a failed
   state when detected.

**Resolved Issues**

-  Fixed hashing method to prevent a collector affinity.

-  Improved the location header returned so it works in non-standard
   port setups.

-  Added previous state to the webhook field.

-  Added a label to the alarm object.

-  Unified the language around the different states in the system.

**Documentation**

-  Try some simple monitoring exercises in the Rackspace Cloud
   Monitoring Getting Started Guide at:

   http://docs.rackspace.com/cm/api/v1.0/cm-getting-started/content/Introduction.html.

-  Get reference information and examples for all endpoints in the
   Rackspace Cloud Monitoring Developers Guide at:

   https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/

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
