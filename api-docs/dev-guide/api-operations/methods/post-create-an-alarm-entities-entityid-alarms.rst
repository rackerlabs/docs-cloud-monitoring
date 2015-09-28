.. _create-an-alarm:

Create an alarm
^^^^^^^^^^^^^^^
.. code::

    POST /entities/{entityId}/alarms

Create a new alarm by using a valid set of attributes from the
`alarms attributes
<http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/service-alarms.html>`__
table.

For more information,
see ` Alarm language
<http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/alerts-language.html#concepts-alarms-alarm-language>`__.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Accepted                 |The location header      |
|                          |                         |contains a link to the   |
|                          |                         |newly created alarm.     |
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

**Example Create alarm: JSON request**

.. code::

   {
       "check_id": "chAAAA",
       "criteria": "if (metric[\"duration\"] >= 2) { return new AlarmStatus(OK); } return new AlarmStatus(CRITICAL);",
       "notification_plan_id": "npAAAAA"
   }

Response
""""""""
This operation does not return a response body.
