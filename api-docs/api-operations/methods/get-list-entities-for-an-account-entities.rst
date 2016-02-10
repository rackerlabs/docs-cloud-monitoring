.. _list-entities-for-an-account:

List entities for an account
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code::

    GET /entities

Lists the entities associated with this account.

This operation can be paginated. For information,
see :ref:`Paginated collections <paginated-collections>`.

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
"""""""
The following table shows the header parameters for the request:

+-----------------+----------------+-----------------------------------------------+
|Name             |Type            |Description                                    |
+=================+================+===============================================+
|X-Auth-Token     |String          |A valid authentication token with              |
|                 |*(Required)*    |administrative access. For details, see        |
|                 |                |:ref:`Get your credentials <auth-credentials>` |
+-----------------+----------------+-----------------------------------------------+

.. note:: This operation does not accept a request body.

Response
""""""""
**Example List entities for account: JSON response**

.. code::

   {
       "values": [
           {
               "id": "enAAAAA",
               "label": "Brand New Entity",
               "ip_addresses": {
                   "entity_ip_addresses_hash_key": "127.0.0.4",
                   "b": "127.0.0.5",
                   "c": "127.0.0.6",
                   "test": "127.0.0.7"
               },
               "metadata": {
                   "all": "kinds",
                   "of": "stuff",
                   "can": "go",
                   "here": "null is not a valid value"
               }
           }
       ],
       "metadata": {
           "count": 1,
           "limit": 50,
           "marker": null,
           "next_marker": null,
           "next_href": null
       }
   }
