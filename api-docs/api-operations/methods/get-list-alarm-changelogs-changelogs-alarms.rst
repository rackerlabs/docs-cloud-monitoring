.. _list-alarm-changelogs:

List alarm changelogs
^^^^^^^^^^^^^^^^^^^^^
.. code::

    GET /changelogs/alarms

Lists alarm changelogs for this account.

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
**Example List alarm changelogs: JSON response**

.. code::

   {
       "values": [
           {
               "id": "4c5e28f0-0b3f-11e1-860d-c55c4705a286",
               "timestamp": 1320890228991,
               "entity_id": "enPhid7noo",
               "alarm_id": "alahf9vuNa",
               "check_id": "chIe7vohba",
               "state": "WARNING",
               "analyzed_by_monitoring_zone_id": "DFW"
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
