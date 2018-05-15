.. _install-and-configure:

===============================
Install and configure the agent
===============================

This section provides instructions for installing and configuring the
Rackspace Monitoring Agent. Instructions are also provided in the How-To
article `Install and configure the Rackspace Monitoring Agent <https://support.rackspace.com/how-to/install-and-configure-the-rackspace-monitoring-agent/>`_.


.. _install-agent:

Install the agent
~~~~~~~~~~~~~~~~~

* :ref:`Install the agent using meta packages <install-agent-meta-packages>`
* :ref:`Install the agent with copy and paste <install-agent-copy-paste>`
* :ref:`Install the agent step-by-step <install-agent-step-by-step>`
* :ref:`Install the agent on Windows <install-agent-windows>`

Use of the Rackspace Monitoring Agent is optional. If you choose to use the
agent, you must install it on each server that you want to monitor.

Package Manager installation is supported for the following operating systems:

-  Ubuntu and Debian

-  Red Hat, Fedora, and CentOS

-  Windows

For more information about the agent, see `How the monitoring agent
works <http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/Concepts.html#how-agent-works>`__.
For information about the agent endpoints, including attributes and code
samples, see the :ref:`Agent
API operations <agents-operations>`
section. The Rackspace Monitoring agent is distributed under the `Apache
license <http://www.apache.org/licenses/LICENSE-2.0.html>`__.

For information about installing the agent from source, see
``https://github.com/racker/virgo``.

This section offers information about the methods available to install
monitoring agent:

-  The :ref:`meta packages
   method <install-agent-meta-packages>`. Use the meta
   packages procedure for the simplest, and recommended, method.

-  The :ref:`copy-and-paste agent installation
   method <install-agent-copy-paste>`. This method
   provides simple commands, per environment, that you can use to
   quickly install the monitoring agent. This method is fine if you are
   doing a small deployment and don't need to use scripts to install the
   agent multiple times.

-  The :ref:`granular step procedure
   method <install-agent-step-by-step>`. Use the step
   procedure if you want to understand, and possibly customize, each
   step of the agent installation. This method is also valuable if you
   will be automating the agent installation process over several or
   many servers.

..  note::

    Another option for agent installation is to use the `The Cloud
    Intelligence control panel This control panel provides easy monitoring
    configuration and set up as well as graphs for visualizing Rackspace
    Monitoring. For details, see
    :how-to:`Logging in to the Rackspace Intelligence dashboard <logging-in-to-the-rackspace-intelligence-dashboard>`.


.. _install-agent-meta-packages:

Install the agent using meta packages
-------------------------------------

The recommended method for installing the monitoring agent is the meta
packages method. It's recommended because it is the simplest. The meta
packages installation obviates the need to install the certificate or
create a repository manually. That's all done as part of the meta
package.

 
**To install the monitoring agent with the meta package method:**

#. Log into the server that you want to monitor.

#. Open a browser to the `Rackspace Monitoring Meta
   Packages <http://meta.packages.cloudmonitoring.rackspace.com/>`__.

#. Find your operating system and enter the commands provided.

Next, :ref:`run the agent setup program <run-agent-setup-program>`


.. _install-agent-copy-paste:

Install the agent with copy and paste
-------------------------------------

Find your operating system and follow those instructions.

-  :ref:`Ubuntu <install-agent-copy-paste-ubuntu>`

-  :ref:`Debian <install-agent-copy-paste-debian>`

-  :ref:`Red Hat <install-agent-copy-paste-redhat>`

-  :ref:`Fedora <install-agent-copy-paste-fedora>`

-  :ref:`CentOS <install-agent-copy-paste-centos>`


.. _install-agent-copy-paste-ubuntu:

Ubuntu
^^^^^^
 
**To install the agent on Ubuntu with copy and paste:**

#. For all supported releases of Ubuntu, run the following WHOLE COMMAND,
   without line breaks, to add the monitoring agent package repository to
   APT:

      .. code::

         sudo sh -c "echo 'deb http://stable.packages.cloudmonitoring.rackspace.com/ubuntu-$(lsb_release -rs)-x86_64 cloudmonitoring main' > /etc/apt/sources.list.d/rackspace-monitoring-agent.list"

#. Download the signing key for the agent repository and add it to APT:

   .. code::

       curl https://monitoring.api.rackspacecloud.com/pki/agent/linux.asc | sudo apt-key add -

#. Run an APT update to get package information for the new repository:

   .. code::

       sudo apt-get update

#. Install the agent.

   .. code::

       sudo apt-get install rackspace-monitoring-agent

Next, :ref:`run the agent setup program <run-agent-setup-program>`

.. _install-agent-copy-paste-debian:

Debian
^^^^^^
 
**To install the agent on Debian with copy and paste:**

#. Find your Linux distribution and version and run the WHOLE COMMAND
   listed, without line breaks, to add the monitoring agent package
   repository to APT.

   -  **Debian Squeeze**:

      .. code::

          sudo sh -c 'echo "deb http://stable.packages.cloudmonitoring.rackspace.com/debian-squeeze-x86_64 cloudmonitoring main" > /etc/apt/sources.list.d/rackspace-monitoring-agent.list'

   -  **Debian Testing**:

      .. code::

          sudo sh -c 'echo "deb http://stable.packages.cloudmonitoring.rackspace.com/debian-testing-x86_64 cloudmonitoring main" > /etc/apt/sources.list.d/rackspace-monitoring-agent.list'

   -  **Debian Unstable**:

      .. code::

          sudo sh -c 'echo "deb http://stable.packages.cloudmonitoring.rackspace.com/debian-unstable-x86_64 cloudmonitoring main" > /etc/apt/sources.list.d/rackspace-monitoring-agent.list'

   -  **Debian Wheezy**:

      .. code::

          sudo sh -c 'echo "deb http://stable.packages.cloudmonitoring.rackspace.com/debian-wheezy-x86_64 cloudmonitoring main" > /etc/apt/sources.list.d/rackspace-monitoring-agent.list'

#. Download the signing key for the agent repository and add it to APT.

   .. code::

       curl https://monitoring.api.rackspacecloud.com/pki/agent/linux.asc | sudo apt-key add -

#. Run an APT update to get package information for the new repository.

   .. code::

       sudo apt-get update

#. Install the agent.

   .. code::

       sudo apt-get install rackspace-monitoring-agent

Next, :ref:`run the agent setup program <run-agent-setup-program>`


.. _install-agent-copy-paste-redhat:

Red Hat
^^^^^^^

**To install the agent on Red Hat with copy and paste:**

#. Run the listed command to install the package signing key. Please run
   the WHOLE COMMAND.

   -  **Red Hat 5**:

      .. code::

          curl https://monitoring.api.rackspacecloud.com/pki/agent/redhat-5.asc > /tmp/signing-key.asc
          sudo rpm --import /tmp/signing-key.asc

   -  **Red Hat 6**:

      .. code::

          curl https://monitoring.api.rackspacecloud.com/pki/agent/redhat-6.asc > /tmp/signing-key.asc
          sudo rpm --import /tmp/signing-key.asc

   -  **Red Hat 7**:

      .. code::

          curl https://monitoring.api.rackspacecloud.com/pki/agent/redhat-7.asc > /tmp/signing-key.asc
          sudo rpm --import /tmp/signing-key.asc

#. Create and edit a text file at
   /etc/yum.repos.d/rackspace-cloud-monitoring.repo with your favorite
   text editor (like nano or vi). Find your Linux distribution and
   version in the following table, then add the listed configuration block
   to the ``rackspace-cloud-monitoring.repo`` file to add the agent
   repository to yum (Please add the WHOLE BLOCK):

   -  **Red Hat 5**:

      .. code::

          [rackspace]
          name=Rackspace Monitoring
          baseurl=http://stable.packages.cloudmonitoring.rackspace.com/redhat-5-x86_64
          enabled=1

   -  **Red Hat 6**:

      .. code::

          [rackspace]
          name=Rackspace Monitoring
          baseurl=http://stable.packages.cloudmonitoring.rackspace.com/redhat-6-x86_64
          enabled=1

   -  **Red Hat 7**:

      .. code::

          [rackspace]
          name=Rackspace Monitoring
          baseurl=http://stable.packages.cloudmonitoring.rackspace.com/redhat-7-x86_64
          enabled=1

#. Install the agent.

   .. code::

       sudo yum install rackspace-monitoring-agent

Next, :ref:`run the agent setup program <run-agent-setup-program>`.


.. _install-agent-copy-paste-fedora:

Fedora
^^^^^^

 
**To install the agent on Fedora with copy and paste:**

#. Run the listed command to install the package signing key. Please run
   the WHOLE COMMAND.

   -  **Fedora 16**:

      .. code::

          curl https://monitoring.api.rackspacecloud.com/pki/agent/fedora-16.asc > /tmp/signing-key.asc
          sudo rpm --import /tmp/signing-key.asc

   -  **Fedora 17**:

      .. code::

          curl https://monitoring.api.rackspacecloud.com/pki/agent/fedora-17.asc > /tmp/signing-key.asc
          sudo rpm --import /tmp/signing-key.asc

   -  **Fedora 18**:

      .. code::

          curl https://monitoring.api.rackspacecloud.com/pki/agent/fedora-18.asc > /tmp/signing-key.asc
          sudo rpm --import /tmp/signing-key.asc

   -  **Fedora 19**:

      .. code::

          curl https://monitoring.api.rackspacecloud.com/pki/agent/fedora-19.asc > /tmp/signing-key.asc
          sudo rpm --import /tmp/signing-key.asc

   -  **Fedora 20**:

      .. code::

          curl https://monitoring.api.rackspacecloud.com/pki/agent/fedora-20.asc > /tmp/signing-key.asc
          sudo rpm --import /tmp/signing-key.asc

   -  **Fedora 21**:

      .. code::

          curl https://monitoring.api.rackspacecloud.com/pki/agent/fedora-21.asc > /tmp/signing-key.asc
          sudo rpm --import /tmp/signing-key.asc

#. Create and edit a text file at
   /etc/yum.repos.d/rackspace-cloud-monitoring.repo with your favorite
   text editor (like nano or vi). Find your Linux distribution and
   version in the following table, then add the listed configuration block
   to the rackspace-cloud-monitoring.repo file to add the agent
   repository to yum (Please add the WHOLE BLOCK).

   -  **Fedora 16**:

      .. code::

          [rackspace]
          name=Rackspace Monitoring
          baseurl=http://stable.packages.cloudmonitoring.rackspace.com/fedora-16-x86_64
          enabled=1

   -  **Fedora 17**:

      .. code::

          [rackspace]
          name=Rackspace Monitoring
          baseurl=http://stable.packages.cloudmonitoring.rackspace.com/fedora-17-x86_64
          enabled=1

   -  **Fedora 18**:

      .. code::

          [rackspace]
          name=Rackspace Monitoring
          baseurl=http://stable.packages.cloudmonitoring.rackspace.com/fedora-18-x86_64
          enabled=1

   -  **Fedora 19**:

      .. code::

          [rackspace]
          name=Rackspace Monitoring
          baseurl=http://stable.packages.cloudmonitoring.rackspace.com/fedora-19-x86_64
          enabled=1

   -  **Fedora 20**:

      .. code::

          [rackspace]
          name=Rackspace Monitoring
          baseurl=http://stable.packages.cloudmonitoring.rackspace.com/fedora-20-x86_64
          enabled=1

   -  **Fedora 21**:

      .. code::

          [rackspace]
          name=Rackspace Monitoring
          baseurl=http://stable.packages.cloudmonitoring.rackspace.com/fedora-21-x86_64
          enabled=1

#. Install the agent.

   .. code::

       sudo yum install rackspace-monitoring-agent

Next, :ref:`run the agent setup program <run-agent-setup-program>`


.. _install-agent-copy-paste-centos:

CentOS
^^^^^^

 
**To install the agent on CentOS with copy and paste:**

#. Run the listed command to install the package signing key. Please run
   the WHOLE COMMAND.

   -  **CentOS 5**:

      .. code::

          curl https://monitoring.api.rackspacecloud.com/pki/agent/centos-5.asc > /tmp/signing-key.asc
          sudo rpm --import /tmp/signing-key.asc

   -  **CentOS 6**:

      .. code::

          curl https://monitoring.api.rackspacecloud.com/pki/agent/centos-6.asc > /tmp/signing-key.asc
          sudo rpm --import /tmp/signing-key.asc

   -  **CentOS 7**:

      .. code::

          curl https://monitoring.api.rackspacecloud.com/pki/agent/centos-7.asc > /tmp/signing-key.asc
          sudo rpm --import /tmp/signing-key.asc

#. Create and edit a text file at
   /etc/yum.repos.d/rackspace-cloud-monitoring.repo with your favorite
   text editor (like nano or vi). Find your Linux distribution and
   version in the following table, then add the listed configuration block
   to the rackspace-cloud-monitoring.repo file to add the agent
   repository to yum (Please add the WHOLE BLOCK).

   -  **CentOS 5**:

      .. code::

          [rackspace]
          name=Rackspace Monitoring
          baseurl=http://stable.packages.cloudmonitoring.rackspace.com/centos-5-x86_64
          enabled=1

   -  **CentOS 6**:

      .. code::

          [rackspace]
          name=Rackspace Monitoring
          baseurl=http://stable.packages.cloudmonitoring.rackspace.com/centos-6-x86_64
          enabled=1

   -  **CentOS 7**:

      .. code::

          [rackspace]
          name=Rackspace Monitoring
          baseurl=http://stable.packages.cloudmonitoring.rackspace.com/centos-7-x86_64
          enabled=1

#. Install the agent.

   .. code::

       sudo yum install rackspace-monitoring-agent

Next, :ref:`run the agent setup program <run-agent-setup-program>`

.. _install-agent-step-by-step:

Install the agent step-by-step
------------------------------

* :ref:`Ubuntu or Debian <install-agent-steps-ubuntu-debian>`
* :ref:`Red Hat, Fedora, or CentOS <install-agent-steps-redhat-fedora-centos>`

This section provides granular details about each step of the agent
installation process.

.. _install-agent-steps-ubuntu-debian:

Ubuntu or Debian
^^^^^^^^^^^^^^^^

This section explains how to install the agent on a server that is
running an Ubuntu or Debian OS.

These steps have been tested on Ubuntu Lucid 10.04 but should work on
most recent versions of Ubuntu or Debian.

 
**To install the agent on Ubuntu or Debian step by step:**

#. Add a repository for the agent by creating a text file named
   ``rackspace-monitoring-agent.list`` in the
   ``/etc/apt/sources.list.d`` directory.

#. Add the following content to the ``rackspace-monitoring-agent.list``
   file:

   .. code::

       deb <repo-name> cloudmonitoring main

   ``repo-name`` is replaced with the following link with the appropriate package inserted:

   ``http://stable.packages.cloudmonitoring.rackspace.com/ubuntu-[Release Number, such as 14.04]-x86_64``

   For example, to install Ubuntu, version 14.04, your file would
   contain this content:

   .. code::

       deb http://stable.packages.cloudmonitoring.rackspace.com/ubuntu-14.04-x86_64 cloudmonitoring main

#. Add a signing key for the apt repository.

   .. code::

       $ curl https://monitoring.api.rackspacecloud.com/pki/agent/linux.asc | sudo apt-key add -

#. Update your apt-get program to recognize the new repository.

   .. code::

       $ sudo apt-get update

#. Install the agent.

   .. code::

       $ sudo apt-get install rackspace-monitoring-agent

Next, :ref:`run the agent setup program <run-agent-setup-program>`


.. _install-agent-steps-redhat-fedora-centos:

Red Hat, Fedora, or CentOS
^^^^^^^^^^^^^^^^^^^^^^^^^^

This section explains how to install the agent on a server that is
running a Red Hat, Fedora, or CentOS operating system.

 
**To install the agent on Red Hat, Fedora, or CentOS step by step:**

#. Enable the signing key.

   .. code::

       $ curl https://monitoring.api.rackspacecloud.com/pki/agent/<signing-key> > /tmp/signing-key.asc

   .. code::

       $ sudo rpm --import /tmp/signing-key.asc

   ``<signing-key>`` is the correct signing key for your OS:

   +--------------------------------------+--------------------------------------+
   | OS                                   | Signing Key                          |
   +======================================+======================================+
   | Red Hat Enterprise Linux 5, x86-64   | redhat-5.asc                         |
   +--------------------------------------+--------------------------------------+
   | Red Hat Enterprise Linux 6, x86-64   | redhat-6.asc                         |
   +--------------------------------------+--------------------------------------+
   | Red Hat Enterprise Linux 7, x86-64   | redhat-7.asc                         |
   +--------------------------------------+--------------------------------------+
   | Fedora 16, x86-64                    | fedora-16.asc                        |
   +--------------------------------------+--------------------------------------+
   | Fedora 17, x86-64                    | fedora-17.asc                        |
   +--------------------------------------+--------------------------------------+
   | Fedora 18, x86-64                    | fedora-18.asc                        |
   +--------------------------------------+--------------------------------------+
   | Fedora 19, x86-64                    | fedora-19.asc                        |
   +--------------------------------------+--------------------------------------+
   | Fedora 20, x86-64                    | fedora-20.asc                        |
   +--------------------------------------+--------------------------------------+
   | Fedora 21, x86-64                    | fedora-21.asc                        |
   +--------------------------------------+--------------------------------------+
   | CentOS 5, x86-64                     | centos-5.asc                         |
   +--------------------------------------+--------------------------------------+
   | CentOS 6, x86-64                     | centos-6.asc                         |
   +--------------------------------------+--------------------------------------+
   | CentOS 7, x86-64                     | centos-7.asc                         |
   +--------------------------------------+--------------------------------------+

   For example, on Red Hat version 5, you enter:

   .. code::

       $ curl https://monitoring.api.rackspacecloud.com/pki/agent/redhat-5.asc > /tmp/signing-key.asc

   .. code::

       $ sudo rpm --import /tmp/signing-key.asc

#. Set up the yum repository by creating a text file named
   ``rackspace-cloud-monitoring.repo`` in the
   ``/etc/yum.repos.d`` directory.

#. Add the following content to the ``rackspace-cloud-monitoring`` file:

   .. code::

       [rackspace]
       name=Rackspace Monitoring
       baseurl=<repo-name>
       enabled=1

   where ``<repo-name>`` is one of the following available packages:

   -  http://stable.packages.cloudmonitoring.rackspace.com/redhat-5-x86\_64

   -  http://stable.packages.cloudmonitoring.rackspace.com/redhat-6-x86\_64

   -  http://stable.packages.cloudmonitoring.rackspace.com/redhat-7-x86\_64

   -  http://stable.packages.cloudmonitoring.rackspace.com/fedora-16-x86\_64

   -  http://stable.packages.cloudmonitoring.rackspace.com/fedora-17-x86\_64

   -  http://stable.packages.cloudmonitoring.rackspace.com/fedora-18-x86\_64

   -  http://stable.packages.cloudmonitoring.rackspace.com/fedora-19-x86\_64

   -  http://stable.packages.cloudmonitoring.rackspace.com/fedora-20-x86\_64

   -  http://stable.packages.cloudmonitoring.rackspace.com/fedora-21-x86\_64

   -  http://stable.packages.cloudmonitoring.rackspace.com/centos-5-x86\_64

   -  http://stable.packages.cloudmonitoring.rackspace.com/centos-6-x86\_64

   -  http://stable.packages.cloudmonitoring.rackspace.com/centos-7-x86\_64

   For example, to install Red Hat version 6, your file would contain
   the following content:

   .. code::

       [rackspace]
       name=Rackspace Monitoring
       baseurl=http://stable.packages.cloudmonitoring.rackspace.com/redhat-6-x86_64/
       enabled=1

#. Install the agent packages.

   .. code::

       $ sudo yum update

   .. code::

       $ sudo yum install rackspace-monitoring-agent

Next, :ref:`run the agent setup program <run-agent-setup-program>`


.. _install-agent-windows:

Install the agent on Windows
----------------------------

You install the monitoring agent on a Windows system just like you
install other software: download the installation package and run the
installer.

 
**To install the agent on Windows**

#. Download the latest stable agent installer.

   -  **64-bit systems: Windows 2008 and Windows 2012**:
      http://stable.packages.cloudmonitoring.rackspace.com/rackspace-monitoring-agent-x64.msi

   -  **32-bit legacy systems: Windows 2008**:
      http://stable.packages.cloudmonitoring.rackspace.com/rackspace-monitoring-agent.msi

#. Run the installer. The installer automatically exits when it is
   complete.

#. Next, :ref:`run the agent setup program <run-agent-setup-program>` to
   generate a configuration file. Without a configuration file, the agent
   closes and is restarted by the Windows Service Manager. To prevent this
   continuous restarting, run the setup program immediately after
   installing the agent.


.. _configure-agent:

Configure the agent
~~~~~~~~~~~~~~~~~~~

When you configure a monitoring agent using the automated setup program, the
configuration process automatically creates a configuration file,
``rackspace-monitoring-agent.cfg`` and deploys it to one of the
following directories on the customer's server.

- On Linux systems, navigate to the ``/etc directory``.

-  On Windows systems, navigate to ``C:\ProgramData\Rackspace Monitoring\config\``.

You can also create or edit the configuration file manually to specify or
update the following attributes:

 .. list-table::
    :widths: 30 20 30
    :header-rows: 1

    * - Option
      - Type
      - Description
    * - monitoring\_token
      - string
      - Required. This token is a string that is either provided by the API
        or created during the --setup process. This token gives the agent
        access to the monitoring services for an account.
    * - monitoring\_id
      - string
      - Optional. Specifies a user-provided id string that identifies this
        agent to the monitoring services.
    * - monitoring\_snet\_region
      - string
      - Optional. This option tells the agent to connect to the agent
        endpoints over the Rackspace ServiceNet (instead of over the public
        Internet). Valid regions are DFW, ORD, LON, SYD, HKG, and IAD. If
        option is set, the value must match the region of the agent and the
        service it is running on.
    * - monitoring\_endpoints
      - comma-delimited sets of
        ``ip:port`` values
      - Optional. Provides a series of endpoint IP addresses for the agent to
        connect to instead of the default endpoint addresses.
    * - monitoring\_query\_endpoints
      - comma-delimited sets of
        ``ip:port`` values
      - Optional. Provides a series of API IP addresses for the agent to
        connect to instead of the default API addresses.
    * - monitoring\_proxy\_url
      - string
      - Optional. Provides a URL string to a HTTP Proxy service that supports
        the CONNECT command. This configuration must support CONNECT on port
        443. Additionally, ``HTTP_PROXY`` and ``HTTPS_PROXY`` are supported.                                                                                     |

You can use any of the following options to specify the configuration
attributes for the monitoring agent:

-  For the simplest, fastest set up, use the `agent Setup
   program: ref:<configure-agent-with-setup>` that automates the configuration
   process and simplifies the process.

-  To step through each task in the configuration process at your own pace,
   complete the :ref:`manual set up process <configure-agent-manually>`

-  To create a re-usable YAML file for each check you want the agent to
   perform, complete the :ref:`YAML file agent
   configuration process <configure-agent-with-YAML>`.


.. _configure-agent-with-setup:

Configuring the agent with the Setup program
---------------------------------------------

The agent Setup program provides the easiest way to get started with the
agent. Setup completes the following configuration tasks for you:

-  Configures an agent token that the agent uses to authenticate with
   |product name|.

-  Creates an agent configuration file,
   ``rackspace-monitoring-agent.cfg``.

   On Linux systems this file is located in the ``/etc`` directory

   On Windows systems, you can find it in
   ``C:\ProgramData\Rackspace Monitoring\config\``.

-  Verifies connectivity to the Rackspace data centers.

-  Associates the agent with a monitoring entity.

You can also manually edit the agent configuration file. See
:ref:`Configure the agent manually <configure-agent-manually>` for details.

..  note::
    The Setup program supports the HTTP proxy environment variable.

.. _run-agent-setup-program:

Run the agent setup program
^^^^^^^^^^^^^^^^^^^^^^^^^^^

You need your Rackspace user name and API key to run the setup program.
If you don't have them, follow the process to
:ref:`get your credentials <get-credentials>`.

To run the program, complete the following steps:

#. Log in as the root user on the server where you installed the agent
   package.

   -  On Linux: Enter the following command to run the Setup program:

      .. code::

          $ rackspace-monitoring-agent --setup

      Use this command to run Setup with the HTTP proxy variable:

      .. code::

          $ HTTP_PROXY=<ip_address:port> rackspace-monitoring-agent --setup

      Alternately, you can use an FQDN:

      .. code::

          $ HTTP_PROXY=<FQDN> rackspace-monitoring-agent --setup

   -  On Windows, the agent location depends on the version of the agent
      installed and the architecture of the operating system.

      ..  note::
         If you are using PowerShell, precede the path with an ampersand
         (&).

      For a 64-bit system with the 64-bit agent installed, enter the
      following command:

      .. code::

          $"C:\Program Files\Rackspace Monitoring\rackspace-monitoring-agent.exe" -o --setup

      For a 64-bit system with the 32-bit agent installed, enter the
      following command:

      .. code::

          $"C:\Program Files (x86)\Rackspace Monitoring\rackspace-monitoring-agent.exe" -o --setup

      For a 32-bit system with the 32-bit agent installed, enter the
      following command:

      .. code::

          $"C:\Program Files\Rackspace Monitoring\rackspace-monitoring-agent.exe" -o --setup

   A list of Setup settings appears, which includes the agent ID. The
   agent ID matches the hostname of the server.

#. When prompted, enter your Rackspace Cloud user name.

#. When prompted, enter either your API key or your Cloud Control Panel
   password.

   Note that this entry is displayed in clear text while it is typed;
   therefore, using your API key instead of your password is
   recommended. Neither value is stored in clear text, it is used only
   for this initial authentication.

   The Rackspace Monitoring service creates an agent token and syncs it with
   the entity representing the resource that you are monitoring.

   You should see the message ``Agent successfully connected!``

   The agent should automatically start.

   The next prompt displays a list of Rackspace Monitoring entities.

..  note::

    A Rackspace Monitoring entity is created automatically for every Rackspace
    cloud server on your account. But if you install the agent on a
    dedicated server, or on a server not hosted with Rackspace, including a
    server in a Rackspace private cloud, entities are not automatically
    created. Instead, you will have to manually create an entity and agent
    token.

    After you have an agent token, associate it with the resource entity by
    choosing the entity ID created for your resource, or select the option
    to create a new entity. If you create a new monitoring entity on your
    server, it won't be visible in the Cloud Control Panel, but you can see
    see and configure it using the
    :how-to:`Cloud Intelligence dashboard <logging-in-to-the-rackspace-intelligence-dashboard>`
    You need the entity ID when you create checks to monitor the health of your server; see
    :ref:`First steps with the agent <first-steps>`

To learn more, see the article :how-to:`Monitoring: Differences Between
Rackspace Server Users and Non-Rackspace Server
Users <monitoring-differences-between-rackspace-server-users-and-non-rackspace-server-users>`.

.. _configure-agent-manually:

Configuring the agent manually
------------------------------

..  note::
    Using the Setup program is the preferred way to set up the agent. This
    section is provided as an alternate method of setting up the agent. If
    you used the Setup program to complete the agent configuration, skip
    this section.

 
**To manually set up the agent**

1. If you have not installed ``raxmon`` yet, install it on your local
   workstation. See :ref:`Install and configure raxmon <gsg-install-raxmon>`.

   If you prefer to use the API, instead of the raxmon CLI, see the
   `entities
   API <http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/service-entities.html>`__
   and `Create an agent
   token <http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/service-agent-tokens.html>`__.

2. **Create an entity in the monitoring service, as follows:**

   .. code::

       $ raxmon-entities-create --label=<entityLabel>

   ``<entityLabel>`` is a name for the new entity. This entity
   represents the server where you're installing the agent. For example,
   if the server is named employee-news, you might use that hostname as
   the ``<entityLabel>``.

   This command returns an entity ID for the new entity, for example,
   ``ent12345``. You need to supply this entity ID for ``<entityId>`` in
   the next several steps.

3. Assign an ID to your agent and associate it with the server entity
   that you just created. Rackspace Monitoring uses this ID for two-way
   communication between the agent and the Rackspace Monitoring endpoint.

   .. code::

       $ raxmon-entities-update --id=<entityId> --agent-id=<agentId>

   The placeholders in the command are defined as follows:

   ``<entityId>``
       The entity ID returned in the previous step.

   ``<agentId>``
       The ID, or name, that you want to assign to the agent installed
       on the server. For the ID value, use any label that makes sense
       for the system that you plan to monitor. For example, you can use
       the server hostname, although the ID does not need to match or
       contain any part of the entity label or the entity ID.

4. Create an agent token.

   The agent uses an agent token to authenticate with the Cloud
   Monitoring endpoint. The token ensures that no one masquerades as
   your server.

   .. code::

       $ raxmon-agent-tokens-create --label="<agent-token-label>"

   ``<agent-token-label>`` is the name for your agent token. You can use
   any name.

5. Enter the following command to see a list of tokens, including the
   one you just created.

   .. code::

       $ raxmon-agent-tokens-list

   Note the agent token value to use in the next few steps.

6. Log in as the root user on the server where you installed the agent.

7. Use ``vi`` or your favorite text editor to edit the
   rackspace-monitoring-agent.cfg file, or create it if it does not
   exist.

   .. code::

       $ sudo vi /etc/rackspace-monitoring-agent.cfg

8. Add the following content to the ``rackspace-monitoring-agent.cfg``
   file:

   .. code::

       monitoring_id <agentId>
       monitoring_token <agentToken>

   The placeholders in the command are defined as follows:

   * ``<agentId>``
       The agent ID you assigned to the agent in Step 3.

   * ``<agentToken>``
       The token value returned for your agent token by the
       **raxmon-agent-tokens-list** command.

9. To set the HTTP proxy variable, add the following entry to the
   configuration file, where ``ip_address:port`` stands for IP address for the
   resource on which you're installing the agent:

   .. code::

      $ HTTP_PROXY=<ip_address:port> rackspace-monitoring-agent --setup


   You can optionally configure the agent to use a reverse proxy to look up
   custom SRV records by having it proxy to LON, DFW, and ORD as shown in the
   following example:

   .. code::

      monitoring_query_endpoints _monitoringagent._tcp.dfw1.prod.monitoring.api.rackspacecloud.com, _monitoringagent._tcp.ord1.prod.monitoring.api.rackspacecloud.com, _monitoringagent._tcp.lon3.prod.monitoring.api.rackspacecloud.com


   To optionally force a connection to a particular IP address and port, add
   the following to your agent configuration file:

   .. code::

      monitoring_endpoints 192.168.95.178:50051, 192.168.95.178:50052, 192.168.95.178:50053

10. You can also set the HTTP proxy variable to use an FQDN. To do so, add the
    following entry to the configuration file where ``FQDN`` stands for the
    fully-qualified domain name for the resource on which you're installing
    the agent:

   .. code::

      $ HTTP_PROXY=<FQDN> rackspace-monitoring-agent --setup

11. To disable automatic updates for your monitoring agent, add the following:

    .. code::

       monitoring_update disabled

You're now ready to start the agent. See
:ref:`Start the agent <start-the-agent>`.

For more information about the agent configuration file, see
:ref:`Agent configuration file <configure-agent>`.


.. _configure-agent-with-YAML:

Configuring the agent with YAML files
-------------------------------------

* :ref:`Example server-side configuration YAML file <configure-server-side-YAML>`
* :ref:`How to use a server-side configuration YAML file <configure-use-server-side-YAML>`
* :ref:`Troubleshoot agent configuration with YAML files <troubleshoot-agent-configuration-with-YAML>`

The server-side monitoring configuration is a new method that enables
you to easily configure Rackspace Monitoring on the server that you want to
monitor. It is especially useful in conjunction with automation tools or
when dealing with duplicate servers. Automation tools like Chef, Puppet,
and Ansible can maintain a repository of configuration files to
automatically create monitoring checks and alarms for a given server or
servers. Server-side monitoring configuration helps you set up
monitoring more quickly.

..  note::
    You must update your agent to take advantage of this new feature. The
    required agent version is 1.0.0-68 or later.

Server-side monitoring configuration files are written in YAML (`YAML
Ain’t Markup Language <http://www.yaml.org/>`__), a text file with a
column-based syntax. You can name YAML files as you like, but they must end in
``.yaml``. Each YAML configuration file can contain
configurations for one check and its associated alarms. You create a
series of YAML files, one for each check that you want. A single file
can be used repeatedly on many servers to configure the same check and
associated alarms for those servers. The YAML configuration files are
read every time you start the agent.

.. note::
  For Windows, the files should have the name of the network interface for
  the Windows network, and ``C:\`` or ``D:\`` for the Windows disk.

The top-level fields in the YAML file represent the check's parameters.
The alarms are configured under a top-level field named ``alarms``. Each
alarm must be given a unique “handle” under the ``alarms`` field;
“handle” is a new term referring to a unique name. The system uses the
alarm “handle” to uniquely identify that alarm within the file. The
system uses the file name to uniquely identify checks and their alarms.

..  note::
	The handle is not the same as the alarm label in the API (or alarm name,
	in the Cloud Control Panel) or the ``alarmId``. Rather, it is a name
	that, along with the YAML file name, uniquely identifies that alarm. It
	is important that the alarm handles and file names be unique because the
	system uses them to identify server-side configured checks and alarms.
	After an alarm or check has been created with server-side configuration
	from a YAML file, the system uses the YAML file name and the alarm
	handle, or just the YAML file name for a check, to detect changes to
	those alarms or that check (for example, an updated YAML file). When you
	use the API to list checks or alarms, you can look at the ``confd_name``
	field to determine if that check or alarm was created by server-side
	configuration; if the field is non-null, the object was created by
	server-side configuration.

The configuration fields used within the YAML files are identical to the
configuration fields used by the API for checks and alarms. The API will
show two configuration fields for every check and alarm that are updated
as part of server-side configuration, ``confd_name`` and ``confd_hash``.
Both are generated from the YAML file, but ``confd_hash`` is generated
each time the YAML file is updated and uploaded to the agent endpoint,
whereas ``confd_name`` is generated at the time of the initial YAML file
deployment. API write requests (PUT or POST) to the ``confd_name`` and
``confd_hash`` fields are ignored. When using the API, you can tell if a
change was made to a server-side configuration object without using
server-side configuration, if the ``confd_name`` field is non-null and
the ``confd_hash`` field is 0 (zero).

After authentication, the agent reads the YAML configuration files and
sends them to the monitoring server. The monitoring service parses the
files and creates, updates, or deletes, the checks and alarms according
to the content of the files. Deleting a YAML configuration file deletes
that check and associated alarms from the monitoring service.


.. _configure-server-side-YAML:

Example server-side configuration YAML files
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* :ref:`File system check <file-sytem-check>`
* :ref:`HTTP check <http-check>`

This section provides two examples of YAML configuration. More examples
are provided in the
:ref:`Server-Side agent configuration YAML file examples <agent-config-yaml-files>`.

.. _file-sytem-check:

File system check
.................

The following example shows a server-side configuration file that sets
up an agent check for a file system at the target "/". The file name is
``my_fs.yaml``. It configures one check to alert on disk usage that
exceeds 90 percent of free space, two alarms, and other agent check
configuration options. The alarms have been given the handles of
``techs`` and ``its``. These handles uniquely identify these alarms
within the context of this check in the same manner that the file name
uniquely identifies this check among other server-side created checks
for this entity.

..  note::
	You can find existing ``notification_plan_id`` values and ``criteria``
	values through the API or the Cloud Control Panel.

 
**Example 4.1. File system check YAML file example**

.. code::

    type        : agent.filesystem
    label       : Check for Main Disk
    disabled    : false
    period      : 60
    timeout     : 30
    details     :
        target  : /
    alarms      :
        techs   :
            label                 : disk used alarm
            notification_plan_id  : npTechnicalContactsEmail
            criteria              : |
                if (percentage(metric['used'], metric['total']) > 90) {
                    return new AlarmStatus(CRITICAL, 'Less than 10% free space left.');
                }
                if (percentage(metric['used'], metric['total']) > 80) {
                    return new AlarmStatus(WARNING, 'Less than 20% free space left.');
                }
        its     :
            label                 : disk used alarm
            notification_plan_id  : npInformationTechEmail
            criteria              : |
                if (percentage(metric['used'], metric['total']) > 95) {
                    return new AlarmStatus(CRITICAL, 'Less than 5% free space left.');
                }
                if (percentage(metric['used'], metric['total']) > 90) {
                    return new AlarmStatus(WARNING, 'Less than 10% free space left.');
                }


.. _http-check:

HTTP check
..........

This example agent configuration file sets up an agent check for HTTP
traffic at the target "/". The file name is ``my_http.yaml``, it
configures one check to alert on a non-responsive web server, one alarm,
and other agent configuration options. The alarm has the handle of
``alarm1``.

 
**Example 4.2. HTTP check YAML file example**

.. code::

    type           : remote.http
    label          : Website check 1
    timeout        : 30
    period         : 90
    target_alias   : default
    details        :
        url        : http://www.foo.com
        method     : GET
    monitoring_zones_poll:
                   - mzord
    alarms         :
        alarm1     :
            label                 : http connect alarm
            notification_plan_id  : npTechnicalContactsEmail


For additional server-side agent configuration file examples, see
“Server-Side Agent Configuration YAML File Examples”.


.. _configure-use-server-side-YAML:

Use a server-side configuration YAML file
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This section describes how to create, update, and delete, a server-side
YAML configuration file.

To create a server-side configuration YAML file, complete the following
steps:

#. Using any text editor, create a YAML file, specifying the extension
   as ``.yaml``. YAML files are column-based, and you create the columns
   with whitespace left-side indentation. *Use spaces to add the
   indentation; tabs are ignored*. The number of spaces that you use to
   create the indentation is unimportant as long as parallel elements
   have the same left justification.

#.

   -  Save the YAML file in the ``rackspace-monitoring-agent.conf.d``
      subdirectory under the ``config`` directory:

   -  *(UNIX)* ``/etc/rackspace-monitoring-agent.conf.d``.

      *(Windows)*
      ``C:\ProgramData\Rackspace Monitoring\config\rackspace-monitoring-agent.conf.d``.

When you start the agent, it creates the checks and alarms.

..  note::
	Ensure that your agent has been set up via the agent setup
	program, or has a valid
	monitoring\_token in the ``/etc/rackspace-monitoring-agent.cfg`` file as
	described in the :ref:`Manual Agent Configuration
	section <configure-agent-manually>`.


Update a server-side configuration file and its checks and alarms
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you change parameters within the configuration files, the agent
updates the corresponding check and alarms after you start, or restart,
the agent and it reads the newly saved file. For information about
starting the agent, see :ref:`Start the agent <start-the-agent>`.


Delete a server-side configuration file and its checks and alarms
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If a server-side YAML configuration file is removed from a server, the
agent deletes the check and corresponding alarms configured in the file
when the server next reads the file. The YAML files are read every time
you start the agent. For information about starting the agent, see
:ref:`Start the agent <start-the-agent>`.

.. _troubleshoot-agent-configuration-with-YAML:

Troubleshoot agent configuration with YAML files
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Q:** How do I know if my server-side configuration was successful on a
particular server or on a group of servers?

**A:** On a single server, you can look at the agent log file for
success or error messages:

.. code::

    Wed Apr 23 03:47:49 2014 INF: Confd -> config_file post overall success
    Wed Apr 23 03:47:49 2014 INF: Confd -> config_file post operation result: success for file handle: mem.yaml at parsing
    Wed Apr 23 03:47:49 2014 INF: Confd -> config_file post operation result: success for file handle: main_disk.yaml at parsing
    Wed Apr 23 03:47:49 2014 INF: Confd -> config_file post operation result: success for check handle: {"check":"default","filename":"mem.yaml"} at unchanged
    Wed Apr 23 03:47:49 2014 INF: Confd -> config_file post operation result: success for check handle: {"check":"default","filename":"main_disk.yaml"} at unchanged
    Wed Apr 23 03:47:49 2014 INF: Confd -> config_file post operation result: success for alarm handle: {"alarm":"alarm1","filename":"mem.yaml"} at unchanged
    Wed Apr 23 03:47:49 2014 INF: Confd -> config_file post operation result: success for alarm handle: {"alarm":"alarm1","filename":"main_disk.yaml"} at unchanged

For a group of servers, or even one server, you can use the API endpoint
to verify that the agent created a check, or use the list alarms API
endpoint to verify that the agent created an alarm. Look for the
``confd_name`` field to have a string value and the ``confd_hash`` to be
a valid SHA1 hash.

.. code::

            {
                "id": "chlLIGmg4X",
                "label": "Check for Main Disk",
                "type": "agent.filesystem",
                "details": {
                    "target": "/"
                },
                "monitoring_zones_poll": null,
                "timeout": 30,
                "period": 60,
                "target_alias": null,
                "target_hostname": null,
                "target_resolver": null,
                "disabled": false,
                "metadata": null,
                "confd_name": "{\"check\":\"default\",\"filename\":\"my_fs2.yaml\"}",
                "confd_hash": "cf4174eef962cc27f7f9a410a39d83e82049803a",
                "created_at": 1398217064602,
                "updated_at": 1398217064602
            }

**Q:** Can I deploy server-side configuration to an existing server or
only to newly created servers?

**A:** You can use server-side configuration on any server, inside or
outside of Rackspace, newly created or existing. The YAML configuration
files are read every time you start the agent. The agent is commonly
started at server boot or you can manually restart it.

**Q:** What happens if I use the API or Control Panel to make a change
to a server that was configured with server-side configuration? Which
takes precedence, the API or the configuration file?

**A:** The change from API or Control Panel takes effect immediately,
but the YAML file is the source of authority. If the API modifies a
check or alarm that was created by server-side configuration, the
object’s ``confd_hash`` value is invalidated with a 0 (zero) value. When
you next start the agent, the object is updated or re-created to match
the values in the server-side configuration YAML file. Note that if a
check or alarm is created through the API or Control Panel, you cannot
modify it through server-side monitoring configuration.


.. _start-the-agent:

Start the agent
~~~~~~~~~~~~~~~

After you perform the configuration and set-up tasks, you're ready to
start the agent.

-  On Linux:

   Enter the following command:

   .. code::

       $ sudo service rackspace-monitoring-agent start

-  On Windows:

   #. Open the Service Manager by clicking **Start > Control Panel >
      Administrative Tools > Service**.

   #. Locate the Rackspace Monitoring Agent service, right-click it, and
      then select **Start**.

   If you just configured the agent, but the service appears to be
   already running, you must restart it before the agent will connect.

The ``rackspace-monitoring-agent`` command lets you manage the agent.
Enter the following command to see the available options:

.. code::

    $ rackspace-monitoring-agent --help

.. _first-steps:

First steps with the agent
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

After you start the agent, you create an entity to monitor and schedule
some agent checks.

 
**To create an entity and agent checks**

#. If you have not installed ``raxmon`` yet, do that now. See
   :ref:`Install and configure raxmon <gsg-install-raxmon>`.
   If you prefer to use the API instead of the ``raxmon`` CLI, see the API operations
   reference for the `entity`_ and `checks`_ resources.

#. Create some monitoring checks for the agent to run.

   For example, the following commands create three monitoring checks.
   The *type* values agent.memory, agent.cpu, and agent.filesystem, are
   agent check types, which means that the checks will run local to the
   system being monitored. And *entityId* is the ID for the entity that
   you associated with the agent.

   .. code::

       $ raxmon-checks-create --entity-id=<entityId> --type=agent.memory --period=30 --label=mem

   .. code::

       $ raxmon-checks-create --entity-id=<entityId> --type=agent.cpu --period=30 --label=cpu

   .. code::

       $ raxmon-checks-create --entity-id=<entityId> --type=agent.filesystem --period=30 --label=root --details="target=/"

.. _entity: http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/service-entities.html
.. _checks: http://docs.rackspace.com/cm/api/v1.0/cm-devguide/content/service-checks.html
