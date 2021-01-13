.. _get-cpu-information:

Get CPU information
-------------------

.. code::

    GET /agents/{agentId}/host_info/cpus

Get information about the host CPUs.

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
^^^^^^^

The following table shows the header parameters for the request:

+-----------------+----------------+-----------------------------------------------+
|Name             |Type            |Description                                    |
+=================+================+===============================================+
|X-Auth-Token     |String          |A valid authentication token with              |
|                 |*(Required)*    |administrative access. For details, see        |
|                 |                |:ref:`Get your credentials <get-credentials>`  |
+-----------------+----------------+-----------------------------------------------+


.. note:: This operation does not accept a request body.

Response
^^^^^^^^

**Example Get CPU information: JSON response**

.. code::

   {
       "timestamp": 1354038712351,
       "info": [
           {
               "name": "cpu.0",
               "vendor": "Intel",
               "model": "Core(TM) i7-2760QM CPU @ 2.40GHz",
               "mhz": 2394,
               "idle": 32872370,
               "irq": 2320,
               "soft_irq": 3390,
               "nice": 10,
               "sys": 247780,
               "user": 235470,
               "wait": 12180,
               "total": 33373520,
               "total_cores": 2,
               "total_sockets": 2
           },
           {
               "name": "cpu.1",
               "vendor": "Intel",
               "model": "Core(TM) i7-2760QM CPU @ 2.40GHz",
               "mhz": 2394,
               "idle": 32921490,
               "soft_irq": 10910,
               "sys": 239540,
               "user": 236780,
               "wait": 12020,
               "total": 33420740,
               "total_cores": 2,
               "total_sockets": 2
           }
       ]
   }
