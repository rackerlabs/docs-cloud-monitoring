v1.14, July 29, 2015 
~~~~~~~~~~~~~~~~~~~~

These release notes correspond to a new-feature release of Rackspace
Monitoring.

What's new
----------

- Automatic upgrades on Linux and Windows were performed.

- New Luvi and Luvit infrastructure was added.

- A number of new hostinfo modules were added:  pam, fstab, cron, login,
  fileperms, kernel_modules, and services. For more information, see
  Hostinfo checks.



Resolved issues
---------------

The following agent-specific changes were made:

- Fixed OpenSSL memory leaks.

- Significantly improved the process for creating agents.

- Made a change to use a built-in libsigar library (when ``/tmp`` is mounted
  with the ``noexec`` option).

- Use a built-in libsigar library (when ``/tmp`` is mounted
  with the ``noexec`` option).

- Upgraded OpenSSL to 1.0.2d.

- Added a gethostname fix for Windows.

- Added a fix for the startup sequence for Windows.

- Added a bug fix for zombie processes with agent plug-ins on UNIX platforms.

- Fixed a minor issue with enumerating the new hostinfo modules via
  raxmon-agent-host-info-types.

- Fixed a bug found in unit tests with a garbage collect in the
  uv_spawn wrapper.





Known issues
------------

|no changes|
