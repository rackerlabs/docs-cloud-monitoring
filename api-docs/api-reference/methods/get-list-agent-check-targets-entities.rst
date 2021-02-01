.. _list-agent-check-targets:

List agent check targets
~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /entities/{entityId}/agent/check_types/{agentCheckType}/targets

Lists agent check targets for this entity.

The ``targets`` endpoint is used retrieve a set of targets
available to the specified agent regarding the specified check type.

Agent check types can gather data for a related set of target
devices on the server where the agent is installed. Not every check
type has a configurable target; currently supported check types with
targets are ``agent.filesystem``, ``agent.disk``, ``agent.network``,
and ``agent.plugin``.

* Targets returned for ``agent.network`` are the network
  interfaces accessible to the agent.
* Targets returned for ``agent.filesystem`` list the mounted filesystems
  accessible by the agent.
* Targets returned for ``agent.disk`` are the disks accessible to the agent.
* Targets returned for ``agent.plugin`` are the plugins installed for
  use with the agent. These plugins are files in the agent's plugin directory
  only, no subdirectories are enumerated or listed. NOTE: On Unix-like
  systems the plugins returned must have execute bits set.

The following table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |The request completed.   |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad request              |The system received an   |
|                          |                         |invalid value in a       |
|                          |                         |request.                 |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |The system received a    |
|                          |                         |request from a user that |
|                          |                         |is not authenticated.    |
+--------------------------+-------------------------+-------------------------+
|403                       |Forbidden                |The system received a    |
|                          |                         |request that the user is |
|                          |                         |not authorized to make.  |
+--------------------------+-------------------------+-------------------------+
|500                       |Internal Server Error    |An unexpected condition  |
|                          |                         |was encountered.         |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The system is            |
|                          |                         |experiencing heavy load  |
|                          |                         |or another system        |
|                          |                         |failure.                 |
+--------------------------+-------------------------+-------------------------+

Request
-------

The following table shows the header parameters for the request:

+-----------------+----------------+-----------------------------------------------+
|Name             |Type            |Description                                    |
+=================+================+===============================================+
|X-Auth-Token     |String          |A valid authentication token with              |
|                 |*(Required)*    |administrative access. For details, see        |
|                 |                |:ref:`Get your credentials <get-credentials>`  |
+-----------------+----------------+-----------------------------------------------+


.. note:: This operation does not accept a request body.

Response
--------

**Example List agent.filesystem check targets: JSON response**

.. code::

   {
       "values": [
           {
               "id": "/",
               "label": "/"
           },
           {
               "id": "/proc",
               "label": "/proc"
           },
           {
               "id": "/sys",
               "label": "/sys"
           },
           {
               "id": "/sys/fs/fuse/connections",
               "label": "/sys/fs/fuse/connections"
           },
           {
               "id": "/sys/kernel/debug",
               "label": "/sys/kernel/debug"
           },
           {
               "id": "/sys/kernel/security",
               "label": "/sys/kernel/security"
           },
           {
               "id": "/dev",
               "label": "/dev"
           },
           {
               "id": "/dev/pts",
               "label": "/dev/pts"
           },
       ],
       "metadata": {
           "count": 14,
           "limit": null,
           "marker": null,
           "next_marker": null,
           "next_href": null
       }
   }
