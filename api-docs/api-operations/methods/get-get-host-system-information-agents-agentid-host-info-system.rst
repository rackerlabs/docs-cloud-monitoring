.. _get-host-system-information:

Get host system information
^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code::

    GET /agents/{agentId}/host_info/system

Get system information for the host.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request completed.   |
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
""""""""""""""""




This table shows the header parameters for the request:

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
**Example Get host system information: JSON response**

.. code::

   {
       "timestamp": 1354039150948,
       "info": {
           "name": "Linux",
           "arch": "x86_64",
           "version": "2.6.32-44-server",
           "vendor": "Ubuntu",
           "vendor_version": "10.04"
       }
   }
