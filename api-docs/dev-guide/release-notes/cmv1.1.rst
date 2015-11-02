v1.1, March 28, 2012 
-----------------------

These release notes correspond to the EAP for Rackspace Cloud
Monitoring.

What's new
~~~~~~~~~~~~

This release includes the following updates:

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

Enhancements
^^^^^^^^^^^^^

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


Resolved issues
~~~~~~~~~~~~~~~~~

-  Fixed hashing method to prevent a collector affinity.

-  Improved the location header returned so it works in non-standard
   port setups.

-  Added previous state to the webhook field.

-  Added a label to the alarm object.

-  Unified the language around the different states in the system.
