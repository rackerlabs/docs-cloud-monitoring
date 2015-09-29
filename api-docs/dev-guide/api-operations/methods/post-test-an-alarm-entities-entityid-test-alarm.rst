.. _test-an-alarm:

Test an alarm
^^^^^^^^^^^^^
.. code::

    POST /entities/{entityId}/test-alarm

The ``test_alarm`` endpoint is used to post alarm criteria and alarm
data to test whether the alarm criteria is valid and to show
how the alarm state is evaluated. You cannot specify an existing
alarm ID with this endpoint; instead, you provide the alarm's criteria
within the request. The ``test_alarm`` response not only provides
the final evaluated state, but also includes all state transitions
noticed during the calculation.

To test an alarm, you need to provide one or more observations. An
observation consists of a set of metrics from a single data center,
such as DFW, LON, and IAD. A group of observations consist of a set of
metrics from more than one data center.

Cloud Monitoring passes the observation(s) that you provide to the event
processors, and then captures and returns an array of all state changes
in the same order that they were evaluated. The state returned by the
test alarm depends both upon the criteria and the metrics provided for
the test alarm. For example, if you have a criteria that returns "CRITICAL"
if a certain metric is above a threshold and "OK" otherwise, you should
expect to receive a "CRITICAL" response if you provide a metric with a
value above that threshold and an "OK" response if you provide a metric with
a value below that threshold.

When you test an alarm, you provide a list of check data, which you can
retrieve from a :ref:`test check <test-a-check>` operation.

.. note::
   A ``consecutiveCount`` of 1 is always used for these calls.
   If another value is set in your criteria it is overridden.

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
|500                       |Internal Server Error    |An unexpected condition  |
|                          |                         |was encountered.         |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The system is            |
|                          |                         |experiencing heavy load  |
|                          |                         |or another system        |
|                          |                         |failure.                 |
+--------------------------+-------------------------+-------------------------+

Request
"""""""
The following table shows the header parameters for the request:

+-----------------+----------------+-----------------------------------------------+
|Name             |Type            |Description                                    |
+=================+================+===============================================+
|X-Auth-Token     |String          |A valid authentication token with              |
|                 |*(Required)*    |administrative access. For details, see        |
|                 |                |:ref:`Get your credentials <auth-credentials>` |
+-----------------+----------------+-----------------------------------------------+

**Example Test alarms criteria**

.. code::

   :set consecutiveCount=1
       if (metric["busy_workers"] > 2) {
         return new AlarmStatus(WARNING);
       }
       if (metric["busy_workers"] > 3) {
         return new AlarmStatus(CRITICAL);
       }
       return new AlarmStatus(OK);

**Example Test alarm: JSON request**

.. code::

   {
       "criteria": "if (metric[\"code\"] == \"404\") { return new AlarmStatus(CRITICAL, \"not found\"); } return new AlarmStatus(OK);",
       "check_data": [
           {
               "timestamp": 1319222001982,
               "monitoring_zone_id": "mzxJ4L2IU",
               "available": true,
               "status": "code=200,rt=0.257s,bytes=0",
               "metrics": {
                   "bytes": {
                       "type": "i",
                       "data": "0"
                   },
                   "tt_firstbyte": {
                       "type": "I",
                       "data": "257"
                   },
                   "tt_connect": {
                       "type": "I",
                       "data": "128"
                   },
                   "code": {
                       "type": "s",
                       "data": "200"
                   },
                   "duration": {
                       "type": "I",
                       "data": "257"
                   }
               }
           }
       ]
   }

Response
""""""""
**Example Test alarm: JSON response**

.. code::

   [
       {
           "timestamp": 1319224500831,
           "state": "OK",
           "status": "Matched default return statement"
       }
   ]

**Example Test alarm, multi-state: JSON response**

.. code::

   [
       {
           "state": "OK",
           "status": "Ping responds as expected.",
           "timestamp": "1417732774575"
       },
       {
           "state": "WARNING",
           "status": "blah.",
           "timestamp": "1417732795200"
       },
       {
           "state": "CRITICAL",
           "status": "cnt=6,avail=0,min=-nan,max=-nan,avg=-nan",
           "timestamp": "1417732795216"
       }
   ]
