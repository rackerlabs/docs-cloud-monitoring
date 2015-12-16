.. _request-response-types:

Request/Response types
~~~~~~~~~~~~~~~~~~~~~~~~~

The Rackspace Monitoring API supports both the JSON and XML data
serialization formats. The request format is specified using the
``Content-Type`` header and is required for operations that have a
request body. The response format can be specified in requests using the
``Accept`` header. Note that it is possible for a response to be
serialized using a format different from the request (see example
below). If no response format is specified, JSON is the default.

**Table: Response Types**


+--------+----------------------+-----------------+---------+
| Format | Accept Header        | Query Extension | Default |
+========+======================+=================+=========+
| JSON   | application/json     | .json           | Yes     |
+--------+----------------------+-----------------+---------+
| JSONP* | application/json     | .json           | No      |
+--------+----------------------+-----------------+---------+
| XML    | application/xml      | .xml            | No      |
+--------+----------------------+-----------------+---------+


\*JSONP is the same as JSON except that the ``X-Auth-Token`` header is
replaced with an HTTP query parameter with the same name. An additional
HTTP query parameter JSONP indicates the method name to wrap the JSON
response in.

In the request example below, notice that Content-Type is set
to application/json, but application/xml is requested via the Accept
header:

 
**Example: JSON Request with Headers**

.. code::

    POST https://monitoring.api.rackspacecloud.com/v1.0/<your_account_number>/entities/enHBMKJpe6/test-check/
    X-Auth-Token: <your_auth_token>
    Content-Type: application/json
    Accept: application/xml
    '{ "details" : {  },
      "label" : "Website check 1",
      "monitoring_zones_poll" : [ "mzdfw" ],
      "period" : "60",
      "target_alias" : "default",
      "timeout" : 30,
      "type" : "remote.ping"
    }'

Therefore an XML response format is returned:

 
**Example: XML Response with Headers**

.. code::

    <checks_data>
        <check_data>
            <timestamp>1332542815237</timestamp>
            <monitoring_zone_id>mzdfw</monitoring_zone_id>
            <available>false</available>
            <status>cnt=5,avail=0,min=-nan,max=-nan,avg=-nan</status>
            <metrics>
                <average>
                    <type>n</type>
                    <data/>
                </average>
                <minimum>
                    <type>n</type>
                    <data/>
                </minimum>
                <available>
                    <type>n</type>
                    <data>0.000000000000e+00</data>
                </available>
                <maximum>
                    <type>n</type>
                    <data/>
                </maximum>
                <count>
                    <type>i</type>
                    <data>5</data>
                </count>
            </metrics>
        </check_data>
    </checks_data>
