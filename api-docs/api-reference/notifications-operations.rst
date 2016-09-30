.. _notifications-operations:

=============
Notifications
=============

A notification is a destination to which an alert is sent. Each notification
must be be a variety of different notification types, which will evolve over
time.

For instance, with a webhook type notification Rackspace Monitoring posts JSON
formatted data to a user-specified URL on an alert condition (Check goes from
OK -> CRITICAL and so on).

The default ``ntTechnicalContactsEmail`` notification emails all of the
technical contacts on file for an account. You can use the default notification
to create a notification plan just like you can for other notifications. The
notification alerts the technical contacts only on state changes as defined in
the notification plan.

**Attributes**

+----------------+-------------------------+-----------------------------------+
| Name           | Description             | Validation                        |
+================+=========================+===================================+
| **details**    | A hash of notification  | * Hash [String, String between 1  |
|                | specific details based  |   and 255 characters long:Non-    |
|                | on the notification     |   empty string,String between 1   |
|                | type.                   |   and 4096 characters long        |
|                |                         | * Array or object with number of  |
|                |                         |   items between 0 and 256         |
+----------------+-------------------------+-----------------------------------+
| **label**      | Friendly name for the   | * String between 1 and 255        |
|                | notification            |   characters long                 |
+----------------+-------------------------+-----------------------------------+
| **type**       | The notification type   | * String                          |
|                | to send                 | * One of (webhook, email          |
|                |                         |   pagerduty, sms, managed,        |
|                |                         |   technicalContactsEmail,         |
|                |                         |   atomHopper)                     |
+----------------+-------------------------+-----------------------------------+
| **metadata**   | Arbitrary key/value     | * Optional                        |
|                | pairs.                  | * Hash [String,String between 1   |
|                |                         |   and 255 characters long:String, |
|                |                         |   String between 1 and 255        |
|                |                         |   characters long]                |
|                |                         | * Array or object with number of  |
|                |                         |   items between 0 and 256         |
+----------------+-------------------------+-----------------------------------+

Use the following notifications API operations to create, view, and manage
notifications.

.. contents::
   :local:
   :depth: 1

.. include:: methods/post-create-a-notification.rst
.. include:: methods/post-test-a-notification.rst
.. include:: methods/get-list-notifications.rst
.. include:: methods/post-test-an-existing-notification.rst
.. include:: methods/get-notification-by-id.rst
.. include:: methods/put-update-a-notification.rst
.. include:: methods/delete-a-notification.rst
