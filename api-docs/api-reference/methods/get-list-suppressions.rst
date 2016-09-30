.. _list-suppressions:

List suppressions
~~~~~~~~~~~~~~~~~

.. code::

    GET /suppressions

Lists the suppressions. Use
``/supressions?id=supressionOneId & id=supressionTwoId`` to filter the results
to only include information on the specified suppressions.

This operation can be paginated. For information,
see :ref: `Paginated collections <paginated-collections>`.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |Request completed.       |
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

.. note:: This operation does not accept a request body.

Response
--------

**Example List Suppressions: JSON response**

.. code::

   {
       "values": [
           {
               "id": "spAAAAA",
               "notification_plans": ['npfooBar'],
               "entities": [],
               "checks": ['en123:ch123'],
               "alarms": [],
               "start_time": 1378492433027,
               "end_time": 1378492433027
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
