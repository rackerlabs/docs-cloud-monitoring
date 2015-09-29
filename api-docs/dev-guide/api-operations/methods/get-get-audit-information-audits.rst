.. _get-audit-information:

Get audit information
^^^^^^^^^^^^^^^^^^^^^
.. code::

    GET /audits

Returns audit information for the specified account.

Rackspace Cloud Monitoring records every write operation in an audit.
For more information on how audits are recorded, see
`Audits <http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/general-api-info-audits.html>`__.

Audits are accessible as a
`Time Series Collection
<http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/api-time-series-collections.html>`__.
By default the API queries the last 7 days of audit information.

This operation can be paginated. For information, see
`Paginated collections
<http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/api-paginated-collections.html>`__.

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


.. note:: This operation does not accept a request body.

Response
""""""""
**Example Get audit information: JSON response**

.. code::

   {
       "values": [
           {
               "id": "84428400-0b26-11e1-9dd4-d7e69257c9a7",
               "headers": {
                   "host": "127.0.0.1",
                   "user-agent": "ele-client/ae0a53c",
                   "accept": "application/xml",
                   "content-type": "application/xml",
                   "x-auth-token": "917ac3575c29e2f27e7236836a732615d62e416d4aead4d5",
                   "content-length": 254,
                   "connection": "close"
               },
               "url": "/v1.0/entities",
               "app": "entities",
               "query": null,
               "txnId": ".rh-nzQM.h-ele.r-Kxysr1TO.c-189.ts-1320879585331.v-ae0a53c",
               "payload": "{\"label\":\"0NwhqrC05xKh22OEYZhcQdwkw\",\"ip_addresses\":{\"default\":\"10.0.0.2\"},\"metadata\":{\"all\":\"kinds\",\"of\":\"stuff\",\"can\":\"go\",\"here\":\"null is not a valid value\"}}",
               "method": "POST",
               "account_id": "frank",
               "who": null,
               "why": null,
               "statusCode": 201
           },
           {
               "id": "849f22f0-0b26-11e1-9dd4-d7e69257c9a7",
               "headers": {
                   "host": "127.0.0.1",
                   "user-agent": "ele-client/ae0a53c",
                   "accept": "application/xml",
                   "content-type": "application/xml",
                   "x-auth-token": "917ac3575c29e2f27e7236836a732615d62e416d4aead4d5",
                   "content-length": 51,
                   "connection": "close"
               },
               "url": "/v1.0/entities/enuAc9qZRB",
               "app": "entities",
               "query": null,
               "txnId": ".rh-nzQM.h-ele.r-lobnFBE4.c-195.ts-1320879585945.v-ae0a53c",
               "payload": "{\"label\":\"testing.example.com\"}",
               "method": "PUT",
               "account_id": "frank",
               "who": null,
               "why": null,
               "statusCode": 204
           }
       ],
       "metadata": {
           "count": 2,
           "limit": 50,
           "marker": null,
           "next_marker": null,
           "next_href": null
       }
   }
