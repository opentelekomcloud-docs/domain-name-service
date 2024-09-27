:original_name: dns_usermanual_0027.html

.. _dns_usermanual_0027:

Creating a User and Granting DNS Permissions
============================================

To implement fine-grained permissions control over your DNS resources, `IAM <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0026.html>`__ is a good choice. With IAM, you can:

-  Create IAM users for employees based on your enterprise's organizational structure. Each IAM user will have their own security credentials for accessing DNS resources.
-  Grant only the permissions required for users to perform a specific task.
-  Entrust another account or cloud service to perform efficient O&M on your DNS resources.

Skip this part if your account does not need individual IAM users.

The following describes the procedure for granting permissions (see :ref:`Figure 1 <dns_usermanual_0027__en-us_topic_0172268189_fig12481104618719>`).

**Prerequisites**
-----------------

You have learned about DNS permissions (see :ref:`Permissions <dns_pd_0002>`) and have chosen the right policies or roles based on your requirements. For the permission policies of other services, see `System Permissions <https://docs.otc.t-systems.com/permissions/index.html>`__.

Process Flow
------------

.. _dns_usermanual_0027__en-us_topic_0172268189_fig12481104618719:

.. figure:: /_static/images/en-us_image_0000001906813634.png
   :alt: **Figure 1** Process for granting permissions

   **Figure 1** Process for granting permissions

#. .. _dns_usermanual_0027__en-us_topic_0172268189_li10269636890:

   `Create a user group and grant permissions <https://docs.otc.t-systems.com/identity-access-management/umn/getting_started/creating_a_user_group_and_assigning_permissions.html>`__.

   Create a user group on the IAM console and assign the **DNS Administrator** policy to the group.

#. `Create a user and add the user to the user group <https://docs.otc.t-systems.com/identity-access-management/umn/getting_started/creating_a_user_and_adding_the_user_to_a_user_group.html>`__

   Create a user on the IAM console and add the user to the group created in step :ref:`1 <dns_usermanual_0027__en-us_topic_0172268189_li10269636890>`.

#. `Log in to the management console as the created user <https://docs.otc.t-systems.com/identity-access-management/umn/getting_started/logging_in_as_a_user.html>`__.

   Log in to the DNS console by using the created user, and verify that the user only has read permissions for DNS.

   -  Choose **Service List** > **Domain Name Service**. On the **Dashboard** page, click **Private Zones**. Then click **Create Private Zone** in the upper right corner. If the private zone can be created, the DNS Administrator policy is in effect.
   -  Choose any other service from **Service List**. If a message appears indicating that you have insufficient permissions to access the service, the **DNS Administrator** policy is in effect.
