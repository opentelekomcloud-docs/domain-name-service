:original_name: en-us_topic_0057773658.html

.. _en-us_topic_0057773658:

Creating a Private Zone
=======================

**Scenarios**
-------------

Create a private zone to resolve a private domain name within VPCs.

**Prerequisites**
-----------------

-  You have created a VPC.
-  You have created an ECS in the VPC and planned a domain name (example.com) for the ECS.

**Procedure**
-------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane, choose **Private Zones**.

   The **Private Zones** page is displayed.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click **Create Private Zone**.

#. Set the required parameters.


   .. figure:: /_static/images/en-us_image_0000001124782805.png
      :alt: **Figure 1** Creating a private zone


      **Figure 1** Creating a private zone

   :ref:`Table 1 <en-us_topic_0057773658__dns_qs_0006_en-us_topic_0035467699_table2052132816642>` describes the parameters.

   .. _en-us_topic_0057773658__dns_qs_0006_en-us_topic_0035467699_table2052132816642:

   .. table:: **Table 1** Parameters for creating a private zone

      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | Parameter             | Description                                                                                                                        | Example Value           |
      +=======================+====================================================================================================================================+=========================+
      | Name                  | Name of the private zone, which is the private domain name you have planned for the ECS                                            | example.com             |
      |                       |                                                                                                                                    |                         |
      |                       | You can enter a top-level domain that complies with the domain naming rules.                                                       |                         |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | VPC                   | VPC to be associated with the private zone                                                                                         | -                       |
      |                       |                                                                                                                                    |                         |
      |                       | .. note::                                                                                                                          |                         |
      |                       |                                                                                                                                    |                         |
      |                       |    This VPC must be the same as the VPC where the servers are deployed. Otherwise, the domain name cannot be resolved.             |                         |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | Email                 | (Optional) Email address of the administrator managing the private zone                                                            | HOSTMASTER@example.com  |
      |                       |                                                                                                                                    |                         |
      |                       | It is recommended that you set the email address to **HOSTMASTER@\ Domain name**.                                                  |                         |
      |                       |                                                                                                                                    |                         |
      |                       | For more information about the email address, see :ref:`Why Was the Email Address Format Changed in the SOA Record? <dns_faq_009>` |                         |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | Tags                  | (Optional) Identifier of a resource                                                                                                | example_key1            |
      |                       |                                                                                                                                    |                         |
      |                       | Each tag contains a key and a value. You can add a maximum of 20 tags to a zone.                                                   | example_value1          |
      |                       |                                                                                                                                    |                         |
      |                       | For details about tag key and value requirements, see :ref:`Table 2 <en-us_topic_0057773658__dns_qs_0006_table1393932617253>`.     |                         |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | Description           | (Optional) Supplementary information about the zone                                                                                | This is a zone example. |
      |                       |                                                                                                                                    |                         |
      |                       | You can enter a maximum of 255 characters.                                                                                         |                         |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------+

   .. _en-us_topic_0057773658__dns_qs_0006_table1393932617253:

   .. table:: **Table 2** Tag key and value requirements

      +-----------------------+------------------------------------------------------------------------+-----------------------+
      | Parameter             | Requirements                                                           | Example Value         |
      +=======================+========================================================================+=======================+
      | Key                   | -  Cannot be left blank.                                               | example_key1          |
      |                       | -  Must be unique for each resource.                                   |                       |
      |                       | -  Can contain a maximum of 36 characters.                             |                       |
      |                       | -  Can contain only letters, digits, hyphens (-), and underscores (_). |                       |
      +-----------------------+------------------------------------------------------------------------+-----------------------+
      | Value                 | -  Cannot be left blank.                                               | example_value1        |
      |                       | -  Can contain a maximum of 43 characters.                             |                       |
      |                       | -  Can contain only letters, digits, hyphens (-), and underscores (_). |                       |
      +-----------------------+------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

#. Switch back to the **Private Zones** page.

   View the created private zone in the zone list.

#. Click the zone name to add a record set.

   On the **Record Sets** page, click **Add Record Set**. For detailed operations, see :ref:`Overview <dns_usermanual_0035>`.

   .. note::

      Click the zone name to view zone details. You can view SOA and NS record sets automatically generated by the system.

      -  The SOA record set defines the DNS server that is the authoritative information source for a particular domain name.
      -  The NS record set defines authoritative DNS servers for a domain name.

**Follow-up Operations**
------------------------

After a private zone is created, you can perform the following operations:

-  Add record sets for it. For details, see :ref:`Overview <dns_usermanual_0035>`.
-  Modify or delete it, or view its details. For details, see :ref:`Managing Private Zones <dns_usermanual_0033>`.

.. |image1| image:: /_static/images/en-us_image_0148391090.png
