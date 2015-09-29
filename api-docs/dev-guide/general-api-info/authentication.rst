.. _authentication-ovw: 

==============
Authentication
==============

Each REST request against the Cloud Big Data service requires the inclusion of a specific 
authorization token, supplied in the ``X-Auth-Token`` HTTP header. Customers obtain this 
token by first using the Rackspace Cloud Identity service and supplying a valid user 
name and API access key.

To authenticate, you submit a ``POST/v2.0/tokens`` request, presenting valid Rackspace 
customer credentials in the message body to a Rackspace authentication endpoint.

.. note::
    For more detailed information about Rackspace Cloud authentication through the Identity 
    service API that includes detailed information about authentication tokens, responses, 
    and information about the service catalog and service types, see the 
    `Rackspace Cloud Identity API Quickstart Guide`_.
    
.. _Rackspace Cloud Identity API Quickstart: http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide/content/QuickStart-000.html 


.. _auth-credentials:

Get your credentials
~~~~~~~~~~~~~~~~~~~~~

You can use either of the following sets of credentials:

-  Your user name and password

-  Your user name and API key

Your user name and password are the ones that you use to log in to the `Rackspace Cloud Control Panel`_. 
If you know your username and password, you can find your API key by logging into the 
control panel and looking up your account information from the **Account > Settings** menu.

..  note:: 
    If you authenticate with username and password credentials, you can use multi-factor 
    authentication to add an additional level of account security. However, this feature is 
    not supported for username and API key credentials. For more information, see 
    `Multi-factor authentication`_ in the *Cloud Identity Client Developer Guide*.

.. _Multi-factor authentication: http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide/content/MFA_Ops.html
.. _Rackspace Cloud Control Panel: https://mycloud.rackspace.com/


.. _auth-global:

Use the Global Authentication Endpoint
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use the following global endpoint to authenticate with the Rackspace Cloud Identity service:

``https://identity.api.rackspacecloud.com/v2.0/``


.. _send-credentials:

Send your credentials to your authentication endpoint
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you know your credentials and your authentication endpoint, and you can issue a ``POST /v2.0/tokens`` request in an API call, you have all the basic information that you need to use the Rackspace Cloud Identity service.

You can use `cURL`_ to perform the authentication process in two steps: get a token, and send the token to a service.

.. _cURL: http://curl.haxx.se/

#. Get an authentication token by providing your user name and either your API key or your password. Following are examples of both approaches:

   **Example: User name and API key**

   .. code::  

        curl -X POST https://auth.api.rackspacecloud.com/v2.0/tokens -d 
    	'{ "auth":{ "RAX-KSKEY:apiKeyCredentials":{ "username":"yourUserName", "apiKey":"yourApiKey" } } }' -H "Content-type: application/json"


	**Example: User name and password**

	.. code::  

    	curl -X POST https://auth.api.rackspacecloud.com/v2.0/tokens -d
    	'{"auth":{"passwordCredentials":{"username":"yourUserName","password":"yourPassword"}}}' -H "Content-type: application/json"


#. Review the authentication response.

   -  Successful authentication returns a token that you can use as evidence that your 
      identity has already been authenticated along with a service catalog, which lists 
      the endpoints that you can use for Rackspace Cloud services. To use the token, pass 
      it to other services as an `X-Auth-Token` header.

   -  If the Identity service returns a returns a 401 message with a request for 
      additional credentials, your account requires `multi-factor authentication`_. 
      To complete the authentication process, submit a second **POST tokens** request 
      with these multi-factor authentication credentials:

   -  The session ID value returned in the `WWW-Authenticate: OS-MF sessionId` header 
      parameter that is included in the response to the initial authentication request.

   -  The passcode from the mobile phone associated with your user account.
          
   **Example: Authentication request with multi-factor authentication credentials**

   .. code::  

    	$curl https://identity.api.rackspacecloud.com/v2.0/tokens \
    	-X POST \
    	-d '{"auth": {"RAX-AUTH:passcodeCredentials": {"passcode":"1411594"}}}'\
    	-H "X-SessionId: $SESSION_ID" \
    	-H "Content-Type: application/json" --verbose | python -m json.tool


#. Use the authentication token to send a **GET** request to a service that you want to use.

   The following example shows passing an authentication token to the Cloud Monitoring service 
   by using the Cloud Monitoring service catalog endpoint that was returned along with the token.

   **Example: cURL get account information request: JSON**

   .. code::  

    	curl -i -X GET https://monitoring.api.rackspacecloud.com/v1.0/yourAccountID/account -d  \
    	-H "X-Auth-Token: yourAuthToken" \
		-H "Accept: application/json"\
		-H "Content-type: application/json"

.. note:: 

   - Authentication tokens are typically valid for 24 hours. Applications should be designed 
     to re-authenticate after receiving a 401 (Unauthorized) response from a service endpoint.

   - If you are programmatically parsing an authentication response, be aware that 
     service names are stable for the life of the particular service and can be used as keys. 
     You should also be aware that a user's service catalog can include multiple uniquely 
     named services that perform similar functions. In Cloud Identity 2.0, the service 
     type attribute can be used as a key by which to recognize similar services.
     
   - For more detailed information about Rackspace Cloud authentication through the Identity 
     service API that includes detailed information about authentication tokens, responses, 
     and information about the service catalog and service types, see 
     the `Rackspace Cloud Identity API Quickstart guide`_.
    
.. _Rackspace Cloud Identity API Quickstart guide: http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide/content/QuickStart-000.html 



