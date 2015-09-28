.. _get-alarms-view-by-notification-plan:

Get alarms view by notification plan
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code::

    GET /views/alarmsByNp/{notificationPlanId}

Returns the alarms using a given notification plan ID.

.. note::
   Note that this call is made with a lower consistency than other
   calls, meaning that because we trade strong consistency for speed,
   the values returned may not be the most up-to-date.

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
The following table shows the URI parameters for the request:

+-----------------+----------------+-------------------------------------------+
|Name             |Type            |Description                                |
+=================+================+===========================================+
|X-Auth-Token     |String          |A valid authentication token with          |
|                 |*(Required)*    |administrative access. For details, see `  |
|                 |                |Retrieving an authentication token         |
|                 |                |<http://docs.rackspace.com/cm/api/v1.0/cm- |
|                 |                |devguide/content/general-api-info-         |
|                 |                |authentication.html#Authenticate-          |
|                 |                |d1e171>`__ This call requires a            |
|                 |                |``notificationPlanId`` as a parameter.     |
+-----------------+----------------+-------------------------------------------+

.. note:: This operation does not accept a request body.

Response
""""""""
**Example Get alarms view by notification plan: JSON response**

.. code::

   {
       "values": [
           {
               "id": "alAAAA",
               "check_id": "chAAAA",
               "entity_id": "enAAAA",
               "notification_plan_id": "npAAAA",
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
