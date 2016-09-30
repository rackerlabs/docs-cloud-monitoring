.. _create-a-notification-plan:

Create a notification plan
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /notification_plans

Create a new notification in the monitoring system by using a valid set of
attributes from the :ref:`notification plans <notification-plans-operations>`
table.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Accepted                 |'Location' header        |
|                          |                         |contains a link to the   |
|                          |                         |newly created            |
|                          |                         |notification plan.       |
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

**Example Create notification plan: JSON request**

.. code::

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

Response
--------

This operation does not return a response body.
