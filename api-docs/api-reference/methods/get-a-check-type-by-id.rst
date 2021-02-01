.. _get-a-check-type-by-id:

Get a check type by ID
~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /check_types/{checkTypeId}

Retrieve information for a single check type.

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

**Example Get check type by ID: JSON response**

.. code::

   {
       "id": "remote.dns",
       "category": "remote",
       "type": "remote",
       "fields": [
           {
               "name": "port",
               "description": "Port number (default: 53)",
               "optional": true
           },
           {
               "name": "query",
               "description": "DNS Query",
               "optional": false
           },
           {
               "name": "record_type",
               "description": "DNS Record Type",
               "optional": false
           }
       ]
   }
