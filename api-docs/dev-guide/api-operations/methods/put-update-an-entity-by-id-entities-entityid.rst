.. _update-an-entity-by-id:

Update an entity by ID
^^^^^^^^^^^^^^^^^^^^^^
.. code::

    PUT /entities/{entityId}

Updates the entity specified by the ``entityId``. You can make partial
updates to an entity. When you submit the update request, only
specify the parameters that you want to update.

For Rackspace Managed Cloud resources, many fields are managed by
Rackspace. If you update these entities, you can only update the
``metadata`` and ``agent_id`` fields using this API operation.
Otherwise, refer to the
`Entities attributes table <http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/service-entities.html>`__.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|204                       |OK                       |The server has fulfilled |
|                          |                         |the request but does not |
|                          |                         |need to return an entity-|
|                          |                         |body.                    |
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
|404                       |Not Found                |The URL, entity, or      |
|                          |                         |account requested is not |
|                          |                         |found in the system.     |
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

+-----------------+----------------+-------------------------------------------+
|Name             |Type            |Description                                |
+=================+================+===========================================+
|X-Auth-Token     |String          |A valid authentication token with          |
|                 |*(Required)*    |administrative access. For details, see `  |
|                 |                |Retrieving an authentication token         |
|                 |                |<http://docs.rackspace.com/cm/api/v1.0/cm- |
|                 |                |devguide/content/general-api-info-         |
|                 |                |authentication.html#Authenticate-d1e171>`__|
+-----------------+----------------+-------------------------------------------+

.. note:: This operation does not accept a request body.

**Example Update entity: JSON request**

.. code::

   {
       "label": "Brand New Entity 2"
   }

Response
""""""""
The following operation does not return a response body.
