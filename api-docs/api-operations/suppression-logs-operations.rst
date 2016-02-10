.. _suppression-logs-operations:

~~~~~~~~~~~~~~~~
Suppression logs
~~~~~~~~~~~~~~~~

.. contents::
   :local:
   :depth: 1
   
The monitoring service maintains a record of alarms that are suppressed
during the time that a suppression is active. Suppression logs are
accessible as a
:ref: `Time Series Collection <time-series-collection>`.
By default the API queries the last 7 days of suppression log information.

Use the suppression logs API operations to create, view, update,
and manage suppression logs.

.. include:: methods/get-list-suppression-logs-suppression-logs.rst
