.. _gsg-create-an-alarm:

Create an alarm
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In this exercise, you set an `alarm <#>`__ for the entity. This example
alarm sends you a warning alert if the average PING response time is
over 50 ms. Remember that alarms always have an entity associated with
them; alarm URLs contain the entity URL. In this example, the entity ID
is enn14Ch5mc, so you issue the following request to create the alarm
and associate it with the entity.

..  note::
      Note
      You cannot customize the Subject line of an alarm email notification,
      but you can customize the body as specified in the alarm criteria. In
      the following example, the "return new AlarmStatus" text in parenthesis,
      ``(OK)`` and ``(WARNING)``, can be customized. There is a 16,384
      character limit on the criteria attribute.

 
**Example: Create an alarm, request: cURL**

.. code::

    curl -i -X POST \
    --data-binary \
    '{
      "check_id": "chyYWNw59I",
      "notification_plan_id": "npkmLh5vVk",
      "criteria": "if (metric[\"duration\"] < 50) { return OK } return WARNING"
    }' \
    -H 'X-Auth-Token: $AUTH_TOKEN \
    -H 'Content-Type: application/json' \
    -H 'Accept: application/json' \
    'https://monitoring.api.rackspacecloud.com/v1.0/$TENANTID/entities/enn14Ch5mc/alarms'

 
**Create an alarm, response: cURL**

.. code::

    HTTP/1.1 201 Created
    X-Ratelimit-Remaining: 49947
    X-Response-Id: .rh-ew99.h-dfw1-maas-prod-api1.r-Kti7H0py.c-39599.ts-1329418764114.v-b9d7626
    Content-Length: 0
    X-Lb: dfw1-maas-prod-api0
    X-Ratelimit-Type: global
    X-Ratelimit-Limit: 50000
    Location: https://monitoring.api.rackspacecloud.com/v1.0/$TENANTID/entities/enn14Ch5mc/alarms/alIxnPKcZp
    Date: Thu, 16 Feb 2012 18:59:24 GMT
    X-Ratelimit-Window: 24 hours
    Content-Type: text/plain

 
**Create an alarm, request: raxmon**

.. code::

    raxmon-alarms-create --criteria="if (metric[\"average\"] < 50) { return new AlarmStatus(OK); }
              return new AlarmStatus(WARNING);" --check-id=chyYWNw59I --notification-plan=npkmLh5vVk --entity-id=enn14Ch5mc

 
**Create an alarm, response: raxmon**

.. code::

    Resource created. ID: alIxnPKcZp

If the endpoint returns a response code of ``201 Created`` and a
``Location`` header that contains the URL of the new alarm, the alarm
was successfully created; otherwise the endpoint returns an error.

Note that because alarms are shared among all of the checks on an
entity, if you have multiple HTTP URLs, you will receive alerts if any
of the checks are lagging.

You can list the available alarms as follows.

 
**List alarms, request: cURL**

.. code::

    curl -i -X GET \
    -H 'X-Auth-Token: $AUTH_TOKEN' \
    -H 'Accept: application/json' \
    'https://monitoring.api.rackspacecloud.com/v1.0/$TENANTID/entities/enn14Ch5mc/alarms'

 
**List alarms, response: cURL**

.. code::

    HTTP/1.1 200 OK
    X-Ratelimit-Remaining: 49941
    X-Response-Id: .rh-qRGT.h-ord1-maas-prod-api0.r-UH0HesoS.c-404.ts-1329420284585.v-a037e7a
    Transfer-Encoding: chunked
    Vary: Accept-Encoding
    X-Lb: ord1-maas-prod-api0
    X-Ratelimit-Type: global
    X-Ratelimit-Limit: 50000
    Date: Thu, 16 Feb 2012 19:24:44 GMT
    X-Ratelimit-Window: 24 hours
    Content-Type: application/json; charset=UTF-8

    36e
    {
        "values": [
            {
                "id": "alIxnPKcZp",
                "label": null,
                "check_type": "remote.ping",
                "check_id": null,
                "criteria": "if (metric[\"average\"] < 50) { return new AlarmStatus(OK); } return new AlarmStatus(WARNING);",
                "notification_plan_id": "npkmLh5vVk",
                "created_at": 1329418764882,
                "updated_at": 1329418764882
            },
        ],
        "metadata": {
            "count": 2,
            "limit": 100,
            "marker": null,
            "next_href": null
        }
    }

 
**List alarms, request: raxmon**

.. code::

    raxmon-alarms-list --entity-id=enn14Ch5mc --details

 
**List alarms, response: raxmon**

.. code::

    {'criteria': u'if (metric["average"] < 50) { return new AlarmStatus(OK); } return new AlarmStatus(WARNING);',
     'driver': <rackspace_monitoring.drivers.rackspace.RackspaceMonitoringDriver object at 0x100649ad0>,
     'entity_id': u'enn14Ch5mc',
     'id': u'alIxnPKcZp',
     'notification_plan_id': u'npkmLh5vVk',
     'type': u'remote.ping'}

    Total: 1

The results show there is one alarm for the entity.
