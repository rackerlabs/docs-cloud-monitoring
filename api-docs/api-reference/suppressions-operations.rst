.. _suppressions-operations:

============
Suppressions
============

Suppressions enable you to suspend alarm notifications for a set period of time.
A single suppression can apply to any number of alarms. For example,
you would use one suppression to suppress all alarm notifications during
a scheduled maintenance period this week and another suppression
for some expected downtime the following week. When creating a suppression,
you specify the following:

- A timestamp at which to start the suppression (specified as milliseconds
  since the Unix epoch in UTC). You can use 0 to represent now.

- A timestamp at which to end the suppression (specify as milliseconds
  since the Unix epoch in UTC). You can use 0 to represent now.

- At least one of the following: a list of notification plans (specified
  by ID), a list of entities (specified by ID), a list of checks
  (specified by *entityID:checkID*), a list of alarms (specified by
  *entityID:alarmID*).

**Attributes**

+------------------------+---------------------------+-------------------------------+
| Name                   | Description               | Validation                    |
+========================+===========================+===============================+
| **alarms**             | A list of alarm IDs (e.g. | * Optional                    |
|                        | "enFooBar:alAbc123") for  | * Array [String,Non-empty     |
|                        | determining notification  |   string]                     |
|                        | suppression.              | * Array or object with number |
|                        |                           |   of items between 0 and 256  |
+------------------------+---------------------------+-------------------------------+
| **checks**             | A list of check IDs (e.g. | * Optional                    |
|                        | "enFooBar:chAbc123") for  | * Array [String,Non-empty     |
|                        | determining notification  |   string]                     |
|                        | suppression.              | * Array or object with number |
|                        |                           |   of items between 0 and 256  |
+------------------------+---------------------------+-------------------------------+
| **end_time**           | The Unix timestamp in     | * Optional                    |
|                        | milliseconds that the     | * Integer                     |
|                        | suppression will end.     |                               |
|                        | Specify 0 to use the      |                               |
|                        | current time.             |                               |
+------------------------+---------------------------+-------------------------------+
| **entities**           | A list of entity IDs for  | * Optional                    |
|                        | determining notification  | * Array [String,Non-empty     |
|                        | suppression.              |   string]                     |
|                        |                           | * Array or object with number |
|                        |                           |   between 0 and 256           |
+------------------------+---------------------------+-------------------------------+
| **label**              | A friendly label for a    | * Optional                    |
|                        | suppression.              | * String between 1 and 255    |
|                        |                           |   characters long             |
+------------------------+---------------------------+-------------------------------+
| **notification_plans** | A list of notification    | * Optional                    |
|                        | plan IDs for determining  | * Array [String,Non-empty     |
|                        | notification suppression. |   string]                     |
|                        |                           | * Array or object with number |
|                        |                           |   of items between 0 and 256  |
+------------------------+---------------------------+-------------------------------+
| **start_time**         | The Unix timestamp in     | * Optional                    |
|                        | milliseconds that the     | * Integer                     |
|                        | suppression will start.   |                               |
|                        | Specify 0 to use the      |                               |
|                        | current time.             |                               |
+------------------------+---------------------------+-------------------------------+

Use the following suppressions API operations to create, view, update, and
manage suppression templates.

.. contents::
   :local:
   :depth: 1

.. include:: methods/post-create-suppression.rst
.. include:: methods/get-list-suppressions.rst
.. include:: methods/get-a-suppression-by-id.rst
.. include:: methods/put-update-a-suppression.rst
.. include:: methods/delete-suppression.rst
