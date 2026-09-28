:original_name: dns_api_70001.html

.. _dns_api_70001:

Introduction
============

You can use Identity and Access Management (IAM) for fine-grained permissions management of your DNS. If your account does not need individual IAM users, you can skip this section.

By default, new IAM users do not have any permissions granted. You need to add a user to one or more groups, and assign policies or roles to these groups. The user then inherits permissions from the groups it is a member of. This process is called authorization. After authorization, the user can perform specified operations on cloud services based on the permissions.

You can grant users permissions by using roles and policies. Roles are a type of coarse-grained authorization mechanism that defines permissions related to user responsibilities. Policies define API-based permissions for operations on specific resources under certain conditions, allowing for more fine-grained, secure access control of cloud resources.

.. note::

   Policy-based authorization is useful if you want to allow or deny the access to an API.

An account has permissions to call all APIs, but IAM users must have the required permissions specifically assigned. The permissions required for calling an API are determined by the actions supported by the API. Only users who have been granted permissions allowing the actions can call the API successfully. For example, if an IAM user queries the public zone list using an API, the user must have been granted permissions that allow the **dns:zone:list** action.

Supported Actions
-----------------

DNS provides system-defined policies that can be directly used in IAM. You can also create custom policies to supplement system-defined policies for more refined access control. Operations supported by policies are specific to APIs. The following are common concepts related to policies:

-  Permissions: statements in a policy that allow or deny certain operations
-  APIs: REST APIs that can be called by a user who has been granted specific permissions
-  Actions: specific operations that are allowed or denied in a custom policy
-  Dependencies: actions which a specific action depends on. When allowing an action for a user, you also need to allow any existing action dependencies for that user.
-  IAM projects/Enterprise projects: the authorization scope of a custom policy. A custom policy can be applied to IAM projects or enterprise projects or both. Policies that contain actions for both IAM and enterprise projects can be used and applied for both IAM and Enterprise Management. Policies that contain actions only for IAM projects can be used and applied to IAM only.

.. note::

   Administrators can check whether an action supports IAM projects or enterprise projects in the action list.

DNS supports the following actions in custom policies:

-  :ref:`Zone Management <dns_api_70002>`: contains actions supported by all zone management APIs, such as the API for creating a zone.
-  :ref:`Record Set Management <dns_api_70003>`: contains actions supported by all record set management APIs, such as the API for creating a record set.
-  :ref:`PTR Record Management <dns_api_70004>`: contains actions supported by all PTR record management APIs, such as the API for creating a PTR record.
-  :ref:`Tag Management <dns_api_70005>`: contains actions supported by all tag management APIs, such as the API for adding a resource tag.
-  :ref:`Record Set Importing <dns_api_70006>`: contains actions supported by all record set importing management APIs, such as the API for creating a task for importing public zone record sets.
-  :ref:`DNSSEC Management <dns_api_70008>`: contains actions supported by all DNSSEC management APIs, such as the API for enabling DNSSEC.
-  :ref:`Endpoint Management <dns_api_70012>`: contains actions supported by all endpoint management APIs, such as the API for creating an endpoint.
-  :ref:`Endpoint Rule Management <dns_api_70013>`: contains actions supported by all endpoint rule management APIs, such as the API for creating an endpoint rule.
