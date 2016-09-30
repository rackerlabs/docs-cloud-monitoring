v1.2, May 10, 2012
~~~~~~~~~~~~~~~~~~

These release notes correspond to the post-Early Access release of
Rackspace Monitoring.

What's new
----------

- You can test execute an existing check. This feature enables you to execute
  a check like the traditional test check, but on a check that is already
  running. This will not actually execute the new check in the same check
  context; it executes in a new context.

- You can now get a list of alarm recipes with templating capabilities. See
  `Alarm Examples <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#document-api-operations/alarm-example-operations>`__.

- You can now delete an entity and have the deletion cascade to all of the
  associated checks and alarms in the system. As a result, you can deprovision
  monitors quickly and easily without having to manually make the deletions.

- You can type check alarms so that you can receive alerts if you set up an
  incorrect alarm, or if an alarm does not behave as expected. The alarm also
  validates that all the metrics you are checking are present, and if they are
  not present, it automatically changes the alarm state to CRITICAL.

- More collector infrastructure was added in the IAD region.

- A metadata field was added on the check type.


Resolved issues
----------------

- Fixed a defect in the networking partitioning logic that leads to more
  consistent operation

- Fixed missing version parameter in next href

- Fixed banner match to be more consistent

- Removed the ability to use duplicate monitoring zones


Known issues
--------------

Alarm states have a race condition. During replay it’s possible to
unintentionally store duplicates.
