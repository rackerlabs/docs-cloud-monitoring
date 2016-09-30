.. _check-operations:

======
Checks
======

A check is a foundational building block of the monitoring system.
The check defines what to monitor and how to monitor. When you define
a check, you specify attributes like the following:

- the parts or pieces of the entity that you want to monitor,
- monitoring frequency
- number of monitoring zones originating the check

You can create up to 1000 checks.

After you create a check, you must :ref:`create an alarm <alarms-operations>`
so that the check sends notifications when it is triggered. Alarms operate on
a single check, and you can configure multiple alarms for a single check. For
example, you might set up a check with two alarms to ensure that an HTTPS
server is responding and that it has a valid certificatej.

.. note::
   For more information, see the :rax-devdocs:`Check types reference
   <check-types-ref>`.

Checks are associated with a parent entity, therefore the REST URLs for
checks are underneath the entity with which they are associated.

**Attributes used for all checks**

+--------------+----------------------------+----------------------------------+
| Name         | Description                | Validation                       |
+==============+============================+==================================+
| **type**     | The type of check          | * Immutable                      |
|              |                            | * String between 1 and 64        |
|              |                            |   characters long                |
+--------------+----------------------------+----------------------------------+
| **details**  | Details specific to        | * Optional                       |
|              | the check type.            | * Hash [String,String between 1  |
|              |                            |   and 255 characters long:       |
|              |                            |   Optional]                      |
|              |                            | * Array or object with number    |
|              |                            |   of items between 0 and 256     |
+--------------+----------------------------+----------------------------------+
| **disabled** | Disables the check.        | * Optional                       |
|              |                            | * Boolean                        |
+--------------+----------------------------+----------------------------------+
| **label**    | A friendly label for       | * Optional                       |
|              | a check.                   | * String between 1 and 255       |
|              |                            |   characters long                |
+--------------+----------------------------+----------------------------------+
| **metadata** | Arbitrary key/value        | * Optional                       |
|              | pairs.                     | * Hash [String,String between 1  |
|              |                            |   and 255 characters long:       |
|              |                            |   Optional]                      |
|              |                            | * Array or object with number    |
|              |                            |   of items between 0 and 256     |
+--------------+----------------------------+----------------------------------+
| **period**   | The period in seconds      | * Optional                       |
|              | for a check. The value     | * Integer                        |
|              | must be greater than the   | * Value (30..1800)               |
|              | minimum period             |                                  |
|              | set on your account.       |                                  |
+--------------+----------------------------+----------------------------------+
| **timeout**  | The timeout in seconds     | * Optional                       |
|              | for a check. This has to   | * Integer                        |
|              | be less than the period.   | * Value (2..1800)                |
+--------------+----------------------------+----------------------------------+

**Attributes used for remote checks**

+----------------------------+---------------------------+---------------------+
| Name                       | Description               | Validation          |
+============================+===========================+=====================+
| **monitoring_zones_poll**  | List of monitoring zones  | * Optional          |
|                            | to poll from. **Note**:   | * Array [String]    |
|                            | This argument is only     |                     |
|                            | required for remote       |                     |
|                            | (non-agent) checks.       |                     |
+----------------------------+---------------------------+---------------------+
| **target_alias**           | A key in the entity's     | * Optional          |
|                            | `ip_addresses` hash used  | * String between 1  |
|                            | to resolve this check to  |   and 64 characters |
|                            | an IP address. This       |   long              |
|                            | parameter is mutually     |                     |
|                            | exclusive with            |                     |
|                            | **target_hostname**.      |                     |
+----------------------------+---------------------------+---------------------+
| **target_hostname**        | The hostname this check   | * Optional          |
|                            | should target. This       | * Valid FQDN, IPv4, |
|                            | parameter is mutually     |   or IPv6 address   |
|                            | exclusive with            |                     |
|                            | **target_alias**.         |                     |
+----------------------------+---------------------------+---------------------+
| **target_resolver**        | Determines how to resolve | * Optional          |
|                            | the check target.         | * IPv4 or IPv6      |
+----------------------------+---------------------------+---------------------+


Use the following Check API operations to create, test, and manage checks and
check configuration.


.. contents::
   :local:
   :depth: 1

.. include:: methods/post-create-a-check.rst
.. include:: methods/post-test-a-check.rst
.. include:: methods/post-test-a-check-with-debug.rst
.. include:: methods/post-test-an-existing-check.rst
.. include:: methods/get-list-checks-for-an-entity.rst
.. include:: methods/get-a-check-by-id.rst
.. include:: methods/put-update-a-check-by-id.rst
.. include:: methods/delete-a-check-by-id.rst
