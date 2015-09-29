.. _available-check-types-and-fields:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Appendix B: Available check types and fields
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Read more about the specific check types in these sections below.
You'll find each check class is a top level section. You can dive
into more depth by clicking on an individual check type.

.. note::
   Most check types include some example metrics. This helps you better
   understand creating successful alarm criteria.

.. _remote-check-types:

Remote check types
~~~~~~~~~~~~~~~~~~

.. _remote-dns:

remote.dns
^^^^^^^^^^
The remote.dns check will run a DNS check against a given target.
This check should assist in verifying functionality of a DNS server,
for example ensuring that it is publishing the domains you think
that it should be publishing.

**Attributes**

+-----------------+-----------------+-------------------------------------------------------+
| Field           | Name            | Validation                                            |
+=================+=================+=======================================================+
| **query**       | DNS Query       | * String                                              |
|                 |                 | * Valid hostname                                      |
+-----------------+-----------------+-------------------------------------------------------+
| **record_type** | DNS Record Type | * String matching the regex                           |
|                 |                 |   /^(A|AAAA|TXT|MX|SOA|CNAME|PTR|NS|MB|MD|MF|MG|MR)$/ |
+-----------------+-----------------+-------------------------------------------------------+
| **port**        | Port number     | * Optional                                            |
|                 | (default: 53)   | * Whole number (may be zero padded)                   |
|                 |                 | * Integer between 1-65535                             |
+-----------------+-----------------+-------------------------------------------------------+

**Metrics**

+----------------+-------------------------------------------+---------------+
| Metric         | Description                               | Type          |
+================+===========================================+===============+
| **answer**     | The list of space separated IP addresses  | String        |
|                | for the specified name resolution.        |               |
+----------------+-------------------------------------------+---------------+
| **rtt**        | The roundtrip time to execute a           | Double        |
|                | remote.dns check.                         |               |
+----------------+-------------------------------------------+---------------+
| **ttl**        | The TTL returned by the DNS query.        | Uint32        |
+----------------+-------------------------------------------+---------------+

.. _remote-ftp-banner:

remote.ftp-banner
^^^^^^^^^^^^^^^^^
