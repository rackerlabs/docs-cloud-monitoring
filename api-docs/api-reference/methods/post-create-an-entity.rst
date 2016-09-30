.. _create-an-entity:

Create an entity
~~~~~~~~~~~~~~~~

.. code::

    POST /entities

Create a new entity in the monitoring system by using a valid set
of attributes from the :ref:`entities attributes <entities-operations>`
table.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |OK                       |The 'Location' header    |
|                          |                         |contains a link to the   |
|                          |                         |newly created entity.    |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad request              |The system received an   |
|                          |                         |invalid value in a       |
|                          |                         |request.                 |
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

The following table shows the header parameters for the request:

+-----------------+----------------+-----------------------------------------------+
|Name             |Type            |Description                                    |
+=================+================+===============================================+
|X-Auth-Token     |String          |A valid authentication token with              |
|                 |*(Required)*    |administrative access. For details, see        |
|                 |                |:ref:`Get your credentials <get-credentials>`  |
+-----------------+----------------+-----------------------------------------------+


**Example Create entity: JSON request**

.. code::

   {
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

Response
--------

This operation does not return a response body.
