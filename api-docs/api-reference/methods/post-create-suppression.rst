.. _create-suppression:

Create suppression
~~~~~~~~~~~~~~~~~~

.. code::

    POST /suppressions

Creates a new suppression.

Specify the characteristics for the suppression using a valid set of
parameters from the :ref:`suppressions attributes <suppressions-operations>`
table.

The different lists (notification_plans, entities, checks, and alarms)
represent the different levels at which suppressions can be defined. When
creating a suppression, carefully consider which scopes you want to use in
order to avoid accidentally suppressing an alarm you did not mean to.

.. note::
   When creating a suppression, the start_time can only be set to 0
   or a time in the future. There is some wiggle room allocated to account
   for the time it takes to receive and process a request, meaning that
   if the start_time is less than 60 seconds in the past, it will be
   considered to be now instead of causing a validation error. If you want
   the suppression to begin immediately, set the start_time to 0.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Suppress notifications   |                         |
|                          |for alarms on check      |                         |
|                          |ch123 on entity en123    |                         |
|                          |using the notification   |                         |
|                          |plan npfooBar            |                         |
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


**Example Create suppression for notifications for alarms on check ch123
on entity en123 using the notification plan npfooBar: JSON request**

.. code::

   {
       "notification_plans": ["npfooBar"],
       "checks": ["en123:ch123"],
       "start_time": 1378492433027,
       "end_time": 1378492433027
   }

Response
--------

**Example: Suppress notifications for alarms on check ch123 on entity
en123 using the notification plan npfooBar**

.. code::

   {
       "notification_plans": ["npfooBar"],
       "checks": ["en123:ch123"],
       "start_time": 1378492433027,
       "end_time": 1378492433027
   }

**Example: Suppress notifications for entity en123 for all notification plans**

.. code::

   {
       "entities": ["en123"],
       "checks": ["en123:ch123"],
       "start_time": 1378492433027,
       "end_time": 1378492433027
   }

**Example: Suppress only check ch123 on entity en123 for all notification plans**

.. code::

   {
       "checks": ["en123:ch123"],
       "start_time": 1378492433027,
       "end_time": 1378492433027
   }

**Example: Suppress all notifications for entity enMonkey and notifications
for check ch123 on entity en123 for all notification plans**

.. code::

   {
       "entities": ["enMonkey"],
       "checks": ["en123:ch123"],
       "start_time": 1378492433027,
       "end_time": 1378492433027
   }

**Example: Suppress all notifications for notification plan npTechnical**

.. code::

   {
       "notification_plans": ["npTechnical"],
       "start_time": 1378492433027,
       "end_time": 1378492433027
   }

**Example: Suppress alarm al123 on entity en123 and alarm alBaz
on entity enMonkey for the notification plan npTechnical**

.. code::

   {
       "notification_plans": ["npTechnical"],
       "alarms": ["en123:al123", "enMonkey:alBaz"],
       "start_time": 1378492433027,
       "end_time": 1378492433027
   }
