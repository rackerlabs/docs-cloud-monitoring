v1.12, April 26, 2015 
~~~~~~~~~~~~~~~~~~~~~

These release notes correspond to a new-feature release of
Rackspace Monitoring.

What's new
----------

- Support for Debian 8 (Jessie) was added.


Resolved issues
---------------

The following agent-specific changes were made:

- Added a small patch to the CPU check for memory usage.

- Added a small patch to support machine enumeration on newer Windows
  instances that lack the xenstore.exe binary.

- Trimmed the Monitoring ID and Monitoring Token configuration variables to
  ensure correctness.

- Fixed the Xen Server 6 package repository.


Known issues
------------

|no changes|
