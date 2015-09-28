.. _alarms-operations:

~~~~~~
Alarms
~~~~~~
Alarms bind alerting rules, entities, and notification plans into
a logical unit. Alarms are responsible for determining a state
(OK, WARNING or CRITICAL) based on the result of a check, and executing
a notification plan whenever that state changes. You create alerting
rules by using the alarm domain-specific language (DSL). For information
about using the DSL, see
`Appendix A <http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/alerts-language.html>`_.
For alarm examples by check, see :ref:`alarm-example-operations`.

**Attributes**
+--------------------------+----------------------------+----------------------------------+
| Name                     | Description                | Validation                       |
+==========================+============================+==================================+
| **check_id**             | The ID of the check to     | * Immutable                      |
|                          | alert on.                  | * String                         |
+--------------------------+----------------------------+----------------------------------+
| **notification_plan_id** | The id of the notification | * Valid notification plan        |
|                          | plan to execute when the   | * Non-empty string               |
|                          | state changes.             |                                  |
+--------------------------+----------------------------+----------------------------------+
| **criteria**             | The alarm DSL for          | * Optional                       |
|                          | describing alerting        | * String between 1 and 16384     |
|                          | conditions and their       |   characters long                |
|                          | output states.             | * Valid alarm                    |
+--------------------------+----------------------------+----------------------------------+
| **disabled**             | Disables the check.        | * Optional                       |
|                          |                            | * Boolean                        |
+--------------------------+----------------------------+----------------------------------+
| **label**                | A friendly label for       | * Optional                       |
|                          | a check.                   | * String between 1 and 255       |
|                          |                            |   characters long                |
+--------------------------+----------------------------+----------------------------------+
| **metadata**             | Arbitrary key/value        | * Optional                       |
|                          | pairs.                     | * Hash [String,String between 1  |
|                          |                            |   and 255 characters long:       |
|                          |                            |   Optional]                      |
|                          |                            | * Array or object with number    |
|                          |                            |   of items between 0 and 256     |
+--------------------------+----------------------------+----------------------------------+

Use the alarms API operations to create, view, and manage alarm
resources.

.. include:: methods/post-create-an-alarm-entities-entityid-alarms.rst
.. include:: methods/post-test-an-alarm-entities-entityid-test-alarm.rst
.. include:: methods/get-list-alarms-entities-entityid-alarms.rst
.. include:: methods/get-get-alarm-by-id-entities-entityid-alarms-alarmid.rst
.. include:: methods/put-update-alarm-by-id-entities-entityid-alarms-alarmid.rst
.. include:: methods/delete-delete-alarm-by-id-entities-entityid-alarms-alarmid.rst
