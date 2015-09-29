.. _update-a-notification:

Update a notification
^^^^^^^^^^^^^^^^^^^^^
.. code::

    PUT /notifications/{notificationId}

Update a notification in the monitoring system by using a valid
set of attributes from the
`notifications attributes <http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/service-notifications.html>`__
table.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|204                       |No Content               |The server has fulfilled |
|                          |                         |the request. Does not    |
|                          |                         |return a response body.  |
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

**Example Update notification: JSON request**

.. code::

   {
       "type": "webhook",
       "details": {
           "url": "https://systems.example.org/new_alert"
       }
   }

Response
""""""""
This operation does not return a response body.
