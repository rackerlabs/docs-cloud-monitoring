.. _notification-type-operations:

==================
Notification types
==================


The notification type categorizes the notifications that you can configure.
When you create a notification, you must specify one of the following Rackspace
Monitoring notification types:

+---------------+-----------------------------------+
| Notification  | Description                       |
+===============+===================================+
| **Email**     | Alerts where the message is       |
|               | delivered to a specified address. |
+---------------+-----------------------------------+
| **Webhook**   | Industry-standard web hooks,      |
|               | where JSON is posted to a         |
|               | configurable URL.                 |
+---------------+-----------------------------------+
| **PagerDuty** | An incident management system     |
|               | integrated with Rackspace         |
|               | Monitoring.                       |
+---------------+-----------------------------------+
| **SMS**       | Text alerts where the message is  |
|               | delivered to any phone number.    |
+---------------+-----------------------------------+
| **VictorOps** | An incident management system     |
|               | integrated with Rackspace         |
|               | Monitoring.                       |
+---------------+-----------------------------------+

The following sections describe the attributes associated with each
notification type and provide information about the notification type
API operations available to retrieve notification type information.


.. contents::
   :local:
   :depth: 1


.. _email-notification:

Email notification type
~~~~~~~~~~~~~~~~~~~~~~~

The email notification takes the following parameters:

+------------+---------------------------------+---------------------------+
| Name       | Description                     | Validation                |
+============+=================================+===========================+
|**address** | Email address to send           | * Email address           |
|            | notifications to                |                           |
+------------+---------------------------------+---------------------------+

.. _webhook-notification:

Webhook notification type
~~~~~~~~~~~~~~~~~~~~~~~~~

The webhook notification takes the following parameters:

+------------+---------------------------------+---------------------------+
| Name       | Description                     | Validation                |
+============+=================================+===========================+
|**url**     | An HTTP or HTTPS URL to POST to | * URL                     |
+------------+---------------------------------+---------------------------+

**Example: Webhook notification POST to a specified URL with JSON Payload**

.. code::

   {
      "event_id": "acOne:enOne:alOne:chOne:1326910500000:WARNING",
      "log_entry_id": "6da55310-4200-11e1-aaaf-cd4c8801b6b1",
      "details": {
          "target": null,
          "timestamp": 1326905540481,
          "metrics": {
              "tt_firstbyte": {
                  "type": "I",
                  "data": 2,
                  "unit": "milliseconds"
              },
              "duration": {
                  "type": "I",
                  "data": 2,
                  "unit": "milliseconds"
              },
              "bytes": {
                  "type": "i",
                  "data": 17,
                  "unit": "bytes"
              },
              "tt_connect": {
                  "type": "I",
                  "data": 0,
                  "unit": "milliseconds"
              },
              "code": {
                  "type": "s",
                  "data": "200",
                  "unit": "unknown"
              }
          },
          "state": "WARNING",
          "status": "warn.",
          "txn_id": "sometransaction",
          "collector_address_v4": "127.0.0.1",
          "collector_address_v6": null,
          "observations": [
              {
                  "monitoring_zone_id": "mzOne",
                  "state": "WARNING",
                  "status": "warn.",
                  "timestamp": 1326905540481,
                  "collectorState": "UP"
              }
          ]
      },
      "entity": {
          "id": "enOne",
          "label": "entity one",
          "ip_addresses": {
              "default": "127.0.0.1"
          },
          "metadata": null,
          "managed": false,
          "uri": null,
          "agent_id": null,
          "created_at": 1326905540481,
          "updated_at": 1326905540481
      },
      "check": {
          "id": "chOne",
          "label": "ch a",
          "type": "remote.http",
          "details": {
              "url": "http://www.foo.com",
              "body": "b",
              "method": "GET",
              "follow_redirects": true,
              "include_body": false
          },
          "monitoring_zones_poll": [
              "mzOne"
          ],
          "timeout": 30,
          "period": 60,
          "target_alias": "default",
          "target_hostname": "",
          "target_resolver": "",
          "disabled": false,
          "metadata": null,
          "confd_name": null,
          "confd_hash": null,
          "active_suppressions": null,
          "scheduled_suppressions": null,
          "created_at": 1326905540481,
          "updated_at": 1326905540481
      },
      "alarm": {
          "id": "alOne",
          "label": "Alarm 1",
          "check_id": "chOne",
          "entity_id": "enOne",
          "criteria": "if (metric[\"t\"] >= 2.1) { return WARNING } return WARNING",
          "disabled": false,
          "notification_plan_id": "npOne",
          "metadata": null,
          "confd_name": null,
          "confd_hash": null,
          "active_suppressions": null,
          "scheduled_suppressions": null,
          "created_at": 1326905540481,
          "updated_at": 1326905540481
          },
          "tenant_id": "91111"
   }

The following fields are contained within a single payload:

+------------+---------------------------------------------+
| Field      | Description                                 |
+============+=============================================+
| eventID    | The ID for the event in the system.         |
+------------+---------------------------------------------+
| logEntryID | The ID for the log entry.                   |
+------------+---------------------------------------------+
| entity     | The entity record that triggered the alert. |
+------------+---------------------------------------------+
| check      | The check record that triggered the alert.  |
+------------+---------------------------------------------+
| alarm      | The alarm record that triggered the alert.  |
+------------+---------------------------------------------+

The following fields will be populated in the request header when your
webhook is called:

+----------------------------+---------------------------------------------+
| Header field               | Description                                 |
+============================+=============================================+
| x-rackspace-webhook-token  | The webhook token defined in an account.    |
|                            | This is used in your web application to     |
|                            | verify that your webhook is called by an    |
|                            | authorized Rackspace service.               |
+----------------------------+---------------------------------------------+

.. _pagerduty-notification:

PagerDuty notification type
~~~~~~~~~~~~~~~~~~~~~~~~~~~

To use PagerDuty with Rackspace Monitoring, go to the
`PagerDuty website <https://www.pagerduty.com/>`_ and sign up for an account.
You will get an API Key in PagerDuty to be used when setting up the
PagerDuty notification. To learn how to use this notification type,
read the PagerDuty blog
`Rackspace Monitoring Now Integrates with PagerDuty
<https://www.pagerduty.com/blog/rackspace-cloud-monitoring-integration/>`_.

+----------------+---------------------------------+---------------------------+
| Name           | Description                     | Validation                |
+================+=================================+===========================+
|**service_key** | The PagerDuty service key to    | * Alphanumeric string     |
|                | use                             | * String between 1 and    |
|                |                                 |   32 characters long      |
+----------------+---------------------------------+---------------------------+

.. _sms-notification:

SMS notification type
~~~~~~~~~~~~~~~~~~~~~
A notification sent by text to your phone, including international
phone numbers; for example +15551234567. Standard text messaging
rates charged by your phone service provider will apply.

+-----------------+---------------------------------+-----------------------------+
| Name            | Description                     | Validation                  |
+=================+=================================+=============================+
|**phone_number** | Phone number to send the        | * String matching the regex |
|                 | notification to, with leading + |   //^\+[0-9]{6,15}$//       |
|                 | and country code (E.164 format) |                             |
+-----------------+---------------------------------+-----------------------------+

.. _victorops-notification:

VictorOps notification type
~~~~~~~~~~~~~~~~~~~~~~~~~~~
A notification sent as a webhook to your VictorOps account.

To use VictorOps with Rackspace Monitoring, go to the
`VictorOps website <https://victorops.com/>`_ and sign up for an account.
You will get an API key and configure routing keys for the teams in
VictorOps. The API key and routing key will be used when setting up the
VictorOps notification. To learn more about this notification type, read the
VictorOps blog
`Internet Age of Unix Philosophy <https://victorops.com/blog/internet-age-unix-philosophy/>`_
and visit the `VictorOps Knowledge Base <http://victorops.force.com/knowledgebase/>`_.

+-----------------+--------------------------------------+----------------------+
| Name            | Description                          | Validation           |
+=================+======================================+======================+
| **routing key** | The optional VictorOps routing_key   |(/^[a-zA-Z0-9-_\.]+$/)|
|                 | to use with Rackspace Monitoring.    |                      |
|                 | You create a routing_key in VictorOps|                      |
|                 | for team on-call configuration.      |                      |
+-----------------+--------------------------------------+----------------------+
| **api key**     | The VictorOps api_key to use with    | UUID v4 format       |
|                 | Rackspace Monitoring. You get this   |                      |
|                 | when you sign up for a VictorOps     |                      |
|                 | account.                             |                      |
+-----------------+--------------------------------------+----------------------+

.. _notification-types-api:

Notification types API operations
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use the following API operations to review information about notification
types.

.. include:: methods/get-list-notification-types.rst
.. include:: methods/get-a-notification-type-by-id.rst
