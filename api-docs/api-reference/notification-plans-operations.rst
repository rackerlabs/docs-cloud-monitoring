.. _notification-plans-operations:

Notification plans
~~~~~~~~~~~~~~~~~~

A notification plan contains a set of notification actions that Rackspace
Monitoring executes when triggered by an alarm. Rackspace Monitoring currently
supports webhook, email, PagerDuty, and SMS notifications.

Each notification state can contain multiple notification actions. For example,
you can create a notification plan that hits a webhook/email to notify your
operations team if a warning occurs. However, if the warning escalates to an
Error, the notification plan could be configured to hit a different
webhook/email that triggers both email and SMS messages to the operations team.

The notification plan supports the following states:

* Critical
* Warning
* OK

The default ``npTechnicalContracsEmail`` notification plan emails all
technical contacts on file for an account whenever the state changes.

**Attributes**

+--------------------+-------------------------+-----------------------------------+
| Name               | Description             | Validation                        |
+====================+=========================+===================================+
| **label**          | Friendly name for the   | * String between 1 and 255        |
|                    | notification.           |   characters long                 |
+--------------------+-------------------------+-----------------------------------+
| **critical_state** | The notification list   | * Optional                        |
|                    | to send to when the     | * Array [Valid Notification]      |
|                    | state is CRITICAL.      |                                   |
+--------------------+-------------------------+-----------------------------------+
| **metadata**       | Arbitrary key/value     | * Optional                        |
|                    | pairs.                  | * Hash [String,String between 1   |
|                    |                         |   and 255 characters long:String, |
|                    |                         |   String between 1 and 255        |
|                    |                         |   characters long]                |
|                    |                         | * Array or object with number of  |
|                    |                         |   items between 0 and 256         |
+--------------------+-------------------------+-----------------------------------+
| **ok_state**       | The notification list   | * Optional                        |
|                    | to send to when the     | * Array [Valid Notification]      |
|                    | state is OK.            |                                   |
+--------------------+-------------------------+-----------------------------------+
| **warning_state**  | The notification list   | * Optional                        |
|                    | to send to when the     | * Array [Valid Notification]      |
|                    | state is WARNING.       |                                   |
+--------------------+-------------------------+-----------------------------------+

Use the following notification plan API operations to create, view, and manage
notification plan resources.

.. contents::
   :local:
   :depth: 1

.. include:: methods/post-create-a-notification-plan.rst
.. include:: methods/get-list-notification-plans.rst
.. include:: methods/get-a-notification-plan-by-id.rst
.. include:: methods/put-update-a-notification-plan-by-id.rst
.. include:: methods/delete-a-notification-plan.rst
