.. _list-notification-types:

List notification types
^^^^^^^^^^^^^^^^^^^^^^^
.. code::

    GET /notification_types

Lists available notification types.

This operation can be paginated. For information,
see `Paginated collections
<http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/api-paginated-collections.html>`__.

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

.. note:: This operation does not accept a request body.

Response
""""""""
**Example List notification types: JSON response**

.. code::

   {
       "values": [
           {
               "id": "webhook",
               "fields": [
                   {
                       "name": "url",
                       "description": "An HTTP or HTTPS URL to POST to",
                       "optional": false
                   }
               ]
           },
           {
               "id": "email",
               "fields": [
                   {
                       "name": "address",
                       "description": "Email address to send notifications to",
                       "optional": false
                   }
               ]
           },
           {
               "id": "pagerduty",
               "fields": [
                   {
                       "name": "service_key",
                       "description": "The PagerDuty service key to use.",
                       "optional": false
                   }
               ]
           },
           {
               "id": "sms",
               "fields": [
                   {
                       "name": "phone_number",
                       "description": "Phone number to send the notification to, with leading + and country code (E.164 format)",
                       "optional": false
                   }
               ]
           },
           {
               "id": "managed",
               "fields": null
           },
           {
               "id": "technicalContactsEmail",
               "fields": null
           },
           {
               "id": "atomHopper",
               "fields": [
                   {
                       "name": "category",
                       "description": "A category by which to identify this notification. Categories will be prefixed by 'monitoring.alerts.', so they will end up looking like: 'monitoring.alerts.USER_DEFINED_CATEGORY'",
                       "optional": false
                   }
               ]
           },
           {
               "id": "victorops",
               "fields": [
                   {
                       "name": "api_key",
                       "description": "The VictorOps api key to use.",
                       "optional": false
                   },
                   {
                       "name": "routing_key",
                       "description": "The VictorOps routing key to use.",
                       "optional": false
                   }
               ]
           }
       ],
       "metadata": {
           "count": 8,
           "limit": 50,
           "marker": null,
           "next_marker": null,
           "next_href": null
       }
   }
