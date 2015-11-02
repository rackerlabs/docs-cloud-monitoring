v1.7, July 03, 2014 
------------------------

These release notes correspond to a New Feature release of Cloud
Monitoring.

What's new
~~~~~~~~~~~~~

-  Server-side configuration is now available. For details, see `Install
   and Configure section of the Cloud Monitoring Getting Started
   Guide </cm/api/v1.0/cm-getting-started/content/install-configure.html#agent-config-file>`__.

   Server-side configuration allows checks and alarms to be configured
   using a YAML file. Users must update their monitoring agent to take
   advantage of this new feature.

   This is an API-only feature that is available globally without regard
   to region.

Resolved issues
~~~~~~~~~~~~~~~~~~~~

-  Agent: Stable package bump to 1.0.0-68. June 27th, 2014. This version
   contains several fixes and enhancements:

   -  Fixes a race condition in the upcoming Server-Side agent
      configuration feature.

   -  Adds the server-side configuration directory during installation.

   -  Small logging adjustments for easier reading.

Documentation issues
~~~~~~~~~~~~~~~~~~~~~~~~

-  Fixed incorrect example and text for `List Agent Check Targets
   section <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#list-agent-check-targets>`__
   in the Cloud Monitoring Developer's Guide.

-  Several minor bug fixes and reliability improvements.
