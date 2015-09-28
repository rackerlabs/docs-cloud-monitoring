.. _list-checks-for-an-entity:

List checks for an entity
^^^^^^^^^^^^^^^^^^^^^^^^^
.. code::

    GET /entities/{entityId}/checks

Lists the checks associated with a given ``entityId``.

Use ``/checks?id=checkOneId & id=checkTwoId`` to filter the
results to only include information on the specified checks.

This operation can be paginated. For information,
see `Paginated collections
<http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/api-paginated-collections.html>`__.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request completed.   |
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

.. note:: This operation does not accept a request body.

Response
""""""""
**Example List checks for entity: JSON response**

.. code::

   {
       "values": [
           {
               "id": "chAAAA",
               "label": "Website check 1",
               "type": "remote.http",
               "details": {
                   "url": "http://www.foo.com",
                   "method": "GET",
                   "follow_redirects": true,
                   "include_body": false
               },
               "monitoring_zones_poll": [
                   "mzA"
               ],
               "timeout": 30,
               "period": 100,
               "target_alias": "entity_ip_addresses_hash_key"
           }
       ],
       "metadata": {
           "count": 1,
           "limit": 50,
           "marker": null,
           "next_marker": null,
           "next_href": null
       }
   }
