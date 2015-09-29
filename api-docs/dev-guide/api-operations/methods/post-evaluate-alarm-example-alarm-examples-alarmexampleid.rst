.. _evaluate-alarm-example:

Evaluate alarm example
^^^^^^^^^^^^^^^^^^^^^^
.. code::

    POST /alarm_examples/{alarmExampleId}

This operation evaluates the template of a
single alarm example by posting the alarm to an endpoint. The
operation uses the arbitrary key/value pairs as specified by the fields
section of the :ref:`Get alarm example by ID <get-alarm-example-by-id>`
operation.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request completed.   |
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

**Example: Evaluate alarm example: JSON request**

This example evaluates a remote.http body match against '12345'.
``POST`` to https://monitoring.api.rackspacecloud.com/v1.0/
``tenantId`` /alarm_examples/remote.http_body_match_1

.. code::

   {
     "values": {
       "string": "12345"
     }
   }

Response
""""""""
**Example: Evaluate alarm example: JSON response**

.. code::

   {
     "bound_criteria": "if (metric['body_match'] regex '12345') {\n  return new AlarmStatus(CRITICAL, '12345 found, returning CRITICAL.');\n}\n"
   }
