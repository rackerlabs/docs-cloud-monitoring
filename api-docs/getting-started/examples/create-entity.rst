
.. _gsg-create-an-entity:


Creating an entity
~~~~~~~~~~~~~~~~~~

The first thing you do to begin monitoring a resource is to create an
`entity <#>`__ that represents the resource in the monitoring system.

Use the following attributes to create the entity:

label
    Assigns a meaningful name to the entity. In the following examples,
    the server is named My Rackspace Server. You can choose a different
    name or use the same one, but note that the label is commonly a
    server name.

ip\_address
    Specifies the server's IP address or addresses. In the following
    examples, the IP address is named "default."

..  note::

      Remember to insert your authorization token and account number as
      previously described in
      :ref:`Authenticate to the Rackspace Cloud<authenticate-to-cloud>` .

 
**Example: Create an entity, request: cURL**

.. code::

    curl -i -X POST \
    --data-binary \
    '{ "ip_addresses" : { "default" : "192.0.2.15" },
      "label" : "My Rackspace Server",
      "metadata" : {  }
    }' \
    -H 'X-Auth-Token: $AUTH_TOKEN' \
    -H 'Content-Type: application/json' \
    -H 'Accept: application/json' \
    'https://monitoring.api.rackspacecloud.com/v1.0/$TENANTID/entities/'

 
**Example: Create an entity, response: cURL**

.. code::

    HTTP/1.1 201 Created
    Content-Length: 0
    X-Response-Id: .rh-ZWac.h-lon3-maas-prod-api0.r-To4aIzNP.c-25577.ts-1326394448414.v-0c7bb08
    X-Powered-By: Express
    Location: https://monitoring.api.rackspacecloud.com/v1.0/$TENANTID/entities/enn14Ch5mc
    Date: Thu, 12 Jan 2012 18:54:08 GMT
    Content-Type: text/plain

If the entity is successfully created, the endpoint returns a response
code of ``201 Created`` and a ``Location`` header with the URL
of the entity. Note that the entity ID is located at the end of the URL.
In this example, the entity ID is enn14Ch5mc. Every entity has a unique
ID, so yours will be different.

 
**Example: Create an entity, request: raxmon**

.. code::

    raxmon-entities-create --label="Monitor Test" --ip-address=default=192.0.2.15

 
**Example: Create an entity, response: raxmon**

.. code::

    Resource created. ID: enMlJzlHDo

If an error message is returned, the endpoint was unable to create the
entity. See the :ref:`Faults section<monitoring-faults>` section.

..  note::

      - For the remaining steps of this tutorial, substitute the ID of the
        entity that you created for "enn14Ch5mc".

     -  You can request a list of all entities for your account at any time.
        You can also list checks, alarms, notifications, and so on.

 
**Example: List all entities, request: cURL**

.. code::

    curl -i -X GET \
    -H 'X-Auth-Token: $AUTH_TOKEN' \
    -H 'Content-Type: application/json' \
    -H 'Accept: application/json' \
    'https://monitoring.api.rackspacecloud.com/v1.0/$TENANTID/entities'

 
**Example: List all entities, request: raxmon**

.. code::

    raxmon-entities-list --details
