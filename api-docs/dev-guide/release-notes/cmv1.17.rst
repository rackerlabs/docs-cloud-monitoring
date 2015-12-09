v1.17, October 22, 2015 
-------------------------

These release notes correspond to a new-feature release of Rackspace Monitoring.

What's New
~~~~~~~~~~~~~

•	Released agent for Ubuntu 15.10.



Resolved issues
~~~~~~~~~~~~~~~~~~~

The following agent-specific changes were made:

•	Windows_perfos: added CPU count to Windows Perfos check.

•	Plugin: close stdin before running check (fixes hang on certain flavors of windows with custom plugins).

• Rhel7: fixed the post install script for detecting chkconfig.

• Hostinfo: Made update to only propogate hostinfo's for the current running operating system



Known issues
~~~~~~~~~~~~~~~~~~~

|no changes|
