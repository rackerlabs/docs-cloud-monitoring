Paginated collections
~~~~~~~~~~~~~~~~~~~~~~~~~~

To reduce load on the service, list operations will return a maximum
number of items at a time. To navigate the collection, the parameters
limit and marker can be set in the URI, for example 
``?limit=200&marker=enCCCCCC``. The marker parameter is the ID of a
first item in the next page. This item can be found in the metadata
object under the ``next_marker`` tag. Items are sorted by the ID name in
a lexicographic order. The limit parameter sets the page size. It
defaults to ``100`` items per page and the maximum value is ``1000``.
Both parameters are optional. If the client requests a limit beyond that
which is not supported an invalidLimit (400) fault may be thrown.

For convenience, collections contain a link to the next page (the
``next_href`` attribute in the metadata object). If there are no more
objects, the ``next_marker`` and ``next_href`` attributes will be empty.
The following examples illustrate two pages in a collection of entities.
The first page was retrieved via a **GET** to
https://monitoring.api.rackspacecloud.com/v1.0/entities?limit=1. In
these examples, the limit parameter sets the page size to a single item.
Subsequent ``next_href`` link will honor the initial page size. Thus, a
client may follow this link to traverse a paginated collection without
having to input the limit parameter.

 
**Example 3.8. List Entities, First Page: XML**

.. code::  

    <?xml version="1.0" encoding="utf-8"?>
    <container>
      <values>
        <entity key="enAAAAA">
          <label>Brand New Entity</label>
          <ip_addresses>
            <a>127.0.0.4</a>
            <b>127.0.0.5</b>
            <c>127.0.0.6</c>
            <test>127.0.0.7</test>
          </ip_addresses>
          <metadata>
            <all>kinds</all>
            <of>stuff</of>
            <can>go</can>
            <here>null is not a valid value</here>
          </metadata>
        </entity>
      </values>
      <metadata>
        <count>1</count>
        <limit>1</limit>
        <marker/>
        <next_marker>enBBBB</next_marker>
        <next_href>https://cmbeta.api.rackspacecloud.com/v1.0/entities?limit=1&marker=enBBBB</next_href>
      </metadata>
    </container>

              

 
**Example 3.9. List Entities, First Page: JSON**

.. code::  

    {
        "values": [
            {
                "key": "enAAAAA",
                "label": "Brand New Entity",
                "ip_addresses": {
                    "a": "127.0.0.4",
                    "b": "127.0.0.5",
                    "c": "127.0.0.6",
                    "test": "127.0.0.7"
                },
                "metadata": {
                    "all": "kinds",
                    "of": "stuff",
                    "can": "go",
                    "here": "null is not a valid value"
                }
            }
        ],
        "metadata": {
            "count": 1,
            "limit": 1,
            "marker": null,
            "next_marker": "enBBBB",
            "next_href": "https://cmbeta.api.rackspacecloud.com/v1.0/entities?limit=1&marker=enBBBB"
        }
    }

              

 
**Example 3.10. List Entities, Second Page: XML**

.. code::  

    <?xml version="1.0" encoding="utf-8"?>
    <container>
      <values>
        <entity key="enBBBB">
          <label>Brand New Entity 2</label>
          <ip_addresses>
            <a>127.0.0.4</a>
            <b>127.0.0.5</b>
            <c>127.0.0.6</c>
            <test>127.0.0.7</test>
          </ip_addresses>
          <metadata>
            <all>kinds</all>
          </metadata>
        </entity>
      </values>
      <metadata>
        <count>1</count>
        <limit>1</limit>
        <marker>enBBBB</marker>
        <next_marker/>
        <next_href/>
      </metadata>
    </container>

              

 
**Example 3.11. List Entities, Second Page: JSON**

.. code::  

    {
        "values": [
            {
                "key": "enBBBB",
                "label": "Brand New Entity 2",
                "ip_addresses": {
                    "a": "127.0.0.4",
                    "b": "127.0.0.5",
                    "c": "127.0.0.6",
                    "test": "127.0.0.7"
                },
                "metadata": {
                    "all": "kinds"
                }
            }
        ],
        "metadata": {
            "count": 1,
            "limit": 1,
            "marker": "enBBBB",
            "next_marker": null,
            "next_href": null
        }
    }

              

In the JSON representation, paginated collections contain a values
property that contains the items in the collection. The link to the next
page is located in the metadata object (``metadata.next_href``
attribute). Clients must follow the ``next_href`` link to continue to
retrieve additional entities belonging to an account.
