.. _rate-limits:

Rate limits
~~~~~~~~~~~~~~~

The following table specifies the default rate limits for different API
operations.

**Table: Cloud Monitoring default rate limits**

+-----------------------------------------------+------------------------------+
| URI                                           | Limit                        |
+===============================================+==============================+
| ``/*``                                        |50000 requests / 24 hours     |
+-----------------------------------------------+------------------------------+
| ``/entities/*/test-check``                    | 500 requests / 24 hours      |
+-----------------------------------------------+------------------------------+
| ``/entities/*/test-alarm``                    | 500 requests / 24 hours      |
+-----------------------------------------------+------------------------------+
|``/notifications/*/test, /test-notifications`` | 200 request / 24 hours       |
+-----------------------------------------------+------------------------------+

Each API response also contains the following headers:

**Table: Cloud Monitoring API response headers**

+--------------------+------------------------------------------+
| Header name        | Description                              |
+====================+==========================================+
| X-RateLimit-Limit  | Limit in affect for the current request. |
+--------------------+------------------------------------------+
| X-RateLimit-Used   | How close you are to being rate limited. |
+--------------------+------------------------------------------+
| X-RateLimit-Window | Rate limit window.                       |
+--------------------+------------------------------------------+
| X-RateLimit-Type   | Type of the rate limit which applies to  |
|                    | the current,request.                     |
+--------------------+------------------------------------------+


Type of the rate limit which applies to the current request.
If you exceed the thresholds established for your account, you'll
receive a 400, Limit has been reached response. HTTP responses are
returned with a ``Reply-After`` header (number of seconds) to notify the
client when it can attempt to try again.

To view the limits that apply to your account, see the Account API operations in the 
:ref:`API Reference <api-reference>`.
