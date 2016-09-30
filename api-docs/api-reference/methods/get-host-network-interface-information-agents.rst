.. _get-host-network-interface-information:

Get host network interface information
--------------------------------------

.. code::

    GET /agents/{agentId}/host_info/network_interaces

Get information about the host network interfaces.

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
**Example Get host network interface information: JSON response**

.. code::

   {
       "timestamp": 1354038900510,
       "info": [
           {
               "name": "lo",
               "type": "Local Loopback",
               "address": "127.0.0.1",
               "netmask": "255.0.0.0",
               "address6": "::1",
               "broadcast": "0.0.0.0",
               "hwaddr": "00:00:00:00:00:00",
               "mtu": 16436,
               "rx_packets": 361762,
               "rx_bytes": 92488304,
               "tx_packets": 361762,
               "tx_bytes": 92488304,
               "flags": 73
           },
           {
               "name": "eth0",
               "type": "Ethernet",
               "address": "192.168.95.128",
               "netmask": "255.255.255.0",
               "address6": "fe80::250:56ff:fe24:bbbb",
               "broadcast": "192.168.95.255",
               "hwaddr": "00:00:00:00:00:00",
               "mtu": 1500,
               "rx_packets": 13142,
               "rx_bytes": 1838773,
               "tx_packets": 12087,
               "tx_bytes": 6282141,
               "flags": 2115
           }
       ]
   }
