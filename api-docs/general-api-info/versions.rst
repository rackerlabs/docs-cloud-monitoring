Versions
~~~~~~~~~~


The Rackspace Monitoring API uses a URI versioning scheme. In the
URI scheme, the first element of the path contains the target version
identifier, for example ``https://monitoring.api.rackspacecloud.com/v1.0/…``.

 
**Example: Request with URI Versioning**

.. code::

    GET /v1.0/entities HTTP/1.1
    Host: monitoring.api.rackspacecloud.com/v1.0/12345/entities
    Accept: application/xml
    X-Auth-Token: eaaafd18-0fed-4b3a-81b4-663c99ec1cbb


New features and functionality that do not break API-compatibility will
be introduced in the current version of the API as extensions (see
below) and the URI will remain unchanged. Features or functionality
changes that would necessitate a break in API-compatibility will require
a new version, which will result in URI version being updated
accordingly. When new API versions are released, older versions will be
marked as ``DEPRECATED``. Providers should work with developers and
partners to ensure there is adequate time to migrate to the new version
before deprecated versions are discontinued.
