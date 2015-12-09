v1.7, July 03, 2014 
------------------------

These release notes correspond to a new-feature release of Rackspace Monitoring.

What's new
~~~~~~~~~~~~~

Server-side configuration is now available. For details, see `Install and Configure section of the Cloud Monitoring Getting Started Guide </cm/api/v1.0/cm-getting-started/content/install-configure.html#agent-config-file>`__.

Server-side configuration allows checks and alarms to be configured using a YAML file. Users must update their monitoring agent to take advantage of this new feature.

This API-only feature is available globally without regard to region.

Resolved issues
~~~~~~~~~~~~~~~~~~~~

The following agent-specific changes were made:
•	Fixed a race condition in the server-side agent configuration feature

•  Added the server-side configuration directory during installation

•	 Made small logging adjustments for easier reading

•  Fixed incorrect example and text for `List Agent Check Targets
   section <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#list-agent-check-targets>`__
   in the Developer Guide.

Known issues
~~~~~~~~~~~~~~~~~~~

|no changes|
