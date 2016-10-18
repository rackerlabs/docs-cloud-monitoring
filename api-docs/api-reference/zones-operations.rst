.. _zones-operations.rst:

================
Monitoring zones
================

A monitoring zone is a location that Rackspace Monitoring
collects data from. Examples of monitoring zones are "US West",
"DFW1" or "ORD1". It is an abstraction for a general location
from which data is collected.

An *endpoint*, also known as a *collector*, collects data from the monitoring
zone. The endpoint is mapped directly to an individual computer or a virtual
machine. A monitoring zone contains many endpoints, all of which will be within
the IP address range listed in the response. The opposite is not true, however,
as there may be unallocated IP addresses or unrelated machines within that IP
address range.

A check references a list of monitoring zones it should be run from.

**Attributes**

+----------------------+---------------------------+------------------------+
| Name                 | Description               | Validation             |
+======================+===========================+========================+
| **country_code**     | Country Code              | * String longer than 2 |
|                      |                           |   characters           |
+----------------------+---------------------------+------------------------+
| **label**            | Label                     | * String               |
|                      |                           | * Non-empty string     |
+----------------------+---------------------------+------------------------+
| **source_ips**       | Source IP list            | * Array [String]       |
+----------------------+---------------------------+------------------------+

Use the following monitoring zones API operations to get information about
monitoring zones and to run traceroutes.

.. contents::
   :local:
   :depth: 1

.. note:: Users cannot create, update, or delete monitoring zones.

.. include:: methods/get-list-monitoring-zones.rst
.. include:: methods/get-monitoring-zone-by-id.rst
.. include:: methods/post-perform-a-traceroute.rst
