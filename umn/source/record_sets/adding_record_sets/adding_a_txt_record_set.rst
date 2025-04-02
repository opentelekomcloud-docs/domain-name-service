:original_name: dns_usermanual_0012.html

.. _dns_usermanual_0012:

Adding a TXT Record Set
=======================

**Scenarios**
-------------

A TXT record set provides description for a domain name.

For details about other record set types, see :ref:`Record Set Types and Configuration Rules <dns_usermanual_0601>`.

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

#. Configure the parameters based on :ref:`Table 1 <dns_usermanual_0012__table5740910174810>`.

   .. _dns_usermanual_0012__table5740910174810:

   .. table:: **Table 1** Parameters for adding a TXT record set

      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------+
      | Parameter             | Description                                                                                                                                   | Example Value                                    |
      +=======================+===============================================================================================================================================+==================================================+
      | Name                  | Prefix of the domain name to be resolved.                                                                                                     | Left blank                                       |
      |                       |                                                                                                                                               |                                                  |
      |                       | For example, if the domain name is **example.com**, the prefix can be as follows:                                                             |                                                  |
      |                       |                                                                                                                                               |                                                  |
      |                       | -  **www**: The domain name is www.example.com, which is usually used for a website.                                                          |                                                  |
      |                       |                                                                                                                                               |                                                  |
      |                       | -  Left blank: The domain name is example.com.                                                                                                |                                                  |
      |                       |                                                                                                                                               |                                                  |
      |                       |    The **Name** field cannot be set to an at sign (@). Just leave it blank.                                                                   |                                                  |
      |                       |                                                                                                                                               |                                                  |
      |                       | -  **abc**: The domain name is abc.example.com, a subdomain of example.com.                                                                   |                                                  |
      |                       |                                                                                                                                               |                                                  |
      |                       | -  **mail**: The domain name is mail.example.com, which is typically used for email servers.                                                  |                                                  |
      |                       |                                                                                                                                               |                                                  |
      |                       | -  **\***: The domain name is \*.example.com, which is a wildcard domain name, indicating all subdomains of example.com.                      |                                                  |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------+
      | Type                  | Type of the record set                                                                                                                        | TXT - Specify text records                       |
      |                       |                                                                                                                                               |                                                  |
      |                       | A message may be displayed indicating that the record set you are trying to add conflicts with an existing record set.                        |                                                  |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------+
      | TTL (s)               | Cache duration of the record set on a local DNS server, in seconds.                                                                           | 300                                              |
      |                       |                                                                                                                                               |                                                  |
      |                       | The value ranges from **1** to **2147483647**, and the default is **300**.                                                                    |                                                  |
      |                       |                                                                                                                                               |                                                  |
      |                       | If your service address changes frequently, set TTL to a smaller value.                                                                       |                                                  |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------+
      | Value                 | Text content                                                                                                                                  | -  Single text record:                           |
      |                       |                                                                                                                                               |                                                  |
      |                       | Configuration rules:                                                                                                                          |    "aaa"                                         |
      |                       |                                                                                                                                               |                                                  |
      |                       | -  Text record values must be enclosed in double quotation marks.                                                                             | -  Multiple text records:                        |
      |                       |                                                                                                                                               |                                                  |
      |                       | -  One or more text record values are supported, each on a separate line.                                                                     |    "bbb"                                         |
      |                       |                                                                                                                                               |                                                  |
      |                       |    A maximum of 50 text record values can be entered.                                                                                         |    "ccc"                                         |
      |                       |                                                                                                                                               |                                                  |
      |                       | -  A single text record value can contain multiple character strings, each of which is double quoted and separated from others using a space. | -  A text record that contains multiple strings: |
      |                       |                                                                                                                                               |                                                  |
      |                       |    One character string cannot exceed 255 characters.                                                                                         |    "ddd" "eee" "fff"                             |
      |                       |                                                                                                                                               |                                                  |
      |                       |    A value must not exceed 4096 characters.                                                                                                   |                                                  |
      |                       |                                                                                                                                               |                                                  |
      |                       | -  The value cannot be left blank.                                                                                                            |                                                  |
      |                       |                                                                                                                                               |                                                  |
      |                       | -  The text cannot contain a backslash (\\).                                                                                                  |                                                  |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------+
      | Tag                   | (Optional) Identifier of a record set. Each tag contains a key and a value. You can add a maximum of 20 tags to a record set.                 | example_key1                                     |
      |                       |                                                                                                                                               |                                                  |
      |                       | For details about tag key and value requirements, see :ref:`Table 2 <dns_usermanual_0012__table191971158112315>`.                             | example_value1                                   |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------+
      | Description           | (Optional) Supplementary information about the record set.                                                                                    | ``-``                                            |
      |                       |                                                                                                                                               |                                                  |
      |                       | You can enter a maximum of 255 characters.                                                                                                    |                                                  |
      +-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------+

   .. _dns_usermanual_0012__table191971158112315:

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
