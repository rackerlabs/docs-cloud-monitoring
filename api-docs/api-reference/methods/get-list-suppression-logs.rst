.. _list-suppression-logs:

List suppression logs
~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /suppression_logs

Lists suppression logs for this account.

.. note::
   When a suppression log is written, the corresponding
   alarm changelog will be updated. Though no notification will
   be sent, the notification history will be updated to include a
   message saying that the notification was suppressed.

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

**Example List suppression logs: JSON response**

.. code::

   {
       "values": [
           {
               "id": '5a628ca0-8ca4-11e3-811c-fb1e1c039d36',
               "entity_id": 'enXXXXX',
               "alarm_id": 'alXXXXX',
               "check_id": 'chXXXXX',
               "notification_plan_id": 'npXXXXX',
               "suppressions": [
                   "spXXXXX"
               ],
               "state": 'OK',
               "timestamp": '1391412327018',
               "transaction_id": '.rh-Skiy.h-ord1-maas-stage-api1.r-zzTqFcaG.c-1553.ts-1391108878406.v-65f8f6c'
           }
       ],
       "metadata": {
           "count": 1,
           "limit": null,
           "marker": null,
           "next_marker": null,
           "next_href": null
       }
   }
