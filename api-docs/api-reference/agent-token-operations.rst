.. _agent-token-operations:

============
Agent tokens
============

Agent tokens are used to authenticate Monitoring Agents to the
Monitoring Service. Multiple Agents on an account can share a single token.

The following table describes the attribute for the Agent token resource.

+--------------+----------------------+----------------------+
| Name         | Description          | Validation           |
+==============+======================+======================+
| **label**    | Label                | * Optional           |
|              |                      | * String             |
+--------------+----------------------+----------------------+

Use the following Agent tokens API operations to create and manage agent tokens.

.. contents::
   :local:
   :depth: 1

.. include:: methods/post-create-an-agent-token.rst
.. include:: methods/get-list-agent-tokens.rst
.. include:: methods/get-an-agent-token-by-id.rst
.. include:: methods/put-update-an-agent-token.rst
.. include:: methods/delete-an-agent-token.rst
