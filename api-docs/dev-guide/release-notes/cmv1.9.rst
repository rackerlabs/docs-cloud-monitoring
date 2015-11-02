v1.9, December 1, 2014 
----------------------------

These release notes correspond to a New Feature release of Cloud
Monitoring.

What's new
~~~~~~~~~~~~~~

-  Email notifications were improved to indicate when an observation was
   too old to be included in a consistency calculation.

-  In place automatic agent upgrades was released and documented.
   Starting with agent version 1.1.0-15, all installed agents will
   automatically upgrade when a new version is released. You can opt out
   of automatic upgrades. See the *Rackspace Cloud Monitoring
   Developer's Guide* for details.

-  The MySQL agent check type was released and documented. See the
   *Rackspace Cloud Monitoring Developer's Guide* for details.

Resolved issues
~~~~~~~~~~~~~~~~~~~~~~

Agent-specific
^^^^^^^^^^^^^^^^

-  November 13, 2014. Stable package bump to 1.1.0-15. A minor version
   bump to fix a memory issue in an upstream package.

-  November 4, 2014. Agent: Stable package bump to 1.1.0-14, includes
   the following fixes:

   -  Correct behavior for configuring properties with service net.

   -  Fix log rotation permissions for Redhat based systems.

-  October 27, 2014. Agent: Stable package bump to 1.1.0-5, includes the
   following fixes and enhancements:

   -  Targets for agent plugins.

   -  Returns the list of plugins.

   -  Memory leak fix in FS\_CALL.

   -  Config: Fix is custom endpoints.

   -  Windows: Fix for powershell parameter expansion.

   -  Initial in place agent upgrades support.

-  September 18, 2014. Agent: Stable package bump to 1.0.3-4. Fixes
   issue with MySQL check type.

-  September 18, 2014. Agent: Stable package bump to 1.0.3-3. Fixes fix
   capturing a socket error on connect.

-  September 14, 2014. Agent: Stable package bump to 1.0.3-0. Changes
   include:

   -  Windows MSI to install for all users by default. This fixes some
      issues with the Rackspace Monitoring Agent not showing up on
      Windows in Add/Remove programs when installed by one user and
      viewed by another.

   -  Do not close MySQL connection on query errors.

-  August 18, 2014. Agent: Stable package bump to 1.0.2-13. Changes
   include:

   -  HTTP proxy CONNECT support.

   -  Upgraded MySQL check with new metrics.

-  Several minor bug fixes and reliability improvements.
