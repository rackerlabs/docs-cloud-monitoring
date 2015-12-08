
.. _gsg-list-all-checks:

Listing all checks for the entity
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


You can list the checks for a specific entity at any time by running a
``GET`` request for the entity ID.

 
**Example List all checks for an entity, request: cURL**

.. code::

    curl -i -X GET \
    -H 'X-Auth-Token: auth_token' \
    -H 'Accept: application/json' \
    'https://monitoring.api.rackspacecloud.com/v1.0/010101/entities/enn14Ch5mc/checks'

 
**Example List all checks for an entity, response: cURL**

.. code::

    HTTP/1.1 200 OK
    X-Ratelimit-Remaining: 49967
    X-Response-Id: .rh-NGRc.h-dfw1-maas-prod-api0.r-fKxxaymj.c-34581.ts-1329407832952.v-b9d7626
    Transfer-Encoding: chunked
    Vary: Accept-Encoding
    X-Lb: dfw1-maas-prod-api1
    X-Ratelimit-Type: global
    X-Ratelimit-Limit: 50000
    Date: Thu, 16 Feb 2012 15:57:12 GMT
    X-Ratelimit-Window: 24 hours
    Content-Type: application/json; charset=UTF-8

    f37
    {
        "values": [
            {
                "id": "chyYWNw59I",
                "label": "Website Ping Check",
                "type": "remote.ping",
                "details": {},
                "monitoring_zones_poll": [
                    "mzord"
                ],
                "timeout": 30,
                "period": "60",
                "target_alias": "default",
                "target_hostname": null,
                "target_resolver": null,
                "disabled": false,
                "collectors": [
                    "co1LKEam0X"
                ],
                "created_at": 1328285429554,
                "updated_at": 1328285429554
            },
    }

 
**Example List all checks for an entity, request: raxmon**

.. code::

    raxmon-checks-list --entity-id=enn14Ch5mc

 
**Example List all checks for an entity, response: raxmon**

.. code::

    <Check: id=chyYWNw59I label=Website Ping Check...>
