v1.6, June 16, 2014 
~~~~~~~~~~~~~~~~~~~

These release notes correspond to a new-feature release of Rackspace
Monitoring.

What's new
----------

- The new `PagerDuty notification type <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#pagerduty-notification-type>`__
  is now fully documented. This notification type allows you to use PagerDuty
  to receive notifications via a page. For details, see
  `Rackspace Monitoring Adds PagerDuty Integration <http://developer.rackspace.com/blog/cloud-monitoring-adds-pagerduty-integration.html>`__
  blog post.

- Rackspace Monitoring now sends a welcome email to the configured technical
  contacts with references on frequently used monitoring features.

Resolved issues
---------------

- Fixed Lua crash dump uploading.

- Enabled Windows plug-in scripts to be written in Batch or PowerShell.

- Fixed the path to agent plug-ins on Windows. The plug-in path for
  Windows is ``C:\Program Files\Rackspace Monitoring\plugins``.

- Fixed an error running plug-ins that use Windows PowerShell  when there are
  spaces in the path.

- Increased the ``check limit`` and the ``alarm limit`` for accounts to 1000
  (increased from 200).

- Added note to the Developer Guide that the maximum limit for
  ``consecutiveCount`` is five.

- Made several minor bug fixes and reliability improvements.

Known issues
------------

|no changes|
