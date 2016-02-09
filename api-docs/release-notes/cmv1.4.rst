
v1.4, August 22, 2012 
-----------------------------------------------------


These release notes correspond to the Unlimited Availability release of Rackspace Monitoring.

What's new
~~~~~~~~~~~

•	You can pass in custom headers for a remote.http check. Depending on the site that you’re testing, this can be crucial in determining if your site is up. See `remote.http <https:/developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#remote-http>`__.

•	You can add a previous operator to the Alarm Language, which enables you to look at a metric value in the previous time period. It is useful for detecting changes. For example, to detect an SSH fingerprint change, you’d construct an Alarm snippet like the following one:

   .. code::

       if (metrics['fingerprint'] != previous(metrics['fingerprint'])) {
         return new AlarmStatus(CRITICAL, 'SSH fingerprint changed to #{fingerprint}');
       }

   For more information, see `Alarm language <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#alarm-language>`__.

•	Email alerts have been improved by including in them observations of the particular check from each monitoring zone. This enables you to get visibility on the status from any of the included monitoring zones of a check. Additionally, the message has been reformatted to look more user friendly.

   Subject:

   .. code::

       ** CRITICAL: host server check on web1.domain.com **

   Body:

   .. code::

       ================== Rackspace Monitoring Notification ===================
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

       This is an automated Rackspace Monitoring notification. You received this email
       because you are listed as a notification recipient.


•	You can include the query strings ``uri`` or ``entityId`` to retrieve specific mapped Rackspace Cloud Servers. You can also retrieve a set of entities by referencing their IDs. You cannot combine retrieving both URIs and entity IDs in the same request, but you can have up to 100 of them in a single request.  See also `Views <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#document-api-operations/views-operations>`__.

• Friendly names were added for the `alarm examples <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#document-api-operations/alarm-example-operations>`__.

•	A metadata attribute was added to the `alarm <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#attributes>`__ API.

•	You can now include no conditionals in the `alarm language <https://developer.rackspace.com/docs/cloud-monitoring/v1/developer-guide/#alarm-language>`__, which enables you to set global filters and rely on the check availability to determine the returned state.


Resolved issues
~~~~~~~~~~~~~~~~

•	Fixed unsetting optional attributes on an update (PUT)

•	Fixed the ``check_type`` to ``alarm`` mapping for delivering inconsistent and non-deterministic updates

•	Fixed how zlib streams are handled when a gzip HTTP stream is inflated

•	Inserted the initial ``OK`` state for the ``alarm change log``

•	Fixed updating the ``target_alias`` after setting the ``target_hostname`` on the initial creation, and vice versa.

Known issues
~~~~~~~~~~~~~~~~~~~

|no changes|
