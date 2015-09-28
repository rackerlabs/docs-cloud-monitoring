.. _create-a-check:

Create a check
^^^^^^^^^^^^^^
.. code::

    POST /entities/{entityId}/checks

Create a new check in the monitoring system by using a valid set
of attributes from the `checks attributes
<http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/service-checks.html>`__ table.
For a tutorial on creating some basic checks,
see `Create checks
<http://docs.rackspace.com/cm/api/v1.0/cm-getting-started/content/concepts-tutorial-create-checks.html>`__
in the Rackspace Cloud Monitoring Getting Started Guide.

A newly-created check does not trigger notifications until you
`create an alarm <http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/service-alarms.html>`__
to generate notifications. You associate alarms with a single check.
You can have multiple alarms for a check, for example
"alert if an HTTPS server is not responding and if it has an invalid certificate,"
but you cannot create a single alarm and associate it with multiple checks.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Created                  |'Location' header        |
|                          |                         |contains a link to the   |
|                          |                         |newly created check.     |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad request              |The system received an   |
|                          |                         |invalid value in a       |
|                          |                         |request.                 |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |The system received a    |
|                          |                         |request from a user that |
|                          |                         |is not authenticated.    |
+--------------------------+-------------------------+-------------------------+
|403                       |Forbidden                |The system received a    |
|                          |                         |request that the user is |
|                          |                         |not authorized to make.  |
+--------------------------+-------------------------+-------------------------+
|500                       |Internal Server Error    |An unexpected condition  |
|                          |                         |was encountered.         |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The system is            |
|                          |                         |experiencing heavy load  |
|                          |                         |or another system        |
|                          |                         |failure.                 |
+--------------------------+-------------------------+-------------------------+

Request
"""""""
The following table shows the header parameters for the request:

+-----------------+----------------+-------------------------------------------+
|Name             |Type            |Description                                |
+=================+================+===========================================+
|X-Auth-Token     |String          |A valid authentication token with          |
|                 |*(Required)*    |administrative access. For details, see `  |
|                 |                |Retrieving an authentication token         |
|                 |                |<http://docs.rackspace.com/cm/api/v1.0/cm- |
|                 |                |devguide/content/general-api-info-         |
|                 |                |authentication.html#Authenticate-d1e171>`__|
+-----------------+----------------+-------------------------------------------+

**Example Create check: JSON request**

.. code::

   {
       "label": "Website check 1",
       "type": "remote.http",
       "details": {
           "url": "http://www.foo.com",
           "method": "GET"
       },
       "monitoring_zones_poll": [
           "mzA"
       ],
       "timeout": 30,
       "period": 100,
       "target_alias": "entity_ip_addresses_hash_key"
   }

Response
""""""""
This operation does not return a response body.
