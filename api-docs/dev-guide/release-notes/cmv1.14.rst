v1.14, July 29, 2015 
-------------------------

These release notes correspond to a new-feature release of Rackspace Monitoring.

What's New
~~~~~~~~~~~~~

•	Automatic Upgrades on Linux and Windows

•	New Luvi and Luvit infrastructure

• Added new hostinfo modules: s numerous modules: pam,fstab,cron,login,fileperms,kernel_modules,services



Resolved issues
~~~~~~~~~~~~~~~~~~~

The following agent-specific changes were made:

•	Fixed OpenSSL memory leaks.

•	Significantly improved process for creating agents and made it easier for users.

• Still 8 MB on Linux and 6 MB RSS on Windows.

• Use a built-in libsigar library (when /tmp is mounted noexec).

• Bumped OpenSSL to 1.0.2d.

• Added gethostname fix for Windows.

• Added a fix for the startup sequence for Windows.

• Added a bug fix for zombie processes with agent plugins on unix platforms.

• Fixed a minor issue with enumerating all the new hostinfo modules via raxmon-agent-host-info-types.

• Fixed a bug found in our unit tests with a garbage collect in the uv_spawn wrapper.





Known issues
~~~~~~~~~~~~~~~~~~~

|no changes|
