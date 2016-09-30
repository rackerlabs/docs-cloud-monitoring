.. _gsg-raxmon-prerequisites:

Prerequisites for using raxmon
------------------------------

**Prerequisites for nova clients**

- Linux or Mac OS X
- Python 2.6 or later
- **setuptools** package, installed by default on Mac OS X
- **pip** package
- Rackspace Cloud account and access to |service|

+--------------------+--------------------------------------------------------+
| Prerequisite       | Description                                            |
+====================+========================================================+
| Python 2.5, 2.6,   | Currently, the raxmon client does not support          |
| or 2.7             | Python 3.                                              |
+--------------------+--------------------------------------------------------+
| **setuptools**     | Installed by default on Mac OS X.                      |
| package            |                                                        |
|                    | Many Linux distributions provide packages to make      |
|                    | **setuptools** easy to install.                        |
|                    |                                                        |
|                    | Search your package manager for **setuptools** to find |
|                    | an installation package. If you cannot find one,       |
|                    | download the **setuptools** package directly from      |
|                    | http://pypi.python.org/pypi/setuptools.                |
+--------------------+--------------------------------------------------------+
| **pip** package    | To install the nova client on a Mac OS X or Linux      |
|                    | system, use **pip** because it is easy and ensures     |
|                    | that you get the latest version of the nova client     |
|                    | from the Python Package Index at                       |
|                    | http://pypi.python.org/pypi/python-novaclient/>.       |
|                    | Also, it lets you update the package later on.         |
|                    |                                                        |
|                    | Install **pip** through the package manager for your   |
|                    | system:                                                |
|                    |                                                        |
|                    | -  Mac OS X                                            |
|                    |                                                        |
|                    |    .. code::                                           |
|                    |                                                        |
|                    |        $ sudo easy_install pip                         |
|                    |                                                        |
|                    | -  Ubuntu                                              |
|                    |                                                        |
|                    |    .. code::                                           |
|                    |                                                        |
|                    |        $ aptitude install python-pip                   |
|                    |                                                        |
|                    | -  Debian                                              |
|                    |                                                        |
|                    |    .. code::                                           |
|                    |                                                        |
|                    |        $ aptitude install python-pip                   |
|                    |                                                        |
|                    | -  Fedora                                              |
|                    |                                                        |
|                    |    .. code::                                           |
|                    |                                                        |
|                    |        $ yum install python-pip                        |
|                    |                                                        |
|                    | -  CentOS, or RHEL (from EPEL or another 3rd party     |
|                    |    repository)                                         |
|                    |                                                        |
|                    |    .. code::                                           |
|                    |                                                        |
|                    |        $ yum install python-pip                        |
|                    |                                                        |
+--------------------+--------------------------------------------------------+

..  note::
      Raxmon is not designed to work on a Windows OS. The tutorial assumes you
      have a Mac OS.
