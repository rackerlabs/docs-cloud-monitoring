.. _alert-trigger-alarm:

Alert Triggering and Alarms
-----------------------------------------

This section describes alerting including an explanation of the alert
flow, the alarm language, the policies that you can create using alarms
and example best practices. In short, Rackspace Cloud Monitoring uses
alarms to evaluate the metrics of a check and decide if a notification
plan should be executed. It is the primary way to describe exactly what
you want to be alerted on.


.. _alert-flow:

Alert flow
~~~~~~~~~~~~~~

Let's take an example user work flow of creating a monitor for a
particular resource and follow it through the system to understand how
the alerting system works:

#. Using the `Checks`_ API resource, create a check
   with one or more monitoring zones (per the ``monitoring_zone_poll``
   attribute). When you apply the check via the API, the check is
   provisioned on the collectors. If the check is successfully applied
   (as indicated by the HTTP response code) the monitor starts executing
   the check.

#. Using the `Alarms`_ API resource, create a new alarm on the entity that matches this 
   particular check.

   Note that alarms are created to match when a specific condition occurs. On this alarm 
   let's assume you've specified the alarm policy as ``QUORUM``. This parameter describes 
   a deterministic way to represent mixed results in a "multi-datacenter" monitoring
   environment. To learn more about this concept, see 
   `Alert Policies <alert-policies>`. You can also read 
   `Best Practices on Alerting <best-practice-alerting>` for more pattern 
   applications of the alarm language.

#. If the monitored resource fails, a state change event is generated
   (since all the collectors agree on the status per the ``QUORUM``
   alert policy) and an alert is triggered. Based on the logic you
   created in the associated notification plan an error notification is
   sent (the call itself is a webhook).

..  note:: 
	If a check fails to execute, by default alarm associated with check returns a 
	``CRITICAL`` state.

    This may change in future versions of the product, however this is
    currently the only behavior allowed. This represents a subclass of
    failures similar to *"Connection Timeout"*'s or other errors where the
    result wasn't simply a failure result, but a result where the user was
    unable to run the check at all.
    
.. _Checks: http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/service-checks.html  
.. _Alarms: http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/service-alarms.html  

.. _alarm-language:

Alarm language
~~~~~~~~~~~~~~~~

The alarm language is one of the most powerful parts of Rackspace Cloud
Monitoring. It describes the mechanism to trigger an event. Upon
triggering an event a notification plan is executed that describes how
to send different notifications.

.. _alarm-language-chk-availability:

Check availability
^^^^^^^^^^^^^^^^^^^

As mentioned above the default evaluation of a check depends upon
whether the check is able to run successfully. We can illustrate this
concept using the HTTP check as an example. If the alarm checks the
status of a 404 response, but the check is actually getting a Connection
Refused message, the result of that check is ``ERROR``. The availability
of the check is determined by the ability to run the check.

..  note:: 
	This is **very important** to understand this concept. All checks that
	go into a ``CRITICAL`` state will always force an `alarm <#>`__ on an
	`entity <#>`__, ``CRITICAL``.

.. _alarm-language-query:

Anatomy of a query
^^^^^^^^^^^^^^^^^^^^

An alarm query is broken down into the following main parts:

**Comments**
    Comments are either line by line comments that begin with a # or
    c-style comments /\* \*/.

    .. code::  

        # This is a comment
        /* This is a comment */
        // This is NOT a comment

**String Literals**
    String  s are surrounded with either ' or ". String  s
    support the following escape sequences:

    +--------------+------------------------------------------------------------------+
    | Sequence     | Value                                                            |
    +==============+==================================================================+
    | ``\"``       | Double quote                                                     |
    +--------------+------------------------------------------------------------------+
    | ``\'``       | Single quote                                                     |
    +--------------+------------------------------------------------------------------+
    | ``\\``       | Backslash                                                        |
    +--------------+------------------------------------------------------------------+
    | ``\b``       | Backspace                                                        |
    +--------------+------------------------------------------------------------------+
    | ``\f``       | Formfeed                                                         |
    +--------------+------------------------------------------------------------------+
    | ``\n``       | Newline                                                          |
    +--------------+------------------------------------------------------------------+
    | ``\r``       | Carriage return                                                  |
    +--------------+------------------------------------------------------------------+
    | ``\t``       | Tab                                                              |
    +--------------+------------------------------------------------------------------+
    | ``\uXXXX``   | Unicode character where XXXX is the hex unicode character code   |
    +--------------+------------------------------------------------------------------+

    Some example string  s:

    .. code::  

        "Foo"           /* A double quoted string */
        'Foo'           /* A single quoted string */
        '"Foo\'s bar\"' /* Single quoted strings may contain unescaped double quotes */
                        /* as well as escaped single or double quotes */
        "'Bar's foo\'"  /* Double quoted strings may contain unescaped single quotes */
                        /* as well as escaped single or double quotes */
        '\u0027abc'     /* A string containing an escaped unicode character */

**Numeric Literals**
    Numeric  s are written without quotation marks. Below are some
    examples:

    .. code::  

        2773.2                 /* Numeric   */
        200                    /* Numeric   */
        -200                   /* Numeric   */
        1.2e-7                 /* Numeric   with exponential notation */

**Declarations**
    This part of the alarm language is the setting declarations, which
    globally control the evaluation of the query. The syntax is shown
    below:

    .. code::  

        :set <name>=<value>

    The current version of the product supports two settings. The first
    setting specifies the `consistency
    level <alerts-language.html#concepts-alarms-alert-policies>`__.

    .. code::  

        :set consistencyLevel=<value>

    This is an important setting that is typically left as ``QUORUM``
    (the default) unless there is a specific need to change it. For more
    information about alerting policies and consistency levels, see
    `Alert Policies (Consistency
    Level) <alerts-language.html#concepts-alarms-alert-policies>`__.

    The second setting is the consecutive alert count. It determines how
    many consecutive evaluations of a state occur before issuing a state
    change. The default for this setting is **1** and the maximum
    allowed is **5**.

    .. code::  

        :set consecutiveCount=<value>

**Conditionals**
    The second part of the query is the conditional statement. The
    conditional statements determine what criterion constitute sending
    an alert on behalf of the user. This is by far the most configurable
    part of the alarm language. There are two types of comparisons:
    numeric comparisons and text comparisons.

    Numeric comparisons have a number of different operators, which are
    listed below:

    .. code::  

        == /* Equality when compared with a   numeric */
        != /* Inequality */
        >= /* Greater than or equal to */
        <= /* Less than or equal to */
        <  /* Less than */
        >  /* Greater than */

    If the left hand side of the conditional is a metric statement and
    the right hand side of the equality is another metric statement,
    then equality and inequality is evaluated based on lexicographical
    comparison.

    Or if the left or right hand side is a   then the following
    operators are available for use.

    .. code::  

        ==     /* String comparison */
        !=     /* String comparison */
        regex  /* Regular expression match */
        nregex /* Regular expression inverse match */

    On top of the single conditional operators, you can also use boolean
    logic to evaluate multiple conditionals in a single alarm. When
    trying to determine if a resource is functioning correctly, this
    built-in flexibility provides you with a powerful tool that lets you
    examine multiple aspects of a single resource.

    The operators available are:

    .. code::  

        && /* And */
        || /* Or */

**Return Statements**
    The third part of the query is the return statements. The return
    statements determine the notification or notifications to execute on
    the notification plan as well as the state of the alarm. There are
    two separate methods to represent a return query:

    Returning the status:

    .. code::  

        return new AlarmStatus(<OK|WARNING|CRITICAL>);
        

    Returning the status and message:

    .. code::  

        return new AlarmStatus(<OK|WARNING|CRITICAL>, <String Status Message>);
        

.. _limit-defaults:     

Limits and defaults
^^^^^^^^^^^^^^^^^^^^^^^
Alarms have limits in their constructs. For instance, there are a
limited set of conditionals you can use in a single alarm query.

The following list describes the limits and defaults for alarms:

-  Minimum conditionals in a single query: **0**

-  Maximum limit of conditionals in a single query:**10**

-  Criteria: **Optional**

   Note that if criteria is not specified the availability of the check
   determines the alarm state.

-  Default consistency level of the alert policy: **QUORUM**

-  Default consecutive alert count: **1**, maximum allowed: **5**.

   Note that the default consecutive alert count for ping checks is
   **3**

-  Maximum length of a metric name string (in characters): **128**

-  Maximum length of a string   representing a metric value (in
   characters): **80**
   
.. _status-msgs:

Status messages
^^^^^^^^^^^^^^^^

Checks and Alarms have status strings that can be up to 128 characters long. A resolution 
policy determines the final message that gets displayed to a user in an email, 
`alarm change log`_, or webhook. This message represents a human readable string for 
the status of the alarm.

The resolution policy is as follows:

-  If no status is specified, then use the value from the most recent
   run `check <#>`__.

-  If it's specified then use the specified string from the
   `alarm <#>`__.

-  String interpolate the message if metric is present.

Status string interpolation will substitute metrics in a special format
to the point in time metric. It looks like this:

.. code::  

    return new AlarmStatus(WARNING, 'The check took #{duration}s to execute');

..  note:: 
	String Interpolation will substitute a ``#{metric-name}`` for its
	corresponding point in time value, it is a very powerful feature.
	
.. _alarm change log: http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/service-changelogs.html	

.. _alert-policies:

Alert policies (consistency level)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Alert policies are set with the ``consistencyLevel`` alarm attribute. The policies 
define a system for interpreting mixed results from a check. Mixed results can occur 
during failure scenarios if you have configured multiple zones to monitor a resource.

There are three different alert policies for handling mixed results:
``ONE``, ``QUORUM``, and ``ALL``. Each policy has trade-offs that should
be considered when determining which to use. The alert policies and
their trade-offs are described next.

..  note:: 
	The ``check period``, a configurable ``check`` attribute that defaults
	to 60 seconds, can affect the alarm state for the ``QUORUM``, and
	``ALL`` policies as it limits what observations are considered recent
	enough to count towards an alert state update. You can see the age of
	the observations in the alert notification email. If the observation is
	older than one and a half times (1.5 x) the ``consecutiveCount`` x
	``check period``, the observation is not considered in determining the
	alert state.

.. _alert-policies-one:

One
^^^^

The alert state is determined by the latest observation that is
different from the current alert state. For example, if the current
alert state is OK and a monitoring zone WARNING or CRITICAL observation
is received, a notification is sent and the alert state is changed to
indicate the most recent zone observation.

The ``ONE`` policy optimizes speed of alerting at the expense of
correctness as any network disruption between Rackspace Cloud Monitoring
and the monitored resource could generate an alert. Additionally, the
``ONE`` policy can cause many notifications as a change in the state of
any one monitoring zone from its previous state results in a
notification and alert state change. This is mitigated in the ``QUORUM``
policy.

.. _alert-policies-quorum:

Quorum
^^^^^^^

The alert state is determined by a change observed in a majority of the
monitoring zones. For example, two of three, or three of five,
monitoring zones report OK and the previous alert state was WARNING. The
calculation is TOTAL / 2 + 1.

The ``QUORUM`` policy is the recommended solution. It offers the best
speed-to-correctness trade-off. A majority of the zones monitoring your
resource must have the same state before an alert state change and
notification. This is the best approach to maintain speed and low
time-to-alert.

.. _alert-policies-all:

All
^^^^^

The alert state is determined by a resource change observed in all of
the monitoring zones. For example, three out of three monitoring zones
report resource CRITICAL and the previous alert state was OK.

The ``ALL`` policy is the most accurate, but is also prone to failure in
significant failure scenarios. If a network partition between our
internal datacenters happens, the alert could be delayed due to the
election process. In this case, a machine has to be marked down, then
the checks are re-evaluated as a group. If they come to a consensus
(with the downed collector) then an alert is generated.

..  note:: 
	Email alert notifications may show some zones in a state that is
	different from the alert state.

.. _constructs-functions:

Constructs and functions
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Function modifiers serve to alter the interpretation of a metric. The
format of a modifier is as follows:

.. code::  

    ex: <funcname>(metric['response_time'])

.. _constructs-functions-prev:

Previous
^^^^^^^^^^

Function name: **previous**

This is used to look back at the same metric in the previous time period
from the same datacenter. This is useful to make sure a value is always
incrementing. Or another use is detecting string changes and sending an
alert on that.

.. code::  

    if (previous(metric['fingerprint']) != metric['fingerprint']) {
        return new AlarmStatus(CRITICAL, 'Fingerprint has changed to: #{fingerprint}');
    }
                
.. _constructs-functions-rate:

Rate
^^^^^^^

Function name: **rate**

This is best used for counters. For instance if you are tracking a gauge
such as bytes\_in on an network interface, this will give you the rate
as defined by this formula where V=value, and T=time.

``(V1 - V0) /                     (T1 - T0)``

.. code::  

    if (rate(metric['rx_bytes']) > 5242880) {
        return new AlarmStatus(CRITICAL, 'Received greater than 5 MBps.');
    }
    if (rate(metric['rx_bytes']) > 1048576) {
        return new AlarmStatus(WARNING, 'Received greater than 1 MBps.');
    }
                
.. _constructs-functions-percent:

Percent
^^^^^^^^^^

Function name: **percentage**

This function is used to calculate a percentage, useful in situations
like the example below.

..  note:: 
	Notice the order of the two statements below, since it executes
	sequentially it is important to be most specific as the first matched
	condition wins. This is true for all conditions, it is commonly exposed
	in statements like this.

.. code::  

    if (percentage(metric['used'], metric['total']) > 90) {
        return new AlarmStatus(CRITICAL, 'Less than 10% free space left.');
    }
    if (percentage(metric['used'], metric['total']) > 80) {
        return new AlarmStatus(WARNING, 'Less than 20% free space left.');
    }
                
.. _best-practice-alerting: 

Best practices on alerting
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This section covers common solution patterns for creating useful alerts.
It focuses on alarms and how you can use the alarm language to best
achieve these patterns.

.. _best-practice-http-check: 

Best practices for HTTP / HTTPS check
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The following example shows a best practice for creating alerts for HTTP and HTTPS 
checks.

- Check for HTTP 404

  **Critical on 404 or Connection Refused**

  This example assumes a provisioned `Remote
  HTTP <appendix-check-types-remote.html#section-ct-remote.http>`__ with
  standard settings. It checks that the return code (which is a metric of
  type string) is the string equivalent of a 404. HTTP response codes are
  numeric, but since they hold no numeric value, we interpret them as
  strings.

  .. code::  

      if (metric['code'] == "404") {
        return new AlarmStatus(CRITICAL, "Page not found!");
      }

- Critical on a specific body match

  **Check for the existence of a body match and error out if present**

  This example assumes a provisioned `Remote
  HTTP <appendix-check-types-remote.html#section-ct-remote.http>`__ with
  an metric called ``body_match`` added to the response. You can use this
  string metric to check the existence of the text, and error out if
  found.

  Using the ``HTTPS`` prefix automatically defaults the port to the
  standard ``443`` instead of port ``80``. This particular example looks
  for the word "forbidden" in the body match, and if found returns
  ``CRITICAL`` with the error message:
  ``"Forbidden found,                         returning CRITICAL."``

  .. code::  

     if (metric['body_match'] regex ".*forbidden.*") {
       return new AlarmStatus(CRITICAL, "Forbidden found, returning CRITICAL.");
     }

- Critical on certificate expiration

  **Check the ``cert_end_in`` metric; critical if less than a week away**

  This example assumes a provisioned `Remote
  HTTP <appendix-check-types-remote.html#section-ct-remote.http>`__
  against an HTTPS server and adds a set of metrics that are specific to
  SSL in the hash of metrics.

  This example checks the certificate expiration in seconds, abbreviated
  as the ``cert_end_in``:

  .. code::  

      /* 2 days = 172 800 seconds */
     if (metric['cert_end_in'] < 172800)
     { return new AlarmStatus(CRITICAL, "Cert expiring in less than 2 days."); 
      }

      /* 1 week = 604 800 seconds */
      if (metric['cert_end_in'] < 604800)
      { return new AlarmStatus(WARNING, "Cert expiring in less than 1 week."); 
      }
      
.. _best-practice-port-check: 

Best practices for port/banner checks
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The following example shows a best practice for creating alerts for port and banner 
checks.

- Failure on banner match

  This example assumes a provisioned `Remote TCP <appendix-check-types-remote.html#section-ct-remote.tcp>`__ check.
  It also specifies a ``banner_match`` *``'OpenSSH.*'``*, which matches
  content based on the text sent from the server upon connection. For a
  complete description, see `Remote TCP <appendix-check-types-remote.html#section-ct-remote.tcp>`__. However
  if a banner matches, then a metric is added to the result, called
  ``banner_match``. One common solution is to check for the existence of
  that metric and return ``CRITICAL`` otherwise.

  .. code::  

      /* Have the check match at the edge */
      if (metric['banner_matched'] != "") {
        return new AlarmStatus(OK);
      }
      /* Or use the regex parser in the
         language to build multiple matches
         in a single alarm. */
      if (metric['banner'] regex "OpenSSH.*") {
        return new AlarmStatus(OK);
      }

      return new AlarmStatus(CRITICAL, "Match not found.");
      
.. _best-practice-DNS-check:       

Best practices for DNS checks
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The following example shows a best practice for creating alerts to check DNS.

**Check for an IP in a DNS query, fail otherwise.**

This example assumes a provisioned `Remote
DNS <appendix-check-types-remote.html#section-ct-remote.dns>`__ check
against a working nameserver. In this example, the alarm matches against
the ``answer`` metric. As with all alarms, if the check is marked
available=false (which in this case means the nameserver fails to
respond) than the alarm is ``CRITICAL``.

.. code::  

    # Match if the 127... address was in the resolution
    # if it wasn't than default to CRITICAL

    if (metric["answer"] regex ".*127.8.2.1.*") {
      return new AlarmStatus(OK, "Resolved the correct address!");
    }
    return new AlarmStatus(CRITICAL);


.. _best-practice-ssh-check: 

Best practices for SSH checks
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The following example uses the Rackspace Cloud Monitoring command line
interface (CLI). For information on downloading and installing the CLI,
see https://github.com/racker/rackspace-monitoring-cli.

One of the most widely used remote checks is the SSH check. This check
not only verifies that something is listening on the expected port, but
establishes an SSH session and returns the host key fingerprint as a
metric, further verifying that the SSH server is operating as expected.

The following example assumes the existence of an entity with the IP
address eth0 and ID enk8YUv0Cd, and a notification plan with ID
nplU9hLUgc. This check connects to an SSH server using port 22 by
default:

.. code::  

    raxmon-checks-create \
    --entity-id=enk8YUv0Cd \
    --label=ssh \
    --type=remote.ssh \
    --target-alias=eth0 \
    --monitoring-zones=mzord,mzdfw,mzlon

**Alarm for this check:**

If the monitoring service is unable to connect to the SSH server for the
check, any alarms using the check will automatically fail. However, we
can additionally verify that the server returns the expected host key
fingerprint, which could reveal an unexpected change on the server or a
man in the middle attack.

.. code::  

    raxmon-alarms-create \
    --entity-id=enk8YUv0Cd \
    --notification-plan-id=nplU9hLUgc \
    --check-id=chTFHxHn0p \
    --criteria="if (metric['fingerprint'] != '13dd6c5df600f9a15c67ea5db491ac9a') { return new AlarmStatus(CRITICAL, 'Incorrect SSH Host Fingerprint'); }"
