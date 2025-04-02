:original_name: dns_usermanual_0010.html

.. _dns_usermanual_0010:

Adding a CNAME Record Set
=========================

Scenarios
---------

If you want to map one domain name to another, add a CNAME record set for the domain name.

For more details, see :ref:`Record Set Types and Configuration Rules <dns_usermanual_0601>`.

Constraints
-----------

-  You can leave the **Name** parameter blank when adding a CNAME record set.
-  You cannot create a CNAME record set with the same name and resolution line as an NS record set.

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

#. Configure the parameters based on :ref:`Table 1 <dns_usermanual_0010__t7e961b6fba5344d9a5d12668c805e2a7>`.

   .. _dns_usermanual_0010__t7e961b6fba5344d9a5d12668c805e2a7:

   .. table:: **Table 1** Parameters for adding a CNAME record set

      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Parameter             | Description                                                                                                                   | Example Value                     |
      +=======================+===============================================================================================================================+===================================+
      | Name                  | Prefix of the domain name to be resolved.                                                                                     | Left blank                        |
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
      | Type                  | Type of the record set                                                                                                        | CNAME - Map one domain to another |
      |                       |                                                                                                                               |                                   |
      |                       | A message may be displayed indicating that the record set you are trying to add conflicts with an existing record set.        |                                   |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | TTL (s)               | Cache duration of the record set on a local DNS server, in seconds.                                                           | 300                               |
      |                       |                                                                                                                               |                                   |
      |                       | The value ranges from **1** to **2147483647**, and the default is **300**.                                                    |                                   |
      |                       |                                                                                                                               |                                   |
      |                       | If your service address changes frequently, set TTL to a smaller value.                                                       |                                   |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Value                 | Domain name alias. You can enter only one domain name.                                                                        | webserver01.example.com           |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Tag                   | (Optional) Identifier of a record set. Each tag contains a key and a value. You can add a maximum of 20 tags to a record set. | example_key1                      |
      |                       |                                                                                                                               |                                   |
      |                       | For details about tag key and value requirements, see :ref:`Table 2 <dns_usermanual_0010__table191971158112315>`.             | example_value1                    |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
      | Description           | (Optional) Supplementary information about the record set.                                                                    | ``-``                             |
      |                       |                                                                                                                               |                                   |
      |                       | You can enter a maximum of 255 characters.                                                                                    |                                   |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+

   .. _dns_usermanual_0010__table191971158112315:

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

#. Switch back to the **Record Sets** page.

   The added record set is in the **Normal** state.

.. |image1| image:: /_static/images/en-us_image_0000001906653140.png
