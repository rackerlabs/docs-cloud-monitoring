.. _account-operations:

Account
~~~~~~~
Manage user accounts including finding out about resource and rate limits
and getting information on write operations, called audits.

**Attributes**

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

.. include:: methods/get-get-account-information-account.rst
.. include:: methods/put-update-properties-on-an-account-account.rst
.. include:: methods/get-get-limits-limits.rst
.. include:: methods/get-get-audit-information-audits.rst
