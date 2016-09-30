.. _get-information-about-host-users:

Get information about host users
--------------------------------

.. code::

    GET /agents/{agentId}/host_info/who

Get information on users who are logged into the host.

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
^^^^^^^

The following table shows the header parameters for the request:

+-----------------+----------------+-----------------------------------------------+
|Name             |Type            |Description                                    |
+=================+================+===============================================+
|X-Auth-Token     |String          |A valid authentication token with              |
|                 |*(Required)*    |administrative access. For details, see        |
|                 |                |:ref:`Get your credentials <get-credentials>`  |
+-----------------+----------------+-----------------------------------------------+

.. note:: This operation does not accept a request body.

Response
^^^^^^^^

**Example Get information about host users: JSON response**

.. code::

   {
       "timestamp": 1354124700975,
       "info": [
           {
               "user": "testuser",
               "device": "tty1",
               "time": 1353953846
           },
           {
               "user": "testuser",
               "device": "pts/2",
               "time": 1354117532,
               "host": "192.168.95.1"
           },
           {
               "user": "testuser",
               "device": "pts/3",
               "time": 1354124463,
               "host": "comp8dv7m.local"
           },
           {
               "user": "testuser",
               "device": "pts/4",
               "time": 1354124661,
               "host": "comp8dv7m.local"
           }
       ]
   }
