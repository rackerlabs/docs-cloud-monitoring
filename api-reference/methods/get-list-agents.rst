.. _list-agents:

List agents
-----------
.. code::

    GET /agents

This operation lists the Agent IDs that have been connected to your
account and when they were last connected. If an agent ID does
not connect to the account for 30 days, the agent ID is automatically
deleted from this list. Time is shown in Coordinated Universal
Time (UTC) as the number of milliseconds that have elapsed
since January 1, 1970.

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
**Example List agents: JSON response**

.. code::

   {
       "values": [
           {
               "id": "00-agent.example.com",
               "last_connected": 1334685407
           },
           {
               "id": "i-need-a-new-agent.example.com",
               "last_connected": 1334685407
           }
       ],
       "metadata": {
           "count": 2,
           "limit": 50,
           "marker": null,
           "next_marker": null,
           "next_href": null
       }
   }
