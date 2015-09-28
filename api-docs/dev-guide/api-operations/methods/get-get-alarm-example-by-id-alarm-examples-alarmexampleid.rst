.. _get-alarm-example-by-id:

Get alarm example by ID
^^^^^^^^^^^^^^^^^^^^^^^
.. code::

    GET /alarm_examples/{alarmExampleId}

Returns the alarm example for the specified alarm example ID.

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

Response
""""""""
**Example Get alarm example by ID: JSON response**

.. code::

   {
       "id": "remote.http_body_match_1",
       "label": "Body match - string found",
       "description": "Alarm which returns CRITICAL if the provided string is found in the body",
       "check_type": "remote.http",
       "criteria": "if (metric['body_match'] regex '${string}') {\n  return new AlarmStatus(CRITICAL, '${string} found, returning CRITICAL.');\n}\n",
       "fields": [
           {
               "name": "string",
               "description": "String to check for in the body",
               "type": "string"
           }
       ]
   }
