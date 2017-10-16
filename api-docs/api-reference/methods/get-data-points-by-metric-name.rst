.. _get-data-points-by-metric-name:

Get data points by  metric name
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /entities/{entityId}/checks/{checkId}/metrics/{metricName}/plot

Queries for all data points of ``metricName`` between two points in time.

``metricName`` refers to the fully concatenated metric described in
:ref:`Metrics API operations
<metrics-operations>`.

This operation does not require a request body.

This operation returns a response body that lists all data points
between two points in time for ``metricName``. To control the data points
returned in the response body, specify the required request URI
parameters described in the following table.

.. note::
   Rackspace Monitoring is currently limited to 1440 data points returned
   per request. If all your data is not returned, break your
   request into multiple requests across smaller time ranges.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request completed.   |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad request              |The system received an   |
|                          |                         |invalid value in a       |
|                          |                         |request.                 |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |The system received a    |
|                          |                         |request from a user that |
|                          |                         |is not authenticated.    |
+--------------------------+-------------------------+-------------------------+
|403                       |Forbidden                |The system received a    |
|                          |                         |request that the user is |
|                          |                         |not authorized to make.  |
+--------------------------+-------------------------+-------------------------+
|405                       |Method Not Allowed       |The method specified in  |
|                          |                         |the request is not       |
|                          |                         |enabled for the          |
|                          |                         |resource. A list of      |
|                          |                         |valid methods for the    |
|                          |                         |requested resource is    |
|                          |                         |included in the response.|
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The response body is too |
|                          |                         |large.                   |
+--------------------------+-------------------------+-------------------------+
|500                       |Internal Server Error    |An unexpected condition  |
|                          |                         |was encountered.         |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The system is            |
|                          |                         |experiencing heavy load  |
|                          |                         |or another system        |
|                          |                         |failure.                 |
+--------------------------+-------------------------+-------------------------+

Request
-------
The following table shows the header parameters for the request:

+-----------------+----------------+-----------------------------------------------+
|Name             |Type            |Description                                    |
+=================+================+===============================================+
|X-Auth-Token     |String          |A valid authentication token with              |
|                 |*(Required)*    |administrative access. For details, see        |
|                 |                |:ref:`Get your credentials <get-credentials>`  |
+-----------------+----------------+-----------------------------------------------+


The following table shows the URI parameters for the request:

+-----------------+----------------+-------------------------------------------+
|Name             |Type            |Description                                |
+=================+================+===========================================+
|{fromTimeStamp}  |String          |``from={fromTimeStamp}`` The timestamp     |
|                 |*(Required)*    |marking the beginning of the time range.   |
|                 |                |The timestamp should be represented as the |
|                 |                |number of milliseconds that have elapsed   |
|                 |                |since January 1, 1970. Note that "Unix     |
|                 |                |time" is typically represented in seconds, |
|                 |                |so in many cases it will be necessary to   |
|                 |                |convert this to milliseconds.              |
+-----------------+----------------+-------------------------------------------+
|{toTimeStamp}    |String          |``to={toTimeStamp}`` The timestamp marking |
|                 |*(Required)*    |the end of the time range. The timestamp   |
|                 |                |should be represented as the number of     |
|                 |                |milliseconds that have elapsed since       |
|                 |                |January 1, 1970. Note that "Unix time" is  |
|                 |                |typically represented in seconds, so in    |
|                 |                |many cases it will be necessary to convert |
|                 |                |this to milliseconds.                      |
+-----------------+----------------+-------------------------------------------+
|{numberPoints}   |String          |``points={numberPoints}`` The number of    |
|                 |*(Required)*    |points you want in the results. Either     |
|                 |                |points or resolution is required. If both  |
|                 |                |are absent, the query will not validate    |
|                 |                |and will return an error. For more         |
|                 |                |information about querying by points, see  |
|                 |                |:ref:`Data granularity <data>`.            |
+-----------------+----------------+-------------------------------------------+
|{granularity}    |String          |``resolution={granularity}`` The           |
|                 |*(Required)*    |granularity of data to query. Valid values |
|                 |                |include: FULL, MIN5, MIN20, MIN60, MIN240  |
|                 |                |or MIN1440. Either points or resolution is |
|                 |                |required. If both are absent, the query    |
|                 |                |will not validate and will return an       |
|                 |                |error. For more information about querying |
|                 |                |by resolution, see :ref:`Data granularity  |
|                 |                |<data>`.                                   |
+-----------------+----------------+-------------------------------------------+
|{stats}          |String          |``select={stats}`` The stats that you want |
|                 |*(Required)*    |returned for the data. The stats available |
|                 |                |for selection are average, variance, min   |
|                 |                |and max. By default, the response includes |
|                 |                |the average stat only. You can use         |
|                 |                |multiple select parameters in a single     |
|                 |                |request. For example, select=variance &    |
|                 |                |select=max displays both variance and max  |
|                 |                |in the response.                           |
+-----------------+----------------+-------------------------------------------+

.. note:: This operation does not accept a request body.

Response
--------

**Example Fetch data points, full resolution: JSON response**

.. code::

   {
       "values": [
           {
               "numPoints": 1,
               "average": 4,
               "timestamp": 1335744000000
           },
           {
               "numPoints": 1,
               "average": 6,
               "timestamp": 1335744000030
           }
       ],
       "metadata": {
           "count": 2,
           "limit": null,
           "marker": null,
           "next_marker": null,
           "next_href": null
       }
   }

**Example Fetch data points, rollup: JSON response**

.. code::

   {
       "values": [
           {
               "numPoints": 1141,
               "average": 4.1,
               "timestamp": 1335744000000
           },
           {
               "numPoints": 2880,
               "average": 6.05,
               "timestamp": 1335830400000
           }
       ],
       "metadata": {
           "count": 2,
           "limit": null,
           "marker": null,
           "next_marker": null,
           "next_href": null
       }
   }
