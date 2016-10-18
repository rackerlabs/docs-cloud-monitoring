v1.8, August 13, 2014
~~~~~~~~~~~~~~~~~~~~~

These release notes correspond to a new-feature release of Rackspace Monitoring.

What's new
----------

- An `SMS notification type <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#sms-notification-type>`__
  is now available. This notification type enables Rackspace Monitoring users
  to receive notifications on an SMS-enabled mobile phone.

This API-only feature is available globally without regard to region.

- A `Windows performance check type <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#agent-windows-perfos>`__
  is now available. This new check type, **agent.windows_perfos**, provides
  metrics on Windows OS performance.

This API-only feature is available globally without regard to region.

- Service level names have changed:

  - The Infrastructure service level has changed to the Managed Infrastructure
    service level.

  - The Managed Cloud service level has changed to the Managed Operations
    service level.


Resolved issues
~~~~~~~~~~~~~~~~~~

- Fixed a crash on Linux if the PID file could not be read.

- Upgraded OpenSSL to 1.0.1i.

- Added an agent host_info_type message to list available host_info types.

- Added host info messages for sysctl and date for WALDO.

- Added new host info type messages and error responses.

- Implemented fixes for various integration tests (XenServer).

- Implemented a CentOS 7 (or systemd based Linux OS) packaging fix.

- Implemented a fix to the non-cryptographic RNG used for mostly reconnect
  logic. It was not seeded, leading to agents to connect at similar times.

- Fixed crash issue for Windows logging.

- Implemented fix for authorization timeouts and reconnects.

- Implemented cleanup and a bug fix for the DNS module in Luvit that caused
  the agent to crash.

- Added support for CentOS 7.

- Added support for server-side monitoring configuration.

- Made the file related to the server-side monitoring configuration available
  as part of the monitoring API response.

- Added a formal link for the Windows 64-bit installer.

- Made latest agent version available through
  http://stable.packages.cloudmonitoring.rackspace.com/VERSION.

- Implemented several minor bug fixes and reliability improvements.


Known issues
------------

|no changes|
