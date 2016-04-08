.. _entities-operations:


Entities
~~~~~~~~

.. contents::
   :local:
   :depth: 1
   
An entity represents the object or resource that you want to monitor.
You can create an entity to monitor your website, a particular web service,
or your Rackspace server, or server instance. Each entity represents only
one item in the monitoring system. For example, if you wanted to
monitor each server in a cluster, you would create an entity for each
of the servers. You would not create a single entity to represent the
entire cluster.

An entity can have multiple checks associated with it. This allows you
to check multiple services on the same host by creating multiple
checks on the same entity, instead of multiple entities each with a
single check.

When you create a new entity in the monitoring system, you specify
the following information:

**Attributes**

+------------------+------------------------+-----------------------------------+
| Name             | Description            | Validation                        |
+==================+========================+===================================+
| **label**        | Defines a name for the | * String between 1 and 255        |
|                  | entity.                |   characters long                 |
|                  |                        | * Non-empty string                |
+------------------+------------------------+-----------------------------------+
| **agent_id**     | Agent to which this    | * Optional                        |
|                  | entity is bound.       | * String matching the regex       |
|                  |                        |   ``/^[-.\w]{1,255}$/``           |
+------------------+------------------------+-----------------------------------+
| **ip_addresses** | Hash of IP addresses   | * Optional                        |
|                  | that can be referenced | * Hash [String,String between 1   |
|                  | by checks on this      |   and 64 characters long: IPv4 or |
|                  | entity.                |   IPv6 address]                   |
|                  |                        | * Array or object with a number   |
|                  |                        |   or items between 0 and 64       |
+------------------+------------------------+-----------------------------------+
| **managed**      | Whether this entity is | * Optional                        |
|                  | managed by Rackspace   | * Boolean                         |
|                  | Managed Cloud.         |                                   |
+------------------+------------------------+-----------------------------------+
| **metadata**     | Arbitrary key/value    | * Optional                        |
|                  | that are passed during | * Hash [String,String between 1   |
|                  | the alerting phase.    |   and 255 characters long:        |
|                  |                        |   String,String between 1 and     |
|                  |                        |   255 characters long]            |
|                  |                        | * Array or object with a number   |
|                  |                        |   of items between 0 and 256      |
+------------------+------------------------+-----------------------------------+
| **uri**          | The Rackspace Cloud    | * Optional                        |
|                  | identifier of this     | * String                          |
|                  | entity. Only applies   |                                   |
|                  | to Rackspace Cloud     |                                   |
|                  | servers.               |                                   |
+------------------+------------------------+-----------------------------------+

.. include:: methods/post-create-an-entity-entities.rst
.. include:: methods/get-list-entities-for-an-account-entities.rst
.. include:: methods/get-get-an-entity-by-id-entities-entityid.rst
.. include:: methods/put-update-an-entity-by-id-entities-entityid.rst
.. include:: methods/delete-delete-entity-by-id-entities-entityid.rst
