
.. _gsg-create-a-check:

Create a check
~~~~~~~~~~~~~~~~~~~~~~~

Any entity that you create can have many checks, each monitoring a different aspect 
of the entity. In this exercise, you create and test a PING check to verify that the web 
server is responding. Use the following attributes:

label
    Assigns a meaningful name to the check. In the following examples,
    the check is named "Website check 1". You can choose a different
    name or use the same one.

type
    Specifies the type of check that you're creating.

monitoring\_zones\_poll
    Specifies the monitoring zones that will launch the check. The
    examples use ``mzdfw``.

timeout
    Specifies the maximum time Cloud Monitoring waits for the check to
    run before considering it to have failed. This value must be less
    than the value for ``period``.

period
    Specifies how often Cloud Monitoring `collectors <#>`__ run the
    check. This value cannot be less than the value for ``timeout``

target\_alias
    Resolves the check to an IP address. The example request, next,
    shows this value as ``default`` because that was the name given as
    the IP address when the entity was created. See the following
    example for an illustration.


**Example: Create a PING check, request: cURL**

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
    -H "X-Auth-Token: $AUTH_TOKEN" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json" \
    'https://monitoring.api.rackspacecloud.com/v1.0/$TENANTID/entities/enn14Ch5mc/checks'

 
**Example: Create a PING check, response: cURL**

.. code::

    HTTP/1.1 201 Created
    Date: Fri, 24 Feb 2012 06:28:51 GMT
    Location: https://monitoring.api.rackspacecloud.com/v1.0/$TENANTID/entities/enn14Ch5mc/checks/chyYWNw59I
    X-RateLimit-Limit: 50000
    X-RateLimit-Remaining: 49969
    X-RateLimit-Window: 24 hours
    X-RateLimit-Type: global
    X-Response-Id: .rh-9pAY.h-lon3-maas-prod-api1.r-2ruPuxLu.c-99739.ts-1330064931513.v-c576983
    X-LB: lon3-maas-prod-api1
    Content-Length: 0
    Content-Type: text/plain

If the check is successfully created, the endpoint returns a response
code of ``201 Created`` and a ``Location:`` header containing the URL of
the check. In this example, the check ID is chyYWNw59I, but yours will
be different.

If an error message is returned, see the `Faults section<monitoring-faults>` section in the *Rackspace Cloud
Monitoring Developer's guide*.

..  note::

      Checks are *always* associated with an entity. Therefore all check URLs
      contain the entity URL. For example, the ID of the entity created
      earlier in this tutorial is enn14Ch5mc, so the check URLs would begin
      with
      **https://monitoring.api.rackspacecloud.com/v1.0/010101/entities/enn14Ch5mc/**.

 
**Example: Create a PING check, request: raxmon**

.. code::

    raxmon-checks-create --entity-id=enn14Ch5mc --type=remote.ping --label="Website check 1" --monitoring-zones=mzdfw --timeout=30 --period=60 --target-alias=default

 
**Example: Create a PING check, response: raxmon**

.. code::

    Resource created. ID: chyYWNw59I
