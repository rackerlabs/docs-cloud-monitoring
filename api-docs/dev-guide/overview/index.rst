.. _overview:

About the API
-----------------------------------------

The Rackspace Monitoring API service enables developers to analyze cloud services
and dedicated infrastructure through a simple Representational State Transfer
(REST) web service interface.

The API currently supports monitoring for external services. The key benefits you receive
from using the Rackspace Monitoring API include the following:

**Use of Domain Specific Language (DSL)**
    The Rackspace Monitoring API uses a DSL, which makes it a
    powerful tool for configuring advanced monitoring features. For
    example, typically complex tasks, such as defining triggers on
    thresholds for metrics or performing an inverse string match become
    much easier with a concise, special purpose language created for
    defining alarms. For alarm concept information, see :ref:`Alarm and
    alert <concepts>`.

**Monitoring from Multiple Datacenters**
    Rackspace Monitoring allows you to simultaneously monitor the
    performance of different resources from multiple datacenters and
    provides a clear picture of overall system health. It includes
    tunable parameters to interpret mixed results which help you to
    create deliberate and accurate alerting policies. For more
    information, see :ref:`Alert Policies <alert-policies-and-types>`.

**Alarms and Notifications**
    When an alarm occurs on a monitored resource, Rackspace Monitoring sends
    you a notification so that you can take the
    appropriate action to either prevent an adverse situation from
    occurring or rectify a situation that has already occurred. These
    notifications are sent based on the severity of the alert as defined
    in the notification plan. For more information, see
    :ref:`Notifications <notification-plans-operations>`.

**Collection of Data**
    Rackspace Monitoring allows you to collect a variety of data
    that you can use for other tasks, such as researching trends or
    measuring critical data. For more information, see
    :ref:`Metrics <metrics-operations>`.

For more information about the basic foundations of this API, see
:ref:`Monitoring key terms and concepts <concepts>`.

.. toctree:: :hidden:
   :maxdepth: 2

   additional-resources
   Pricing and terms of service <pricing-service-level>
   api-service-updates
