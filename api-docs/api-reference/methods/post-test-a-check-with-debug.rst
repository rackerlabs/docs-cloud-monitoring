.. _test-a-check-with-debug:

Test a check with debug
~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /entities/{entityId}/test-check

Test a check and include extra check type-specific debugging
information, if available.

This operation causes Rackspace Cloud Monitoring to attempt to run
the check on the specified monitoring zones and return the results.
This enables you to test the check parameters in a single step
before the check is actually created in the system. This call also includes
debug information. Currently debug information is only available for the
remote.http check and includes the response body.

.. note::
   Only the first 512 KB of the response body is read. If the response
   body is longer, it is truncated to 512KB.

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
**Example Test a check: JSON request**

.. code::

   {
       "type": "remote.http",
       "details": {
           "url": "http://www.foo.com",
           "method": "GET"
       },
       "monitoring_zones_poll": [
           "mzA"
       ],
       "timeout": 30,
       "target_alias": "default"
   }

Response
--------

**Example Test check with debug: JSON response**

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
           },
           "debug_info": {
               "body": "<html><body>My shiny website</body></html>"
           }
       }
   ]
