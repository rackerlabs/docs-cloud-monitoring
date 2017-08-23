.. _agent-config-yaml-files:

================================
Agent configuration files (YAML)
================================

Review the server-side agent configuration file examples to learn how to
apply monitoring configurations across your environment.

After you create the configuration files, they can serve as templates that can
be shared, updated, and used with automation tools to standardize, maintain,
and update monitoring configurations as required.

For more information, see the
`Monitor Like a Pro With Server-Side Configuration
<https://blog.rackspace.com/monitor-like-a-pro-with-server-side-configuration>`_
article on the Rackspace Blog.


.. contents::
   :local:
   :depth: 2


.. _agent-plugin-check:

Agent plugin check
~~~~~~~~~~~~~~~~~~

This example agent plugin check YAML file for server-side agent
configuration, shows how to setup a script,
"Test-LatencyServer2Server.sh", to run with 2 parameters,
``10.10.10.123`` and ``destination.com``, passed on its command-lines.

.. note::
   YAML arrays, list, and sequences, such as the one shown in ``args`` in the
   following example, require a comma-separated list inside the square
   brackets. Although passing a space-separated list seems intuitively correct,
   the result is a single argument passed to the script specified by file.

.. code::

    type        : agent.plugin
    label       : Server to Server Latency Test Script
    disabled    : false
    period      : 60
    timeout     : 30
    details     :
        file  : Test-LatencyServer2Server.sh
        args  : [10.10.10.123,destination.com]
    alarms      :
        status   :
            label                 : Server to Server Latency Test
            notification_plan_id  : npXXXXXX
            criteria              : |
                if (metric[‘destination_response_time'] > 80) `
                { return new AlarmStatus(CRITICAL, 'The network latency is greater than 80ms'); } \
                return new AlarmStatus(OK, 'Network latency is normal');


.. _cpu-check-with-alarm:

CPU check with alarm
~~~~~~~~~~~~~~~~~~~~

This example YAML file for server-side agent configuration creates a CPU
check with alarm, file name: "cpu.yaml".

.. code::

    type    : agent.cpu
    label   : CPU
    period  : 60
    timeout : 10
    alarms  :
        cpu-usage:
            label: CPU usage
            notification_plan_id: npXXXXXXXX
            criteria: |
                if (metric['usage_average'] > 95) {
                  return new AlarmStatus(CRITICAL, 'CPU usage is
    #{usage_average}%, above your critical threshold of 95%');
                }
                if (metric['usage_average'] > 90) {
                  return new AlarmStatus(WARNING, 'CPU usage is
    #{usage_average}%, above your warning threshold of 90%');
                }
                return new AlarmStatus(OK, 'CPU usage is #{usage_average}%,
    below your warning threshold of 90%');


.. filesystem-check-with-alarm:

Filesystem check; alarm
~~~~~~~~~~~~~~~~~~~~~~~

This example YAML file for server-side agent configuration creates a
filesystem check for the root filesystem with alarm, file name:
"filesystem.yaml".

.. code::

    type    : agent.filesystem
    label   : Filesystem - /
    period  : 60
    timeout : 10
    details :
        target : /
    alarms  :
        disk-size:
            label: Usage on /
            notification_plan_id: npXXXXXXXX
            criteria: |
                if (percentage(metric['used'], metric['total']) > 90) {
                    return new AlarmStatus(CRITICAL, 'Disk usage is above
    90%,
    #{used} out of #{total}');
                }
                if (percentage(metric['used'], metric['total']) > 80) {
                    return new AlarmStatus(WARNING, 'Disk usage is above 80%,
    #{used} out of #{total}');
                }

.. _load-average-check-without-an-alarm:

Load average check; no alarm
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This example YAML file for server-side agent configuration creates a
load average check without an alarm, file name: "loadavg.yaml".

.. code::

    type    : agent.load_average
    label   : Load average
    period  : 60
    timeout : 10


.. _memory-check-with-alarm:

Memory check; alarm
~~~~~~~~~~~~~~~~~~~

This example YAML file for server-side agent configuration creates a
memory check with alarm with an alarm, file name: "memory.yaml".

.. code::

    type    : agent.memory
    label   : Memory
    period  : 60
    timeout : 10
    alarms  :
        actual-memory-usage:
            label: Memory usage
            notification_plan_id: npXXXXXXXX
            criteria: |
                if (percentage(metric['actual_used'], metric['total']) > 90)
    {
                  return new AlarmStatus(CRITICAL, "Memory usage is above
    your
    critical threshold of 90%");
                }
                if (percentage(metric['actual_used'], metric['total']) > 80)
    {
                  return new AlarmStatus(WARNING, "Memory usage is above your
    warning threshold of 80%");
                }
                return new AlarmStatus(OK, "Memory usage is below your
    warning
    threshold of 80%");


.. _network-check-without-alarms:

Network check; no alarms
~~~~~~~~~~~~~~~~~~~~~~~~

This example YAML file for server-side agent configuration creates a
network check without alarms, file name: ``network.eth0.yaml``.

.. code::

    type    : agent.network
    label   : Network - eth0
    period  : 60
    timeout : 10
    details :
        target : eth0
