.. _gsg-delete-an-entity:

Deleting an entity 
~~~~~~~~~~~~~~~~~~

Now that you have completed the exercises in this tutorial, you can
remove the entity that you created. Removing an entity also removes all
associated checks and alarms.

..  note::
      Note
      To quickly delete an entity and all of its children, use
      ```raxmon--entities-delete``.
      However, you will not be able to manually delete your Rackspace server
      entities as they are auto-created and deleted by Rackspace automation
      upon server build/destroy.

 
**Example:Delete an entity, request: cURL**

.. code::

    H 'X-Auth-Token: $AUTH_TOKEN' \
    -H 'Accept: application/json' \
    'https://monitoring.api.rackspacecloud.com/v1.0/$TENANTID/entities/enn14CH5mc'

 
**Example 2.40. Delete an entity, response: cURL**

.. code::

    HTTP/1.1 204 No Content
    X-Ratelimit-Remaining: 49984
    X-Response-Id: .rh-zyPa.h-dfw1-maas-prod-api0.r-6RuOWE2V.c-236.ts-1330555655887.v-50c8c2d
    Content-Length: 0
    X-Lb: dfw1-maas-prod-api0
    X-Ratelimit-Type: global
    X-Ratelimit-Limit: 50000
    Date: Wed, 29 Feb 2012 22:47:35 GMT
    X-Ratelimit-Window: 24 hours
    Content-Type: text/plain

 
**Example 2.41. Delete an entity, request: raxmon**

.. code::

    raxmon-entities-delete --id=ENTITY_ID

 
**Example 2.42. Delete an entity, response: raxmon**

.. code::

    Resource deleted

 
**Example: Delete checks, request: cURL**

.. code::

    curl -i -X \
    DELETE \
    -H 'X-Auth-Token: $AUTH_TOKEN' \
    -H 'Accept: application/json' \
    'https://monitoring.api.rackspacecloud.com/v1.0/$TENANTID/entities/enn14Ch5mc/checks/chyYWNw59I

 
**Example: Delete checks, response: cURL**

.. code::

    HTTP/1.1 204 No Content
    X-Ratelimit-Remaining: 49993
    X-Response-Id: .rh-Fxp3.h-ord1-maas-prod-api0.r-4Fb5IwLs.c-455.ts-1330554327071.v-50c8c2d
    Content-Length: 0
    X-Lb: ord1-maas-prod-api1
    X-Ratelimit-Type: global
    X-Ratelimit-Limit: 50000
    Date: Wed, 29 Feb 2012 22:25:27 GMT
    X-Ratelimit-Window: 24 hours
    Content-Type: text/plain

 
**Example: Delete a check, request: raxmon**

.. code::

    raxmon-checks-delete --id=CHECK_ID

 
**Example 2.46. Delete a check, response: raxmon**

.. code::

    Resource deleted

 
**Example: Delete alarms, request: cURL**

.. code::

    curl -i -X \
    DELETE \
    -H 'X-Auth-Token: $AUTH_TOKEN' \
    'https://monitoring.api.rackspacecloud.com/v1.0/$TENANTID/entities/enn14CH5mc/alarms/alIxnPKczp

 
**Example: Delete alarms, response: cURL**

.. code::

    HTTP/1.1 204 No Content
    X-Ratelimit-Remaining: 49987
    X-Response-Id: .rh-GLyy.h-dfw1-maas-prod-api0.r-2Ulro75y.c-32883.ts-1330554811888.v-6fee2d2
    Content-Length: 0
    X-Lb: dfw1-maas-prod-api1
    X-Ratelimit-Type: global
    X-Ratelimit-Limit: 50000
    Date: Wed, 29 Feb 2012 22:33:31 GMT
    X-Ratelimit-Window: 24 hours
    Content-Type: text/plain

 
**Example: Delete an alarm, request: raxmon**

.. code::

    raxmon-checks-delete --id=ALARM_ID

 
**Example: Delete an alarm, response: raxmon**

.. code::

    Resource deleted
