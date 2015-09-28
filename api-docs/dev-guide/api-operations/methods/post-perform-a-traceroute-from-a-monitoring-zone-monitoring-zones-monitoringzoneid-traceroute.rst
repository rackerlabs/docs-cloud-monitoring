.. _perform-a-traceroute-from-a-monitoring-zone:

Perform a traceroute from a monitoring zone
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code::

    POST /monitoring_zones/{monitoringZoneId}/traceroute

This API operation lets you run a traceroute from a monitoring zone
to a Hostname or IP address. Like all Cloud Monitoring features,
the Traceroute API is fully dual stack, supporting both IPv4 and IPv6.
The Traceroute API can be used to debug networking issues between
the Cloud Monitoring collectors and your infrastructure.

.. note:: Hop numbers can repeat, which indicates a split in the route.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |Request completed.       |
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

**Example Traceroute: JSON request**

.. code::

   {
       "target": "google.com",
       "target_resolver": "IPv4"
   }

Response
""""""""
**Example Traceroute: JSON response**

.. code::

   {
       "result": [
           {
               "number": 1,
               "rtts": [
                   3.025,
                   3.116,
                   3.189
               ],
               "ip": "50.57.208.106"
           },
           {
               "number": 2,
               "rtts": [
                   0.675,
                   0.943,
                   1.083
               ],
               "ip": "50.56.6.34"
           },
           {
               "number": 3,
               "rtts": [
                   0.558,
                   0.824
               ],
               "ip": "50.56.6.16"
           },
           {
               "number": 3,
               "rtts": [
                   0.606
               ],
               "ip": "50.56.6.18"
           },
           {
               "number": 4,
               "rtts": [
                   0.239,
                   0.252,
                   0.247
               ],
               "ip": "184.106.126.139"
           },
           {
               "number": 5,
               "rtts": [
                   3.418,
                   3.444,
                   3.453
               ],
               "ip": "69.31.110.241"
           },
           {
               "number": 6,
               "rtts": [
                   1.219,
                   1.231
               ],
               "ip": "69.31.110.249"
           },
           {
               "number": 6,
               "rtts": [
                   1.3
               ],
               "ip": "69.31.110.253"
           },
           {
               "number": 7,
               "rtts": [
                   2.463,
                   2.224,
                   2.196
               ],
               "ip": "206.223.119.21"
           },
           {
               "number": 8,
               "rtts": [
                   1.831,
                   2.041,
                   1.814
               ],
               "ip": "209.85.254.130"
           },
           {
               "number": 9,
               "rtts": [
                   2.558,
                   1.977,
                   3.105
               ],
               "ip": "72.14.237.133"
           },
           {
               "number": 10,
               "rtts": [
                   51.028
               ],
               "ip": "216.239.46.214"
           },
           {
               "number": 10,
               "rtts": [
                   29.526
               ],
               "ip": "216.239.46.216"
           },
           {
               "number": 10,
               "rtts": [
                   48.987
               ],
               "ip": "216.239.46.214"
           },
           {
               "number": 11,
               "rtts": [
                   105.6
               ],
               "ip": "216.239.46.219"
           },
           {
               "number": 11,
               "rtts": [
                   128.521
               ],
               "ip": "216.239.43.5"
           },
           {
               "number": 11,
               "rtts": [
                   105.548
               ],
               "ip": "216.239.46.219"
           },
           {
               "number": 12,
               "rtts": [
                   109.492
               ],
               "ip": "72.14.235.175"
           },
           {
               "number": 12,
               "rtts": [
                   106.523
               ],
               "ip": "72.14.235.173"
           },
           {
               "number": 12,
               "rtts": [
                   105.952
               ],
               "ip": "72.14.235.175"
           },
           {
               "number": 13,
               "rtts": [
                   106.482
               ],
               "ip": "216.239.43.233"
           },
           {
               "number": 13,
               "rtts": [
                   106.92,
                   106.681
               ],
               "ip": "209.85.253.20"
           },
           {
               "number": 14,
               "rtts": [
                   129.616
               ],
               "ip": "72.14.236.191"
           },
           {
               "number": 14,
               "rtts": [
                   106.329
               ],
               "ip": "209.85.252.83"
           },
           {
               "number": 14,
               "rtts": [
                   106.253
               ],
               "ip": "216.239.49.45"
           },
           {
               "number": 15,
               "rtts": [],
               "ip": "*"
           },
           {
               "number": 16,
               "rtts": [
                   106.101,
                   106.075,
                   106.48
               ],
               "ip": "173.194.78.139"
           }
       ]
   }
