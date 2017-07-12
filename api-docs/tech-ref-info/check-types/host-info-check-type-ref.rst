.. _hostinfo-check-type-ref:


Hostinfo checks
~~~~~~~~~~~~~~~

.. contents::
   :local:
   :depth: 1

Hostinfo checks are a special class of checks that run on demand.

In contrast to the remote and agent check types which enable you to schedule
alarms or alerts for remote and agent-type checks and run them on a regular
schedule, you cannot schedule Hostinfo checks or create alarms or alerts for
them.

Create Hostinfo checks to perform tasks like the following:

- Fetch data on demand. For example, you can use a Hostinfo check to pipe data
  about the host to other services or applications.

- Run occasional checks to troubleshoot an issue.

- Periodically fetch data from large clusters of servers with the granularity
  of fetching from an individual computer. For example, use a Hostinfo check
  to retrieve information from a dashboard built on Kibana.

- Use in conjunction with service helper software to generate suggestions that
  are based on the status of a system or piece information that is required by
  support technicians.


The following table provides a list of the Hostinfo checks supported by the monitoring
service.

**Hostinfo checks supported by Rackspace Monitoring**

+------------------------+-----------------------------------------------------------+
| Hostinfo type          | Description                                               |
+========================+===========================================================+
| `connections`_         | Runs the :code:`arp -an` and :code:`netstate -naten`      |
|                        | commands and retrieves information about any open         |
|                        | listening ports and any connections to them.              |
+------------------------+-----------------------------------------------------------+
| `iptables`_            | Runs the :code:`iptables -S` command to retrieve data     |
|                        | about IPv4 policies.                                      |
+------------------------+-----------------------------------------------------------+
| `ip6tables`_           | Runs the :code:`iptables -S` command to retrieve data     |
|                        | about IPv6 policies.                                      |
+------------------------+-----------------------------------------------------------+
| `autoupdates`_         | Checks if automatic updates are enabled on a Linux        |
|                        | distribution.                                             |
+------------------------+-----------------------------------------------------------+
| `passwd`_              | Reads /etc/passwd and then runs the :code:`passwd -S`     |
|                        | command for every user. Obtains password-related          |
+------------------------+-----------------------------------------------------------+
| `pam`_                 | Reads /etc/pam.d and retrieves data about                 |
|                        | pluggable authentication modules.                         |
+------------------------+-----------------------------------------------------------+
| `cron`_                | Reads files in the crontabs directory and                 |
|                        | retrieves information about scheduled Cron jobs.          |
+------------------------+-----------------------------------------------------------+
| `kernel_modules`_      | Reads the /proc/modules virtual directory and             |
|                        | retrieves data about the modules that are loaded          |
|                        | into the kernel.                                          |
+------------------------+-----------------------------------------------------------+
| `cpu`_                 | Retrieves information about the host's CPU.               |
+------------------------+-----------------------------------------------------------+
| `disk`_                | Retrieves information about the host's hard disks.        |
+------------------------+-----------------------------------------------------------+
| `filesystem`_          | Retrieves information about the host's filesystem.        |
+------------------------+-----------------------------------------------------------+
| `filesystem_state`_    | Retrieves information about the read-only/read-write      |
|                        | filesystems.                                              |
+------------------------+-----------------------------------------------------------+
| `login`_               | Reads /etc/login.defs and retrieves data about the        |
|                        | login shell. This check does not retrieve any             |
|                        | password information or any other sensitive data.         |
+------------------------+-----------------------------------------------------------+
| `memory`_              | Retrieve information about the host's memory.             |
+------------------------+-----------------------------------------------------------+
| `network`_             | Retrieves information about the host's network            |
|                        | interface.                                                |
+------------------------+-----------------------------------------------------------+
| `nil`_                 | Returns no information. This Hostinfo check is            |
|                        | mainly used within the monitoring agent code              |
|                        | itself.                                                   |
+------------------------+-----------------------------------------------------------+
| `packages`_            | Runs either the :code:`dpkg-query` or                     |
|                        | :code:`rpm -qa` command and retrieves a list of           |
|                        | package names and versions.                               |
+------------------------+-----------------------------------------------------------+
| `procs`_               | Retrieves information about the processes that            |
|                        | are running on the host.                                  |
+------------------------+-----------------------------------------------------------+
| `system`_              | Retrieves information about the host's operating          |
|                        | system.                                                   |
+------------------------+-----------------------------------------------------------+
| `who`_                 | Retrieves information about the user, device, time        |
|                        | and host.                                                 |
+------------------------+-----------------------------------------------------------+
| `date`_                | Retrieves the date and time on the host.                  |
+------------------------+-----------------------------------------------------------+
| `sysctl`_              | Runs the :code:`sysctl -A` command and retrieves all      |
|                        | possible key-value pairs of the kernel parameters         |
|                        | that can be set at runtime.                               |
+------------------------+-----------------------------------------------------------+
| `sshd`_                | Runs the :code:`sshd -T` command and retrieves the        |
|                        | configuration parameters for the open SSH daemon.         |
+------------------------+-----------------------------------------------------------+
| `fstab`_               | Reads /etc/fstab and retrieves information about          |
|                        | the file system configuration.                            |
+------------------------+-----------------------------------------------------------+
| `fileperms`_           | Reads a pre-specified list of files and checks and	       |
|                        | retrieves their permissions.                              |
+------------------------+-----------------------------------------------------------+
| `services`_            | Reads a few folders and files and generates a list	       |
|                        | of startup services.                                      |
+------------------------+-----------------------------------------------------------+
| `deleted\_libs`_       | Greps through the output of :code:`lsof -nnP` to          |
+------------------------+-----------------------------------------------------------+
| `cve`_                 | Retrieves a unique sorted list of common                  |
|                        | vulnerabilities and exposures that have been              |
|                        | patched on the host system.                               |
+------------------------+-----------------------------------------------------------+
| `last\_logins`_        | Runs last to get information about previous               |
|                        | icurrent logged-in user, bootups and when :code:`last`    |
|                        | started logging.                                          |
+------------------------+-----------------------------------------------------------+
| `remote\_services`_    | Runs the :code:`netstat -tlpen` command to obtain a       |
|                        | list of active internet connections to servers            |
|                        | and underlying programs that are using them.              |
+------------------------+-----------------------------------------------------------+
| `ip4routes`_           | Runs the :code:`netstat -nr4` command and retrieves       |
|                        | information about the kernel's IPv4 routing               |
|                        | tables.                                                   |
+------------------------+-----------------------------------------------------------+
| `ip6routes`_           | Runs the :code:`netstat -nr6` command and retrieves       |
|                        | information about the kernel's IPv6 routing               |
|                        | tables                                                    |
+------------------------+-----------------------------------------------------------+
| `apache2`_             | Retrieves information about the host's apache2            |
|                        | instance and installation if it exists.                   |
+------------------------+-----------------------------------------------------------+
| `fail2ban`_            | Retrieves information about the host's fail2ban           |
|                        | instance and installation.                                |
+------------------------+-----------------------------------------------------------+
| `lsyncd`_              | Checks the status of the live syncing daemon or           |
|                        | lsyncd.                                                   |
+------------------------+-----------------------------------------------------------+
| `nginx\_config`_       | Returns vhosts, version, includes, status (0 if           |
|                        | everything is ok when :code:`nginx -t` is run),           |
|                        | configuration path, prefix and configure                  |
|                        | arguments for local nginx.                                |
+------------------------+-----------------------------------------------------------+
| `wordpress`_           | Returns the path, version and edition of local            |
|                        | Wordpress instances found via the apache2 and             |
|                        | nginx configurations.                                     |
+------------------------+-----------------------------------------------------------+
| `magento`_             | Returns the path, version and edition of local            |
|                        | Magento instances found via the apache2 and nginx         |
|                        | configurations.                                           |
+------------------------+-----------------------------------------------------------+
| `php`_                 | Returns information such as version, type  (HHVM/PHP), and|
|                        | errors related to PHP. Uses the CLI and log files to      |
|                        | to extract this information.                              |
+------------------------+-----------------------------------------------------------+
| `postfix`_             | Checks the status of the postfix mail server.             |
+------------------------+-----------------------------------------------------------+

You can use the Rackspace Monitoring API to run Hostinfo checks. To run a
hostinfo check, issue the following cURL request:

Use the following cURL request to run Hostinfo checks by using the monitoring
service.

.. code::

     curl -H 'X-Auth-Token: $token' '\
          https://monitoring.api.rackspacecloud.com/v1.0/ \
          <tenandID>/agents/<agent_id>/host_info/<hostinfo_type>

For more information about how to work with checks using the Rackspace Monitoring API, see the
Checks section in the Rackspace Monitoring Developer Guide. For more information working with Hostinfo checks,
see the Agent host information.


.. _connections: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/CONNECTIONS.json

.. _iptables: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/IPTABLES.json

.. _ip6tables: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/IP6TABLES.json

.. _autoupdates: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/AUTOUPDATES.json

.. _passwd: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/PASSWD.json

.. _pam: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/PAM.json

.. _cron: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/CRON.json

.. _kernel_modules: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/KERNEL_MODULES.json

.. _cpu: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/CPU.json

.. _disk: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/DISK.json

.. _filesystem: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/FILESYSTEM.json

.. _filesystem_state: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/FILESYSTEM_STATE.json

.. _login: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/LOGIN.json

.. _memory: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/MEMORY.json

.. _network: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/NETWORK.json

.. _nil: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/NIL.json

.. _packages: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/PACKAGES.json

.. _procs: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/PROCS.json

.. _system: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/SYSTEM.json

.. _who: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/WHO.json

.. _date: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/DATE.json

.. _sysctl: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/SYSCTL.json

.. _sshd: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/SSHD.json

.. _fstab: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/FSTAB.json

.. _fileperms: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/FILEPERMS.json

.. _services: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/SERVICES.json

.. _deleted_libs: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/DELETED_LIBS.json

.. _cve: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/CVE.json

.. _last_logins: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/LAST_LOGINS.json

.. _remote_services: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/REMOTE_SERVICES.json

.. _ip4routes: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/IP4ROUTES.json

.. _ip6routes: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/IP6ROUTES.json

.. _apache2: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/APACHE2.json

.. _fail2ban: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/FAIL2BAN.json

.. _lsyncd: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/LSYNCD.json

.. _nginx_config: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/NGINX_CONFIG.json

.. _wordpress: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/WORDPRESS.json

.. _magento: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/MAGENTO.json

.. _php: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/PHP.json

.. _postfix: https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent/blob/master/hostinfo/debug/POSTFIX.json
