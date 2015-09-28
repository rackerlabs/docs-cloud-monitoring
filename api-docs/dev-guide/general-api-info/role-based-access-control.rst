.. _role-based-access-control:


Role based access control (RBAC)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Role Based Access Control (RBAC) restricts access to the capabilities of
Rackspace Cloud services, including the Rackspace Cloud Monitoring API,
to authorized users only. RBAC enables Rackspace Cloud customers to
specify which account users of their Cloud account have access to which
Rackspace Cloud Monitoring API service capabilities, based on roles
defined by Rackspace. 
(See :ref:`Cloud Monitoring product roles and capabilities <monitoring-rbac>`.)
The permissions to perform certain operations in the Rackspace Cloud
Monitoring API – create, read, update, delete – are assigned to specific
roles. The account owner assigns these roles, either multiproduct
(global) or product-specific (for example, Cloud Monitoring only) to
account users.


Assigning roles to account users
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The account owner, `identity:user-admin` can create account users,
`identity:default` on the account and then assign roles to those
users. The roles grant the account users specific permissions for
accessing the Cloud services and capabilities. Each account has only one
account owner, and that role is assigned by default to any Rackspace
Cloud account when the account is created. Account owners cannot hold
any additional roles because they already have full access to all
services and capabilities.

You can assign roles programmatically through the API or by using the
Cloud Control panel interface.

Use the following API operations to add account users and manage role
assignments:

-  `Add account user`_

-  `Assign role to account users`_

-  `Delete role from account user`_

For information about implementing RBAC by using the Cloud Control Panel
and other RBAC-related topics, see the following Rackspace Knowledge
Center articles:

- `Getting Started with role-based access control (RBAC)`_

- `Managing role-based access control through Cloud Control Panel`_


.. comments  Reference URLs

.. _Add account user: http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide/content/POST_addUser_v2.0_users_User_Calls.html

.. _Assign role to account users: http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide/content/PUT_addUserRole__v2.0_users__userId__roles_OS-KSADM__roleid__Role_Calls.html

.. _Delete role from account user: http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide/content/DELETE_deleteUserRole__v2.0_users__userId__roles_OS-KSADM__roleid__Role_Calls.html

.. _Managing role-based access control through Cloud Control Panel: http://www.rackspace.com/knowledge_center/article/managing-role-based-access-control-rbac

.. _Getting Started with role-based access control (RBAC): http://www.rackspace.com/knowledge_center/article/getting-started-with-role-based-access-control-rbac-0


.. _monitoring-rbac:

Roles available for Cloud Monitoring
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Three roles (admin, creator, and observer) can be used to access the Cloud Monitoring API 
specifically. The following table describes these
roles and their permissions.

.. _monitor-rbac-roles-capabilities:

**Table: Cloud Monitoring product roles and capabilities**

+--------------------------------------+--------------------------------------+
| Role name                            | Role permissions                     |
+======================================+======================================+
| ``monitoring:admin``                 | This role provides Create, Read,     |
|                                      | Update, and Delete permissions in    |
|                                      | Cloud Monitoring, where access is    |
|                                      | granted.                             |
+--------------------------------------+--------------------------------------+
| ``monitoring:creator``               | This role provides Create and Read   |
|                                      | permissions in Cloud Monitoring,     |
|                                      | where access is granted.             |
+--------------------------------------+--------------------------------------+
| ``monitoring:observer``              | This role provides Read permission   |
|                                      | in Cloud Monitoring, where access is |
|                                      | granted.                             |
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

The account owner can set roles for both multiproduct and Cloud Monitoring scope, and 
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
| User is assigned the               | Appears that the user    | Yes, for Cloud         |
| following roles:                   | has only the             | Monitoring only.       |
| **multiproduct,observer**          | **multiproduct,observer**| The user has the       |
| and                                | role.                    | **observer** role for  |
| **Cloud Monitoring,admin.**        |                          | for the rest of the    |
|                                    |                          | products.              |
+------------------------------------+--------------------------+------------------------+
| User is assigned the following     | Appears that the user    | Yes, for all products. |
| roles:, **multiproduct,admin**     | has only the the         | The Cloud Monitoring   |
| and **Cloud Monitoring,observer**. | **multiproduct:admin**   | **observer** role is   |
|                                    | role.                    | *observer* role is     |
|                                    |                          | ignored.               |
+------------------------------------+--------------------------+------------------------+


.. _rbac-permissions-cross-reference:

RBAC permissions cross-reference to Cloud Monitoring operations
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

API operations for Cloud Monitoring may or may not be available to all
roles. To see which operations are permitted to invoke which calls,
review the Knowledge Center
article `Detailed permissions matrix for Cloud Monitoring`_.


.. _Detailed permissions matrix for Cloud Monitoring: http://www.rackspace.com/knowledge_center/article/detailed-permissions-matrix-for-cloud-monitoring
