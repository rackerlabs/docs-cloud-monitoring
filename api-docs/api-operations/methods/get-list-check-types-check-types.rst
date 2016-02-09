.. _list-check-types:

List check types
^^^^^^^^^^^^^^^^
.. code::

    GET /check_types

Lists all available check types.

This operation can be paginated. For information, see
:ref:`Paginated collections <paginated-collections>`.

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
**Example List check types: JSON response**

.. code::

   {
       "values": [
           {
               "id": "remote.dns",
               "category": "remote",
               "type": "remote",
               "fields": [
                   {
                       "name": "port",
                       "description": "Port number (default: 53)",
                       "optional": true
                   },
                   {
                       "name": "query",
                       "description": "DNS Query",
                       "optional": false
                   },
                   {
                       "name": "record_type",
                       "description": "DNS Record Type",
                       "optional": false
                   }
               ]
           },
           {
               "id": "remote.ssh",
               "category": "remote",
               "type": "remote",
               "fields": [
                   {
                       "name": "port",
                       "description": "Port number (default: 22)",
                       "optional": true
                   }
               ]
           },
           {
               "id": "remote.smtp",
               "category": "remote",
               "type": "remote",
               "fields": [
                   {
                       "name": "port",
                       "description": "Port number (default: 25)",
                       "optional": true
                   },
                   {
                       "name": "ehlo",
                       "description": "EHLO parameter",
                       "optional": true
                   },
                   {
                       "name": "from",
                       "description": "From parameter",
                       "optional": true
                   },
                   {
                       "name": "to",
                       "description": "To parameter (if blank, a \"quit\" is issued before sending a to line, and the connection is terminated)",
                       "optional": true
                   },
                   {
                       "name": "payload",
                       "description": "Specifies the payload",
                       "optional": true
                   },
                   {
                       "name": "starttls",
                       "description": "Should the connection be upgraded to TLS/SSL",
                       "optional": true
                   }
               ]
           },
           {
               "id": "remote.http",
               "category": "remote",
               "type": "remote",
               "fields": [
                   {
                       "name": "url",
                       "description": "Target URL",
                       "optional": false
                   },
                   {
                       "name": "body",
                       "description": "Body match regular expression (body is limited to 100k)",
                       "optional": true
                   },
                   {
                       "name": "headers",
                       "description": "Arbitrary headers which are sent with the request.",
                       "optional": true
                   },
                   {
                       "name": "body_matches",
                       "description": "Body match regular expressions (body is limited to 100k, matches are truncated to 80 characters)",
                       "optional": true
                   },
                   {
                       "name": "method",
                       "description": "HTTP method (default: GET)",
                       "optional": true
                   },
                   {
                       "name": "auth_user",
                       "description": "Optional auth user",
                       "optional": true
                   },
                   {
                       "name": "auth_password",
                       "description": "Optional auth password",
                       "optional": true
                   },
                   {
                       "name": "follow_redirects",
                       "description": "Follow redirects (default: true)",
                       "optional": true
                   },
                   {
                       "name": "payload",
                       "description": "Specify a request body (limited to 1024 characters). If following a redirect, payload will only be sent to first location",
                       "optional": true
                   }
               ]
           },
           {
               "id": "remote.tcp",
               "category": "remote",
               "type": "remote",
               "fields": [
                   {
                       "name": "port",
                       "description": "Port number",
                       "optional": false
                   },
                   {
                       "name": "banner_match",
                       "description": "Banner match regex.",
                       "optional": true
                   },
                   {
                       "name": "send_body",
                       "description": "Send a body. If a banner is provided the body is sent after the banner is verified.",
                       "optional": true
                   },
                   {
                       "name": "body_match",
                       "description": "Body match regex. Key/Values are captured when matches are specified within the regex. Note: Maximum body size 1024 bytes.",
                       "optional": true
                   },
                   {
                       "name": "ssl",
                       "description": "Enable SSL",
                       "optional": true
                   }
               ]
           },
           {
               "id": "remote.ping",
               "category": "remote",
               "type": "remote",
               "fields": [
                   {
                       "name": "count",
                       "description": "Number of pings to send within a single check",
                       "optional": true
                   }
               ]
           },
           {
               "id": "remote.ftp-banner",
               "category": "remote",
               "type": "remote",
               "fields": [
                   {
                       "name": "port",
                       "description": "Port number (default: 21)",
                       "optional": true
                   }
               ]
           },
           {
               "id": "remote.imap-banner",
               "category": "remote",
               "type": "remote",
               "fields": [
                   {
                       "name": "port",
                       "description": "Port number (default: 143)",
                       "optional": true
                   },
                   {
                       "name": "ssl",
                       "description": "Enable SSL",
                       "optional": true
                   }
               ]
           },
           {
               "id": "remote.pop3-banner",
               "category": "remote",
               "type": "remote",
               "fields": [
                   {
                       "name": "port",
                       "description": "Port number (default: 110)",
                       "optional": true
                   },
                   {
                       "name": "ssl",
                       "description": "Enable SSL",
                       "optional": true
                   }
               ]
           },
           {
               "id": "remote.smtp-banner",
               "category": "remote",
               "type": "remote",
               "fields": [
                   {
                       "name": "port",
                       "description": "Port number (default: 25)",
                       "optional": true
                   },
                   {
                       "name": "ssl",
                       "description": "Enable SSL",
                       "optional": true
                   }
               ]
           },
           {
               "id": "remote.postgresql-banner",
               "category": "remote",
               "type": "remote",
               "fields": [
                   {
                       "name": "port",
                       "description": "Port number (default: 5432)",
                       "optional": true
                   },
                   {
                       "name": "ssl",
                       "description": "Enable SSL",
                       "optional": true
                   }
               ]
           },
           {
               "id": "remote.telnet-banner",
               "category": "remote",
               "type": "remote",
               "fields": [
                   {
                       "name": "port",
                       "description": "Port number (default: 23)",
                       "optional": true
                   },
                   {
                       "name": "banner_match",
                       "description": "Banner to check",
                       "optional": true
                   },
                   {
                       "name": "ssl",
                       "description": "Enable SSL",
                       "optional": true
                   }
               ]
           },
           {
               "id": "remote.mysql-banner",
               "category": "remote",
               "type": "remote",
               "fields": [
                   {
                       "name": "port",
                       "description": "Port number (default: 3306)",
                       "optional": true
                   },
                   {
                       "name": "ssl",
                       "description": "Enable SSL",
                       "optional": true
                   }
               ]
           },
           {
               "id": "remote.mssql-banner",
               "category": "remote",
               "type": "remote",
               "fields": [
                   {
                       "name": "port",
                       "description": "Port number (default: 1433)",
                       "optional": true
                   },
                   {
                       "name": "ssl",
                       "description": "Enable SSL",
                       "optional": true
                   }
               ]
           }
       ],
       "metadata": {
           "count": 14,
           "limit": 50,
           "marker": null,
           "next_marker": null,
           "next_href": null
       }
   }
