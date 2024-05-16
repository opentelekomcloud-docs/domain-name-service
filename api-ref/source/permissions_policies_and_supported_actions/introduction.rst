:original_name: dns_api_70001.html

.. _dns_api_70001:

Introduction
============

This topic describes fine-grained permissions management for your DNS resources. Skip this topic if your cloud account does not need individual IAM users.

By default, new IAM users do not have any permissions granted. You need to add a user to one or more groups, and assign policies or roles to these groups. The user then inherits permissions from the groups it is a member of. This process is called authorization. After authorization, the user can perform specified operations on cloud services based on the permissions.

You can grant users permissions by using roles and policies. Roles are a type of coarse-grained authorization mechanism that defines permissions related to user responsibilities. Policies define API-based permissions for operations on specific resources under certain conditions, allowing for more fine-grained, secure access control of cloud resources.

.. note::

   Policy-based authorization is useful if you want to allow or deny the access to an API.

An account has permissions to call all APIs, but IAM users must have the required permissions specifically assigned. The permissions required for calling an API are determined by the actions supported by the API. Only users who have been granted permissions allowing the actions can call the API successfully. For example, if an IAM user queries the public zone list using an API, the user must have been granted permissions that allow the **dns:zone:list** action.

Supported Actions
-----------------

DNS provides system-defined policies that can be directly used in IAM. You can also create custom policies and use them to supplement system-defined policies, implementing more refined access control. Actions supported by policies are specific to APIs. The following are common concepts related to policies:

-  Permission: A statement in a policy that allows or denies certain operations.
-  APIs: REST APIs that can be called in a custom policy.
-  Actions: added to a custom policy to control permissions for specific operations.
-  Related actions: Actions on which a specific action depends to take effect. When assigning permissions for the action to a user, you also need to assign permissions for the dependent actions.
-  IAM projects or enterprise projects: Type of projects in which policies can be used to grant permissions. A policy can be applied to IAM projects, enterprise projects, or both. Policies that contain actions supporting both IAM projects and enterprise projects can be assigned to user groups and take effect in both IAM and Enterprise Management. Policies that only contain actions supporting IAM projects can be assigned to user groups and only take effect in IAM. Such policies will not take effect if they are assigned to user groups in Enterprise Management.

.. note::

   The check mark (Y) indicates that an action takes effect. The cross mark (x) indicates that an action does not take effect.

DNS supports the following actions that can be defined in custom policies:

-  :ref:`Zone Management <dns_api_70002>`: contains actions supported by all zone management APIs, such as the API for creating a zone.
-  :ref:`Record Set Management <dns_api_70003>`: contains actions supported by all record set management APIs, such as the API for creating a record set.
-  :ref:`PTR Record Management <dns_api_70004>`: contains actions supported by all PTR record management APIs, such as the API for creating a PTR record.
-  :ref:`Tag Management <dns_api_70005>`: contains actions supported by all tag management APIs, such as the API for adding a resource tag.
