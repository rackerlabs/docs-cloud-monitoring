==================================================================
Cloud Monitoring release notes v1.8, August 13, 2014 
==================================================================

These release notes correspond to a New Feature release of Cloud
Monitoring.

**New Features**

-  SMS notification type is now available. For details, see the `SMS
   notification type
   section <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#sms-notification-type>`__
   of the Cloud Monitoring Developer's Guide.

   SMS notification type allows Cloud Monitoring users to receive
   notifications on an SMS-enabled mobile phone.

   This is an API-only feature that is available globally without regard
   to region.

-  Windows operating system performance check type is now available. For
   details, see the `agent.windows\_perfos
   section <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#agent-windows-perfos>`__
   of the Cloud Monitoring Developer's Guide.

   This new check type, agent.windows\_perfos, provides metrics on
   Windows operating system performance.

   This is an API-only feature that is available globally without regard
   to region.

-  The service level name for Infrastructure Service Level has been
   changed to Managed Infrastructure Service Level.

   The service level name for Managed Cloud Service Level has been
   changed to Managed Operations Service Level.

**Resolved Issues**

-  August 7, 2014. Agent: Stable package bump to 1.0.2-5. This releases
   a new version of the Rackspace Monitoring Agent, version 1.0.2-5.
   Changes include:

   -  Fixes a crash on Linux if the PID file cannot be read.

-  August 6, 2014. Agent: Stable package bump 1.0.2-3. This releases a
   new version of the Rackspace Monitoring Agent, version 1.0.2-3.
   Changes include:

   -  OpenSSL upgraded to 1.0.1i

   -  Agent host\_info\_type message to list available host\_info types

   -  Added host info messages for sysctl and date for WALDO

-  August 4, 2014. Agent: A new version of the Rackspace Monitoring
   Agent, version 1.0.1-25. Changes include:

   -  New host info type messages and error responses

   -  Fixes for various integration tests (xenserver)

-  July 25, 2014. Agent: Stable package bump to 1.0.1-14. This is a
   minor bump for a Centos 7 (or systemd based Linux OS) packaging fix.

-  July 24, 2014. Agent: Stable package bump to 1.0.1-8. This version
   contains a fix to the non-cryptographic RNG used for mostly reconnect
   logic. It was not seeded leading to agents to connect at similar
   times.

-  July 22, 2014. Agent: Stable package bump to 1.0.1-6. This minor
   version bump contains a couple fixes:

   -  Crash fix for Windows logging.

   -  Fix for authorization timeouts and reconnects.

-  July 15, 2014. Agent: Stable package bump to 1.0.0-75. This version
   of the cloud monitoring agent includes minor bug fixes. Changes
   include:

   -  Cleanup and a bug fix for the DNS module in Luvit that caused the
      agent to crash.

   -  CentOS 7 support.

   -  Server-side monitoring configuration support.

   -  The file related to the server-side monitoring configuration is
      submitted, stored and available as part of the monitoring API
      response.

   -  Formal link for Windows 64-bit installer.

   -  The latest agent version is now available through
      URL:http://stable.packages.cloudmonitoring.rackspace.com/VERSION.

-  Several minor bug fixes and reliability improvements.

**Documentation**

-  Try some simple monitoring exercises in the Rackspace Cloud
   Monitoring Getting Started Guide at:

   http://docs.rackspace.com/cm/api/v1.0/cm-getting-started/content/Introduction.html.

-  Get reference information and examples for all endpoints in the
   Rackspace Cloud Monitoring Developers Guide at:

	https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#developer-guide

-  To see all the Rackspace API operations in one place, go
   to\ `api.rackspace.com <http://api.rackspace.com/>`__. Use the links
   on the left to see the different product API references.

-  To see the Cloud Monitoring API operations per language, view
   the\ `Quick Start for Cloud
   Monitoring <https://developer.rackspace.com/docs/cloud-monitoring/getting-started/>`__.
   Use the tabs at the top to see the different supported languages.

**Talk to Us**

Do you have questions about Rackspace Cloud Monitoring? Would you like
to give us feedback on how we're doing?

-  Join us in our chat room at: Freenode IRC at #cloudmonitoring

   Or just click the following link:

   `Webchat <https://webchat.freenode.net?channels=cloudmonitoring&uio=d4>`__

-  You can also provide feedback using our feedback form:

   `Product Feedback
   Forum <https://rackspace.uservoice.com/forums/71021-product-feedback>`__

-  Get support:

   `File a ticket here (managed customers
   only) <https://manage.rackspacecloud.com/Tickets/YourTickets.do>`__

   `Rackspace Support site <http://support.rackspace.com/>`__
