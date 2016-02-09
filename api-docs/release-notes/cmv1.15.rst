v1.15, August 15, 2015 
-------------------------

These release notes correspond to a new-feature release of Rackspace Monitoring.

What's new
~~~~~~~~~~~~

|no changes|


Resolved issues
~~~~~~~~~~~~~~~~~~~

The following agent-specific changes were made:

•	Fixed a bug in the socket timeout logic found for service net monitoring agents (including DBaaS).

•	Fixed a bug on service net reconnects.

• Improved the hostinfo infrastructure for future releases.

• Updated various components within Luvit for improved stability.

• Added fixes for hostinfo and disabling prelink on RPM systems.

• Added a fix for the RPM packaging for the previous 2.1.16 release.

• Fixed an issue with Ubuntu 15.04 and systemd registration across reboots.

• Upgraded an underlying library (libuv) that the agent uses for asynchronous I/O operations. There was a regression in this library that could potentially cause performance issues with file system operations.


Known issues
~~~~~~~~~~~~~~~~~~~

|no changes|
