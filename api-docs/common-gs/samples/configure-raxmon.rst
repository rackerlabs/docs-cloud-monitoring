.. _gsg-configure-raxmon:

Configuring the client
----------------------

Although you can specify your Rackspace credentials and URLs as
command-line options, it saves time to add them to the Rackspace Monitoring
client configuration file.

Complete the following steps to configure the client with your credentials
and the URLs for Rackspace Monitoring and the Rackspace Identity service.

#. If you do not already have your API key, follow the
   instructions in :ref:`Get your credentials <get-credentials>`

#. Using vi or your favorite text editor, open the ``.raxrc`` file in
   your home directory. Following is an example of the vi command to open the
   file.

   .. code::

       $  vi ~/.raxrc

#. Edit the file to specify your Rackspace username and API key, and the
   :rax-devdocs:`Rackspace Identity endpoint
   <cloud-identity/v2/general-api-info/service-access/>` for your account.
   Following is an example of the ``.raxrc`` file with Rackspace credentials
   and URLs:

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
