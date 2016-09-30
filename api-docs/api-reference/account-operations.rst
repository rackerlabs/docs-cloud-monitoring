.. _account-operations:

=======
Account
=======

Use the following Account operations to manage user accounts including finding
out about resource and rate limits and getting information on write operations,
called audits.

.. contents::
   :local:
   :depth: 1

The following table describes the Account operations attributes:

+--------------------+-----------------------+-------------------------------------+
| Name               | Description           | Validation                          |
+====================+=======================+=====================================+
| **metadata**       | Arbitrary key/value   | * Optional                          |
|                    | pairs                 | * Hash [String, String between 1    |
|                    |                       |   and 255 characters long:String,   |
|                    |                       |   String between 1 and 255          |
|                    |                       |   characters long]                  |
|                    |                       | * Array or object with number of    |
|                    |                       |   items between 0 and 256           |
+--------------------+-----------------------+-------------------------------------+
| **webhook_token**  |                       | * Optional                          |
|                    |                       | * String between 10 and 64          |
|                    |                       |   characters long                   |
+--------------------+-----------------------+-------------------------------------+

.. include:: methods/get-account-information.rst
.. include:: methods/put-update-properties-on-an-account.rst
.. include:: methods/get-limits.rst
.. include:: methods/get-audit-information.rst
