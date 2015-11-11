v1.1, March 28, 2012 
-----------------------

These release notes correspond to the Early Access release of Cloud Monitoring.

What's new
~~~~~~~~~~~~

•	You can test execute a notification. This makes it easy to execute test checks and verify that you’ll receive the payload. You can also test existing notifications.

•	Support has been added for JSONP for retrieval in the API. This gives you the tools to access the API from the browser directly.

•	Rate limiting and the time window of the rate limiting are now exposed to you through headers. This helps us with transparency and lets you know when you’re getting close to reaching your account rate limits.

•	An email notification type has been added so that you can receive email on your alerts.

•	Alarm History has been renamed to Alarm Notification History.

•	A key-value hash to facilitate multiple body matches is supported.

•	Previous state has been added to the webhook payload.

•	Audits now expose the tenant ID.

•	HTTP CORS headers have been added so that you can now do cross-domain requests.

•	The notification history log and the alarm change log have been unified.

•	Support dealing with time ordered mixed results has been improved.

•	Type checking for the alarm subsystem has been improved.

•	Detection for missing metrics has been added, as well as automatically outputting a failed state when detected.


Resolved issues
~~~~~~~~~~~~~~~~~

•	Fixed hashing method to prevent a collector affinity

•	Improved the location header returned so it works in nonstandard port setups

•	Added previous state to the webhook field

•	Added a label to the alarm object

•	Unified the language around the different states in the system

Known issues
~~~~~~~~~~~~~~~~~~~

|no changes|
