.. _monitoring-faults:


======
Faults
======

When an error occurs the system returns an HTTP error response code
denoting the type of error and additional information in the fault
response body.

API operations that return an error return one of the fault objects described
in this section.  All fault objects extend from the base fault,
``serviceFault``, for easier exception handling  for languages that support it.

The following table lists possible error types with their associated error
codes and descriptions.


.. list-table::
   :widths: 25 6 59
   :header-rows: 1


   * - Error type
     - Error code
     - Description
   * - badRequest
     - 400
     - The system received an invalid value in a request
   * - requiredNotFoundError
     - 400
     - A required related object is not found in the system.
   * - invalidLimit
     - 400
     - Invalid limit has been specified.
   * - childrenExistError
     - 400
     - The system cannot perform the requested operation due to remaining
       child,objects. Details attribute also contains a ``type`` field which
       specified a type of the existing child object.
   * - alarmParseError
     - 400
     - Alarm criteria cannot be parsed. Details attribute also contains the
       following fields: input, error_position, error_line, error_column,
       error_token, message.
   * - invalidKeyPrefix
     - 400
     - Provided key prefix is invalid.
   * - agentNotConnected
     - 400
     - Agent Not Connected
   * - agentDoesNotExist
     - 400
     - Agent does not exist.
   * - limitReached
     - 400
     - Limit has been reached. Please contact cmbeta@rackspace.com to increase
       our limit.
   * - rateLimitReached
     - 429
     - Rate limit has been reached. Please wait before trying again.
   * - indexCardinalityConstraintViolation
     - 400
     - A resource with the specified index already exists in the system.
   * - unauthorizedError
     - 401
     - The system received a request from a user that is not authenticated.
   * - forbiddenError
     - 403
     - The system received a request that the user is forbidden to make.
   * - missingCapabilitiesError
     - 403
     - The system received a request that the user is not authorized to make.
   * - notFoundError
     - 404
     - The URL requested is not found in the system.
   * - parentNotFoundError
     - 404
     - The parent node requested is not found in the system.
   * - checkDoesNotSupportTargets
     - 400
     - The check type does not support targets.
   * - requestTimeout
     - 500
     - The system has timed out. Please attempt the request again.
   * - requestTooLargeError
     - 413
     - The response body is too large.
   * - internalError
     - 500
     - The system suffered an internal failure.
   * - notImplementedError
     - 501
     - The request is for a feature that has not yet been implemented.
   * - systemFailureError
     - 503
     - The system is experiencing heavy load or another system failure.

All error responses have the following elements:

- The ``code`` element shows the HTTP error code.
- The ``type`` element shows the type of error.
- The ``request_id`` helps API operators debug the request in a support ticket,
  if necessary.
- The ``message`` field, when present, informs the user of the exact problem
  that the API detected.

  The following examples show the XML and JSON response body for a ``404``
  notFoundError:

   
  **Example: XML Not Found Fault**

  .. code::

      <?xml version="1.0" encoding="UTF-8"?>
      <fault><type>notFoundError</type><code>404</code><message>Item not found.<message><details>Error Details...</details>
      </fault>

   
  **Example: JSON Not Found Fault**

  .. code::

      {
          "type": "notFoundError",
          "code": "404",
          "message": "Item not found.",
          "details": "Error Details..."
      }
