v1.5, March 31, 2014 
-------------------------

These release notes correspond to a New Feature release of Cloud
Monitoring.

What's new
~~~~~~~~~~~

-  Added a new “suppressions” feature, which enables you to suspend
   monitoring alarms for set periods of time. See
   `Suppressions <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#suppressions>`__.

Resolved issues
~~~~~~~~~~~~~~~~

-  Many minor bug fixes and reliability improvements.

Documentation issues
~~~~~~~~~~~~~~~~~~~~~~~~~

-  Clarified the descriptions of the alert policies to include how the
   polling window affects the alarm state. See `Alert Policies
   (Consistency
   Level) <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#alarm-language>`__.

-  Added note to the effect that hop numbers in the response that are
   repeated indicate more than one hop at the same juncture (packet
   split).

-  Added explanation of the agent connections GUID attribute (it is a
   string that does not always conform to GUID formats).
