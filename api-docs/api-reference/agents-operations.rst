.. _agents-operations:

======
Agents
======

The optional Monitoring Agent resides on the host server being
monitored. You can use the agent to gather on-host metrics
based on agent checks and push them to Rackspace Monitoring where
you can analyze them, use them with the Rackspace Monitoring
infrastructure, and archive them.

.. note::

   To learn about installing and configuring monitoring agents, read the
   :ref:`Install and configure <install-and-configure>` section.

The agent adheres to a few core design principals to ensure it fits easily
and securely into your infrastructure:

* **Size**
  The agent uses very few resources. The design goal of the agent is to run
  as a single process with as few dependencies as possible. The agent
  consumes a nominal amount of RAM.

* **Security**
  The agent has multiple layers of security to protect your infrastructure.
  The agent is designed using best practices like package signing,
  x509 certificates, and TLS throughout the agent infrastructure.

* **Simple Protocol**
  The agent communicates with Rackspace Monitoring via a documented
  JSON protocol.

* **Open Source**
  The agent source code is available under the Apache 2.0 license. This
  gives your the ability to inspect the implementation and compile the
  agent on platforms where native packages are not supported.
  See the `source repository <https://github.com/virgo-agent-toolkit/rackspace-monitoring-agent>`_.

Security
~~~~~~~~

The agent implements several layers of security to protect your
infrastructure:

* **Signed Install Binaries**
  Agent Linux binaries and repositories are signed using public key
  cryptography and verified using distribution native methods. See
  :ref:`Install and configure <install-and-configure>`
  for instructions.

* **Secure Endpoint Connections**
  Connections to the Agent Endpoint use TLS and trust only a single root
  CA certificate that is directly under Rackspace control.

* **No Arbitrary Commands**
  The goal of the agent is to gather metrics about your system. The agent
  is not designed for you to run arbitrary commands on your system. This
  means that even if your Rackspace API token is compromised the only
  thing an attacker will have access to is metric data.

* **Signed Updates**
  Agent updates are verified against a cryptographic digest which is signed
  by the agent root certificate authority. This signing certificate is
  separate from the endpoint TLS certificate and the signing is done on
  a single computer, off-line. This means that the security of updates
  is separated from that of the endpoint.

Agent IDs
~~~~~~~~~

Agent IDs are user specified strings that are a maximum of 255
characters and can contain letters, numbers, dashes (-) and
dots (.). If you used the Setup wizard to install and configure
the agent on your host server, the agent ID for your agent is the
fully qualified domain name (FQDN) of the host on which the agent
is installed.

Agents API operations
~~~~~~~~~~~~~~~~~~~~~

Use the following agents API operations to get information about agents and
agent connections.

.. contents::
   :local:
   :depth: 1

.. include:: methods/get-list-agents.rst
.. include:: methods/get-agent-by-id.rst
.. include:: methods/get-list-agent-connections.rst
.. include:: methods/get-list-agent-connection-by-id.rst
