v1.11, March 28, 2015 
-------------------------

These release notes correspond to a new-feature release of Rackspace Monitoring.

What's New
~~~~~~~~~~~~~

• List `checks <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#list-checks-for-an-entity>`__ for an entity

•	List `alarms <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#list-alarms>`__ for an entity

•	List `notifications <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#list-notifications>`__ for an account

•	List `notification plans <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#list-notification-plans>`__ for an account

•	List `supressions <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#list-suppressions>`__ for an account


Resolved issues
~~~~~~~~~~~~~~~~~~~

The following agent-specific changes were made:

•	Added support for Fedora 22

•	Fixed * systemd networking dependency (notably on Red Hat Enterprise Linux 7 and CentOs7)

•	Added support for Debian 8 (Jessie)

•	Trimmed the Monitoring ID and Monitoring Token configuration variables to ensure correctness

•	Fixed the Xen Server 6 package repo

•	Implemented support for machine enumeration on newer Windows instances that lack the xenstore.exe binary

•	Modified check scheduling to prevent a thundering herd issue

•	Changed garbage collection to incrementally garbage collect

•	Optimized a few parser components to use less memory

•	Fixed a thundering herd issue for test checks

•	Tuned OpenSSL options (compression and buffers)

•	Fixed memory leak with new connections

•	Fixed an issue with the MySQL check on DBaaS (and other MySQL instances) of not closing the connection gracefully

•	Upgraded OpenSSL to 1.0.1L

•	Implemented a fix for automatic upgrade logging after an update

Known issues
~~~~~~~~~~~~~~~~~~~

|no changes|
