.. _metrics-operations:

=======
Metrics
=======

When Monitoring checks run, they generate metrics. These metrics are stored as
full resolution data points in the Rackspace Monitoring system. Full resolution
data points are periodically rolled up (condensed) into coarser data points.

Depending on your needs, you can use the metrics API to fetch individual data
points (fine-grained) or rolled up data points (coarse-grained) over a period
of time.

The following sections describe the different types of metrics and provide
information about the metrics API operations you can use to review metrics
data.

* :ref:`cumulative-metrics`
* :ref:`data`
* :ref:`data-point`
* :ref:`metrics-api`


.. _cumulative-metrics:

Cumulative and instantaneous metrics
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Numeric metrics present numbers in one of the two ways, as
cumulative values or instantaneous (snapshot) values.

.. list-table:: **Numeric metric types**
   :widths: 15 30 20 20
   :header-rows: 1

   * - Type
     - Alarm
     - Graph
     - Description
   * - Cumulative metric
     - if (rate(metric[$metricname]) > $threshold)
       {return new AlarmStatus(CRITICAL, 'rate is greater than $threshold');
       }
     - Draw the change rates of the values, the "derivative of order of one."
     - The value presents cumulative statistics from the time the metric
       was created. The value keeps growing.

       Example: ``agent.network - rx-bytes``
   * - Instantaneous metric
     - if (metric[$metricname]) > $threshold)
       { return new AlarmStatus(CRITCAL, 'value is greater than $threshold');
       }
     - Typically draw the value directly.
     - The value presents the state at the time the metric is collected.
       The value can change in any direction.

       Example: ``agent.filesystem - used``

.. _data:

Data granularity
~~~~~~~~~~~~~~~~

Rackspace Monitoring supports several granularities of data: full resolution
data and rollups computed at 5, 20, 60, 240 and 1440 minute intervals.

When you fetch metrics data points, you specify several parameters to control
the granularity of data returned:

* A time range for the points
* Either the number of points you want returned or the resolution of the
  data you want returned

When you query by points, the API selects the resolution that will return you
the number of points you requested. The API makes the assumption of a 30 second
frequency, performs the calculation, and selects the appropriate resolution.

.. note::
   Because the API performs calculations to determine the points returned
   for a particular resolution, the number of points returned may differ
   from the specific number of points you request.

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

Alternately, the next table shows the resolution the API calculates depending
upon the number of points you request:

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

Rackspace Monitoring expires data points according to the following schedule:

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

Use the following metrics API operations to create, view, and manage metrics
resources.

.. contents::
   :local:
   :depth: 1

.. include:: methods/get-list-metrics-by-check-id.rst
.. include:: methods/get-data-points-by-metric-name.rst
