.. _create_first_monitor:

Create your first monitor
------------------------------------

This chapter contains a tutorial that will help you become familiar with
basic monitoring operations. Examples are provided in cURL with JSON
formatting. You can also complete this tutorial by using the Cloud
Monitoring command-line interface, raxmon. An example raxmon command is
also shown for each operation.

..  note::

      Raxmon is not designed to work on a Windows OS. The tutorial assumes you
      have a Mac OS.

For the purpose of this tutorial, assume that you have a new web server
that you want to ensure is running and responding to requests. Following
is the basic workflow for the tutorial:

#. :ref:`Install and configure raxmon <gsg-install-and-configure-raxmon>`, 
   the Rackspace monitoring command-line interface (CLI).

#. :ref:`Create an entity <gsg-create-an-entity>` to represent the server in the monitoring system.

#. Review the :ref:`list of monitoring zones <gsg-list-monitoring-zones>`.

#. Define **three** checks for the entity by completing the following tasks in sequence:
      
   - :ref:`Create a check <gsg-create-a-check>`
   - :ref:`Test the checks <gsg-test-check>`
   - :ref:`List of all checks <gsg-list-all-checks>`.

#. Set up an :ref:`email notification <gsg-setup-notifications>` and
   :ref:`create a notification plan <gsg-make-notification-plan>` so you can receive 
   information about the entity.

#. Define **two** alarms by completing the steps in :ref:`Create an alarm <gsg-create-an-alarm>` 
   and assign them to a check to begin the monitoring process.

#. Delete :ref:`the entity <gsg-delete-an-entity>` and its child objects: the checks and alarms.

   ..  note::

      In the exercises for this tutorial, include your authorization token where you
      see ``$AUTH_TOKEN`` and your account number where you see ``TENANTID``.


.. include:: examples/create-entity.rst
.. include:: examples/list-monitoring-zones.rst
.. include:: examples/create-checks.rst
.. include:: examples/test-check.rst
.. include:: examples/list-all-checks.rst
.. include:: examples/setup-notifications.rst
.. include:: examples/create-notification-plan.rst
.. include:: examples/create-alarm.rst
.. include:: examples/delete-entity.rst
