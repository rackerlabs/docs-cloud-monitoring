.. _get-overview-view:

Get overview (entity, checks, alarms and alarm states) view
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code::

    GET /views/overview

Returns the overview view for this account.

The overview view includes a list of entities on your account and
each entity's child check and alarm objects. Along with the child check
and alarm objects, the view also includes the latest computed state
for each check and alarm pair. If the latest state for a check and
alarm pair is not available, the alarm hasn't been evaluated yet and
the current state for pair is 'UNKNOWN'.


.. note::
   In a request, you can filter for returned entities by ``uri``
   or ``entityId``, but you cannot use both filter types in the same
   request. When filtering by ``entityId``, an HTTP 404 error is
   returned if any supplied entityIds are unknown or incorrect.
   When filtering requests by entity ``uri``, unknown URIs are
   ignored, and entities are returned for any correct URIs. An
   HTTP 404 error is returned only if no known URIs are supplied.


.. note::
   In a request, you can also filter the overview and latest_alarm_states views by one agentId or multiple agentIds.

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
|404                       |Not Found                |The URL, entity, or      |
|                          |                         |account requested is not |
|                          |                         |found in the system.     |
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


The following table shows the URI parameters for the request:

+-----------------+----------------+-------------------------------------------+
|Name             |Type            |Description                                |
+=================+================+===========================================+
|{uri}            |String          |The entity's URI.                          |
|                 |*(Required)*    |                                           |
+-----------------+----------------+-------------------------------------------+
|{entityId}       |String          |The ID for the entity. Use the List        |
|                 |*(Required)*    |entities operation to find the             |
|                 |                |``entityId`` if you don't know it.         |
+-----------------+----------------+-------------------------------------------+

.. note:: This operation does not accept a request body.

Response
""""""""
**Example Get overview view: JSON response**

.. code::

   {
       "values": [
           {
               "entity": {
                   "id": "enBBBBIPV4",
                   "label": "entity b v4",
                   "ip_addresses": {
                       "default": "127.0.0.1"
                   },
                   "metadata": null
               },
               "checks": [
                   {
                       "id": "chFour",
                       "label": "ch a",
                       "type": "remote.http",
                       "details": {
                           "url": "http://www.foo.com",
                           "method": "GET"
                       },
                       "monitoring_zones_poll": [
                           "mzA"
                       ],
                       "timeout": 30,
                       "period": 60,
                       "target_alias": "default",
                       "target_hostname": "",
                       "target_resolver": "",
                       "disabled": false
                   }
               ],
               "alarms": [
                   {
                       "id": "alThree",
                       "check_id": "chFour",
                       "criteria": "if (metric[\"size\"] >= 200) { return new AlarmStatus(CRITICAL); }",
                       "notification_plan_id": "npOne"
                   }
               ],
               "latest_alarm_states": [
                   {
                       "timestamp": 1321898988,
                       "entity_id": "enBBBBIPV4",
                       "alarm_id": "alThree",
                       "check_id": "chFour",
                       "status": "everything is ok",
                       "state": "OK",
                       "previous_state": "WARNING",
                       "analyzed_by_monitoring_zone_id": null
                   }
               ]
           },
           {
               "entity": {
                   "id": "enCCCCIPV4",
                   "label": "entity c v4",
                   "ip_addresses": {
                       "default": "127.0.0.1"
                   },
                   "metadata": null
               },
               "checks": [],
               "alarms": [],
               "latest_alarm_states": []
           },
           {
               "entity": {
                   "id": "enAAAAIPV4",
                   "label": "entity a",
                   "ip_addresses": {
                       "default": "127.0.0.1"
                   },
                   "metadata": null
               },
               "checks": [
                   {
                       "id": "chOne",
                       "label": "ch a",
                       "type": "remote.http",
                       "details": {
                           "url": "http://www.foo.com",
                           "method": "GET"
                       },
                       "monitoring_zones_poll": [
                           "mzA"
                       ],
                       "timeout": 30,
                       "period": 60,
                       "target_alias": "default",
                       "target_hostname": "",
                       "target_resolver": "",
                       "disabled": false
                   },
                   {
                       "id": "chThree",
                       "label": "ch a",
                       "type": "remote.http",
                       "details": {
                           "url": "http://www.foo.com",
                           "method": "GET"
                       },
                       "monitoring_zones_poll": [
                           "mzA"
                       ],
                       "timeout": 30,
                       "period": 60,
                       "target_alias": "default",
                       "target_hostname": "",
                       "target_resolver": "",
                       "disabled": false
                   },
                   {
                       "id": "chTwo",
                       "label": "ch a",
                       "type": "remote.http",
                       "details": {
                           "url": "http://www.foo.com",
                           "method": "GET"
                       },
                       "monitoring_zones_poll": [
                           "mzA"
                       ],
                       "timeout": 30,
                       "period": 60,
                       "target_alias": "default",
                       "target_hostname": "",
                       "target_resolver": "",
                       "disabled": false
                   }
               ],
               "alarms": [
                   {
                       "id": "alOne",
                       "label": "Alarm 1",
                       "check_id": "chOne",
                       "criteria": "if (metric[\"duration\"] >= 2) { return new AlarmStatus(OK); } return new AlarmStatus(CRITICAL);",
                       "notification_plan_id": "npOne"
                   },
                   {
                       "id": "alTwo",
                       "label": "Alarm 2",
                       "check_id": "chOne",
                       "criteria": "if (metric[\"size\"] >= 200) { return CRITICAL } return OK",
                       "notification_plan_id": "npOne"
                   }
               ],
               "latest_alarm_states": [
                   {
                       "timestamp": 1321898988,
                       "entity_id": "enAAAAIPV4",
                       "alarm_id": "alOne",
                       "check_id": "chOne",
                       "status": "matched return statement on line 7",
                       "state": "WARNING",
                       "previous_state": "OK",
                       "analyzed_by_monitoring_zone_id": null
                   },
                   {
                       "timestamp": 1321898988,
                       "entity_id": "enAAAAIPV4",
                       "alarm_id": "alOne",
                       "check_id": "chTwo",
                       "state": "CRITICAL",
                       "analyzed_by_monitoring_zone_id": null
                   }
               ]
           }
       ],
       "metadata": {
           "count": 3,
           "limit": 50,
           "marker": null,
           "next_marker": null,
           "next_href": null
       }
   }
