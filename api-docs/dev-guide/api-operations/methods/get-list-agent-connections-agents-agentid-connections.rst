.. _list-agent-connections:

List agent connections
^^^^^^^^^^^^^^^^^^^^^^
.. code::

    GET /agents/{agentId}/connections

This operation lists the connections that are currently active
for an agent. Agents are connected to three monitoring zones
when operating normally.

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

+-----------------+----------------+-----------------------------------------------+
|Name             |Type            |Description                                    |
+=================+================+===============================================+
|X-Auth-Token     |String          |A valid authentication token with              |
|                 |*(Required)*    |administrative access. For details, see        |
|                 |                |:ref:`Get your credentials <auth-credentials>` |
+-----------------+----------------+-----------------------------------------------+


.. note:: This operation does not accept a request body.

Response
""""""""
**Example List agent connections: JSON response**

.. code::

   {
       "values": [
           {
               "id": "cntl4qsIbA",
               "guid": "0b49b96d-24c9-45ca-c585-4040707f4880",
               "agent_id": "00-agent.example.com",
               "process_version": "0.1.2.16",
               "bundle_version": "0.1.2.16",
               "agent_ip": "10.1.2.3"
           },
           {
               "id": "cnyHsfATLd",
               "guid": "0b49b96d-24c9-45ca-c585-4040707f4880",
               "agent_id": "00-agent.example.com",
               "process_version": "0.1.2.16",
               "bundle_version": "0.1.2.16",
               "agent_ip": "10.1.2.3"
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
