.. _hostinfo_checks:

Hostinfo checks types
-----------------------

Host information checks are a special class of checks that are used to fetch data on demand instead of on a regularly scheduled basis.The remote and agent-type checks are more closely connected to the larger Rackspace monitoring ecosystem. You can schedule alarms or alerts for remote and agent-type checks and run these checks on a regular schedule. Hostinfo checks cannot be scheduled and you cannot set any alarms or alerts for them.You can use Hostinfo checks to fetch data on demand, for example if you want to pipe da- ta about the host to other services or applications. Hostinfo checks are also convenient if you want to occasionally check something or want to narrow down a problem. You can also use Hostinfo checks to periodically fetch data from large clusters of servers but require the granularity of individual computers: for example for information dashboards that are built with Kibana. Hostinfo checks are also useful for service helper software that generates suggestions that are based on the status of a system or piece information that is required by support technicians.

.. _available_hostinfo_checks:

Available Hostinfo checks
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following table provides a list of all the Hostinfo checks that are
currently available.

+------------------------+---------------------------------------------------+
| Hostinfo type		     | Description                                       |
+========================+===================================================+
| [connections](https:   | Runs the ``arp -an`` and ``netstate -naten``      |
| //github.com/virgo-a   | commands and retrieves information about any open |
| gent-toolkit/rackspa   | listening ports and any connections to them.      |
| ce-monitoring-agent/   |                                                   |
| blob/master/hostinfo   |                                                   |
| /debug/CONNECTIONS.j   |                                                   |
| son)                   |                                                   |
+------------------------+---------------------------------------------------+
| [iptables] (https://g  | Runs the ``iptables -S`` command to retrieve data |
| ithub.com/virgo-agen   | about IPv4 policies.                              |
| t-toolkit/rackspace-   |                                                   |
| monitoring-agent/blo   |                                                   |
| b/master/hostinfo/de   |                                                   |
| bug/IPTABLES.json)     |                                                   |
+------------------------+---------------------------------------------------+
| [ip6tables] (https://  | Runs the ``iptables -S`` command to retrieve data |
| github.com/virgo-age   | about IPv6 policies.                              |
| nt-toolkit/rackspace   |                                                   |
| -monitoring-agent/bl   |                                                   |
| ob/master/hostinfo/d   |                                                   |
| ebug/IP6TABLES.json>)  |                                                   |
|                        |                                                   |
+------------------------+---------------------------------------------------+
| [autoupdates] (https:  | Checks if automatic updates are enabled on a Linux|
| //github.com/virgo-a   | distribution.                                     |
| gent-toolkit/rackspa   |                                                   |
| ce-monitoring-agent/   |                                                   |
| blob/master/hostinfo   |                                                   |
| /debug/AUTOUPDATES.j   |                                                   |
| son)                   |                                                   |
+------------------------+---------------------------------------------------+
| [passwd] (https://git  | Reads /etc/passwd and then runs the ``passwd -S`` |
| hub.com/virgo-agent-   | xommand for every user. Obtains password-related  |
| toolkit/rackspace-mo   | data.                                             |
| nitoring-agent/blob/   |                                                   |
| master/hostinfo/debu   |                                                   |
| g/PASSWD.json)         |                                                   |
+------------------------+---------------------------------------------------+
| [pam] (https://github  | Reads /etc/pam.d and retrieves data about         |
| .com/virgo-agent-too   | pluggable authentication modules.                 |
| lkit/rackspace-monit   |                                                   |
| oring-agent/blob/mas   |                                                   |
| ter/hostinfo/debug/P   |                                                   |
| AM.json)               |                                                   |
+------------------------+---------------------------------------------------+
| [cron] (https://githu  | Reads files in the crontabs directory and         |
| b.com/virgo-agent-to   | retrieves information about scheduled Cron jobs.  |
| olkit/rackspace-moni   |                                                   |
| toring-agent/blob/ma   |                                                   |
| ster/hostinfo/debug/   |                                                   |
| CRON.json)             |                                                   |
+------------------------+---------------------------------------------------+
| [kernel\_modules] (ht  | Reads the /proc/modules virtual directory and     |
| tps://github.com/vir   | retrieves data about the modules that are loaded  |
| go-agent-toolkit/rac   | into the kernel.                                  |
| kspace-monitoring-ag   |                                                   |
| ent/blob/master/host   |                                                   |
| info/debug/KERNEL_MO   |                                                   |
| DULES.json)            |                                                   |
+------------------------+---------------------------------------------------+
| [cpu] (https://github  | Retrieves information about the host's CPU.       |
| .com/virgo-agent-too   |                                                   |
| lkit/rackspace-monit   |                                                   |
| oring-agent/blob/mas   |                                                   |
| ter/hostinfo/debug/C   |                                                   |
| PU.json)               |                                                   |
+------------------------+---------------------------------------------------+
| [disk] (https://githu  | Retrieves information about the host's hard disks.|
| b.com/virgo-agent-to   |                                                   |
| olkit/rackspace-moni   |                                                   |
| toring-agent/blob/ma   |                                                   |
| ster/hostinfo/debug/   |                                                   |
| DISK.json>             |                                                   |
+------------------------+---------------------------------------------------+
| [filesystem](https:/   | Retrieves information about the host's filesystem.|
| /github.com/virgo-ag   |                                                   |
| ent-toolkit/rackspac   |                                                   |
| e-monitoring-agent/b   |                                                   |
| lob/master/hostinfo/   |                                                   |
| debug/FILESYSTEM.jso   |                                                   |
| n)                     |                                                   |
+------------------------+---------------------------------------------------+
| [login] (https://gith  | Reads /etc/login.defs and retrieves data about the|
| ub.com/virgo-agent-t   | login shell. This check does not retrieve any     |
| oolkit/rackspace-mon   | password information or any other sensitive data. |
| itoring-agent/blob/m   |                                                   |
| aster/hostinfo/debug   |                                                   |
| /LOGIN.json)           |                                                   |
+------------------------+---------------------------------------------------+
| [memory] (https://git  | Retrieve information about the host's memory.     |
| hub.com/virgo-agent-   |                                                   |
| toolkit/rackspace-mo   |                                                   |
| nitoring-agent/blob/   |                                                   |
| master/hostinfo/debu   |                                                   |
| g/MEMORY.json)         |                                                   |
+------------------------+---------------------------------------------------+
| [network] (https://gi  | Retrieves information about the host's network    |
| thub.com/virgo-agent   | interface.                                        |
| -toolkit/rackspace-m   |                                                   |
| onitoring-agent/blob   |                                                   |
| /master/hostinfo/deb   |                                                   |
| ug/NETWORK.json)       |                                                   |
+------------------------+---------------------------------------------------+
| [nil] (https://github  | Returns no information. This Hostinfo check is    |
| .com/virgo-agent-too   | mainly used within the monitoring agent code      |
| lkit/rackspace-monit   | itself.                                           |
| oring-agent/blob/mas   |                                                   |
| ter/hostinfo/debug/N   |                                                   |
| IL.json)               |                                                   |
+------------------------+---------------------------------------------------+
| [packages] (https://g  | Runs either the ``dpkg-query`` or ``rpm -qa``     |
| ithub.com/virgo-agen   | command and retrieves a list of package names and |
| t-toolkit/rackspace-   | versions.                                         |
| monitoring-agent/blo   |                                                   |
| b/master/hostinfo/de   |                                                   |
| bug/PACKAGES.json)     |                                                   |
+------------------------+---------------------------------------------------+
| [procs] (https://gith  | Retrieves information about the processes that    |
| ub.com/virgo-agent-t   | are running on the host.                          |
| oolkit/rackspace-mon   |                                                   |
| itoring-agent/blob/m   |                                                   |
| aster/hostinfo/debug   |                                                   |
| /PROCS.json)           |                                                   |
+------------------------+---------------------------------------------------+
| [system] (https://git  | Retrieves information about the host's operating  |
| hub.com/virgo-agent-   | system.                                           |
| toolkit/rackspace-mo   |                                                   |
| nitoring-agent/blob/   |                                                   |
| master/hostinfo/debu   |                                                   |
| g/SYSTEM.json)         |                                                   |
+------------------------+---------------------------------------------------+
| [who] (https://github  | Retrieves information about the user, device, time|
| .com/virgo-agent-too   | and host.                                         |
| lkit/rackspace-monit   |                                                   |
| oring-agent/blob/mas   |                                                   |
| ter/hostinfo/debug/W   |                                                   |
| HO.json)               |                                                   |
+------------------------+---------------------------------------------------+
| [date] (https://githu  | Retrieves the date and time on the host.          |
| b.com/virgo-agent-to   |                                                   |
| olkit/rackspace-moni   |                                                   |
| toring-agent/blob/ma   |                                                   |
| ster/hostinfo/debug/   |                                                   |
| DATE.json)             |                                                   |
+------------------------+---------------------------------------------------+
| [sysctl] (https://git  | Runs the ``sysctl -A`` command and retrieves all  |
| hub.com/virgo-agent-   | possible key-value pairs of the kernel parameters |
| toolkit/rackspace-mo   | that can be set at runtime.                       |
| nitoring-agent/blob/   |                                                   |
| master/hostinfo/debu   |                                                   |
| g/SYSCTL.json)         |                                                   |
+------------------------+---------------------------------------------------+
| [sshd] (https://githu  | Runs the ``sshd -T`` command and retrieves the    |
| b.com/virgo-agent-to   | configuration parameters for the open SSH daemon. |
| olkit/rackspace-moni   |                                                   |
| toring-agent/blob/ma   |                                                   |
| ster/hostinfo/debug/   |                                                   |
| SSHD.json)             |                                                   |
+------------------------+---------------------------------------------------+
| [fstab] (https://gith  | Reads /etc/fstab and retrieves information about  |
| ub.com/virgo-agent-t   | the host's file systems table.                    |
| oolkit/rackspace-mon   |                                                   |
| itoring-agent/blob/m   |                                                   |
| aster/hostinfo/debug   |                                                   |
| /FSTAB.json)           |                                                   |
+------------------------+---------------------------------------------------+
| [fileperms] (https://  | Reads a pre-specified list of files and checks and|
| github.com/virgo-age   | retrieves their permissions.                      |
| nt-toolkit/rackspace   |                                                   |
| -monitoring-agent/bl   |                                                   |
| ob/master/hostinfo/d   |                                                   |
| ebug/FILEPERMS.json)   |                                                   |
|                        |                                                   |
+------------------------+---------------------------------------------------+
| [services] (https://g  | Reads a few folders and files and generates a list|
| ithub.com/virgo-agen   | of startup services.                              |
| t-toolkit/rackspace-   |                                                   |
| monitoring-agent/blo   |                                                   |
| b/master/hostinfo/de   |                                                   |
| bug/SERVICES.json)     |                                                   |
+------------------------+---------------------------------------------------+
| [deleted\_libs] (http  | Greps through the output of ``lsof -nnP`` to      |
| s://github.com/virgo   | retrieve a list of processes that are using       |
| -agent-toolkit/racks   | deleted libs that no longer exist on the host.    |
| pace-monitoring-agen   |                                                   |
| t/blob/master/hostin   |                                                   |
| fo/debug/DELETED_LIB   |                                                   |
| S.json)                |                                                   |
+------------------------+---------------------------------------------------+
| [cve] (https://github  | Retrieves a unique sorted list of common          |
| .com/virgo-agent-too   | vulnerabilities and exposures that have been      |
| lkit/rackspace-monit   | patched on the host system.                       |
| oring-agent/blob/mas   |                                                   |
| ter/hostinfo/debug/C   |                                                   |
| VE.json)               |                                                   |
+------------------------+---------------------------------------------------+
| [last\_logins] (https  | Runs last to get information about previous logins|
| ://github.com/virgo-   | , current logged-in user, bootups and when 'last' |
| agent-toolkit/racksp   | started logging.                                  |
| ace-monitoring-agent   |                                                   |
| /blob/master/hostinf   |                                                   |
| o/debug/LAST_LOGINS.   |                                                   |
| json)                  |                                                   |
+------------------------+---------------------------------------------------+
| [remote\_services](h   | Runs the ``netstat -tlpen`` command to obtain a   |
| ttps://github.com/vi   | list of active internet connections to servers    |
| rgo-agent-toolkit/ra   | and underlying programs that are using them.      |
| ckspace-monitoring-a   |                                                   |
| gent/blob/master/hos   |                                                   |
| tinfo/debug/REMOTE_S   |                                                   |
| ERVICES.json)          |                                                   |
+------------------------+---------------------------------------------------+
| [ip4routes] (https://  | Runs the ``netstat -nr4`` command and retrieves   |
| github.com/virgo-age   | information about the kernel's IPv4 routing       |
| nt-toolkit/rackspace   | tables.                                           |
| -monitoring-agent/bl   |                                                   |
| ob/master/hostinfo/d   |                                                   |
| ebug/IP4ROUTES.json)   |                                                   |
+------------------------+---------------------------------------------------+
| [ip6routes] (https://  | Runs the ``netstat -nr6`` command and retrieves   |
| github.com/virgo-age   | information about the kernel's IPv6 routing       |
| nt-toolkit/rackspace   | tables                                            |
| -monitoring-agent/bl   |                                                   |
| ob/master/hostinfo/d   |                                                   |
| ebug/IP6ROUTES.json)   |                                                   |
+------------------------+---------------------------------------------------+
| [apache2] (https://gi  | Retrieves information about the host's apache2    |
| thub.com/virgo-agent   | instance and installation if it exists.           |
| -toolkit/rackspace-m   |                                                   |
| onitoring-agent/blob   |                                                   |
| /master/hostinfo/deb   |                                                   |
| ug/APACHE2.json)       |                                                   |
+------------------------+---------------------------------------------------+
| [fail2ban] (https://g  | Retrieves information about the host's fail2ban   |
| ithub.com/virgo-agen   | instance and installation.                        |
| t-toolkit/rackspace-   |                                                   |
| monitoring-agent/blo   |                                                   |
| b/master/hostinfo/de   |                                                   |
| bug/FAIL2BAN.json)     |                                                   |
+------------------------+---------------------------------------------------+
| [lsyncd] (https://git  | Checks the status of the live syncing daemon or   |
| hub.com/virgo-agent-   | lsyncd.                                           |
| toolkit/rackspace-mo   |                                                   |
| nitoring-agent/blob/   |                                                   |
| master/hostinfo/debu   |                                                   |
| g/LSYNCD.json)         |                                                   |
+------------------------+---------------------------------------------------+
| [nginx\_config] (http  | Returns vhosts, version, includes, status (0 if   |
| s://github.com/virgo   | everything is ok when ``nginx -t`` is run),       |
| -agent-toolkit/racks   | configuration path, prefix and configure          |
| pace-monitoring-agen   | arguments for local nginx.                        |
| t/blob/master/hostin   |                                                   |
| fo/debug/NGINX_CONFI   |                                                   |
| G.json)                |                                                   |
+------------------------+-----------------------------------------------------+
| [wordpress] (https://  | Returns the path, version and edition of local    |
| github.com/virgo-age   | Wordpress instances found via the apache2 and     |
| nt-toolkit/rackspace   | nginx configurations.                             |
| -monitoring-agent/bl   |                                                   |
| ob/master/hostinfo/d   |                                                   |
| ebug/WORDPRESS.json)   |                                                   |
+------------------------+-----------------------------------------------------+
| [magento] (https://gi  | Returns the path, version and edition of local    |
| thub.com/virgo-agent   | Magento instances found via the apache2 and nginx |
| -toolkit/rackspace-m   | configurations.                                   |
| onitoring-agent/blob   |                                                   |
| /master/hostinfo/deb   |                                                   |
| ug/MAGENTO.json)       |                                                   |
+------------------------+-----------------------------------------------------+
| [php] (https://github  | Returns information such as version, type         |
| .com/virgo-agent-too   | (HHVM/PHP), and errors related to PHP. Uses the   |
| lkit/rackspace-monit   | CLI and log files to extract this information.    |
| oring-agent/blob/mas   |                                                   |
| ter/hostinfo/debug/P   |                                                   |
| HP.json)               |                                                   |
+------------------------+----------- ---------------------------------------+
| [postfix] (https://gi  | Checks the status of the postfix mail server.     |
| thub.com/virgo-agent   |                                                   |
| -toolkit/rackspace-m   |                                                   |
| onitoring-agent/blob   |                                                   |
| /master/hostinfo/deb   |                                                   |
| ug/POSTFIX.json)       |                                                   |
+------------------------+---------------------------------------------------+

You can use the Cloud Monitoring API to run Hostinfo checks. To run a hostinfo check, issue the following cURL request:For more information on how to work with checks using the Cloud Monitoring API, see the Checks section in the Cloud Monitoring Developer Guide. For more information working with Hostinfo checks, see Agent host information.