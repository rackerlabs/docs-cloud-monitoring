.. _list-alarm-notification-history-by-check-id:

List alarm notification history by check ID
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /entities/{entityId}/alarms/{alarmId}/notification_history/{checkId}

Lists alarm notification history for a given alarm and check.

This operation can be paginated. For information, see
:ref:`Paginated collections <paginated-collections>`.

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
-------

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
--------

**Example List alarm notification history by check ID: JSON response**

.. code::

   {
       "values": [
           {
               "id": "646ac7b0-0b34-11e1-a0a1-0ff89fa2fa26",
               "timestamp": 1320885544875,
               "notification_plan_id": "npOne",
               "transaction_id": "sometransaction",
               "status": "matched return statement on line 6",
               "state": "WARNING",
               "previous_state": "OK",
               "notification_results": [
                   {
                       "notification_id": "ntOne",
                       "notification_type": "webhook",
                       "notification_details": {
                           "url": "http://admin.example.com/notify/"
                       },
                       "in_progress": false,
                       "message": "Success: Webhook successfully executed",
                       "success": true,
                       "attempts": [
                           {
                               "message": "ECONNREFUSED, Connection refused",
                               "from": "ele"
                           },
                           {
                               "message": "Unexpected status code \"404\". Expected one of: /2[0-9]{2}/",
                               "from": "ele"
                           },
                           {
                               "message": "Success: Webhook successfully executed",
                               "from": "ele"
                           }
                       ]
                   },
                   {
                       "notification_id": "ntFive",
                       "notification_type": "webhook",
                       "notification_details": {
                           "url": "https://down.example.com/notify/"
                       },
                       "in_progress": false,
                       "success": false,
                       "attempts": [
                           {
                               "message": "ECONNREFUSED, Connection refused",
                               "from": "ele"
                           },
                           {
                               "message": "ECONNREFUSED, Connection refused",
                               "from": "ele"
                           },
                           {
                               "message": "ECONNREFUSED, Connection refused",
                               "from": "ele"
                           },
                           {
                               "message": "ECONNREFUSED, Connection refused",
                               "from": "ele"
                           },
                           {
                               "message": "ECONNREFUSED, Connection refused",
                               "from": "ele"
                           },
                           {
                               "message": "ECONNREFUSED, Connection refused",
                               "from": "ele"
                           },
                           {
                               "message": "ECONNREFUSED, Connection refused",
                               "from": "ele"
                           },
                           {
                               "message": "ECONNREFUSED, Connection refused",
                               "from": "ele"
                           },
                           {
                               "message": "ECONNREFUSED, Connection refused",
                               "from": "ele"
                           },
                           {
                               "message": "ECONNREFUSED, Connection refused",
                               "from": "ele"
                           }
                       ],
                       "message": "Notification failed after 10 attempts"
                   }
               ]
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
