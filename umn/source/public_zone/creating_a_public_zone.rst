:original_name: en-us_topic_0035467702.html

.. _en-us_topic_0035467702:

Creating a Public Zone
======================

Scenarios
---------

Create a public zone on the DNS console to resolve your domain name.

Prerequisites
-------------

You have registered a domain name.

Procedure
---------

If your domain name is registered with a third-party registrar, create a public zone and add record sets to it on the DNS console.

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane, choose **Public Zones**.

   The **Public Zones** page is displayed.

#. Click **Create Public Zone**.

#. Set the parameters.


   .. figure:: /_static/images/en-us_image_0000001124643421.png
      :alt: **Figure 1** Creating a public zone


      **Figure 1** Creating a public zone

   :ref:`Table 1 <en-us_topic_0035467702__en-us_topic_0035467699_en-us_topic_0035467699_table2052132816642>` describes the parameters.

   .. _en-us_topic_0035467702__en-us_topic_0035467699_en-us_topic_0035467699_table2052132816642:

   .. table:: **Table 1** Parameters for creating a public zone

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | Parameter             | Description                                                                                                                                | Example Value           |
      +=======================+============================================================================================================================================+=========================+
      | Name                  | Name of the public zone, which is the domain name you registered                                                                           | example.com             |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | Email                 | (Optional) Email address of the administrator managing the public zone                                                                     | HOSTMASTER@example.com  |
      |                       |                                                                                                                                            |                         |
      |                       | It is recommended that you set the email address to **HOSTMASTER@\ Domain name**.                                                          |                         |
      |                       |                                                                                                                                            |                         |
      |                       | For more information about the email address, see :ref:`Why Was the Email Address Format Changed in the SOA Record? <dns_faq_009>`         |                         |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | Tags                  | (Optional) Identifier of a resource                                                                                                        | example_key1            |
      |                       |                                                                                                                                            |                         |
      |                       | Each tag contains a key and a value. You can add a maximum of 20 tags to a zone.                                                           | example_value1          |
      |                       |                                                                                                                                            |                         |
      |                       | For details about tag key and value requirements, see :ref:`Table 2 <en-us_topic_0035467702__en-us_topic_0035467699_table18290035121711>`. |                         |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | Description           | (Optional) Supplementary information about the zone                                                                                        | This is a zone example. |
      |                       |                                                                                                                                            |                         |
      |                       | You can enter a maximum of 255 characters.                                                                                                 |                         |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+

   .. _en-us_topic_0035467702__en-us_topic_0035467699_table18290035121711:

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

   View the created public zone on the **Public Zones** page.

#. Click the zone name or click **Add Record Set** under **Operation**.

   On the **Record Sets** page, click **Add Record Set**. For detailed operations, see :ref:`Overview <dns_usermanual_0035>`.

   .. note::

      Click the zone name to view zone details. You can view SOA and NS record sets automatically generated by the system.

      -  The SOA record set defines the DNS server that is the authoritative information source for a particular domain name.

      -  The NS record set defines authoritative DNS servers for a zone.

Follow-up Operations
--------------------

After a public zone is created, you can perform the following operations:

-  Add record sets for it. For details, see :ref:`Overview <dns_usermanual_0035>`.
-  Modify or delete it, or view its details. For details, see :ref:`Managing Public Zones <dns_usermanual_0031>`.
