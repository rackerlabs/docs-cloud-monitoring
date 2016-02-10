.. _update-a-notification-plan-by-id:

Update a notification plan by ID
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code::

    PUT /notification_plans/{notificationPlanId}

Updates the notification plan properties.

You can make partial updates to a notification plan. When you submit
the update request, only specify the parameters you want to update.

Update a notification in the monitoring system by using a valid
set of attributes from the
:ref:`notification plans <notification-plans-operations>`
table.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
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

**Example Update notification plan: JSON request**

.. code::

   {
       "critical_state": [
           "ntBBBB"
       ],
       "warning_state": []
   }

Response
""""""""
This operation does not return a response body.
