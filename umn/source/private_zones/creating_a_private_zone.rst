:original_name: en-us_topic_0057773658.html

.. _en-us_topic_0057773658:

Creating a Private Zone
=======================

**Scenarios**
-------------

Create a private zone to map a private domain name to a private IP address within a VPC.

**Prerequisites**
-----------------

-  You have created a VPC.
-  You have created an ECS in the VPC and planned to use a private domain name (example.com) for the ECS.

**Procedure**
-------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Private Zones**.

   The **Private Zones** page is displayed.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click **Create Private Zone**.

#. Configure the parameters.


   .. figure:: /_static/images/en-us_image_0000001906813838.png
      :alt: **Figure 1** Creating a private zone

      **Figure 1** Creating a private zone

   :ref:`Table 1 <en-us_topic_0057773658__en-us_topic_0138290710_en-us_topic_0035467699_table2052132816642>` describes the parameters.

   .. _en-us_topic_0057773658__en-us_topic_0138290710_en-us_topic_0035467699_table2052132816642:

   .. table:: **Table 1** Parameters for creating a private zone

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | Parameter             | Description                                                                                                                                         | Example Value           |
      +=======================+=====================================================================================================================================================+=========================+
      | Domain Name           | Domain name you have planned for the ECS.                                                                                                           | example.com             |
      |                       |                                                                                                                                                     |                         |
      |                       | You can enter a top-level domain that complies with the domain naming rules.                                                                        |                         |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | VPC                   | VPC to be associated with the private zone.                                                                                                         | N/A                     |
      |                       |                                                                                                                                                     |                         |
      |                       | .. note::                                                                                                                                           |                         |
      |                       |                                                                                                                                                     |                         |
      |                       |    This VPC must be the same as the VPC where your other cloud resources are deployed. If the VPC is different, the domain name cannot be resolved. |                         |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | Email                 | (Optional) Email address of the administrator managing the private zone.                                                                            | HOSTMASTER@example.com  |
      |                       |                                                                                                                                                     |                         |
      |                       | Recommended email address: **HOSTMASTER@\ Domain name**                                                                                             |                         |
      |                       |                                                                                                                                                     |                         |
      |                       | For details about the email address, see :ref:`Why Was the Email Address Format Changed in the SOA Record? <dns_faq_009>`                           |                         |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | Tag                   | (Optional) Identifier of the domain name.                                                                                                           | example_key1            |
      |                       |                                                                                                                                                     |                         |
      |                       | Each tag contains a key and a value. You can add a maximum of 20 tags to a zone.                                                                    | example_value1          |
      |                       |                                                                                                                                                     |                         |
      |                       | For details about tag key and value requirements, see :ref:`Table 2 <en-us_topic_0057773658__en-us_topic_0138290710_table1393932617253>`.           |                         |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | Description           | (Optional) Supplementary information about the zone.                                                                                                | This is a zone example. |
      |                       |                                                                                                                                                     |                         |
      |                       | You can enter a maximum of 255 characters.                                                                                                          |                         |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+

   .. _en-us_topic_0057773658__en-us_topic_0138290710_table1393932617253:

   .. table:: **Table 2** Tag key and value requirements

      +-----------------------+--------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Requirements                                                                         | Example Value         |
      +=======================+======================================================================================+=======================+
      | Key                   | -  Cannot be left blank.                                                             | example_key1          |
      |                       | -  Must be unique for each resource.                                                 |                       |
      |                       | -  Can contain a maximum of 128 characters.                                          |                       |
      |                       | -  Can contain letters, digits, spaces, and the following characters: \_ . : = + - @ |                       |
      |                       | -  Cannot start or end with a space, or cannot start with **\_sys\_**.               |                       |
      +-----------------------+--------------------------------------------------------------------------------------+-----------------------+
      | Value                 | -  Can be left blank.                                                                | example_value1        |
      |                       | -  Can contain a maximum of 255 characters.                                          |                       |
      |                       | -  Can contain letters, digits, spaces, and the following characters: \_ . : = + - @ |                       |
      +-----------------------+--------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

#. Switch back to the **Private Zones** page.

   You can view the created private zone in the zone list.

#. Click the domain name to add record sets.

   On the **Record Sets** page, click **Manage Record Set**. For detailed operations, see :ref:`Record Set Overview <dns_usermanual_0035>`.

   .. note::

      Click the domain name to view SOA and NS record sets automatically generated for the zone.

      -  The SOA record set identifies the base DNS information about the domain name.
      -  The NS record set defines authoritative DNS servers for the domain name.

**Follow-up Operations**
------------------------

After a private zone is created, you can perform the following operations:

-  Add record sets for it. For details, see :ref:`Record Set Overview <dns_usermanual_0035>`.
-  Modify or delete it, or view its details. For details, see :ref:`Managing Private Zones <dns_usermanual_0033>`.

.. |image1| image:: /_static/images/en-us_image_0000001906973766.png
