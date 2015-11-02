==================================================================
Cloud Monitoring release notes v1.11, March 28, 2015 
==================================================================


These release notes correspond to a New Feature release of Cloud
Monitoring.

**New features**

-  List \ `Checks <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#list-checks-for-an-entity>`__ by
   List of IDs API operation endpoint

-  List \ `Alarms <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#list-alarms>`__ by
   List of IDs API operation endpoint

-  List \ `Notifications <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#list-notifications>`__ by
   List of IDs API operation endpoint

-  List \ `Notification
   plans <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#list-notification-plans>`__ by
   List of IDs API operation endpoint

-  List \ `Supressions <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#list-suppressions>`__ by
   List of IDs API operation endpoint

**Agent-specific**

-  May 29, 2015. Agent: Stable package bump to 1.1.0-86. Changes
   include:

   -  Added support for Fedora 22.

   May 27, 2015. Agent: Stable package bump to 1.1.0-85. Changes
   include:

   -  Includes a fix for: \* systemd networking dependency (notably on
      RHEL7 and Centos7 flavors).

   April 26, 2015. Agent: Stable package bump to 1.1.0-81. Changes
   include:

   -  Added support for Debian 8 (Jessie).

   April 24, 2015. Agent: Stable package bump to 1.1.0-80. Changes
   include:

   -  Trim the Monitoring ID and Monitoring Token configuration
      variables to ensure correctness.

   -  Fix the Xen Server 6 package repo.

-  April 20, 2015. Agent: Stable package bump to 1.1.0-77. Changes
   include:

   -  Small patch to support machine enumeration on newer Windows
      instances that lack the xenstore.exe binary.

-  March 26, 2015. Stable package bump to 1.1.0-71. This release has
   some significant performance changes within it, including:

   -  Check scheduling has been modified to prevent a thundering heard
      issue

   -  Garbage Collection has been changed to incrementally garbage
      collect

   -  A few parser components have been optimized to use less memory

   -  Fixed a thundering heard issue for test checks

-  March 16, 2015. Agent: Stable package bump to 1.1.0-54. Changes
   include:

   -  OpenSSL options tuning (compression and buffers)

-  March 3, 2015. Agent: Stable package bump to 1.1.0-53. Changes
   include:

   -  Memory leak fix with new connections

-  February 4, 2015. Agent: Stable package bump to 1.1.0-41. Changes
   include:

   -  A fix for an issue with the MySQL check on DBaaS (and other mysql
      instances) of not closing the connection gracefully

-  January 27, 2015. Agent: Stable package bump to 1.1.0-34. Changes
   include:

   -  An OpenSSL bump to 1.0.1L

-  January 26, 2015. Agent: Stable package bump to 1.1.0-31. Changes
   include:

   -  A fix for automatic upgrade logging post update

**Documentation**

-  Try some simple monitoring exercises in the Rackspace Cloud
   Monitoring Getting Started Guide at:

   http://docs.rackspace.com/cm/api/v1.0/cm-getting-started/content/Introduction.html.

-  Get reference information and examples for all endpoints in the
   Rackspace Cloud Monitoring Developers Guide at:

	https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#document-developer-guide

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

   `Product Feedback Forum <https://feedback.rackspace.com/>`__

-  Get support:

   `File a ticket here (managed customers
   only) <https://mycloud.rackspace.com/>`__

   `Rackspace Support site <http://support.rackspace.com/>`__
