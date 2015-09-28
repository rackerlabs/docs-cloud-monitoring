.. _changelogs-operations.rst:

Changelogs
~~~~~~~~~~
The monitoring service records changelogs for alarm statuses.
Changelogs are accessible as a time series collection. When accessing a
time series collection, two parameters beyond the base paginated
collection API are available: from and to. For details,
see `Time Series Collection <http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/api-time-series-collections.html>`_.

By default the API queries the last 7 days of changelog information.

Use the changelogs API operations to view and manage changelogs.

.. include:: methods/get-list-alarm-changelogs-changelogs-alarms.rst
.. include:: methods/get-get-alarm-changelogs-by-entity-id-changelogs-alarms.rst
