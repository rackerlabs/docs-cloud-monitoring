.. _alarm-notification-history-operations:

==========================
Alarm notification history
==========================

The monitoring service keeps a record of notifications sent for each alarm.
This history is further subdivided by the check on which the notification
occurred. Every attempt to send a notification is recorded, making this
history a valuable tool in diagnosing issues with unreceived notifications,
in addition to offering a means of viewing the history of an alarm's statuses.

Alarm notification history is accessible as a time series collection. When
accessing a time series collection, two parameters beyond the base paginated
collection API are available: from and to. For details, see
:ref: `Time Series Collection <time-series-collections>`.

By default alarm notification history is stored for 30 days and the
API queries the last 7 days of information.

Use the following alarms notification history API operations to view the
notification history for alarms and checks.

.. contents::
   :local:
   :depth: 1

.. include:: methods/get-list-alarm-notification-history.rst
.. include:: methods/get-list-alarm-notification-history-by-checkid.rst
.. include:: methods/get-list-a-single-alarm-notification.rst
