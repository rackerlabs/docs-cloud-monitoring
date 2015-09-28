.. _get-disk-information:

Get disk information
^^^^^^^^^^^^^^^^^^^^
.. code::

    GET /agents/{agentId}/host_info/disks

Get information about the disks available on the host.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request completed.   |
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

.. note:: This operation does not accept a request body.

Response
""""""""
**Example Get disk information: JSON response**

.. code::

   {
       "timestamp": 1354039239737,
       "info": [
           {
               "read_bytes": 213685248,
               "reads": 23758,
               "rtime": 18160,
               "write_bytes": 8399753216,
               "writes": 2056309,
               "wtime": 3341340,
               "time": 458360,
               "name": "/"
           },
           {
               "read_bytes": 22974464,
               "reads": 899,
               "rtime": 440,
               "write_bytes": 15360,
               "writes": 8,
               "time": 400,
               "name": "/boot"
           }
       ]
   }
