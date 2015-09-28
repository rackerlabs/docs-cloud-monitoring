.. _metrics-operations:

~~~~~~~
Metrics
~~~~~~~
When Monitoring checks run, they generate metrics. These metrics
are stored as full resolution data points in the Cloud Monitoring
system. Full resolution data points are periodically rolled up
(condensed) into coarser data points.

Depending on your needs, you can use the metrics API to fetch
individual data points (fine-grained) or rolled up data points
(coarse-grained) over a period of time.

Use the metrics API operations to create, view, and manage metrics resources.

* :ref:`cumulative-metrics`
* :ref:`data`
* :ref:`data-point`
* :ref:`metrics-api`


.. _cumulative-metrics:

Cumulative and instantaneous metrics
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Numeric metrics present numbers in one of the two ways, as
cumulative values or instantaneous (snapshot) values.

+----------------+------------------------------------------------+------------------------------+--------------------------------------+
| Type           | Alarm                                          | Graph                        | Description                          |
+================+================================================+==============================+======================================+
| Cumulative     | if (rate(metric[$metricname]) > $threshold) {  | Draw the change rates of     | The value presents cumulative        |
| metric         | return new AlarmStatus(CRITICAL,               | the values, the "derivative  | statistics from the time the metric  |
|                | 'rate is greater than $threshold');            | of order of one."            | was created. The value keeps         |
|                | }                                              |                              | growing.                             |
|                |                                                |                              |                                      |
|                |                                                |                              | Example: agent.network - rx-bytes    |
+----------------+------------------------------------------------+------------------------------+--------------------------------------+
| Instantaneous  | if (metric[$metricname]) > $threshold)         | Typically draw the           | The value presents the state at      |
| metric         | {                                              | value directly.              | the time the metric is collected.    |
|                | return new AlarmStatus(CRITCAL,                |                              | The value can change in any          |
|                | 'value is greater than $threshold');           |                              | direction.                           |
|                | }                                              |                              |                                      |
|                |                                                |                              | Example: agent.filesystem - used     |
+----------------+------------------------------------------------+------------------------------+--------------------------------------+

.. _data:

Data granularity
~~~~~~~~~~~~~~~~
Cloud Monitoring supports several granularities of data:
full resolution data and rollups computed at 5, 20, 60, 240
and 1440 minute intervals.

When you fetch metrics data points, you specify several parameters
to control the granularity of data returned:

* A time range for the points
* Either the number of points you want returned or the resolution of the
  data you want returned

When you query by points, the API selects the resolution that will
return you the number of points you requested. The API makes
the assumption of a 30 second frequency, performs the calculation,
and selects the appropriate resolution.

.. note::
   Because the API performs calculations to determine the points returned
   for a particular resolution, the number of points returned may differ
   from the specific number of points you request.

Consider that you want to query data for a 48-hour time range
between the timestamps from=1354647221000 and to=1358794421000
(specified in milliseconds that have elapsed since January 1, 1970).
The following table shows the number of points that the API returns
for a given resolution:

+------------------------+--------------------+
| You specify resolution | API returns points |
+========================+====================+
| FULL                   | 5760               |
+------------------------+--------------------+
| MIN5                   | 576                |
+------------------------+--------------------+
| MIN20                  | 144                |
+------------------------+--------------------+
| MIN60                  | 48                 |
+------------------------+--------------------+
| MIN240                 | 12                 |
+------------------------+--------------------+
| MIN1440                | 2                  |
+------------------------+--------------------+

Alternately, the next table shows the resolution the
API calculates depending upon the number of points you request:

+------------------------+---------------------------+
| You specify points in  | API calculates resolution |
| the range              |                           |
+========================+===========================+
| 3168-infinite          | FULL                      |
+------------------------+---------------------------+
| 360-3167               | MIN5                      |
+------------------------+---------------------------+
| 96-359                 | MIN20                     |
+------------------------+---------------------------+
| 30-95                  | MIN60                     |
+------------------------+---------------------------+
| 7-29                   | MIN240                    |
+------------------------+---------------------------+
| 0-6                    | MIN1440                   |
+------------------------+---------------------------+

.. _data-point:

Data point expiration
~~~~~~~~~~~~~~~~~~~~~
Cloud Monitoring expires data points according to the following schedule:

+------------+------------+
| Resolution | Expiration |
+============+============+
| FULL       | 2 days     |
+------------+------------+
| MIN5       | 10 days    |
+------------+------------+
| MIN20      | 20 days    |
+------------+------------+
| MIN60      | 155 days   |
+------------+------------+
| MIN240     | 300 days   |
+------------+------------+
| MIN1440    | 5 years    |
+------------+------------+

.. _metrics-api:

Metrics API operations
~~~~~~~~~~~~~~~~~~~~~~

.. include:: methods/get-list-metrics-by-check-id-entities-entityid-checks-checkid-metrics.rst
.. include:: methods/get-get-data-points-by-metric-name-entities-entityid-checks-checkid-metrics-metricname-plot.rst
