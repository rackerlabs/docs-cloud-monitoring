.. _check-status-codes:

Check status codes
~~~~~~~~~~~~~~~~~~

This section provides a list of a set of status messages and codes that can be
returned by various check types.

The following table lists the status messages for various check types and
provides a resolution for the issue.

.. list-table:: Remote http check metrics
   :widths: 20 35 20
   :header-rows: 1

   * - Status code or message
     - Description
     - Resolution
   * - ``prevented by ACL 'global'``
     - The HTTP remote check is attempting to access an IP Address that is a
       private address (127.x.x.x, 192.168.x.x, etc).
     - Private IP addresses are not supported. Specify a public IP address
       instead.
   * - unknown content encoding
     - The content could not be copied fully to the monitoring zone endpoint.
     - Be sure that the content body of your web page is equal to or below the
       100k limit. If you are using compression, be sure that the compressed
       page is less than or equal to 100k.  See
       :ref: `remote.http <remote_http>`.
   * - ``zlib: out-of-memory``
     - The size of the webpage is too large (> 500k) for the content check.
     - Reduce the page content or use a custom 'healthcheck' page that is less
       than 500k in size.
   * - ``attempt to concatenate local *ameth* (a nil value)``
     - Occurs when the target of the remote check is using an unsupported
       authentication method. Currently supported authentication methods are
       *basic* and *digest*.  *NTLM* is currently not supported.
     - Change the authentication method to a supported method.                                                                                                                                                 |
