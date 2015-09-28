.. _agent-token-operations:


Agent tokens
~~~~~~~~~~~~
Agent tokens are used to authenticate Monitoring Agents to the
Monitoring Service. Multiple Agents on an account can share a single token.

**Attributes**

+--------------+----------------------+----------------------+
| Name         | Description          | Validation           |
+==============+======================+======================+
| **label**    | Label                | * Optional           |
|              |                      | * String             |
+--------------+----------------------+----------------------+

.. include:: methods/post-create-an-agent-token-agent-tokens.rst
.. include:: methods/get-list-agent-tokens-agent-tokens.rst
.. include:: methods/get-get-an-agent-token-by-id-agent-tokens-tokenid.rst
.. include:: methods/put-update-an-agent-token-agent-tokens-tokenid.rst
.. include:: methods/delete-delete-an-agent-token-agent-tokens-tokenid.rst
