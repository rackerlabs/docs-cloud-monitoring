.. _gsg-test-check:

Testing the check
~~~~~~~~~~~~~~~~~

Testing the check runs the check once and lists the check's metrics.
This is an easy way to verify and view your metrics. Later, you can use
the test check output to help you build alarms.

 
**Example: Create a test check, request: cURL**

.. code::

    curl -i \
    --data-binary \
    '{ "details" : {  },
      "label" : "Website check 1",
      "monitoring_zones_poll" : [ "mzdfw" ],
      "period" : "60",
      "target_alias" : "default",
      "timeout" : 30,
      "type" : "remote.ping"
    }' \
    -H 'X-Auth-Token: $AUTH_TOKEN' \
    -H 'Content-Type: application/json' \
    -H 'Accept: application/json' \
    'https://monitoring.api.rackspacecloud.com/v1.0/$TENANTID/entities/enn14Ch5mc/test-check/'

 
**Example:  Create a test check, response: cURL**

.. code::

    HTTP/1.1 200 OK
    X-Ratelimit-Remaining: 497
    X-Response-Id: .rh-VE2m.h-lon3-maas-prod-api0.r-pm6oiwjm.c-37726.ts-1329263604920.v-3aec925
    Transfer-Encoding: chunked
    Vary: Accept-Encoding
    X-Lb: lon3-maas-prod-api1
    X-Ratelimit-Type: test_check
    X-Ratelimit-Limit: 500
    Date: Tue, 14 Feb 2012 23:53:24 GMT
    X-Ratelimit-Window: 24 hours
    Content-Type: application/json; charset=UTF-8

    [
        {
            "timestamp": 1329263613579,
            "monitoring_zone_id": "mzdfw",
            "available": true,
            "status": "cnt=5,avail=100,min=0.0018,max=0.0020,avg=0.0019",
            "metrics": {
                "minimum": {
                    "type": "n",
                    "data": "1.808000029996e-03"
                },
                "available": {
                    "type": "n",
                    "data": "1.000000000000e+02"
                },
                "maximum": {
                    "type": "n",
                    "data": "1.990000018850e-03"
                },
                "count": {
                    "type": "i",
                    "data": "5"
                },
                "average": {
                    "type": "n",
                    "data": "1.866600010544e-03"
                }
            }
        }
    ]

 
**Example: Create a test check, request: raxmon**

.. code::

    raxmon-checks-test --entity-id=enn14Ch5mc --type=remote.ping --monitoring-zones=mzdfw --timeout=30 --period=60 --target-alias=default

 
**Example: Create a test check, response: raxmon**

.. code::

    [{u'available': True, u'timestamp': 1329334696399,
    u'monitoring_zone_id': u'mzdfw',
    u'status': u'cnt=5,avail=100,min=0.0018,max=0.0020,avg=0.0019',
    u'metrics': {u'count': {u'data': u'5', u'type': u'i'},
    u'available': {u'data': u'1.000000000000e+02', u'type': u'n'},
    u'average': {u'data': u'1.874800003134e-03', u'type': u'n'},
    u'minimum': {u'data': u'1.803999999538e-03', u'type': u'n'},
    u'maximum': {u'data': u'2.022000029683e-03', u'type': u'n'}}}]
