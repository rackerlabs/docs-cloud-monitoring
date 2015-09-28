.. _authentication-ovw:

Authentication
~~~~~~~~~~~~~~~~~

Every REST request against the Rackspace Cloud Monitoring API requires
the inclusion of a specific authorization token, supplied by the
``X-Auth-Token`` HTTP header. You obtain this token by first using the
Rackspace Cloud Identity Service and supplying a valid Rackspace account
username and API access key.

The Rackspace Cloud Identity Service serves as the entry point to all
Rackspace Cloud APIs and is itself a RESTful web service. For a complete
discussion of authentication, see `Cloud Identity Client Developer
Guide <http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide/content/Overview-d1e65.html>`__.

Rackspace Cloud Identity Service endpoints
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You can use the Rackspace Cloud Identity authentication endpoints from
version 1.1 or version 2.0. The legacy v1.1 API endpoint only supports
authentication services, but you can use tokens from version 1.1 in
version 2.0 API calls.

..  note:: 
      If your Rackspace Cloud account requires multi-factor authentication,
      you can only authenticate with Identity API version 2.0 or later.

+------------+--------------------------------+---------------------------------+
| Resource   | V2.0                           | V1.0                            |
+============+================================+=================================+
| Global     | https://identity.api.rackspace | https://identity.api.rackspacec |
| endpoint   | cloud.com/v2.0                 | loud.com/v1.1                   |
+------------+--------------------------------+---------------------------------+
| Documentat | `Cloud Identity Client         | `Cloud Authentication Client    |
| ion        | Developer Guide - API          | Developer Guide - API           |
|            | v2.0 <http://docs.rackspace.co | v1.1 <http://docs.rackspace.com |
|            | m/auth/api/v2.0/auth-client-de | /auth/api/v1.1/auth-client-devg |
|            | vguide/content/QuickStart-000. | uide/content/index.html>`__     |
|            | html>`__                       |                                 |
+------------+--------------------------------+---------------------------------+

In response to valid credentials, an authentication request to the Cloud
Identity Service returns an authentication token and a service catalog
that contains a list of all services and endpoints available for this
token. Because the authentication token expires after 24 hours, you must
generate a new token once a day.



Retrieving the authentication token
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

See the *Rackspace Cloud Identity Guide* for information about how to retrieve the 
authentication, annotated request and response available. request and response format and 
parameters. 