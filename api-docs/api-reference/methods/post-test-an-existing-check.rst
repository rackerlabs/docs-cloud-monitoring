.. _test-an-existing-check:

Test an existing check
~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /entities/{entityId}/checks/{checkId}/test

Test an existing check inline.

This operation causes Rackspace Cloud Monitoring to attempt to run a
duplicate check on the specified monitoring zones and return the
results. This enables you to test the check parameters.

.. note::
   This operation does NOT cause the already-created check to
   be run, but rather creates a duplicate check with the same
   parameters as the original, and performs the test using that.
   You can copy the results of a test check response and paste
   it directly into a :ref:`test alarm <test-an-alarm>`.

There is no request body, just posting to the URL executes the request.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |Request completed.       |
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

**Example Test existing check: JSON response**

.. code::

   [
       {
           "timestamp": 1319222001982,
           "monitoring_zone_id": "mzxJ4L2IU",
           "available": true,
           "status": "code=200,rt=0.257s,bytes=0",
           "metrics": {
               "bytes": {
                   "type": "i",
                   "data": "0"
               },
               "tt_firstbyte": {
                   "type": "I",
                   "data": "257"
               },
               "tt_connect": {
                   "type": "I",
                   "data": "128"
               },
               "code": {
                   "type": "s",
                   "data": "200"
               },
               "duration": {
                   "type": "I",
                   "data": "257"
               }
           }
       }
   ]
