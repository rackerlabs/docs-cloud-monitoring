================================================================
Cloud Monitoring release notes v1.6, June 16, 2014 
================================================================


These release notes correspond to a New Feature release of Cloud
Monitoring.

**New Features**

-  PagerDuty notification type is now fully documented. The new
   PagerDuty notification type allows you to use PagerDuty to receive
   notifications via a page. For details, see `PagerDuty notification
   type <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#pagerduty-notification-type>`_
   and `Cloud Monitoring Adds PagerDuty
   Integration <http://developer.rackspace.com/blog/cloud-monitoring-adds-pagerduty-integration.html>`__
   blog post.

-  Customer's Welcome Mail. Monitoring now sends a welcome email to the
   configured technical contacts with references on frequently used
   monitoring features.

**Resolved Issues**

-  Agent: Stable package bump to 1.0.0-7, the first of the 1.0 series.
   This fixed Lua crash dump uploading, and enabled Windows plugin
   scripts to be written in Batch or Powershell. For details, see `Cloud
   Monitoring Adds Server Monitoring Graphs and
   More <http://www.rackspace.com/blog/cloud-monitoring-adds-server-monitoring-graphs-and-more>`__
   blog post.

-  Agent: Stable package bump to 1.0.0-8, fixes the path to agent
   plugins on Windows. The plugin path for Windows is C:\\Program
   Files\\Rackspace Monitoring\\plugins.

-  Agent: Stable package bump to 1.0.0-60, corrects an error running
   plugins that use Windows Powershell  when there are spaces in the
   path.

-  The ``check limit`` and the ``alarm limit`` for accounts is now 1000
   (increased from 200).

-  Added note to the Developer's Guide that the maximum limit for
   ``consecutiveCount`` is five (5).

-  Several minor bug fixes and reliability improvements.

**Documentation**

-  Try some simple monitoring exercises in the Rackspace Cloud
   Monitoring Getting Started Guide at:

   http://docs.rackspace.com/cm/api/v1.0/cm-getting-started/content/Introduction.html.

-  Get reference information and examples for all endpoints in the
   Rackspace Cloud Monitoring Developers Guide at:

   https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#developer-guide.

**Talk to Us**

Do you have questions about Rackspace Cloud Monitoring? Would you like
to give us feedback on how we're doing?

-  Join us in our chat room at: Freenode IRC at #cloudmonitoring

   Or just click the following link:

   `Webchat <http://webchat.freenode.net?channels=cloudmonitoring&uio=d4>`__

-  You can also provide feedback using our feedback form:

   `Product Feedback
   Forum <http://feedback.rackspacecloud.com/forums/71021-product-feedback/category/41927-cloud-monitoring>`__

-  Get support:

   `File a ticket here (managed customers
   only) <https://manage.rackspacecloud.com/Tickets/YourTickets.do>`__

   `Rackspace Support site <http://support.rackspace.com/>`__
