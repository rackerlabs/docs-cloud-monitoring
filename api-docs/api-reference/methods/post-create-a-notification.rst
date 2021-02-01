.. _create-a-notification:

Create a notification
~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /notifications

Create a new notification in the monitoring system by using a
valid set of attributes from the
:ref:`notifications attributes <notifications-operations>`
table.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Accepted                 |'Location' header        |
|                          |                         |contains a link to the   |
|                          |                         |newly created check.     |
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

**Example Create webhook notification: JSON request**

.. code::

   {
       "label": "my webhook #1",
       "type": "webhook",
       "details": {
           "url": "https://systems.example.org/alert"
       }
   }

**Example Create email notification: JSON request**

.. code::

   {
       "label": "my email #1",
       "type": "email",
       "details": {
           "address": "test@example.com"
       }
   }

**Example Create PagerDuty notification: JSON request**

.. code::

   {
     "label": "my PagerDuty #1",
     "type": "pagerduty",
     "details": {
     "service_key": "abcd1234abcd1234abcd1234abcd1234"
     }
   }

**Example Create SMS notification: JSON request**

.. code::

   {
     "label": "my SMS #1",
     "type": "sms",
     "details": {
     "phone_number": "+15551234567"
     }
   }

Response
--------

This operation does not return a response body.
