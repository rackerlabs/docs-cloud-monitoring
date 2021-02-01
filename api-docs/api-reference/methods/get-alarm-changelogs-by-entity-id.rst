.. _get-alarm-changelogs:

Get alarm changelogs by entity ID
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /changelogs/alarms

Lists alarm changelogs for this account, filtered by entity ID.

.. note::
   To filter returned changelogs by a given entityId, include
   a query string with ``entityId={entityId}`` parameter in the request.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request completed.   |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |The system received a    |
|                          |                         |request from a user that |
|                          |                         |is not authenticated.    |
+--------------------------+-------------------------+-------------------------+
|403                       |Forbidden                |The system received a    |
|                          |                         |request that the user is |
|                          |                         |not authorized to make.  |
+--------------------------+-------------------------+-------------------------+
|500                       |Internal Server Error    |An unexpected condition  |
|                          |                         |was encountered.         |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The system is            |
|                          |                         |experiencing heavy load  |
|                          |                         |or another system        |
|                          |                         |failure.                 |
+--------------------------+-------------------------+-------------------------+

Request
-------

The following table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{entityId}                |String *(Required)*      |The ID for the           |
|                          |                         |monitoring zone. Use the |
|                          |                         |List entities operation  |
|                          |                         |to find the ``entityId`` |
|                          |                         |if you don't know it.    |
+--------------------------+-------------------------+-------------------------+

.. note:: This operation does not accept a request body.

Response
--------

This operation does not return a response body.
