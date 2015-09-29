.. _list-notification-plans-with-managed-plans-returned-first:

List notification plans with managed plans returned first
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code::

    GET /private/reach/notification_plans

Returns the list of notification plans for a given account,
with the guarantee that ``npManaged`` will be the first listed
notification plan OR that any plans that have an ``AtomHopper`` type
notification will be listed first and ``npManaged`` will not be included.

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
**Example List private notification plans: JSON response**

.. code::

   {
       "values": [
           {
               "id": "npWAtTznlR",
               "label": "AH Notification Plan",
               "critical_state": [
                   "ntRCJcQ4ty"
               ],
               "warning_state": [
                   "ntRCJcQ4ty"
               ],
               "ok_state": [
                   "ntRCJcQ4ty"
               ],
               "created_at": 1404418574844,
               "updated_at": 1404418574844,
               "metadata": null
           },
           {
               "id": "npTechnicalContactsEmail",
               "label": "Technical Contacts - Email",
               "critical_state": [],
               "warning_state": [],
               "ok_state": [],
               "metadata": null
           },
           {
               "id": "npceUghAkN",
               "label": "email Bob",
               "critical_state": [
                   "ntoW52GxPu"
               ],
               "warning_state": [
                   "ntoW52GxPu"
               ],
               "ok_state": [
                   "ntoW52GxPu"
               ],
               "created_at": 1418336431821,
               "updated_at": 1418336602125,
               "metadata": null
           }
       ],
       "metadata": {
           "count": 3,
           "limit": 100,
           "marker": null,
           "next_marker": null,
           "next_href": null
       }
   }
