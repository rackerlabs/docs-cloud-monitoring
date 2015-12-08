.. _gsg-setup-notifications:


Setting up notifications 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In most cases, you and perhaps several people on your team will be
interested in multiple alarms. Cloud Monitoring lets you set up
notification plans that can be shared among multiple alarms. In this
exercise, you create the `notification <#>`__ first, then the
`notification plan <#>`__, and then finally the alarms.

Note that to create an alarm, you need a notification plan, and to
create a notification plan, you need at least one notification; however,
the notifications on the notification plan can be updated or deleted
from the plan at any point, even after the plan has been added to an
alarm.

A notification specifies how a user will receive informational messages
when an alarm is triggered. Notifications can be an email, a webhook, or
a page (using PagerDuty), or an SMS text.

Create an email notification, which will be an attribute to the
notification plan.

 
**Example: Create a notification, request: cURL**

.. code::

    curl -i -X POST \
    --data-binary \
       '{ "details" : { "address" : "joe@example.org" },
      "label" : "Alert email 1",
      "type" : "email"
    }' \
    -H 'X-Auth-Token: auth_token' \
    -H 'Content-Type: application/json' \
    'https://monitoring.api.rackspacecloud.com/v1.0/010101/notifications'

|

 
**Example: Create a notification, response: cURL**

.. code::

    HTTP/1.1 201 Created
    X-Ratelimit-Remaining: 49964
    X-Response-Id: .rh-00oi.h-ord1-maas-prod-api1.r-WZWtj0Vc.c-5711.ts-1329408343356.v-b9d7626
    Content-Length: 0
    X-Lb: ord1-maas-prod-api1
    X-Ratelimit-Type: global
    X-Ratelimit-Limit: 50000
    Location: https://monitoring.api.rackspacecloud.com/v1.0/010101/notifications/nt2T8WtWte
    Date: Thu, 16 Feb 2012 16:05:43 GMT
    X-Ratelimit-Window: 24 hours
    Content-Type: text/plain

|

 
**Example: Create a notification, request: raxmon**

.. code::

    raxmon-notifications-create --label="Alert email 1" --type=email --details=address=joe@example.org

|

 
**Example: Create a notification, response: raxmon**

.. code::

    Resource created. ID: nt2T8WtWte

|

If the notification is successfully created, the endpoint returns a
response code of ``201 Created`` and a ``Location`` header that contains
the URL of the notification. If an error message is returned, the
endpoint was unable to create the notification.
