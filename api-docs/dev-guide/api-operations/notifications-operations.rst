.. _notifications-operations:

~~~~~~~~~~~~~
Notifications
~~~~~~~~~~~~~
A notification is a destination to which an alert is sent. It can
be a variety of different notification types, which will evolve over time.

For instance, with a webhook type notification Rackspace Cloud
Monitoring posts JSON formatted data to a user-specified URL on an
alert condition (Check goes from OK -> CRITICAL and so on).

A notification, ntTechnicalContactsEmail, is provided by default
which will email all of the technical contacts on file for an account.
It can be used to create a notification plan just as a normal
notification would be used and will only alert the technical contacts
on state changes as defined in the notification plan.

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

Use the notifications API operations to create, view, and manage
notifications.

.. include:: methods/post-create-a-notification-notifications.rst
.. include:: methods/post-test-a-notification-test-notification.rst
.. include:: methods/get-list-notifications-notifications.rst
.. include:: methods/post-test-an-existing-notification-notifications-notificationid-test.rst
.. include:: methods/get-get-notification-by-id-notifications-notificationid.rst
.. include:: methods/put-update-a-notification-notifications-notificationid.rst
.. include:: methods/delete-delete-a-notification-notifications-notificationid.rst
