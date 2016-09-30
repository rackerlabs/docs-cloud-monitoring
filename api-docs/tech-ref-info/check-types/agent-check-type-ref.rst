.. _agent-check-type-ref:

Agent check types
~~~~~~~~~~~~~~~~~

Rackspace Monitoring supports the following agent check types.

.. contents::
   :local:
   :depth: 1


.. _agent_apache_check:

agent.apache check
------------------

The **agent.apache** check will retrieve Apache HTTP server metrics

Attributes
^^^^^^^^^^

+-----------+------------------------------------------------------------------+----------------------+
| Field     | Description                                                      | Validation           |
+===========+==================================================================+======================+
| timeout   | Specifies the plugin execution timeout in milliseconds.          | Optional. Integer.   |
+-----------+------------------------------------------------------------------+----------------------+
| url       | Specifies the URL. Defaults to http://127.0.0.1/server-status.   | Optional. URL.       |
+-----------+------------------------------------------------------------------+----------------------+

Metrics
^^^^^^^

+-----------------------+----------------------------------------------------------------------------------------+---------+
| Metric                | Description                                                                            | Type    |
+=======================+========================================================================================+=========+
| busy_workers          | Specifies the number of workers serving requests                                       | Int64   |
+-----------------------+----------------------------------------------------------------------------------------+---------+
| bytes_per_request     | Averages giving the number of request per second, the number of bytes served second.   | Int64   |
+-----------------------+----------------------------------------------------------------------------------------+---------+
| bytes_per_second      | Averages giving the number of requests per second, the number of bytes per request.    | Int64   |
+-----------------------+----------------------------------------------------------------------------------------+---------+
| closing               | The number of workers closing the connection.                                          | Int64   |
+-----------------------+----------------------------------------------------------------------------------------+---------+
| cpu_load              | Total percentage of CPU used by workers                                                | Double  |
+-----------------------+----------------------------------------------------------------------------------------+---------+
| dns                   | The number of workers performing DNS lookup.                                           | Int64   |
+-----------------------+----------------------------------------------------------------------------------------+---------+
| gracefully_fishing    | The number of workers gracefully fishing                                               | Int64   |
+-----------------------+----------------------------------------------------------------------------------------+---------+
| idle                  | The number of idle cleanup workers.                                                    | Int64   |
+-----------------------+----------------------------------------------------------------------------------------+---------+
| idle_workers          | The number of idle workers.                                                            | Int64   |
+-----------------------+----------------------------------------------------------------------------------------+---------+
| keepalive             | The number of workers kept alive (reading).                                            | Int64   |
+-----------------------+----------------------------------------------------------------------------------------+---------+
| logging               | The number of workers logging.                                                         | Int64   |
+-----------------------+----------------------------------------------------------------------------------------+---------+
| open                  | The number of workers with no current process.                                         | Int64   |
+-----------------------+----------------------------------------------------------------------------------------+---------+
| reading               | The number of workers reading the request                                              | Int64   |
+-----------------------+----------------------------------------------------------------------------------------+---------+
| requests_per_second   | The number of requests per second.                                                     | Int64   |
+-----------------------+----------------------------------------------------------------------------------------+---------+
| sending               | The number of workers sending a reply.                                                 | Int64   |
+-----------------------+----------------------------------------------------------------------------------------+---------+
| starting              | The number of workers starting up.                                                     | Int64   |
+-----------------------+----------------------------------------------------------------------------------------+---------+
| total_access          | Total number of accesses served.                                                       | Int64   |
+-----------------------+----------------------------------------------------------------------------------------+---------+
| total_kbytes          | Total kilobytes served.                                                                | Int64   |
+-----------------------+----------------------------------------------------------------------------------------+---------+
| uptime                | Time since the last start/restart in milliseconds.                                     | Int64   |
+-----------------------+----------------------------------------------------------------------------------------+---------+
| waiting               | The number of workers waiting for connection.                                          | Int64   |
+-----------------------+----------------------------------------------------------------------------------------+---------+

.. _agent_cpu:

agent.cpu
---------

The agent.cpu check will attempt to measure the usage of the CPU on a
host.

Attributes

No fields are present for this particular check type.

Metrics
^^^^^^^

+----------------------------+--------------------------------------------------------+----------+
| Metric                     | Description                                            | Type     |
+============================+========================================================+==========+
| idle_percent_average       | Recent percentage of CPU time spent idle.              | Double   |
+----------------------------+--------------------------------------------------------+----------+
| irq_percent_average        | Recent percentage of CPU time spent handling hardware  | Double   |
|                            | interrupts.                                            |          |
+----------------------------+--------------------------------------------------------+----------+
| max_cpu_usage              | Recent percentage utilization of the most-utilized CPU.| Double   |
|                            | This is useful to detect when some                     |          |
|                            | CPUs are pegged while others are idle.                 |          |
+----------------------------+--------------------------------------------------------+----------+
| min_cpu_usage              |Recent percentage utilization of the least-utilized CPU.| Double   |
|                            |This is useful to detect when some                      |          |
|                            |CPUs are pegged while others are idle.                  |          |
+----------------------------+--------------------------------------------------------+----------+
| stolen_percent_average     | Recent percentage of CPU time spent waiting for        | Double   |
|                            | the CPU to service other virtual CPUs.                 |          |
+----------------------------+--------------------------------------------------------+----------+
| sys_percent_average        |Recent percentage of CPU time utilized by kernel mode   | Double   |
|                            |processes.                                              |          |
+----------------------------+--------------------------------------------------------+----------+
| usage_average              |Recent percentage of CPU time utilized by all processes.| Double   |
|                            |processes.                                              |          |
+----------------------------+--------------------------------------------------------+----------+
| user_percent_average       |Recent percentage of CPU time utilized by user mode     | Double   |
|                            |processes in a "wait" state.                            |          |
+----------------------------+--------------------------------------------------------+----------+
| wait_percent_average       | Recent percentage of CPU time utilized by processes    | Double   |
|                            | in a "wait" state.                                     |          |
+----------------------------+--------------------------------------------------------+----------+

.. _agent_disk:

agent.disk
----------

The **agent.disk** check exposes disk related metrics (service time, wait
time, etc.).

Attributes
^^^^^^^^^^

+-----------+--------------------------------------------------------------------------------------+
| Field     | Description                               | Validation                               |
+===========+===========================================+==========================================+
| target    | The disk to check (eg '/dev/xvda1')       | String between 1 and 512 characters long |
+-----------+--------------------------------------------------------------------------------------+


Metrics
^^^^^^^

+-----------------+----------------------------------------------------------------------------------------------------------------------+----------+
| Metric          | Description                                                                                                          | Type     |
+=================+======================================================================================================================+==========+
| queue           | Disk utilization time, the prefix  / will change depending on the mount points discovered.                           | Int64    |
+-----------------+----------------------------------------------------------------------------------------------------------------------+----------+
| read_bytes      | The number of physical disk bytes read, the prefix / will change depending on the mount points discovered.           | Int64    |
+-----------------+----------------------------------------------------------------------------------------------------------------------+----------+
| reads           | The number of physical disk reads, the prefix / will change depending on the mount points discovered.                | Int64    |
+-----------------+----------------------------------------------------------------------------------------------------------------------+----------+
| rtime           | The amount of time spent reading, the prefix / will change depending on the mount points discovered.                 | Int64    |
+-----------------+----------------------------------------------------------------------------------------------------------------------+----------+
| write_bytes     | The number of physical disk bytes written, the prefix / will change depending on the mount points discovered.        | Int64    |
+-----------------+----------------------------------------------------------------------------------------------------------------------+----------+
| writes          | The number of physical disk writes, the prefix / will change depending on the mount points discovered.               | Int64    |
+-----------------+----------------------------------------------------------------------------------------------------------------------+----------+
| wtime           | The amount of time spent writing, the prefix / will change dependending on the mount points discovered.              | Int64    |
+-----------------+----------------------------------------------------------------------------------------------------------------------+----------+

.. _agent_filesystem:

agent.filesystem
----------------

The **agent.filesystem** check exposes file system related metrics (free
space, used space, etc.)

Attributes
^^^^^^^^^^

+-----------+------------------------------+-------------------------------------+
| Field     | Description                  | Validation                          |
+===========+==============================+=====================================+
| target    |The mount point to check,     | String between 1 and 512            |
|           |either :code:`/var` or        | characters long.                    |
|           |``C:\``                       |                                     |
|           |                              |                                     |
+-----------+------------------------------+-------------------------------------+


Metrics
^^^^^^^

+-----------------+--------------------------------------------------+----------+
| Metric          | Description                                      | Type     |
+=================+==================================================+==========+
| avail           | Available space on the filesystem in kilobytes,  | Int64    |
|                 | including reserved space.                        |          |
+-----------------+--------------------------------------------------+----------+
| free            | Free space available on the filesystem in        | Int64    |
|                 | kilobytes including reserved space.              |          |
+-----------------+--------------------------------------------------+----------+
| options         | The option used to mount the device to the       | Int64    |
|                 | filesystem. Includes the **rw** f                |          |
|                 | which indicates the device is in read/write mode.|          |
+-----------------+--------------------------------------------------+----------+
| total           | Total space on the filesystem, in kilobytes.     | Int64    |
+-----------------+--------------------------------------------------+----------+
| used            | Used space on the filesystem, in kilobytes.      | Int64    |
+-----------------+--------------------------------------------------+----------+
| files           | Number of inodes on the filesystem.              | Int64    |
+-----------------+--------------------------------------------------+----------+
| free_files      | Number of free inodes on the filesystem.         | Int64    |
+-----------------+--------------------------------------------------+----------+

.. note::

   The `files` and `free_files` metrics are not available on Windows.



.. _agent_filesystem_state:

agent.filesystem_state
-------------------------

The **agent.filesystem_state** check exposes filesystem metrics for
read-write/read-only system mounts.

Attributes
~~~~~~~~~~~~

No fields are present for this particular check type.

Metrics
~~~~~~~~~~~~

+-----------------+--------------------------------------------------+----------+
| Metric          | Description                                      | Type     |
+=================+==================================================+==========+
| total_ro        | Total number of filesystems mounted read-only.   | Int64    |
+-----------------+--------------------------------------------------+----------+
| total_rw        | Total number of filesystems mounted read-write   | Int64    |
+-----------------+--------------------------------------------------+----------+
| devices_ro      | Comma delimited list of devices mounted          | String   |
|                 | read-only.                                       |          |
+-----------------+--------------------------------------------------+----------+
| devices_rw      | Comma delimited list of devices mounted          | String   |
|                 | read-write.                                      |          |
+-----------------+--------------------------------------------------+----------+

.. _agent_load_average:

agent.load_average
------------------

The **agent.load_average** check will attempt to measure the Unix-style Load Average on a host.

Attributes
^^^^^^^^^^

No fields are present for this particular check type.

Metrics
^^^^^^^

+----------+--------------------------------+---------+
| Metric   | Description                    | Type    |
+==========+================================+=========+
| 1m       | One minute load average.       | Double  |
+----------+--------------------------------+---------+
| 5m       | Five minute load average.      | Double  |
+----------+--------------------------------+---------+
| 15m      | Fifteen minute load average.   | Double  |
+----------+--------------------------------+---------+

.. _agent_memory:

agent.memory
------------

Attributes
^^^^^^^^^^

No fields are present for this particular check type.

Metrics
^^^^^^^

The memory available to the system is used in three different ways:

- Used by the processese running in the system, this value is under "actual_used" metric.
- Used by the kernel, this value is not returned from the check but can be deduced.
- Not used by either the running processes or kernel, this value is under "free" metric.

For convenience, the system returns the value of used/free memory for the case
of including kernel and excluding kernel so that you don't have to do the
calculation in your head.

+-------------------+----------------------------------------------------------------------------------+---------+
| Metric            | Description                                                                      | Type    |
+===================+==================================================================================+=========+
| actual_free       | The amount of free memory, 'free' plus kernel memory.                            | Int64   |
+-------------------+----------------------------------------------------------------------------------+---------+
| actual_used       | The actual amount of used memory excluding kernel memory.                        | Int64   |
+-------------------+----------------------------------------------------------------------------------+---------+
| free              | The amount of free memory not including kernel memory.                           | Int64   |
+-------------------+----------------------------------------------------------------------------------+---------+
| ram               | The amount of RAM.                                                               | Int64   |
+-------------------+----------------------------------------------------------------------------------+---------+
| swap_free         | The amount of free SWAP memory.                                                  | Int64   |
+-------------------+----------------------------------------------------------------------------------+---------+
| swap_page_in      | The number of SWAP-in pages.                                                     | Int64   |
+-------------------+----------------------------------------------------------------------------------+---------+
| swap_page_out     | The number of SWAP-out pages.                                                    | Int64   |
+-------------------+----------------------------------------------------------------------------------+---------+
| swap_total        | The total amount of SWAP memory.                                                 | Int64   |
+-------------------+----------------------------------------------------------------------------------+---------+
| swap_used         | The amount of used SWAP memory.                                                  | Int64   |
+-------------------+----------------------------------------------------------------------------------+---------+
| total             | The total amount of memory.                                                      | Int64   |
+-------------------+----------------------------------------------------------------------------------+---------+
| used              | The total amount of used memory, 'actual_used' plus kernel memory                | Int64   |
+-------------------+----------------------------------------------------------------------------------+---------+

.. _agent_mysql:

agent.mysql
-----------

The **agent.mysql** check will retrieve MySQL server metrics

..  note::

    Except for the replication.slave\_running' metric, all metrics starting
    with replication will not show up if there is no slave running.


Attributes
^^^^^^^^^^

+------------+----------------------------------------------------------+------------------------------------------------------+
| Field      | Description                                              | Validation                                           |
+============+==========================================================+======================================================+
| host       | Mysql server hostname (default: 127.0.0.1).              | Optional. Valid hostname, IPv4 or IPv6 address       |
+------------+----------------------------------------------------------+------------------------------------------------------+
| mycnf      | Specifies whether my.cnf should be loaded.               | Optional. Boolean.                                   |
+------------+----------------------------------------------------------+------------------------------------------------------+
| password   | Specifies the server password.                           | Optional. String between 1 and 255 characters long   |
+------------+----------------------------------------------------------+------------------------------------------------------+
| port       | Specifies the Mysql server port (default: 3306).         | Optional. Integer between 1-65535 inclusive          |
+------------+----------------------------------------------------------+------------------------------------------------------+
| socket     | Specifies the path to the domain socket.                 | Optional. String between 1 and 255 characters long   |
+------------+----------------------------------------------------------+------------------------------------------------------+
| timeout    | Specifies the plugin execution timeout in milliseconds   | Optional. Integer                                    |
+------------+----------------------------------------------------------+------------------------------------------------------+
| username   | Specifies the username.                                  | Optional. String between 1 and 16 characters long    |
+------------+----------------------------------------------------------+------------------------------------------------------+


Metrics
^^^^^^^

+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| Metric                                     | Description                                                                                                                                                                                                                                                                                                           | Type            |
+============================================+=======================================================================================================================================================================================================================================================================================================================+=================+
| bytes_received                             |The number of bytes received from all clients. (statvar_Bytes_received)                                                                                                                                                                                                                                                | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| bytes_sent                                 | The number of bytes sent to all clients. (statvar_Bytes_sent)                                                                                                                                                                                                                                                         | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| core.aborted_clients                       | The number of connections that were aborted because the client died without closing the connection properly. (statvar_Aborted_clients)                                                                                                                                                                                | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| core.connections                           | The number of connection attempts (successful or not) to the MySQL server. (statvar_Connections)                                                                                                                                                                                                                      | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| core.queries                               | The number of statements executed by the server. (statvar_Queries)                                                                                                                                                                                                                                                    | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| core.uptime                                | The number of seconds that the server has been up. (statvar_Uptime)                                                                                                                                                                                                                                                   | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| handler.commit                             | The number of internal COMMIT statements. (statvar_Handler_commit)                                                                                                                                                                                                                                                    | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| handler.delete                             | The number of times that rows have been deleted from tables. (statvar_Handler_delete)                                                                                                                                                                                                                                 | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| handler.read_first                         | The number of times the first entry in an index was read. (statvar_Handler_read_first)                                                                                                                                                                                                                                | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| handler.read_key                           | The number of requests to read a row based on a key. If this value is high, it is a good indication that your tables are properly indexed for your queries. (statvar_Handler_read_key)                                                                                                                                | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| handler.read_next                          | The number of requests to read the next row in key order. This value is incremented if you are querying an index column with a range constraint or if you are doing an index scan. (statvar_Handler_read_next)                                                                                                        | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| handler.read_prev                          | he number of requests to read the previous row in key order. This read method is mainly used to optimize ORDER BY ... DESC. (statvar_Handler_read_prev)                                                                                                                                                               | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| handler.read_rnd                           | The number of requests to read a row based on a fixed position. This value is high if you are doing a lot of queries that require sorting of the result. You probably have a lot of queries that require MySQL to scan entire tables or you have joins that do not use keys properly. (statvar_Handler_read_rnd)      | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| handler.rollback                           | The number of requests for a storage engine to perform a rollback operation. (statvar_Handler_rollback).                                                                                                                                                                                                              | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| handler.savepoint                          | The number of requests for a storage engine to place a savepoint. (statvar_Handler_savepoint).                                                                                                                                                                                                                        | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| handler.savepoint_rollback                 | The number of requests for a storage engine to roll back to a savepoint. (statvar_Handler_savepoint_rollback).                                                                                                                                                                                                        | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| handler.update                             | The number of requests to update a row in a table. (statvar_Handler_update).                                                                                                                                                                                                                                          | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| handler.write                              | The number of requests to insert a row in a table. (statvar_Handler_write).                                                                                                                                                                                                                                           | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.buffer_pool_pages_data              | The number of pages containing data (dirty or clean). (statvar_Innodb_buffer_pool_pages_data).                                                                                                                                                                                                                        | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.buffer_pool_pages_dirty             | The number of pages currently dirty. (statvar_Innodb_buffer_pool_pages_dirty).                                                                                                                                                                                                                                        | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.buffer_pool_pages_flushed           | The number of buffer pool page-flush requests. (statvar_Innodb_buffer_pool_pages_flushed).                                                                                                                                                                                                                            | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.buffer_pool_pages_free              | The number of free pages. (statvar_Innodb_buffer_pool_pages_free).                                                                                                                                                                                                                                                    | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.buffer_pool_pages_total             | The total size of the buffer pool, in pages. (statvar_Innodb_buffer_pool_pages_total).                                                                                                                                                                                                                                | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.buffer_pool_read_requests           | The number of logical read requests. (statvar_Innodb_buffer_pool_read_requests).                                                                                                                                                                                                                                      | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.buffer_pool_reads                   | The number of logical reads that InnoDB could not satisfy from the buffer pool, and had to read directly from the disk. (statvar_Innodb_buffer_pool_reads).                                                                                                                                                           | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.buffer_pool_size                    | The size in bytes of the memory buffer InnoDB uses to cache data and indexes of its tables. (sysvar_innodb_buffer_pool_size).                                                                                                                                                                                         | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.data_pending_fsyncs                 | The current number of pending fsync() operations. (statvar_Innodb_data_pending_fsyncs).                                                                                                                                                                                                                               | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.data_pending_reads                  | The current number of pending reads. (statvar_Innodb_data_pending_reads).                                                                                                                                                                                                                                             | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.data_pending_writes                 | The current number of pending writes. (statvar_Innodb_data_pending_writes).                                                                                                                                                                                                                                           | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.pages_created                       | The number of pages created. (statvar_Innodb_pages_created).                                                                                                                                                                                                                                                          | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.pages_read                          | The number of pages read. (statvar_Innodb_pages_read).                                                                                                                                                                                                                                                                | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.pages_written                       | The number of pages written. (statvar_Innodb_pages_written).                                                                                                                                                                                                                                                          | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.row_lock_time                       | The total time spent in acquiring row locks, in milliseconds. (statvar_Innodb_row_lock_time).                                                                                                                                                                                                                         | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.row_lock_time_avg                   | The average time to acquire a row lock, in milliseconds. (statvar_Innodb_row_lock_time_avg).                                                                                                                                                                                                                          | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.row_lock_time_max                   | The maximum time to acquire a row lock, in milliseconds. (statvar_Innodb_row_lock_time_max).                                                                                                                                                                                                                          | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.row_lock_waits                      | The number of times a row lock had to be waited for. (statvar_Innodb_row_lock_waits).                                                                                                                                                                                                                                 | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.rows_deleted                        | The number of rows deleted from InnoDB tables. (statvar_Innodb_rows_deleted).                                                                                                                                                                                                                                         | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.rows_inserted                       | The number of rows inserted into InnoDB tables. (statvar_Innodb_rows_inserted).                                                                                                                                                                                                                                       | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.rows_read                           | The number of rows read from InnoDB tables. (statvar_Innodb_rows_read).                                                                                                                                                                                                                                               | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| innodb.rows_updated                        | The number of rows updated in InnoDB tables. (statvar_Innodb_rows_updated).                                                                                                                                                                                                                                           | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| key.buffer_size                            | Index blocks for MyISAM tables are buffered and are shared by all threads. (sysvar_key_buffer_size).                                                                                                                                                                                                                  | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| max.connections                            | The maximum permitted number of simultaneous client connections. (sysvar_max_connections).                                                                                                                                                                                                                            | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| qcache.free_blocks                         | The number of free memory blocks in the query cache. (statvar_Qcache_free_blocks).                                                                                                                                                                                                                                    | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| qcache.free_memory                         | The amount of free memory for the query cache. (statvar_Qcache_free_memory).                                                                                                                                                                                                                                          | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| qcache.hits                                | The number of query cache hits. (statvar_Qcache_hits).                                                                                                                                                                                                                                                                | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| qcache.inserts                             | The number of queries added to the query cache. (statvar_Qcache_inserts).                                                                                                                                                                                                                                             | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| qcache.lowmem_prunes                       | The number of queries that were deleted from the query cache because of low memory. (statvar_Qcache_lowmem_prunes).                                                                                                                                                                                                   | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| qcache.not_cached                          | The number of noncached queries (not cacheable, or not cached due to the query_cache_type setting). (statvar_Qcache_not_cached).                                                                                                                                                                                      | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| qcache.queries_in_cache                    | The number of queries registered in the query cache. (statvar_Qcache_queries_in_cache).                                                                                                                                                                                                                               | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| qcache.size                                | The amount of memory allocated for caching query results. (sysvar_query_cache_size).                                                                                                                                                                                                                                  | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| qcache.total_blocks                        | The total number of blocks in the query cache. (statvar_Qcache_total_blocks).                                                                                                                                                                                                                                         | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| replication.exec_master_log_pos            | The position in the current master binary log file to which the SQL thread has read and executed, marking the start of the next transaction or event to be processed. (show-slave-status.html).                                                                                                                       | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| replication.last_errno                     | The error number returned by the most recently executed statement. (show-slave-status.html).                                                                                                                                                                                                                          | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| replication.last_io_error                  | error message of the most recent error that caused the I/O thread to stop (show-slave-status.html).                                                                                                                                                                                                                   | String          |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| replication.max_relay_log_size             | If a write by a replication slave to its relay log causes the current log file size to exceed the value of this variable, the slave rotates the relay logs (closes the current file and opens the next one). (sysvar_max_relay_log_size).                                                                             | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| replication.read_master_log_pos            | The position in the current master binary log file up to which the I/O thread has read. (show-slave-status.html).                                                                                                                                                                                                     | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| replication.relay_log_pos                  | The position in the current relay log file up to which the SQL thread has read and executed. (show-slave-status.html).                                                                                                                                                                                                | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| replication.seconds_behind_master          | In essence, this field measures the time difference in seconds between the slave SQL thread and the slave I/O thread. (show-slave-status.html).                                                                                                                                                                       | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| replication.slave_io_running               | Whether the I/O thread is started and has connected successfully to the master. Internally, the state of this thread is represented by one of the following three values: MYSQL_SLAVE_NOT_RUN, MYSQL_SLAVE_RUN_NOT_CONNECT, MYSQL_SLAVE_RUN_CONNECT (show-slave- status.html).                                        | Boolean         |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| replication.slave_io_state                 | A copy of the State field of the SHOW PROCESSLIST output for the slave I/O thread. This tells you what the thread is doing: trying to connect to the master, waiting for events from the master, reconnecting to the master, and so on. (show-slave-status.html).                                                     | String          |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| replication.slave_open_temp_tables         | The number of temporary tables that the slave SQL thread currently has open. If the value is greater than zero, it is not safe to shut down the slave. (statvar_Slave_open_temp_tables).                                                                                                                              | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| replication.slave_retried_transactions     | The total number of times since startup that the replication slave SQL thread has retried transactions. (statvar_Slave_retried_transactions).                                                                                                                                                                         | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| replication.slave_running                  | This is ON if this server is a replication slave that is connected to a replication master, and both the I/O and SQL threads are running; otherwise, it is OFF. (statvar_Slave_running).                                                                                                                              | String          |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| replication.slave_sql_running              | Whether the SQL thread is started. (show- slave-status.html).                                                                                                                                                                                                                                                         | Boolean         |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| thread.cache_size                          | How many threads the server should cache for reuse. (sysvar_thread_cache_size).                                                                                                                                                                                                                                       | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| threads.connected                          | The number of currently open connections. (statvar_Threads_connected).                                                                                                                                                                                                                                                | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| threads.created                            | The number of threads created to handle connections. (statvar_Threads_created).                                                                                                                                                                                                                                       | Cumulative      |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
| threads.running                            | The number of threads that are not sleeping. (statvar_Threads_running).                                                                                                                                                                                                                                               | Instantaneous   |
+--------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+

.. _agent_network:

agent.network
-------------

The **agent.network** check will attempt to measure the usage of network
devices on a host.

Attributes
^^^^^^^^^^

+-----------+-----------------------------------------------------------------------------------------+
| Field     | Description                                  | Validation                               |
+===========+==============================================+==========================================+
| target    | The network device to check (eg 'eth0)       | String between 1 and 512 characters long |
+-----------+-----------------------------------------------------------------------------------------+

Metrics
^^^^^^^

+---------------+---------------------------------------------------------------------------------------------+---------+
| Metric        | Description                                                                                 | Type    |
+===============+=============================================================================================+=========+
| rx_bytes      | The number of bytes received over the interface.                                            | Int64   |
+---------------+---------------------------------------------------------------------------------------------+---------+
| rx_dropped    | The number of packets received and subsequently dropped over the interface.                 | Int64   |
+---------------+---------------------------------------------------------------------------------------------+---------+
| rx_errors     | The number of errors received over the interface.                                           | Int64   |
+---------------+---------------------------------------------------------------------------------------------+---------+
| rx_packets    | The number of packets received over the interface.                                          | Int64   |
+---------------+---------------------------------------------------------------------------------------------+---------+
| speed         | The speed at which the bytes were transmitted over the interface.                           | Int64   |
+---------------+---------------------------------------------------------------------------------------------+---------+
| tx_bytes      | The number of bytes transmitted over the interface.                                         | Int64   |
+---------------+---------------------------------------------------------------------------------------------+---------+
| tx_dropped    | The number of packets attempted transmitting and subsequently dropped over the interface.   | Int64   |
+---------------+---------------------------------------------------------------------------------------------+---------+
| tx_error      | The number of errors while transmitting over the interface.                                 | Int64   |
+---------------+---------------------------------------------------------------------------------------------+---------+
| tx_packets    | The number of packets transmitted over the interface.                                       | Int64   |
+---------------+---------------------------------------------------------------------------------------------+---------+

.. _agent_mssql_database:

agent.mssql_database
--------------------

The **agent.mssql_database** check returns metrics for a Microsoft SQL Server database.

Attributes
^^^^^^^^^^

+------------------+-----------------------------------+------------------------------------------------------+
| Field            | Description                       | Validation                                           |
+==================+===================================+======================================================+
| db               | MS SQL Server database name       | String between 1 and 255 characters long             |
+------------------+-----------------------------------+------------------------------------------------------+
| hostname         | MS SQL Server hostname            | Optional. Valid hostname, IPv4 or IPv6 address       |
+------------------+-----------------------------------+------------------------------------------------------+
| password         | MS SQL Server password            | Optional. String between 1 and 255 characters long   |
+------------------+-----------------------------------+------------------------------------------------------+
| serverinstance   | MS SQL Server instance to query   | Optional. String between 1 and 255 characters long   |
+------------------+-----------------------------------+------------------------------------------------------+
| username         | MS SQL Server username            | Optional. String between 1 and 255 characters long   |
+------------------+-----------------------------------+------------------------------------------------------+

.. _agent_mssql_buffer_manager:

agent.mssql_buffer_manager
--------------------------

The **agent.mssql_buffer_manager** check returns metrics for the
Microsoft SQL Server buffer manager.

Attributes
^^^^^^^^^^

+------------------+-----------------------------------+------------------------------------------------------+
| Field            | Description                       | Validation                                           |
+==================+===================================+======================================================+
| computer         | MS SQL Server computer name       | Optional. Valid hostname, IPv4 or IPv6 address       |
+------------------+-----------------------------------+------------------------------------------------------+
| serverinstance   | MS SQL Server instance to query   | Optional. String between 1 and 255 characters long   |
+------------------+-----------------------------------+------------------------------------------------------+

.. _agent_mssql_sql_statistics:

agent.mssql_sql_statistics
--------------------------

The **agent.mssql_sql_statistics** check returns metrics for the
Microsoft SQL Server SQL statistics.

Attributes
^^^^^^^^^^

+------------------+-----------------------------------+------------------------------------------------------+
| Field            | Description                       | Validation                                           |
+==================+===================================+======================================================+
| computer         | MS SQL Server computer name       | Optional. Valid hostname, IPv4 or IPv6 address       |
+------------------+-----------------------------------+------------------------------------------------------+
| serverinstance   | MS SQL Server instance to query   | Optional. String between 1 and 255 characters long   |
+------------------+-----------------------------------+------------------------------------------------------+

.. _agent_mssql_plan_cache:

agent.mssql_plan_cache
---------------------------

The agent.mssql_plan_cache check returns metrics for the Microsoft SQL Server plan cache.

Attributes
^^^^^^^^^^

+------------------+-----------------------------------+------------------------------------------------------+
| Field            | Description                       | Validation                                           |
+==================+===================================+======================================================+
| computer         | MS SQL Server computer name       | Optional. Valid hostname, IPv4 or IPv6 address       |
+------------------+-----------------------------------+------------------------------------------------------+
| serverinstance   | MS SQL Server instance to query   | Optional. String between 1 and 255 characters long   |
+------------------+-----------------------------------+------------------------------------------------------+

.. _agent_mssql_memory_manager:

agent.mssql_memory_manager
--------------------------

The **agent.mssql_memory_manager** check returns metrics for the Microsoft SQL Server memory manager.

Attributes
^^^^^^^^^^

+------------------+-----------------------------------+------------------------------------------------------+
| Field            | Description                       | Validation                                           |
+==================+===================================+======================================================+
| computer         | MS SQL Server computer name       | Optional. Valid hostname, IPv4 or IPv6 address       |
+------------------+-----------------------------------+------------------------------------------------------+
| serverinstance   | MS SQL Server instance to query   | Optional. String between 1 and 255 characters long   |
+------------------+-----------------------------------+------------------------------------------------------+

.. _agent_mssql_version:

agent.mssql_version
-------------------

The **agent.mssql_version** check returns version information for
Microsoft SQL Server.

Attributes
^^^^^^^^^^

+------------------+-----------------------------------+------------------------------------------------------+
| Field            | Description                       | Validation                                           |
+==================+===================================+======================================================+
| hostname         | MS SQL Server hostname            | Optional. Valid hostname, IPv4 or IPv6 address       |
+------------------+-----------------------------------+------------------------------------------------------+
| password         | MS SQL Server password            | Optional. String between 1 and 255 characters long   |
+------------------+-----------------------------------+------------------------------------------------------+
| serverinstance   | MS SQL Server instance to query   | Optional. String between 1 and 255 characters long   |
+------------------+-----------------------------------+------------------------------------------------------+
| username         | MS SQL Server username            | Optional. String between 1 and 255 characters long   |
+------------------+-----------------------------------+------------------------------------------------------+

.. _agent_plugin:

agent.plugin
------------

The **agent.plugin** check will attempt to run a custom plugin on a host.


Custom plugins are simply executable files which report metrics via
``stdout``. Plugins are placed on the server to be monitored at an
installation path that depends on the operating system:

+----------------------------------------------------------------------------------------------------+----------------------------------------------------------+
| Operating System                                                                                   | Installation Path                                        |
+====================================================================================================+==========================================================+
| Linux                                                                                              | /usr/lib/rackspace-monitoring-agent/plugins/             |
+----------------------------------------------------------------------------------------------------+----------------------------------------------------------+
| Windows (32-bit agent installed on a 64-bit system )                                               | C:\\Program Files (x86)\\Rackspace Monitoring\\plugins   |
+----------------------------------------------------------------------------------------------------+----------------------------------------------------------+
| Windows (64-bit agent installed on a 64-bit system or 32-bit agent installed on a 32-bit system)   | C:\\Program Files\\Rackspace Monitoring\\plugins         |
+----------------------------------------------------------------------------------------------------+----------------------------------------------------------+

After the plugin has been installed on the server, create an ``agent.plugin``
check that specifies the name of the executable file so that the plugin can
begin reporting metrics to the monitoring system, like any other check.
If the plugin requires any command line arguments, you can specify them using
the optional ``args`` array.

Attributes
^^^^^^^^^^

+-----------+---------------------------------------------------------+-----------------------------------------------------------------------------------------------+
| Field     | Description                                             | Validation                                                                                    |
+===========+=========================================================+===============================================================================================+
| file      | Name of the plugin file                                 | String matching the regex //[a-zA-Z0-9\.\- _]+//                                              |
+-----------+---------------------------------------------------------+-----------------------------------------------------------------------------------------------+
| args      | Command-line arguments which are passed to the plugin   | Optional. Array [Non-empty string]. Array or object with number of items between 0 and 10     |
+-----------+---------------------------------------------------------+-----------------------------------------------------------------------------------------------+
| timeout   | Plugin execution timeout in milliseconds                | Optional. Integer                                                                             |
+-----------+---------------------------------------------------------+-----------------------------------------------------------------------------------------------+

Metrics
^^^^^^^

The metrics returned are defined in the plugin script. A plugin can send up to fifty unique metrics at a time.

**Community Plugin Repository**

A curated repository of plugins created by Rackspace Monitoring users is
avaliable on
`GitHub <https://github.com/racker/rackspace-monitoring-agent-plugins-contrib>`__.
Contributions are welcome!

..  note::

    The Rackspace Monitoring Agent is also capable of executing Cloudkick
    plugins, so if you are a Cloudkick user you can just drop in any
    existing plugin and it should just work.


**Creating Custom Plugins**

Creating custom plugins is as simple as writing a script that prints a
status and up to fifty metrics to standard out. The format of the status
line is:

.. code::

    status <status>

The status string should describe whether the check was able to
successfully gather metrics. It could be as simple as "success" to
incidate that metrics were successfully gathered. *When an error occurs
that prevents metrics from being gathered, plugins should print a status
that describes the error, then should exit non-zero without printing any
metric lines.*

The status line can be followed by up to fifty metric lines. Each
line is output in the following format:


.. code::

    metric <name> <type> <value>

The following descriptions provide information about parameter values.

.. list-table:: **Capacity management**
   :widths: 30 70
   :header-rows: 1

   * - Parameter
     - Description
   * - name
     - The name of the metric. No spaces are allowed. The format is
       alpha numeric with colon (:), underscore (\_) and dot (.) allowed.
       Example: ``memory_free``.
   * - type
     - The metric can be any of the following types:

       ``int32`` Signed 32 bit integer value.

       ``uint32`` Unsigned 32 bit integer value.

       ``int64`` Signed 64 bit integer value.

       ``uint64`` Unsigned 64 bit integer value.

       ``double`` Floating point values.

       ``string``
           A string value.

           **Note:** the monitoring system records string
           metrics every time they change. String metrics are designed for
           recording an enumerated state which infrequently changes (for
           example an HTTP response code which is always 200 during normal
           operation). You should not store arbitrary, frequently changing
           values in a string metric.
   * - value
     - The value assigned to the metric.

Putting it all together, the output of a plugin that has successfully
executed might look something like:

.. code::

    status Turkey thermometer returned valid response
    metric internal_temperature uint32 165
    metric ambient_temperature uint32 325

If the plugin failed, it might print the following before exiting
non-zero:

.. code::

    status Turkey thermometer not responding

.. _agent_redis:

agent.redis
-----------

The **agent.redis** check will retrieve Redis server metrics

Attributes
^^^^^^^^^^

+------------------+-----------------------------------+------------------------------------------------------+
| Field            | Description                       | Validation                                           |
+==================+===================================+======================================================+
| hostname         | Redis server hostname             | Valid hostname, IPv4 or IPv6 address                 |
+------------------+-----------------------------------+------------------------------------------------------+
| password         | Optional Redis server password    | Optional. String between 1 and 255 characters long   |
+------------------+-----------------------------------+------------------------------------------------------+
| port             | Redis server port                 | Integer between 1-65535 inclusive                    |
+------------------+-----------------------------------+------------------------------------------------------+
| timeout          |Connection timeout in milliseconds | Optional. Integer                                    |
+------------------+-----------------------------------+------------------------------------------------------+


Metrics
^^^^^^^

+--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+----------+
| Metric                         | Description                                                                                                                                   | Type     |
+================================+===============================================================================================================================================+==========+
| bgrewriteaof_in_progress       | (Redis 2.4.16 only) Flag indicating a RDB save is on-going.                                                                                   | Int32    |
+--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+----------+
| bgsave_in_progress             | (Redis 2.4.16 only) Flag indicating a RDB save is on-going.                                                                                   | Int32    |
+--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+----------+
| blocked_clients                | Number of clients pending on a blocking call (BLPOP, BRPOP, BRPOPLPUSH)                                                                       | Int32    |
+--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+----------+
| changes_since_last_save        | (Redis 2.4.16 only) Number of changes since the last dump.                                                                                    | Int32    |
+--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+----------+
| connected_clients              | Number of client connections (excluding connections from slaves).                                                                             | Int32    |
+--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+----------+
| evicted_keys                   | Number of evicted keys due to maxmemory limit.                                                                                                | Int32    |
+--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+----------+
| pubsub_patterns                | Global number of pub/sub pattern with client subscriptions.                                                                                   | Int32    |
+--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+----------+
| total_commands_processed       | Total number of commands processed by the server.                                                                                             | Gauge    |
+--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+----------+
| total_connections_received     | Total number of connections accepted by the server.                                                                                           | Gauge    |
+--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+----------+
| uptime_in_seconds              | Number of seconds since Redis server start.                                                                                                   | Int32    |
+--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+----------+
| used_memory                    | Total number of bytes allocated by Redis using its allocator (either standard libc, jemalloc, or an alternative allocator such as tcmalloc.   | Int32    |
+--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+----------+
| version                        | Version of the server.                                                                                                                        | String   |
+--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+----------+

.. _agent_windows_perfos:

agent.windows_perfos
---------------------------

The **agent.windows_perfos** check returns metrics regarding windows
performance data. This check is only available on Windows platforms.

Attributes
^^^^^^^^^^

No fields are present for this particular check type.

Metrics
^^^^^^^
+-------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------+
| Metric                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | Type     |
+===============================+============================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+==========+
| AlignmentFixupsPersec         | Alignment Fixups/sec - Shows the rate, in incidents per second, at which alignment faults,were fixed by the system.                                                                                                                                                                                                                                                                                                                                                                                        | Uint32   |
+-------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------+
| ContextSwitchesPersec         | Context Switches/sec - Shows the combined rate, in incidents per second, at which all processors on the computer were switched from one thread to another. It is the sum of the values of Thread Context Switches/sec for each thread running on all processors on the computer, and is measured in numbers of switches. Context switches occur when a running thread voluntarily relinquishes the processor, or is preempted by a higher priority, ready thread.                                          | Uint32   |
+-------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------+
| ExceptionDispatchesPersec     | Exception Dispatches/sec - Shows the rate, in incidents per second, at which exceptions were dispatched by the system.                                                                                                                                                                                                                                                                                                                                                                                     | Uint64   |
+-------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------+
| FileControlBytesPersec        | File Control Bytes/sec - Shows the overall rate, in incidents per second, at which bytes were transferred for all file system operations that were neither read nor write operations, such as file system control requests and requests for information about device characteristics or status.                                                                                                                                                                                                            | Uint32   |
+-------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------+
| FileControlOperationsPersec   | File Control Operations/sec - Shows the combined rate, in incidents per second, of file system operations that were neither read nor write operations, such as file system control requests and requests for information about device characteristics or status. This is the inverse of File Data Operations/sec.                                                                                                                                                                                          | Uint32   |
+-------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------+
| FileDataOperationsPersec      | File Data Operations/sec - Shows the combined rate, in incidents per second, of read and write operations on disks, serial, or parallel devices. This is the inverse of File Control Operations/sec.                                                                                                                                                                                                                                                                                                       | Uint32   |
+-------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------+
| FileReadBytesPersec           | File Read Bytes/sec - Shows the overall rate, in incidents per second, at which bytes were read to satisfy file system read requests to all devices on the computer, including read operations from the file system cache.                                                                                                                                                                                                                                                                                 | Uint64   |
+-------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------+
| FileReadOperationsPersec      | The number of errors while transmitting over the interface.                                                                                                                                                                                                                                                                                                                                                                                                                                                | Uint32   |
+-------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------+
| FileWriteBytesPersec          | File Write Bytes/sec - Shows the overall rate, in incidents per second, at which bytes were written to satisfy file system write requests to all devices on the computer, including write operations to the file system cache.                                                                                                                                                                                                                                                                             | Uint64   |
+-------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------+
| FloatingEmulationsPersec      | Floating Emulations/sec - Shows the rate, in incidents per second, of floating emulations performed by the system.                                                                                                                                                                                                                                                                                                                                                                                         | Uint32   |
+-------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------+
| PercentRegistryQuotaInUse     | Percentage of the total registry quota allowed that is currently being used by the system. This property displays the current percentage value only; it is not an average.                                                                                                                                                                                                                                                                                                                                 | Uint32   |
+-------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------+
| Processes                     | Shows the number of processes in the computer at the time of data collection. This is an instantaneous count, not an average over the time interval. Each process represents a program that is running.                                                                                                                                                                                                                                                                                                    | Uint32   |
+-------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------+
| ProcessorQueueLength          | Processor Queue Length - Shows the number of threads in the processor queue. Unlike the disk counters, this counter shows ready threads only, not threads that are running. There is a single queue for processor time, even on computers with multiple processors.Therefore, if a computer has multiple processors, you need to divide this value by the number of processors servicing the workload. A sustained processor queue of greater than two threads generally indicates processor congestion.   | Uint32   |
+-------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------+
| SystemCallsPersec             | System Calls/sec - Shows the combined rate, in incidents per second, of calls to operating system service routines by all processes running on the computer. These routines perform all of the basic scheduling and synchronization of activities on the computer, and provide access to non-graphic devices, memory management, and name space management.                                                                                                                                                | Uint32   |
+-------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------+
| SystemUpTime                  | System Up Time - Shows the total time, in seconds, that the computer has been operational since it was last started.                                                                                                                                                                                                                                                                                                                                                                                       | Uint64   |
+-------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------+
| Threads                       | Shows the number of threads in the computer at the time of data collection. This is an instantaneous count, not an average over the time interval. A thread is the basic executable entity that can execute instructions in a processor.                                                                                                                                                                                                                                                                   | Uint32   |
+-------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------+
