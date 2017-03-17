.. _audits:

======
Audits
======

Every write operation performed against the API (**PUT**, **POST** or
**DELETE**) generates an audit record that is stored for 30 days. Audits
record a variety of information about the request including the method,
URL, headers, query string, transaction ID, the request body and the
response code. They also store information about the action performed
including a JSON list of the previous state of any modified objects. For
example, when you perform an update on an entity, the audit records the
state of the entity before modification.

You can also use ``_who`` and ``_why`` parameters in the query string which
will be included in the transaction object.

Audits can be retrieved using the `list audits endpoint`_ endpoint.


.. _list audits endpoint: ../api-reference/account-operations/#get-audit-information
