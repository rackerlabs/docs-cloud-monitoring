v1.3, June 14, 2012 
~~~~~~~~~~~~~~~~~~~

These release notes correspond to the Limited Availability release of
Rackspace Monitoring.

What's new
----------

- The new Traceroute API lets you run a traceroute from a monitoring zone to
  a hostname or IP address. Like all Rackspace Monitoring features, the
  Traceroute API is fully dual stack, supporting both IPv4 and IPv6. The
  Traceroute API can be used to debug networking issues between the Rackspace
  Monitoring collectors and your infrastructure. See the
  `Traceroute section <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#perform-a-traceroute-from-a-monitoring-zone>`__.

- Metric interpolation on the alarm status string enables you to include
  metrics from a check in the status string returned by an alarm. For example,
  to include the HTTP status code from a remote.http check, your alarm could
  look as follows:

   .. code::

                       if (metrics['code'] != "200") {
                           return new AlarmStatus(CRITICAL, 'Bad HTTP Status: #{code}');
                       }

  For more information, see `Alarm language <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#alarm-language>`__

- Payload was added to the remote.http check, which enables you send a request
  body during a HTTP/HTTPS request. See also
  `remote.http attributes <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#remote-check-types>`__.

- You can specify the number of ICMP packets to send out on the ``remote.ping check``.

- The Certificate Authority chain used to validate SSL certificates has been
  updated, which will result in fewer false positives.

- The ``remote.tcp`` check now features the ``body_match_metric`` when you
  specify the ``send_body`` command.

- You can now add the remote IP address of the collector that alerted you to
  the webhook notification payload.


Resolved issues
-----------------

- Fixed writable date and time fields that were supposed to be immutable.

- Fixed the DSL string escaping to enable you to specify special characters.
  See the following example:

   .. code::

                   if (metric['code'] nregex '2\\d\\d') {
                     return new AlarmStatus(CRITICAL, 'Invalid status code #{code}');
                   }


Known issues
------------

|no changes|
