.. _agent-targets-operations:


Agent targets
~~~~~~~~~~~~~
Each agent check type gathers data for a related set of targets
on the server. The targets are usually a device
(network interface, drive, partition, etc). For example,
agent.network gathers data for network devices; however, the
actual list of target devices is specific to the configuration
of the host server. By focusing on specific targets, you can
efficiently narrow the metric data the agent gathers.

For information about agent check types, see
:ref: `Available check types and fields <available-check-types-and-fields>`.

.. include:: methods/get-list-agent-check-targets-entities-entityid-agent-check-types-agentchecktype-targets.rst
