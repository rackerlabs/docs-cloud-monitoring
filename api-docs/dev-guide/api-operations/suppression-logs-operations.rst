.. _suppression-logs-operations:

~~~~~~~~~~~~~~~~
Suppression logs
~~~~~~~~~~~~~~~~
The monitoring service maintains a record of alarms that are suppressed
during the time that a suppression is active. Suppression logs are
accessible as a
`Time Series Collection <http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/api-time-series-collections.html>`_.
By default the API queries the last 7 days of suppression log information.

Use the suppression logs API operations to create, view, update,
and manage suppression logs.

.. include:: methods/get-list-suppression-logs-suppression-logs.rst
