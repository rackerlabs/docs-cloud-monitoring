.. _rate-limits:

======
Limits
======

All accounts, by default, have a preconfigured set of thresholds, or *limits*,
to manage capacity and prevent abuse of the system. The system recognizes two
kinds of limits: *rate limits* and *resource limits*. Rate limits are
thresholds that are reset after a certain amount of time passes. Absolute
limits are fixed. Rate limits are processed via the `Repose service`_.

To view the limits that apply to your account, use the
:ref:`Account API operations <account-operations>`.

.. note::

    If the default limits are too low for your particular application,
    contact Rackspace Cloud support to request an increase. All requests
    require reasonable justification.

.. _Repose service: http://www.openrepose.org


Rate limits
~~~~~~~~~~~

Rate limits are specified in terms of both a human-readable wildcard URI and a
machine-processable regular expression. The regular expression boundary
matcher ``^`` takes effect after the root URI path.

.. _api-info-limits-ratelimits:

.. list-table:: **Rackspace Monitoring default rate limits**
   :widths: 20 50
   :header-rows: 1

   * - URI
     - Limit
   * - ``/*``
     - 50000 requests / 24 hours
   * - ``/entities/*/test-check``
     - 500 requests / 24 hours
   * - ``/entities/*/test-alarm``
     - 500 requests / 24 hours
   * - ``/notifications/*/test, /test-notifications``
     - 200 request / 24 hours

Each API response also contains the following rate limit headers:

.. list-table:: ** Rackspace Monitoring API response headers**
   :widths: 20 50
   :header-rows: 1

   * - Header name
     - Description
   * - X-RateLimit-Limit
     - Limit in affect for the current request
   * - X-RateLimit-Used
     - How close you are to being rate limited
   * - X-RateLimit-Window
     - Rate limit window
   * - X-RateLimit-Type
     - Type of the rate limit which applies to the current request

When you exceed the thresholds established for your account, API requests
return the following error: ``400, Limit has been reached``. The HTTP response
includes a ``Reply-After`` header (number of seconds) to notify the
client when it can attempt to try again.

To view the limits that apply to your account, see the Account API operations
in the :ref:`API Reference <api-reference>`.

Resource limits
~~~~~~~~~~~~~~~

The following table below lists the default limits for different resources.
When you exceed the threshold for checks or alarms, API requests to create
a check or alarm return the
following error:  ``400 Limit has been reached``.

.. list-table:: ** Rackspace Monitoring resource limits**
   :widths: 20 50
   :header-rows: 1

   * - Resource
     - Limit
   * - checks
     - 1000
   * - alarms
     - 10000

To view the limits that apply to your account, use the `Account resource and API operations`_.

.. _Account resource and API operations: http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/service-account.html
