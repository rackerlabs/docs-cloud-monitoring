.. _service-access:

========================
Service access endpoints
========================

For Rackspace Monitoring, use the following endpoint to access the API.
Replace the ``$TENANT_ID`` variable with your Rackspace Cloud account number
which is available from the :ref:`Cloud Control Panel <get-credentials>`.

``https://monitoring.api.rackspacecloud.com/v1.0/$TENANT_ID``

You can find the complete URI to access the |apiservice| in the service catalog
that is returned in the :ref:`authentication response <review-auth-resp>`.
Search the catalog for the service name, ``rax:monitor`` . Then copy the URI
from the ``publicURL`` field included in the service information.
