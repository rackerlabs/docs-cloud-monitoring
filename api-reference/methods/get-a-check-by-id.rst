.. _get-a-check-by-id:

Get a check by ID
~~~~~~~~~~~~~~~~~~

.. code::

    GET /entities/{entityId}/checks/{checkId}

Use this operation to retrieve the current state of a check.

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
|404                       |Not Found                |The URL, entity, or      |
|                          |                         |account requested is not |
|                          |                         |found in the system.     |
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The response body is too |
|                          |                         |large.                   |
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
-------

The following table shows the header parameters for the request:

+-----------------+----------------+-----------------------------------------------+
|Name             |Type            |Description                                    |
+=================+================+===============================================+
|X-Auth-Token     |String          |A valid authentication token with              |
|                 |*(Required)*    |administrative access. For details, see        |
|                 |                |:ref:`Get your credentials <get-credentials>`  |
+-----------------+----------------+-----------------------------------------------+

.. note::

   This operation does not accept a request body.

Response
--------

**Example Get check by ID: JSON response**

.. code::

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
