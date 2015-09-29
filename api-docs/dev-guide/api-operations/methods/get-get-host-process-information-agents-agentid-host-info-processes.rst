.. _get-host-process-information:

Get host process information
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code::

    GET /agents/{agentId}/host_info/processes

Get information about the host processes.

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
**Example Get host process information: JSON response**

.. code::

   {
       "timestamp": 1354040508264,
       "info": [
           {
               "pid": 1,
               "exe_name": "/sbin/init",
               "exe_cwd": "/",
               "exe_root": "/",
               "time_total": 2080,
               "time_sys": 2010,
               "time_user": 70,
               "time_start_time": 1354005304000,
               "state_name": "init",
               "state_priority": 20,
               "state_threads": 1,
               "memory_size": 24387584,
               "memory_resident": 2088960,
               "memory_share": 1335296,
               "memory_major_faults": 24,
               "memory_minor_faults": 7810,
               "memory_page_faults": 7834
           }
       ]
   }
