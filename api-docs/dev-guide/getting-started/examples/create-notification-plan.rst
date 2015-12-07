
.. _gsg-make-a-notification-plan:

Create a notification plan 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

A notification represents a single action, such as sending an email to a
specific address, whereas a notification plan represents a set of
actions. Assuming the ID of the notification that you created is
``nt2T8WtWte``, following is an example of how you might specify the
attributes for a notification plan:

label
    Specifies a descriptive name for the notification plan.

warning\_state
    Specifies a list of notification IDs to send when the state is
    WARNING.

critical\_state
    Specifies a list of notification IDs to send when the state is
    CRITICAL.

ok\_state
    Specifies a list of notification IDs to send when the state is OK.

In this case, you're configuring the system to send an email when a
state changes.

 
**Example: Create a notification plan, request: cURL**

.. code::

    curl -i -X POST \
    --data-binary \
    '{
          "label": "Notification Plan 1",
          "warning_state": [
              "nt2T8WtWte"
          ],
          "critical_state": [
              "nt2T8WtWte"
          ],
          "ok_state": [
             "nt2T8WtWte"
          ]
    }' \
    -H 'X-Auth-Token: $AUTH_TOKEN' \
    -H 'Content-Type: application/json' \
    -H 'Accept: application/json' \
    'https://monitoring.api.rackspacecloud.com/v1.0/$TENANTID/notification_plans'

 
**Example: Create a notification plan, response: cURL**

.. code::

    HTTP/1.1 201 Created
    X-Ratelimit-Remaining: 49958
    X-Response-Id: .rh-ew99.h-dfw1-maas-prod-api1.r-dRuk75SF.c-35593.ts-1329410023443.v-b9d7626
    Content-Length: 0
    X-Lb: dfw1-maas-prod-api0
    X-Ratelimit-Type: global
    X-Ratelimit-Limit: 50000
    Location: https://monitoring.api.rackspacecloud.com/v1.0/010101/notification_plans/npkmLh5vVk
    Date: Thu, 16 Feb 2012 16:33:43 GMT
    X-Ratelimit-Window: 24 hours
    Content-Type: text/plain

 
**Example: Create a notification plan, request: raxmon**

.. code::

    raxmon-notification-plans-create --label="Notification Plan 1" --critical-state=nt2T8WtWte --warning-state=nt2T8WtWte --ok-state=nt2T8WtWte

 
**Example: Create a notification plan, response: raxmon**

.. code::

    Resource created. ID: npkmLh5vVk

If the endpoint responds with a ``201 Created`` and a ``Location``
header that contains the URL of the new notification plan, the
notification plan was created. If the notification plan was not created,
an error is returned.
