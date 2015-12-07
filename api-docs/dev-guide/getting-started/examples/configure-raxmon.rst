
.. _gsg-configure-raxmon:

Configure raxmon 
^^^^^^^^^^^^^^^^^^^^^^^


Configure raxmon with your credentials and the URLs for Cloud Monitoring
and the Rackspace Cloud Identity Service.

 
**To configure raxmon**

Although you can specify your Rackspace credentials and URLs as
command-line options, it saves time to add them to the raxmon
configuration file.

#. If you do not already have your API key, find it by using the
   instructions in `Obtaining an API
   key <http://docs.rackspace.com/cm/api/v1.0/cm-getting-started/content/Authentication.html#finding-key>`__.

#. Using vi or your favorite text editor, open the ``.raxrc`` file in
   your home directory for editing:

   .. code::

       $  vi ~/.raxrc

#. Edit the file to specify your Rackspace username and API key, and the
   correct `identity
   endpoint <http://docs.rackspace.com/cm/api/v1.0/cm-getting-started/content/Authentication.html#auth-endpoint>`__
   for your account location. Following is an example of the ``.raxrc``
   file with Rackspace credentials and URLs:

   .. code::

       [credentials]
       username=MyRackspaceAcct
       api_key=0000000000000000000

       [api]
       url=https://monitoring.api.rackspacecloud.com/v1.0

       [auth_api]
       url=https://identity.api.rackspacecloud.com/v2.0/tokens

       [ssl]
       verify=true
