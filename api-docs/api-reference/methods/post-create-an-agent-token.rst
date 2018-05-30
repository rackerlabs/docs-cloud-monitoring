.. _create-an-agent-token:

Create an agent token
~~~~~~~~~~~~~~~~~~~~~

.. code::

    POST /agent_tokens


Create agent tokens using a valid set of parameters from the :ref:`agent
token attributes <agent-token-operations>` table.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Accepted                 |'Location' header        |
|                          |                         |contains a link to the   |
|                          |                         |newly created check.     |
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
-------

The following table shows the header parameters for the request:

+-----------------+----------------+-----------------------------------------------+
|Name             |Type            |Description                                    |
+=================+================+===============================================+
|X-Auth-Token     |String          |A valid authentication token with              |
|                 |*(Required)*    |administrative access. For details, see        |
|                 |                |:ref:`Get your credentials <get-credentials>`  |
+-----------------+----------------+-----------------------------------------------+



**Example Create agent token: JSON request**

.. code::

   {
       "label": "Some Label"
   }

Response
--------

This operation does not return a response body.

The newly created agent token is conveyed in the ``X-Object-ID``
response header, as shown in the following example:

.. code::

   HTTP/1.1 201 Created
   Date: Wed, 30 May 2018 18:43:04 GMT
   Server: Apache/2.4.7 (Ubuntu) OpenSSL/1.0.1f
   Location: https://monitoring.api.rackspacecloud.com/v1.0/hybrid:000000/agent_tokens/d9208af....hybrid:000000
   Via: 1.1 Repose (Repose/8.8.3.0)
   X-Object-ID: d9208af....hybrid:000000
