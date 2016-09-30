.. _request-response-types:

======================
Request/Response types
======================

The |apiservice| supports JSON data serialization request and response format.

The request format is specified by using the ``Content-Type`` header and is
required for operations that have a request body. This header is required for
operations that have a request body. The syntax for the ``Content-Type``
header is:

.. code::

    Content-Type: application/format

Where ``format`` is ``json``.

The response format is specified by using one of the following methods:

-  ``Accept`` header. The syntax for the ``Accept`` header is::

       Accept: application/format

   Where ``format`` is ``json``.

|apiservice| also supports the \*JSONP format. This format  is the same as
JSON except that the ``X-Auth-Token`` header is replaced with an HTTP query
parameter with the same name. An additional HTTP query parameter JSONP
indicates the method name to wrap the JSON response in.
