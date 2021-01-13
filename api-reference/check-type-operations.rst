.. _check-type-operations:

===========
Check types
===========

Each check within Rackspace Monitoring has a designated check
type. The check type instructs the monitoring system how to
check the monitored resource.

Check types for commonly encountered web protocols, such as HTTP
(remote.http), IMAP (remote.imap-banner) , SMTP (remote.smtp),
and DNS (remote.dns) are provided. Monitoring commonly encountered
infrastructure servers like MySQL (remote.mysql-banner) and
PostgreSQL (remote.postgresql-banner) are also available.
Monitoring custom server uptime can be accomplished with the
remote.tcp banner check to check for a protocol-defined banner
at the beginning of a connection. Gathering metrics from server
software to create alerts against can be accomplished using the
remote.http check type and the 'extract' attribute to define the format.

In addition to the standard Rackspace Monitoring check types, you can
also use agent check types if the Monitoring Agent is installed on
the server you are monitoring.

For a list of available check types, see
:ref:`Available check types and fields
<check-types-ref>`.

Checks generate metrics upon which alarms will alert. The metrics
generated often depend on the parameters for the check, using the
extract attribute on the remote.http check for example.
However, the default metrics are always present. Use the
:ref:`Test check <check-operations>` to determine the exact metrics available.

The following table summarizes the attributes for Check Type resources:

**Attributes**

+-------------------------+-------------------------------+--------------------+
| Name                    | Description                   | Validation         |
+=========================+===============================+====================+
| **category**            | The category the check is in. | * String           |
+-------------------------+-------------------------------+--------------------+
| **type**                | The name of the supported     | * String           |
|                         | check type.                   |                    |
+-------------------------+-------------------------------+--------------------+
| **fields**              | Check type fields.            | * Optional         |
|                         |                               | * Array [Optional] |
+-------------------------+-------------------------------+--------------------+
| **supported_platforms** | Platforms on which an agent   | * Optional         |
|                         | check type is supported. This | * Array [String]   |
|                         | is advisory information only. |                    |
|                         | The check may still work on   |                    |
|                         | other platforms, or report    |                    |
|                         | that check execution failed   |                    |
|                         | at runtime.                   |                    |
+-------------------------+-------------------------------+--------------------+

Use the following check type API operations to view checks by check type.

.. contents::
   :local:
   :depth: 1

.. include:: methods/get-list-check-types.rst
.. include:: methods/get-a-check-type-by-id.rst
