:original_name: dns_pd_0002.html

.. _dns_pd_0002:

Permissions
===========

If you need to assign different permissions to personnel in your enterprise to access your DNS resources, Identity and Access Management (IAM) is a good choice for fine-grained permissions management. IAM provides identity authentication, permissions management, and access control, helping you to securely access your cloud resources.

With IAM, you can create IAM users and assign permissions to control their access to specific resources. For example, if you want some software developers in your enterprise to use DNS resources but do not want them to delete DNS resources or perform any other high-risk operations, you can create IAM users and grant permission to use DNS resources but not permission to delete them.

If your account does not require individual IAM users for permissions management, you can skip this section.

IAM is a free service. You only pay for the resources in your account.

DNS Permissions
---------------

New IAM users do not have any permissions assigned by default. You need to first add them to one or more groups and attach policies or roles to these groups. The users then inherit permissions from the groups and can perform specified operations on cloud services based on the permissions they have been assigned.

DNS resources include the following:

-  Public zone: global-level resource
-  Private zone: project-level resource
-  PTR record: project-level resource

DNS permissions for global-level resources cannot be set in the global service project and must be granted for each project.

When you set **Scope** to **Region-specific projects** and select the specified projects in the specified regions, the users only have permissions for DNS in the selected projects. If you set **Scope** to **All resources**, the users have permissions for DNS in all region-specific projects. When accessing DNS, the users need to switch to the authorized region.

You can grant permissions by using roles and policies.

-  Roles: A coarse-grained authorization strategy provided by IAM to assign permissions based on users' job responsibilities. Only a limited number of service-level roles are available for authorization. Cloud services depend on each other. When you grant permissions using roles, you also need to attach dependent roles. Roles are not ideal for fine-grained authorization and least privilege access.
-  Policies: A fine-grained authorization strategy that defines permissions required to perform operations on specific cloud resources under certain conditions. This type of authorization is more flexible and is ideal for least privilege access. For example, you can grant users only permissions to manage DNS resources of a certain type. A majority of fine-grained policies contain permissions for specific APIs, and permissions are defined using API actions. For the API actions supported by DNS, see "Permissions and Supported Actions" in the *Domain Name Service API Reference*.

:ref:`Table 1 <dns_pd_0002__table815366162217>` lists system-defined permissions supported by DNS.

.. _dns_pd_0002__table815366162217:

.. table:: **Table 1** System-defined permissions for DNS

   +-------------------+--------------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------+
   | Role/Policy Name  | Description              | Type                | Dependencies                                                                                                             |
   +===================+==========================+=====================+==========================================================================================================================+
   | DNS Administrator | Full permissions for DNS | System-defined role | **Tenant Guest** and **VPC Administrator**, which must be attached in the same project as the **DNS Administrator** role |
   +-------------------+--------------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------+

:ref:`Table 2 <dns_pd_0002__table175119544357>` lists common operations supported by system-defined permissions for DNS.

.. _dns_pd_0002__table175119544357:

.. table:: **Table 2** Common operations supported by system-defined permissions

   ======================================== =================
   Operation                                DNS Administrator
   ======================================== =================
   Creating a public zone                   Supported
   Viewing a public zone                    Supported
   Modifying a public zone                  Supported
   Deleting a public zone                   Supported
   Creating a private zone                  Supported
   Viewing a private zone                   Supported
   Modifying a private zone                 Supported
   Deleting a private zone                  Supported
   Associating a VPC with a private zone    Supported
   Disassociating a VPC from a private zone Supported
   Adding a record set                      Supported
   Viewing a record set                     Supported
   Modify a record set                      Supported
   Deleting a record set                    Supported
   Creating a PTR record                    Supported
   Viewing a PTR record                     Supported
   Modifying a PTR record                   Supported
   Deleting a PTR record                    Supported
   ======================================== =================

Helpful Links
-------------

-  `IAM Service Overview <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0026.html>`__
-  :ref:`Creating a User and Granting DNS Permissions <dns_usermanual_0027>`
-  "Permissions Policies and Supported Actions" in the *Domain Name Service API Reference*
