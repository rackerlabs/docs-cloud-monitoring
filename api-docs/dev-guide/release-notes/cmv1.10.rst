v1.10, January 23, 2015 
----------------------------


These release notes correspond to a new-feature release of Cloud Monitoring.

What's new
~~~~~~~~~~~~~~

•	A `VictorOps notification type <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#victorops-notification-type>`__ was added.

•	The entity ID is now returned in the `API response for list alarms <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#list-alarms>`__.

•	An API operation to list `entities <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#list-entities-for-an-account>`__ by account was added.


Resolved issues
~~~~~~~~~~~~~~~~~~~~~

The following agent-specific changes were made:

•	Added a new metric on Linux to show whether a networking link is up or down

•	Implemented a fix for automatic upgrades

•	Fixed a memory leak for Luvit

•	Fixed a connection memory leak

•	Added support for Fedora 21

Known issues
~~~~~~~~~~~~~~~~~~~

|no changes|
