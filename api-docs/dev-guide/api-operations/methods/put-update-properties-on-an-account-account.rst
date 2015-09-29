.. _update-properties-on-an-account:

Update properties on an account
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code::

    PUT /account

Updates account properties.

Refer to the attributes described in the
`Accounts attributes table <http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/service-account.html>`__ may be updated.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|204                       |OK                       |The server has fulfilled |
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

**Example Update account: JSON request**

.. code::

   {
       "webhook_token":"test123456"
   }

Response
""""""""
This operation does not return a response body.
