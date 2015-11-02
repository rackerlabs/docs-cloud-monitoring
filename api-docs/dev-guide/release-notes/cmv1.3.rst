================================================================
Cloud Monitoring release notes v1.3, June 14, 2012 
================================================================

These release notes correspond to the pre "Unlimited Availability"
release of Cloud Monitoring.

**New Features**

-  *Traceroute API:* This API lets you run a Traceroute from a
   Monitoring Zone to a Hostname or IP address. Like all Cloud
   Monitoring features, the Traceroute API is fully dual stack,
   supporting both IPv4 and IPv6. The Traceroute API can be used to
   debug networking issues between the Cloud Monitoring collectors and
   your infrastructure.

   `Traceroute
   Docs <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#perform-a-traceroute-from-a-monitoring-zone>`__

-  *Metric interpolation on the Alarm status string:* This allows you to
   include metrics from a Check in the status string returned by an
   Alarm. For example, to include the HTTP status code from a
   ``remote.http`` Check, your Alarm could look like this:

   .. code::  

                       if (metrics['code'] != "200") {
                           return new AlarmStatus(CRITICAL, 'Bad HTTP Status: #{code}');
                       }

   `Alarm DSL
   Docs <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#alarm-language>`__

-  *Add payload to the remote.http check:* This allows you send a
   request body during a HTTP/HTTPS request.

   `remote.http
   attributes <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#remote-check-types>`__

**Enhancements**

-  Allow a user to specify the number of ICMP packets to send out on the
   ``remote.ping`` check.

-  Updated Certificate Authority chain used to validate SSL
   certificates, resulting in less false positives.

-  ``remote.tcp`` check now features the ``body_match_metric`` when
   specifying the send\_body command.

-  Add the remote IP address of the collector that alerted you to the
   Webhook notification payload.

**Resolved Issues**

-  Fixed writable date and time fields that were supposed to be
   immutable.

-  Fixed the DSL string escaping to allow you to specify special
   characters, example below:

   .. code::  

                   if (metric['code'] nregex '2\\d\\d') {
                     return new AlarmStatus(CRITICAL, 'Invalid status code #{code}');
                   }
