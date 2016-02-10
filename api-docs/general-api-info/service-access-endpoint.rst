.. service-access-endpoints

Service access endpoints
~~~~~~~~~~~~~~~~~~~~~~~~

For Rackspace Monitoring, uses the following endpoint to access the
API:

``https://monitoring.api.rackspacecloud.com/v1.0/$TENANT_ID``


Replace the $TENANT_ID with your Rackspace Cloud account number.


Your account number is returned as part of the authentication
service response, after the final '/' in the ``X-Server-Management-Url``
header. :ref:`Authentication <authentication-ovw>`
for more information.



Replace the $TENANT_ID with your Rackspace Cloud account number which is available on the
:ref:`Cloud Control Panel <auth-credentials>`.

You can find the complete URI to access the |apiservice| in the service catalog
that is returned in the :ref:`authentication response <review-auth-resp>` .
Search the catalog for the service name, ``rax:monitor`` . Then copy the URI
from the publicURL field included in the service information.
