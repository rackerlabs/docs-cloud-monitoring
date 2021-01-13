v1.5, March 31, 2014 
~~~~~~~~~~~~~~~~~~~~

These release notes correspond to a new-feature release of Rackspace Monitoring.

What's new
----------

A new “suppressions” feature was added. This feature enables you to suspend
monitoring alarms for set periods of time. See
`Suppressions <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#suppressions>`__.


Resolved issues
---------------

Made many minor bug fixes and reliability improvements.

Documentation issues
--------------------

- Clarified the descriptions of the alert policies to include how the polling
  window affects the alarm state. See
  `Alert Policies (Consistency Level) <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#alarm-language>`__.

- Added note that hop numbers in the response that are repeated indicate more
  than one hop at the same juncture (packet split).

- Added explanation of the agent connections GUID attribute (it is a string
  that does not always conform to GUID formats).

Known issues
------------

|no changes|
