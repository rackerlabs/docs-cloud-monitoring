.. _list-alarms:

List alarms
^^^^^^^^^^^
.. code::

    GET /entities/{entityId}/alarms

List the alarms on the specified ``entityId``. Use
``/alarms?id=alarmOneId & id=alarmTwoId`` to filter the results to only
include information on the specified alarms.

This operation can be paginated. For information, see
`Paginated collections
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
**Example List alarms: JSON response**

.. code::

   {
       "values": [
           {
               "id": "alAAAA",
               "check_id": "chAAAA",
               "entity_id": "enZZZZA",
               "criteria": "if (metric[\"duration\"] >= 2) { return new AlarmStatus(OK); } return new AlarmStatus(CRITICAL);"
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
