
.. _gsg-install-raxmon:


Install raxmon
^^^^^^^^^^^^^^^^^

Follow these steps to install raxmon on your local workstation if you
don't already have a version installed.

If you have an earlier version installed, you must
`upgrade <http://docs.rackspace.com/cm/api/v1.0/cm-getting-started/content/upgrade-raxmon.html>`__
to version 0.4.6 or higher.

Before you install raxmon, you must have Python version 2.5, 2.6, or 2.7 installed on your local computer (the computer on which you will install raxmon).

.. important::
      Important
      Raxmon is not supported on a Windows OS.

 
**To install raxmon**

#. Log in to a bash shell on your local workstation as the user who has
   write permissions to ``/usr/local/bin``.

#. Install the Python pip command as follows:

   .. code::

       $ sudo yum install -y python-setuptools

   .. code::

       $ sudo easy_install pip

#. Install raxmon as follows:

   .. code::

       $ sudo pip install rackspace-monitoring-cli
