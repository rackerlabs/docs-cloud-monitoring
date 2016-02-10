.. _list-notification-plans:

List notification plans
^^^^^^^^^^^^^^^^^^^^^^^
.. code::

    GET /notification_plans

Lists the notification plans for the Rackspace Cloud Monitoring account.
Use ``/notification_plans?id=notification_planOneId & id=notification_planTwoId``
to filter the results to only include information on the specified
notification plans.

This operation can be paginated. For information,
see :ref:`Paginated collections <paginated-collections>`.

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
**Example List notification plans: JSON response**

.. code::

   {
       "values": [
           {
               "label": "Notification Plan 1",
               "critical_state": [
                   "ntAAAA"
               ],
               "warning_state": [
                   "ntCCCCC"
               ],
               "ok_state": [
                   "ntBBBB"
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
