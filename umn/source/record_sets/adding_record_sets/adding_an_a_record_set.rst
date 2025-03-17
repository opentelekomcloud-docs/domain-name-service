:original_name: dns_usermanual_0007.html

.. _dns_usermanual_0007:

Adding an A Record Set
======================

**Scenarios**
-------------

If you want end users to access your website, web application, or cloud server configured with an IPv4 address via its domain name, add an A record set for this domain name.

For more information about the types of record sets, see :ref:`Record Set Types and Configuration Rules <dns_usermanual_0601>`.

Prerequisites
-------------

You have a website, web application, or cloud server and obtained an IPv4 address.

**Procedure**
-------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane, choose **Public Zones** or **Private Zones**.

   The zone list is displayed.

#. (Optional) If you have selected **Private Zones**, click |image1| on the upper left corner to select the region and project.

#. Click the domain name.

#. Click **Add Record Set**.

   The **Add Record Set** dialog box is displayed.

#. Configure the parameters based on :ref:`Table 1 <dns_usermanual_0007__table219785892310>`.

   .. _dns_usermanual_0007__table219785892310:

   .. table:: **Table 1** Parameters for adding an A record set

      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Parameter             | Description                                                                                                                   | Example Value                     |
      +=======================+===============================================================================================================================+===================================+
      | Name                  | Prefix of the domain name to be resolved.                                                                                     | www                               |
      |                       |                                                                                                                               |                                   |
      |                       | For example, if the domain name is **example.com**, the prefix can be as follows:                                             |                                   |
      |                       |                                                                                                                               |                                   |
      |                       | -  **www**: The domain name is www.example.com, which is usually used for a website.                                          |                                   |
      |                       |                                                                                                                               |                                   |
      |                       | -  Left blank: The domain name is example.com.                                                                                |                                   |
      |                       |                                                                                                                               |                                   |
      |                       |    The **Name** field cannot be set to an at sign (@). Just leave it blank.                                                   |                                   |
      |                       |                                                                                                                               |                                   |
      |                       | -  **abc**: The domain name is abc.example.com, a subdomain of example.com.                                                   |                                   |
      |                       |                                                                                                                               |                                   |
      |                       | -  **mail**: The domain name is mail.example.com, which is typically used for email servers.                                  |                                   |
      |                       |                                                                                                                               |                                   |
      |                       | -  **\***: The domain name is \*.example.com, which is a wildcard domain name, indicating all subdomains of example.com.      |                                   |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Type                  | Type of the record set.                                                                                                       | A - Map domains to IPv4 addresses |
      |                       |                                                                                                                               |                                   |
      |                       | A message may be displayed indicating that the record set you are trying to add conflicts with an existing record set.        |                                   |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | TTL (s)               | Cache duration of the record set on a local DNS server, in seconds.                                                           | 300                               |
      |                       |                                                                                                                               |                                   |
      |                       | The value ranges from **1** to **2147483647**, and the default is **300**.                                                    |                                   |
      |                       |                                                                                                                               |                                   |
      |                       | If your service address changes frequently, set TTL to a smaller value.                                                       |                                   |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Value                 | IPv4 addresses mapped to the domain name.                                                                                     | 192.168.12.2                      |
      |                       |                                                                                                                               |                                   |
      |                       | You can enter a maximum of 50 record values, each on a separate line.                                                         | 192.168.12.3                      |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Tag                   | (Optional) Identifier of a record set. Each tag contains a key and a value. You can add a maximum of 20 tags to a record set. | example_key1                      |
      |                       |                                                                                                                               |                                   |
      |                       | For details about tag key and value requirements, see :ref:`Table 2 <dns_usermanual_0007__table191971158112315>`.             | example_value1                    |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Description           | (Optional) Supplementary information about the record set.                                                                    | N/A                               |
      |                       |                                                                                                                               |                                   |
      |                       | You can enter a maximum of 255 characters.                                                                                    |                                   |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+

   .. _dns_usermanual_0007__table191971158112315:

   .. table:: **Table 2** Tag key and value requirements

      +-----------------------+--------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Requirements                                                                         | Example Value         |
      +=======================+======================================================================================+=======================+
      | Key                   | -  Cannot be left blank.                                                             | example_key1          |
      |                       | -  Must be unique for each resource.                                                 |                       |
      |                       | -  Can contain a maximum of 36 characters.                                           |                       |
      |                       | -  Can contain only letters, digits, hyphens (-), at signs (@), and underscores (_). |                       |
      +-----------------------+--------------------------------------------------------------------------------------+-----------------------+
      | Value                 | -  Cannot be left blank.                                                             | example_value1        |
      |                       | -  Can contain a maximum of 43 characters.                                           |                       |
      |                       | -  Can contain only letters, digits, hyphens (-), at signs (@), and underscores (_). |                       |
      +-----------------------+--------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

#. Switch back to the **Record Sets** page.

   The added record set is in the **Normal** state.

Related Operations
------------------

For details about how to configure A record sets, see :ref:`Configuring a Public Zone <en-us_topic_0035467699>`.

.. |image1| image:: /_static/images/en-us_image_0000001906653140.png
