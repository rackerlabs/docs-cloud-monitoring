.. _remote-check-type-ref:

=====================
Remote check types
=====================

Rackspace Monitoring supports the following remote check types.

.. contents::
   :local:
   :depth: 1


.. _remote_dns:

remote.dns
--------------

The **remote.dns** check will run a DNS check against a given target. This
check should assist in verifying functionality of a DNS server, for
example ensuring that it is publishing the domains you think that it
should be publishing.

Attributes
~~~~~~~~~~~~~~

+----------------+-------------------------------------------------+---------------------------------------------------------------------------------------------+
| Field          | Description                                     | Validation                                                                                  |
+================+=================================================+=============================================================================================+
| query          | Specifies the DNS query.                        | String, valid hostname                                                                      |
+----------------+-------------------------------------------------+---------------------------------------------------------------------------------------------+
| record_type    | Specifies the DNS record type.                  | String matching the regex ``/^(A|AAAA| TXT|MX|SOA|CNAME|PTR|NS|MB|MD| MF|MG|MR)$/``         |
+----------------+-------------------------------------------------+---------------------------------------------------------------------------------------------+
| port           | Specifies the port number. The default is 53.   | Optional, whole number (may be zero padded), must be an integer between 1-65535 inclusive   |
+----------------+-------------------------------------------------+---------------------------------------------------------------------------------------------+


Metrics
~~~~~~~~~~~~~~

+----------+-------------------------------------------------------------------------------+----------+
| Metric   | Description                                                                   | Type     |
+==========+===============================================================================+==========+
| answer   | The list of space-separated IP addresses for the specified name resolution.   | String   |
+----------+-------------------------------------------------------------------------------+----------+
| rtt      | The roundtrip time to execute a remote.dns check.                             | Double   |
+----------+-------------------------------------------------------------------------------+----------+
| ttl      | Specifies the port number. The default is 53.                                 | Uint32   |
+----------+-------------------------------------------------------------------------------+----------+

.. _remote_ftp_banner:

remote.ftp-banner
-----------------------

The **remote.ftp-banner** check will attempt to connect to a FTP server and verify that it re- sponds to the connection.

Attributes
~~~~~~~~~~~~~~

+---------+-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| Field   | Description                                     | Validation                                                                                                                     |
+=========+=================================================+================================================================================================================================+
| port    | Specifies the port number. The default is 21.   | This field is optional. Must be a whole number (may be zero padded). This value must be an integer between 1-65535 inclusive   |
+---------+-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+

Metrics
~~~~~~~~~~~~~~

+-----------------+----------------------------------------------------------------------------------------------------+----------+
| Metric          | Description                                                                                        | Type     |
+=================+====================================================================================================+==========+
| banner          | The string sent from the server on connect                                                         | String   |
+-----------------+----------------------------------------------------------------------------------------------------+----------+
| banner_match    | The matched string from the ``banner_match`` regular expression specified during check creation.   | String   |
+-----------------+----------------------------------------------------------------------------------------------------+----------+
| body_match      | The string representing the body match specified in a remote.ftp-banner check.                     | String   |
+-----------------+----------------------------------------------------------------------------------------------------+----------+
| duration        | The time it took to finish executing the check in milliseconds.                                    | Uint32   |
+-----------------+----------------------------------------------------------------------------------------------------+----------+
| tt_body         | The time to the body measured in milliseconds.                                                     | Uint32   |
+-----------------+----------------------------------------------------------------------------------------------------+----------+
| tt_connect      | The time to connect measured in milliseconds.                                                      | Uint32   |
+-----------------+----------------------------------------------------------------------------------------------------+----------+
| tt_firstbyte    | The time to first byte measured in milliseconds.                                                   | Uint32   |
+-----------------+----------------------------------------------------------------------------------------------------+----------+

.. _remote_http:

remote.http
--------------

The **remote.http** check will try to connect to the server and retrieve the
specified URL using the specified method, optionally with the password
and user for authentication, using SSL, and checking the body with a
regex. This can be used to test that a web application running on a
server is responding without generating error messages. It can also test
if the SSL certificate is valid.

..  note::

    The maximum size of the content returned in a remote.http check is 32k,
    with overhead and compression taken into account. This limitation helps
    monitoring remain responsive.


Attributes
~~~~~~~~~~~~~~

+------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------+
| Field            | Description                                                                                            | Validation                                           |
+==================+========================================================================================================+======================================================+
| url              | Specifies the target URL.                                                                              | String between 1 and 8096 characters long            |
+------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------+
| auth_password    | Optional auth password                                                                                 | Optional. String between 1 and 255 characters long   |
+------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------+
| auth_user        | Optional auth user                                                                                     | Optional. String between 1 and 255 characters long   |
+------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------+
| body             | Body match regular expression used to run against HTTP response content and generate metric 'body_match" (see Metrics table below). Body is limited to 100k and match is truncated to 80 characters.                                               | Optional. String between 1 and 255 characters long   |
+------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------+
| body_matches     | A map of key/regular-expression pairs used to run against HTTP response content and generate one metric "body_match_" for each key/regular-expression pair (see Metrics table below). Body is limited to 100k and match is truncated to 80 characters.       | Optional. Hash [String,String between 1 and 50       |
|                  |                                                                                                        | characters long, String matching the                 |
|                  |                                                                                                        | regex /^[-_ a-z0-9]+$/i: String,String between       |
|                  |                                                                                                        | 1 and 255 characters long]. Array or object          |
|                  |                                                                                                        | with number of items between 0 and 4.                |
+------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------+
| follow_redirects | Follow redirects (default:true)                                                                        | Optional. Boolean.                                   |
+------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------+
| headers          | Arbitrary headers which are sent with the request.                                                     | Optional. Hash [String,String between 1 and 50       |
|                  |                                                                                                        | characters long: String,String between 1 and 50      |
|                  |                                                                                                        | characters long]. Array or object with number        |
|                  |                                                                                                        | of items between 0 and 10. A value which is          |
|                  |                                                                                                        | not one of: content-length, user-agent, host,        |
|                  |                                                                                                        | connection, keep-alive, transfer-encoding, upgrade.  |
+------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------+
| method           | HTTP method. The default is GET.                                                                       | Optional. String. One of (HEAD, GET, POST, PUT,      |
|                  |                                                                                                        | DELETE, INFO)                                        |
+------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------+
| payload          | Specify a request body (limited to 1024 characters). If a redirect is set, the payload is only         | Optional. String between 1 and 1024 characters long  |
|                  | sent to the first location.                                                                            |                                                      |
+------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _note:

      When you set up a website, and the check always returns 'unknown content-encoding:'.

      This is because of the HTTP body check limit of 100. This limit is the amount of space that the Monitoring Pollers (where the site is checked from).  If the amount of space required to do the HTTP(S) check is greater than 100k, then only the first 100k can be checked.

      If the customer uses Compression on the pages, such as 'compress' or 'gzip' Content-Encoding, then the full compressed page must be less than or equal to 100k.  This is because the full page must be downloaded and uncompressed before it can verify the check.

      This is also the reason why you can only check against strings within the first 100k of the web page.


Metrics
~~~~~~~~~~~~~~

+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| Metric                            | Description                                                                                                                                                                                                                               | Type      |
+===================================+===========================================================================================================================================================================================================================================+===========+
| body_match                        | The string representing the any matched string from HTTP response content using the regular expression specified in "body_match" attribute in check.| String    |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| body_match_<key>                    | The metric is generated for each <key> specified in "body_matches" check attribute. For example, a "body_matches" value of '{"register":"Register Now!", "contact":"Contact Us"}' will generate two metrics: "body_match_register" and "body_match_contact". | String.   |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| bytes                             | The number of bytes returned from a response payload.                                                                                                                                                                                     | Int32     |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| cert_end                          | The absolute timestamp in seconds for the certificate expiration. This is only available when performing a check on an HTTPS server.                                                                                                      | Uint32    |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| cert_end_in                       | The relative timestamp in seconds until certification expiration. This is only available when performing a check on an HTTPS server.                                                                                                      | Int32     |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| cert_error                        | A string describing a certificate error in our validation. This is only available when performing a check on an HTTPS server.                                                                                                             | String    |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| cert_issuer                       | The issue string for the certificate. This is only available when performing a check on an HTTPS server.                                                                                                                                  | String    |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| cert_start                        | The absolute timestamp of the issue of the certificate. This is only available when performing a check on an HTTPS server.                                                                                                                | Uint32    |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| cert_subject                      | The subject of the certificate. This is only available when performing a check on an HTTPS server.                                                                                                                                        | String    |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| cert_subject_alternative_name     | The alternative name for the subject of the certificate. This is only available when performing a check on an HTTPS server.                                                                                                               |  String   |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| code                              | The status code returned.                                                                                                                                                                                                                 |  String   |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| duration                          | The time it took to finish executing the check in milliseconds.                                                                                                                                                                           |  Uint32   |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| truncated                         | The number of bytes that the result was truncated by.                                                                                                                                                                                     |  Uint32   |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| tt_connect                        | The time to connect measured in milliseconds.                                                                                                                                                                                             |  Uint32   |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| tt_firstbyte                      | The time to first byte measured in milliseconds.                                                                                                                                                                                          |  Uint32   |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+


.. _remote_imap_banner:

remote.imap-banner
-----------------------

The **remote.imap-banner** check will attempt to connect to an IMAP server
and verify that it response to the connection

Attributes
~~~~~~~~~~~~~~

+---------+------------------------------+-----------------------------------------------------------------------------------+
| Field   | Description                  | Validation                                                                        |
+=========+==============================+===================================================================================+
| port    | Port number (default: 143)   | Optional. Whole number (may be zero padded). Integer between 1-65535 inclusive.   |
+---------+------------------------------+-----------------------------------------------------------------------------------+
| ssl     | Enable SSL                   | Optional. Boolean.                                                                |
+---------+------------------------------+-----------------------------------------------------------------------------------+

.. _remote_mssql_banner:

remote.mssql-banner
-----------------------

The **remote.mssql-banner** check will attempt to connect to a Microsoft SQL
database server and verify that it is accepting connections.

Attributes
~~~~~~~~~~~~~~

+---------+------------------------------+-----------------------------------------------------------------------------------+
| Field   | Description                  | Validation                                                                        |
+=========+==============================+===================================================================================+
| port    | Port number (default: 1433)  | Optional. Whole number (may be zero padded). Integer between 1-65535 inclusive.   |
+---------+------------------------------+-----------------------------------------------------------------------------------+
| ssl     | Enable SSL                   | Optional. Boolean.                                                                |
+---------+------------------------------+-----------------------------------------------------------------------------------+

.. _remote_mysql_banner:

remote.mysql-banner
------------------------

The **remote.mysql-banner** check will attempt to connect to a MySQL
database server and verify that it is accepting connections.

Attributes
~~~~~~~~~~~~~~

+---------+------------------------------+-----------------------------------------------------------------------------------+
| Field   | Description                  | Validation                                                                        |
+=========+==============================+===================================================================================+
| port    | Port number (default: 3306)  | Optional. Whole number (may be zero padded). Integer between 1-65535 inclusive.   |
+---------+------------------------------+-----------------------------------------------------------------------------------+
| ssl     | Enable SSL                   | Optional. Boolean.                                                                |
+---------+------------------------------+-----------------------------------------------------------------------------------+

.. _remote_ping:

remote.ping
---------------

The **remote.ping** check will attempt to ping a server.

Attributes
~~~~~~~~~~~~~~

+---------+-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| Field   | Description                                     | Validation                                                                                                                     |
+=========+=================================================+================================================================================================================================+
| count   | Number of pings to send within a single check.  | This field is optional. Must be a whole number (may be zero padded). This value must be an integer between 1-15 inclusive      |
+---------+-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+


Metrics
~~~~~~~~~~~~~~

+-------------+--------------------------------------------------------------------------------------------------+----------+
| Metric      | Description                                                                                      | Type     |
+=============+==================================================================================================+==========+
| available   | The whole number representing the percent of pings that returned back for a remote.ping check.   | Double   |
+-------------+--------------------------------------------------------------------------------------------------+----------+
| average     | The average response time in milliseconds for all ping packets sent out and later retrieved.     | Double   |
+-------------+--------------------------------------------------------------------------------------------------+----------+
| count       | The number of pings (ICMP packets) sent.                                                         | Int32    |
+-------------+--------------------------------------------------------------------------------------------------+----------+
| maximum     | The maximum roundtrip time in milliseconds of an ICMP packet.                                    | Double   |
+-------------+--------------------------------------------------------------------------------------------------+----------+
| minimum     | The minimum roundtrip time in milliseconds of an ICMP packet.                                    | Double   |
+-------------+--------------------------------------------------------------------------------------------------+----------+

.. _remote_pop3_banner:

remote.pop3-banner
---------------------

The **remote.pop3-banner** check will attempt to connect to a POP3 mailbox
server and verify that it responds to the connection.

Attributes
~~~~~~~~~~~~~~

+---------+------------------------------+-----------------------------------------------------------------------------------+
| Field   | Description                  | Validation                                                                        |
+=========+==============================+===================================================================================+
| port    | Port number (default: 110)   | Optional. Whole number (may be zero padded). Integer between 1-65535 inclusive.   |
+---------+------------------------------+-----------------------------------------------------------------------------------+
| ssl     | Enable SSL                   | Optional. Boolean.                                                                |
+---------+------------------------------+-----------------------------------------------------------------------------------+

.. _remote_postgresql_banner:

remote.postgresql-banner
--------------------------

The **remote.postgresql-banner** check will attempt to connect to a
PostgreSQL database server and verify that it is accepting connections.

Attributes
~~~~~~~~~~~~~~

+---------+------------------------------+-----------------------------------------------------------------------------------+
| Field   | Description                  | Validation                                                                        |
+=========+==============================+===================================================================================+
| port    | Port number (default: 5432)  | Optional. Whole number (may be zero padded). Integer between 1-65535 inclusive.   |
+---------+------------------------------+-----------------------------------------------------------------------------------+
| ssl     | Enable SSL                   | Optional. Boolean.                                                                |
+---------+------------------------------+-----------------------------------------------------------------------------------+

.. _remote_smtp_banner:

remote.smtp-banner
--------------------------

The **remote.smtp-banner** check will attempt to connect to a SMTP mail
server and verify that a HELO/EHLO is received.

Attributes
~~~~~~~~~~~~~~

+---------+------------------------------+-----------------------------------------------------------------------------------+
| Field   | Description                  | Validation                                                                        |
+=========+==============================+===================================================================================+
| port    | Port number (default: 25)    | Optional. Whole number (may be zero padded). Integer between 1-65535 inclusive.   |
+---------+------------------------------+-----------------------------------------------------------------------------------+
| ssl     | Enable SSL                   | Optional. Boolean.                                                                |
+---------+------------------------------+-----------------------------------------------------------------------------------+

Metrics
~~~~~~~~~~~~~~

+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| Metric                            | Description                                                                                                                                                                   | Type      |
+===================================+===============================================================================================================================================================================+===========+
| banner                            | The string sent from the server on connect.                                                                                                                                   | String    |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| banner_match                      | The matched string from the ``banner_match`` regular expression specified during check creation.                                                                              | String    |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| bytes                             | The number of bytes returned from a response payload.                                                                                                                         | Int32     |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| cert_end                          | The absolute timestamp in seconds for the certificate expiration. This is only available when performing a check on an HTTPS server.                                          | Uint32    |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| cert_end_in                       | The relative timestamp in seconds until certification expiration. This is only available when performing a check on an HTTPS server.                                          | Int32     |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| cert_error                        | A string describing a certificate error in our validation. This is only available when performing a check on an HTTPS server.                                                 | String    |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| cert_issuer                       | The issue string for the certificate. This is only available when performing a check on an HTTPS server.                                                                      | String    |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| cert_start                        | The absolute timestamp of the issue of the certificate. This is only available when performing a check on an HTTPS server.                                                    | Uint32    |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| cert_subject                      | The subject of the certificate. This is only available when performing a check on an HTTPS server.                                                                            | String    |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| cert_subject_alternative_name     | The alternative name for the subject of the certificate. This is only available when performing a check on an HTTPS server.                                                   |  String   |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| duration                          | The time it took to finish executing the check in milliseconds.                                                                                                               |  Uint32   |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| tt_connect                        | The time to connect measured in milliseconds.                                                                                                                                 |  Uint32   |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+
| tt_firstbyte                      | The time to first byte measured in milliseconds.                                                                                                                              |  Uint32   |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------+

.. _remote_smtp:

remote.smtp
--------------------------

The **remote.smtp** check will attempt to connect to a SMTP mail server,
send an email from the 'from' parameter, to the 'to' parameter, with a
payload specified by the 'payload' parameter setting the EHLO from host
to the value in 'ehlo'.

Attributes
~~~~~~~~~~~~~~

+------------+----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+
| Field      | Description                                                                                                                            | Validation                                                                        |
+============+========================================================================================================================================+===================================================================================+
| ehlo       | Specifies the EHLO parameter.                                                                                                          | Optional. String between 1 and 255 characters long.                               |
+------------+----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+
| from       | Specifies the From parameter.                                                                                                          | Optional. String between 1 and 255 characters long.                               |
+------------+----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+
| payload    | Specifies the payload.                                                                                                                 | Optional. String between 1 and 1024 characters long.                              |
+------------+----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+
| port       | Specifies the port number.                                                                                                             | Optional. Whole number (may be zero padded). Integer between 1-65535 inclusive.   |
+------------+----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+
| starttls   | Specifies whether the connection should be upgraded to TLS/ SSL.                                                                       | Optional. Boolean.                                                                |
+------------+----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+
| to         | Specifies the To parameter. If this field is blank, a “quit” is issued before sending a to line, and the connection is terminated.     | Optional. String between 1 and 255 characters long.                               |
+------------+----------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+

.. _remote_ssh:

remote.ssh
--------------------------

The **remote.ssh** check will attempt to SSH to a target.

Attributes
~~~~~~~~~~~~~~

+---------+-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| Field   | Description                                     | Validation                                                                                                                     |
+=========+=================================================+================================================================================================================================+
| port    | Specifies the port number. The default is 22.   | This field is optional. Must be a whole number (may be zero padded). This value must be an integer between 1-65535 inclusive   |
+---------+-------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+

Metrics
~~~~~~~~~~~~~~

+---------------+-----------------------------------------------------------------------------+----------+
| Metric        | Description                                                                 | Type     |
+===============+=============================================================================+==========+
| duration      | Specifies the time it took to finish executing the check in milliseconds.   | Uint32   |
+---------------+-----------------------------------------------------------------------------+----------+
| fingerprint   | Specifies the ssh fingerprint used to verify identity.                      | String   |
+---------------+-----------------------------------------------------------------------------+----------+

.. _remote_tcp:

remote.tcp
--------------------------


The **remote.tcp** check will attempt to connect to a host and port, and
optionally issue a banner match to ensure that the service is responding
as specified. This can be used to test services that are not covered by
the existing HTTP, SMTP, SSH, MySQL, etc. checks.

Attributes
~~~~~~~~~~~~~~

+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
| Field           | Description                                                                                                                                   | Validation                                                              |
+=================+===============================================================================================================================================+=========================================================================+
| port            | Specifies the port number.                                                                                                                    | Whole number (may be zero padded). Integer between 1-65535 inclusive.   |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
| banner_match    | Specifies the banner match regex.                                                                                                             | Optional. String between 1 and 255 characters long.                     |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
| body_match      | Specifies the body match regex. Key/Values are captured when matches are specified within the regex. Note: Maximum body size is 1024 bytes.   | Optional. String between 1 and 255 characters long.                     |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
| send_body       | Send a body. If a banner is provided the body is sent after the banner is verified.                                                           | Optional. String between 1 and 1024 characters long.                    |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+
| ssl             | Specifies whether SSL is enabled.                                                                                                             | Optional. Boolean.                                                      |
+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------+


Metrics
~~~~~~~~~~~~~~

+-----------------+-----------------------------------------------------------------------------------------------------------+----------+
| Metric          | Description                                                                                               | Type     |
+=================+===========================================================================================================+==========+
| banner          | Specifies the string that is sent from the server on connect.                                             | String   |
+-----------------+-----------------------------------------------------------------------------------------------------------+----------+
| banner_match    | Specifies the matched string from the ``banner_match`` regular expression specified during check creation.| String   |
+-----------------+-----------------------------------------------------------------------------------------------------------+----------+
| duration        | Specifies the time it took to finish executing the check in milliseconds.                                 | Uint32   |
+-----------------+-----------------------------------------------------------------------------------------------------------+----------+
| tt_connect      | Specifies the time to connect measured in milliseconds.                                                   | Uint32   |
+-----------------+-----------------------------------------------------------------------------------------------------------+----------+
| tt_firstbyte    | Specifies the time to first byte measured in milliseconds.                                                | Uint32   |
+-----------------+-----------------------------------------------------------------------------------------------------------+----------+

.. _remote_telnet_banner:

remote.telnet-banner
-----------------------

The **remote.telnet-banner** check will attempt to connect to a Telnet (or
similar protocol) server and verify that an appropriate banner is
received.

Attributes
~~~~~~~~~~~~~~
+-----------------+----------------------------------------------------------------------------------------------------------------------------------------+
| Field           | Description                                        | Validation                                                                        |
+=================+====================================================+===================================================================================+
| port            | Specifies the port number. (Default: 23)           | Optional. Whole number (may be zero padded). Integer between 1-65535 inclusive.   |
+-----------------+------------------------------------------------------------------------------------------+---------------------------------------------+
| banner_match    | Specifies the banner match check.                  | Optional. String between 1 and 255 characters long.                               |
+-----------------+----------------------------------------------------------------------------------------------------------------------------------------+
| ssl             | Specifies whether SSL is enabled.                  | Optional. Boolean.                                                                |
+-----------------+----------------------------------------------------------------------------------------------------------------------------------------+
