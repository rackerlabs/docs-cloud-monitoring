v1.17, October 22, 2015 
~~~~~~~~~~~~~~~~~~~~~~~

These release notes correspond to a new-feature release of
Rackspace Monitoring.

What's new
----------

The agent for Ubuntu 15.10 was released.

Resolved issues
---------------

The following agent-specific changes were made:

- Added CPU count to Windows PerfOS check

- Made a change to close `stdin`  before running a check, which fixes a hang
  on certain flavors of Windows with custom plug-ins.

- For Red Hat Enterprise Linux 7, fixed the post install script for detecting
  chkconfig.

- Made an update to propagate hostinfo only for the current running operating
  system.



Known issues
------------

|no changes|
