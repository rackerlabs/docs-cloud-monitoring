v1.9, December 1, 2014 
----------------------------

These release notes correspond to a new-feature release of Cloud Monitoring.

What's new
~~~~~~~~~~~~~~

•	Email notifications were improved to indicate when an observation was too old to be included in a consistency calculation.

•	In-place automatic agent upgrades was released and documented. Starting with agent version 1.1.0-15, all installed agents will automatically upgrade when a new version is released. You can opt out of automatic upgrades. For details, see the `Developer Guide <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/`>__

•	The MySQL agent check type was released and documented. For details, see the `Developer Guide <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/>`__.


Resolved issues
~~~~~~~~~~~~~~~~~~~~~~

The following agent-specific changes were made:

•	Fixed a memory issue in an upstream package

•	Corrected behavior for configuring properties with ServiceNet

•	Fixed log rotation permissions for Red Hat based systems

•	Added endpoint to return targets for agent plug-ins

•	Added endpoint to return the list of plug-ins

•	Fixed memory leak in FS_CALL

•	Implemented fix for custom endpoints

•	Implemented fix for PowerShell parameter expansion

•	Fixed issue with the MySQL check type

•	Fixed issue with capturing a socket error on connect

•	Added Windows MSI installation for all users by default. This fixes some issues with the Rackspace Monitoring Agent not appearing on Windows in Add/Remove programs when installed by one user and viewed by another.

•	Implemented change to not close a MySQL connection on query errors

•	Added support for HTTP proxy CONNECT

•	Upgraded MySQL check with new metrics

•	Added several minor bug fixes and reliability improvements

Known issues
~~~~~~~~~~~~~~~~~~~

|no changes|
