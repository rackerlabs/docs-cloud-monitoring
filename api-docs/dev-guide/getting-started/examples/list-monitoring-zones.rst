
.. _gsg-list-monitoring-zones:


List monitoring zones
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Before creating a check for the new entity, choose the `monitoring
zones <#>`__ from which you want to run the check. Cloud Monitoring is
server monitored from several monitoring zones to reduce the risk of
noisy alarms and check the response time from different locations around
the world.

Request a list of the monitoring zones, examine the response, and choose
the zone or zones from which you want to launch your first check.

 
**Example: List monitoring zones, request: cURL**

.. code::

    curl -i -X GET \
    -H 'X-Auth-Token: auth_token' \
    -H 'Accept: application/json' \
    'https://monitoring.api.rackspacecloud.com/v1.0/010101/monitoring_zones'

 
**Example: List monitoring zones, response: cURL**

.. code::

    HTTP/1.1 200 OK
    X-Ratelimit-Remaining: 49982
    X-Response-Id: .rh-YQzc.h-lon3-maas-prod-api0.r-kCU9r8nq.c-27354.ts-1329332815801.v-3aec925
    Transfer-Encoding: chunked
    Vary: Accept-Encoding
    X-Lb: lon3-maas-prod-api1
    X-Ratelimit-Type: global
    X-Ratelimit-Limit: 50000
    Date: Wed, 15 Feb 2012 19:06:55 GMT
    X-Ratelimit-Window: 24 hours
    Content-Type: application/json; charset=UTF-8

    428
    {
        "values": [
            {
                "id": "mzdfw",
                "label": "dfw",
                "country_code": "US",
                "source_ips": [
                    "2001:4800:7902:0001::/64",
                    "50.56.142.128/26"
                ]
            },
            {
                "id": "mzhkg",
                "label": "hkg",
                "country_code": "HK",
                "source_ips": [
                    "180.150.149.64/26",
                    "2401:1800:7902:1:0:0:0:0/64"
                ]
            },
            {
                "id": "mzlon",
                "label": "lon",
                "country_code": "GB",
                "source_ips": [
                    "2a00:1a48:7902:0001::/64",
                    "78.136.44.0/26"
                ]
            },
            {
                "id": "mzord",
                "label": "ord",
                "country_code": "US",
                "source_ips": [
                    "2001:4801:7902:0001::/64",
                    "50.57.61.0/26"
                ]
            }
        ],
        "metadata": {
            "count": 4,
            "limit": 100,
            "marker": null,
            "next_href": null
        }
    }

 
**Example: List monitoring zones, request: raxmon**

.. code::

    raxmon-monitoring-zones-list --details

 
**Example: List monitoring zones, response: raxmon**

.. code::

    {'country_code': u'US',
     'driver': <rackspace_monitoring.drivers.rackspace.RackspaceMonitoringDriver object at 0x100562410>,
     'extra': {},
     'id': u'mzdfw',
     'label': u'dfw',
     'source_ips': [u'2001:4800:7902:0001::/64', u'50.56.142.128/26']}
    {'country_code': u'HK',
     'driver': <rackspace_monitoring.drivers.rackspace.RackspaceMonitoringDriver object at 0x100562410>,
     'extra': {},
     'id': u'mzhkg',
     'label': u'hkg',
     'source_ips': [u'180.150.149.64/26', u'2401:1800:7902:1:0:0:0:0/64']}
    {'country_code': u'GB',
     'driver': <rackspace_monitoring.drivers.rackspace.RackspaceMonitoringDriver object at 0x100562410>,
     'extra': {},
     'id': u'mzlon',
     'label': u'lon',
     'source_ips': [u'2a00:1a48:7902:0001::/64', u'78.136.44.0/26']}
    {'country_code': u'US',
     'driver': <rackspace_monitoring.drivers.rackspace.RackspaceMonitoringDriver object at 0x100562410>,
     'extra': {},
     'id': u'mzord',
     'label': u'ord',
     'source_ips': [u'2001:4801:7902:0001::/64', u'50.57.61.0/26']}

**Next step:** Create several checks for the new entity.
