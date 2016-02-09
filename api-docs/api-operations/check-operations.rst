.. _check-operations:

~~~~~~
Checks
~~~~~~

.. contents::
   :local:
   :depth: 1
   

A check is one of the foundational building blocks of the
monitoring system. The check determines the parts or
pieces of the entity that you want to monitor, the monitoring
frequency, how many monitoring zones are originating the check,
and so on. You can create up to 1000 checks.

The check, as created, will not trigger alert messages until
you :ref:`create an alarm <alarms-operations>` to generate notifications.
Alarms operate on a single check and multiple alarms can be created
for a single check (e.g. ensure both that a HTTPS server is responding and that
it has a valid certificate).

.. note::
   For more information see, :rax-devdocs:`Available check types and fields
   <cm/api/v1.0/cm-devguide/content/appendix-check-types.html>`.

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

.. include:: methods/post-create-a-check-entities-entityid-checks.rst
.. include:: methods/post-test-a-check-entities-entityid-test-check.rst
.. include:: methods/post-test-a-check-with-debug-entities-entityid-test-check.rst
.. include:: methods/post-test-an-existing-check-entities-entityid-checks-checkid-test.rst
.. include:: methods/get-list-checks-for-an-entity-entities-entityid-checks.rst
.. include:: methods/get-get-a-check-by-id-entities-entityid-checks-checkid.rst
.. include:: methods/put-update-a-check-by-id-entities-entityid-checks-checkid.rst
.. include:: methods/delete-delete-a-check-by-id-entities-entityid-checks-checkid.rst
