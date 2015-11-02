
v1.4, August 22, 2012 
-----------------------------------------------------


These release notes correspond to the "Unlimited Availability" release
of Cloud Monitoring.

What's new
~~~~~~~~~~~

-  *More HTTP Options:* Pass in custom headers for a ``remote.http``
   check. Depending on the site you're testing, this can be crucial in
   determining if your site is up.

   `remote.http
   Docs <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#remote-http>`__

-  *Add a previous operator to the Alarm Language:* This allows you to
   look at a metric value in the previous time period. It is very useful
   for detecting changes. For example, to detect an SSH fingerprint
   change, you'd construct an Alarm snippet like this:

   .. code::

       if (metrics['fingerprint'] != previous(metrics['fingerprint'])) {
         return new AlarmStatus(CRITICAL, 'SSH fingerprint changed to #{fingerprint}');
       }

   `Alarm DSL
   Docs <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#alarm-language>`__

-  *Improved email alerts:* Included in emails are the observations of
   the particular check from each monitoring zone. This allows you to
   get visibility on the status from any of the included monitoring
   zones of a check. We've also reformatted the message to look more
   user friendly.

   Subject:

   .. code::

       ** CRITICAL: host server check on web1.domain.com **

   Body:

   .. code::

       ================== Rackspace Cloud Monitoring Notification ===================
       Entity: web1.domain.com (50.56.179.42)
       Check: host server check (remote.ping)
       Alarm: Ping packet loss
       Status: CRITICAL
       Date: Mon Aug 13 2012 15:18:59 GMT+0000 (UTC)

       --------------------------- Observations -------------------------------------

       CRITICAL - Packet loss is 20%
       London (LON), 25 sec ago

       OK - Packet loss is normal
       London (LON), 10 sec ago

       OK - Packet loss is normal
       London (LON), 56 sec ago

       ------------------------------------------------------------------------------

       This is an automated Cloud Monitoring notification. You received this email
       because you are listed as a notification recipient.


-  *Retrieve overview by entityId or uri:* Include query strings
   *``uri``* or *``entityId``* to retrieve specific mapped Rackspace
   Cloud Servers (for now). You can also pull down a set of entities by
   referencing their id's. Keep in mind you cannot combine pulling both
   *``uri``*'s and *``entityId``*'s in the same request, but you can
   have up to 100 of them in a single request. See also `Views <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#document-api-operations/views-operations>`__.


Enhancements
^^^^^^^^^^^^^
-  Added friendly names for the
   `Alarm examples <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#document-api-operations/alarm-example-operations>`__.

-  Add a "``metadata``\ " attribute to the
   `alarm <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#attributes>`__
   API.

-  Allow including no conditionals in the `alarm
   language <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#alarm-language>`__,
   allowing you to set global filters, and rely on the check
   availability to determine the returned state.

Resolved Issues
~~~~~~~~~~~~~~~~

-  Fix un-setting optional attributes on an update (PUT).

-  Fix the ``check_type`` -> ``alarm`` mapping for delivering
   inconsistent and non-deterministic updates.

-  Fixed how we handle zlib streams when inflating a gzip http stream.

-  When we combined two services we had briefly did not insert the
   initial ``OK`` state for the ``alarm change log``, this is fixed now.

-  Fixed updating the ``target_alias`` after setting the
   ``target_hostname`` on the initial creation, and vice-versa.
