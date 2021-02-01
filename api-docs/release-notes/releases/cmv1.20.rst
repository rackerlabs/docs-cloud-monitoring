v1.20, January 31, 2016 
~~~~~~~~~~~~~~~~~~~~~~~

These release notes correspond to a new-feature release of Rackspace
Monitoring.

What's new
----------

This release of the monitoring agent includes OpenSSL 1.0.2e.

Resolved issues
---------------

The following agent-specific changes were made:


* Plugins: Executables within directories of the whitelisted folder were not
  being ran correctly

* '-N' command line argument: Skips entity creation on setup

* Set the default locale

* Write the configuration file slightly different to see if extraneous
  characters on some machines gets fixed

* Fixed an issue in an underlying library performing resolv.conf parsing. If
  there was more than one whitespace character in-between the ``nameserver``
  and ``ip`` then the application would not discover the DNS servers
  correctly. This release supports the use of these extra characters.


Known issues
------------

|no changes|
