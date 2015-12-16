.. _role-based-access-control:


Role based access control (RBAC)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Role Based Access Control (RBAC) restricts access to the capabilities of
Rackspace Cloud services, including the Rackspace Monitoring API,
to authorized users only. RBAC enables Rackspace Cloud customers to
specify which account users of their Cloud account have access to which
Rackspace Monitoring API service capabilities, based on roles
defined by Rackspace.
(See :ref:`Rackspace Monitoring product roles and capabilities <monitoring-rbac>`.)
The permissions to perform certain operations in the Rackspace Cloud
Monitoring API – create, read, update, delete – are assigned to specific
roles. The account owner assigns these roles, either multiproduct
(global) or product-specific (for example, Rackspace Monitoring only) to
account users.


Assigning roles to account users
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The account owner (identity:user-admin) can create account users on the
account and then assign roles to those users. The roles grant the
account users specific permissions for accessing the capabilities of the
next gen Cloud Servers service. Each account has only one account owner,
and that role is assigned by default to any Rackspace Cloud account when
the account is created.

See the :rax-devdocs:`Cloud Identity Client Developer Guide <cloud-identity/v2/developer-guide/#document-overview>`
for information about how to perform the following tasks:

* :rax-devdocs:`Add account users <cloud-identity/v2/developer-guide/#add-user>`

* :rax-devdocs:`Add role to user <cloud-identity/v2/developer-guide/#add-role-to-user>`

* :rax-devdocs:`Delete global role from user <cloud-identity/v2/developer-guide/#delete-global-role-from-user>`

For information about implementing RBAC by using the Cloud Control Panel
and other RBAC-related topics, see the following Rackspace Knowledge
Center articles:

- `Getting Started with role-based access control (RBAC)`_

- `Managing role-based access control through Cloud Control Panel`_


.. comments  Reference URLs


.. _Managing role-based access control through Cloud Control Panel: http://www.rackspace.com/knowledge_center/article/managing-role-based-access-control-rbac

.. _Getting Started with role-based access control (RBAC): http://www.rackspace.com/knowledge_center/article/getting-started-with-role-based-access-control-rbac-0


.. _monitoring-rbac:

Roles available for Rackspace Monitoring
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Three roles (admin, creator, and observer) can be used to access the Rackspace Monitoring API
specifically. The following table describes these
roles and their permissions.

.. _monitor-rbac-roles-capabilities:

**Table: Rackspace Monitoring product roles and capabilities**

+--------------------------------------+--------------------------------------+
| Role name                            | Role permissions                     |
+======================================+======================================+
| ``monitoring:admin``                 | This role provides Create, Read,     |
|                                      | Update, and Delete permissions in    |
|                                      | Rackspace Monitoring, where access   |
|                                      | is granted.                          |
+--------------------------------------+--------------------------------------+
| ``monitoring:creator``               | This role provides Create and Read   |
|                                      | permissions in Rackspace Monitoring, |
|                                      | where access is granted.             |
+--------------------------------------+--------------------------------------+
| ``monitoring:observer``              | This role provides Read permission   |
|                                      | in Rackspace Monitoring, where access|
|                                      | is granted.                          |
+--------------------------------------+--------------------------------------+


Additionally, two multiproduct roles apply to all products. Users with
multiproduct roles inherit access to future products when those products
become RBAC-enabled. The following table describes these roles and their
permissions.


**Table: Multiproduct (global) roles and capabilities**

+--------------------------------------+--------------------------------------+
| Role name                            | Role permissions                     |
+======================================+======================================+
| ``admin``                            | This role provides Create, Read,     |
|                                      | Update, and Delete permissions in    |
|                                      | all products, where access is        |
|                                      | granted.                             |
+--------------------------------------+--------------------------------------+
| ``observer``                         | This role provides Read permission   |
|                                      | across multiple products, where      |
|                                      | access is granted.                   |
+--------------------------------------+--------------------------------------+



.. _resolve-rbac-conflicts:

Resolving conflicts between RBAC multiproduct versus custom (product-specific) roles
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The account owner can set roles for both multiproduct and Rackspace Monitoring scope, and
it is important to understand how any potential conflicts among these roles are resolved.
When two roles appear to conflict, the role that provides the more extensive permissions
takes precedence. Therefore, admin roles take precedence over observer and creator roles,
because admin roles provide more permissions.

The following table shows two examples of how potential conflicts between user roles in
the Control Panel are resolved.

**Table: Resolving role conflicts between user roles in the Control Panel**

+------------------------------------+--------------------------+------------------------+
| Permission                         | Control Panel View       | Can user perform Admin |
|                                    |                          | functions in           |
|                                    |                          | Control Panel?         |
+====================================+==========================+========================+
| User is assigned the               | Appears that the user    | Yes, for Rackspace     |
| following roles:                   | has only the             | Monitoring only.       |
| **multiproduct,observer**          | **multiproduct,observer**| The user has the       |
| and                                | role.                    | **observer** role for  |
| **Rackspace Monitoring,admin.**    |                          | for the rest of the    |
|                                    |                          | products.              |
+------------------------------------+--------------------------+------------------------+
| User is assigned the following     | Appears that the user    | Yes, for all products. |
| roles:, **multiproduct,admin** and | has only the the         | The Rackspace          |
| **Rackspace Monitoring,observer**. | **multiproduct:admin**   | Monitoring             |
|                                    | role.                    | *observer* role is     |
|                                    |                          | ignored.               |
+------------------------------------+--------------------------+------------------------+


.. _rbac-permissions-cross-reference:

RBAC permissions cross-reference to Rackspace Monitoring operations
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

API operations for Rackspace Monitoring may or may not be available to all
roles. To see which operations are permitted to invoke which calls,
review the Knowledge Center
article `Detailed permissions matrix for Rackspace Monitoring`_.


.. _Detailed permissions matrix for Rackspace Monitoring: http://www.rackspace.com/knowledge_center/article/detailed-permissions-matrix-for-cloud-monitoring
