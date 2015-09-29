.. _update-a-suppression:

Update a suppression
^^^^^^^^^^^^^^^^^^^^
.. code::

    PUT /suppressions/{suppressionId}

Updates the suppression specified by the ``suppressionId``.

You can complete partial updates for a suppression. When you submit
the request only include values for the attributes you want to update.
The values on omitted parameters are not updated. Note that updating
a list completely replaces the previous list. Refer to the
`suppressions attributes <http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/service-suppressions.html>`__
table.

.. note::
   Keep the following points in mind when updating a suppression:

   * Until the start_time, you can modify any field on the suppression;
     however, after that time has passed and the suppression has begun
     only the end_time can be updated.
   * The end_time can only be set to 0 or a time in the future.
     As with the start_time, there is an allowance of 60 seconds made to
     account for the time it takes to receive and process a request.
     This means that if the provided end_time is less than 60 seconds in
     the past, it will be considered to be now instead of causing a
     validation error. If you want the suppression to end immediately,
     set the end_time to 0.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|204                       |No Content               |The server has fulfilled |
|                          |                         |the request. Does not    |
|                          |                         |return a response body.  |
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

+-----------------+----------------+-----------------------------------------------+
|Name             |Type            |Description                                    |
+=================+================+===============================================+
|X-Auth-Token     |String          |A valid authentication token with              |
|                 |*(Required)*    |administrative access. For details, see        |
|                 |                |:ref:`Get your credentials <auth-credentials>` |  
+-----------------+----------------+-----------------------------------------------+

**Example Update suppression: JSON request**

.. code::

   {
     "entities": ["en234"],
     "end_time": 1378495433027
   }

Response
""""""""
This operation does not return a response body.
