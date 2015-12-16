.. _time-series-collections:

Time series collections
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Rackspace Monitoring tracks various time-indexed data sets, such
as audits and alarm histories. When accessing a time series collection,
two parameters beyond the base paginated collection API are available:
``from`` and ``to``. These parameters take integer values, which are
interpreted as timestamps expressed in milliseconds since 00:00:00 UTC
on January 1, 1970. If the ``to`` value is not specified it defaults to
the current time. Each time series collection specifies a default offset
from the current time, which is used when the ``from`` value is not
supplied. For example, if no ``to`` or ``from`` values are specified
when retrieving an alarm history, then it will be treated as a query for
the last 7 days of data.

The standard paginated collection API is available on top of the time
series collection API. For example, performing a **GET** on
https://monitoring.api.rackspacecloud.com/v1.0/audits?from=1320044400000&to=1320652800000
should retrieve audits from the first 7 days of November, 2011. However,
since no ``limit`` is supplied a default of 100 is used. Thus, if more
than 100 audits exist during that time period only the first 100 will be
returned. Further audits within the same period can be retrieved using
the ``next_href`` URL, or by constructing a URL by using the
``next_marker`` value to append a ``marker`` to your previous query. For
example, to retrieve the next 100 objects beyond the previous query, you
might use
https://monitoring.api.rackspacecloud.com/v1.0/audits?from=1320044400000&to=1320652800000&marker=16c3de00-038e-11e1-b056-d3a1a3710f94.

You can use the ``reverse`` parameter to retrieve the objects in
reversed order. By default, objects are returned oldest first.

To convert a particular time to UTC, you can use the **date +%s000**
command or a website such as ``http://www.epochconverter.com/``.
