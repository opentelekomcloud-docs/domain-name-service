:original_name: dns_usermanual_0009.html

.. _dns_usermanual_0009:

Adding an NS Record Set
=======================

Scenarios
---------

If you want to specify authoritative DNS servers for a domain name, you can add NS record sets.

For more details, see :ref:`Record Set Types and Configuration Rules <dns_usermanual_0601>`.

Constraints
-----------

-  You can create NS record sets only in public zones.
-  After a public zone is created, an NS record set is automatically created for this zone and cannot be deleted. You can add NS record sets only in the following scenarios:

   -  The **Name** parameter is not left blank. This means that you can add NS record sets for subdomains of a domain name.
   -  The value of the **Line** parameter is not set to **Default**. This means that you can add NS record sets for the domain name with other resolution lines.

**Procedure**
-------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Public Zones**.

   The **Public Zones** page is displayed.

#. Click the domain name.

#. Click **Add Record Set**.

   The **Add Record Set** dialog box is displayed.

6. Configure the parameters based on :ref:`Table 1 <dns_usermanual_0009__table51864159122254>`.

   .. _dns_usermanual_0009__table51864159122254:

   .. table:: **Table 1** Parameters for adding an NS record set

      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------+
      | Parameter             | Description                                                                                                                   | Example Value                                  |
      +=======================+===============================================================================================================================+================================================+
      | Name                  | Prefix of the domain name to be resolved.                                                                                     | abc                                            |
      |                       |                                                                                                                               |                                                |
      |                       | For example, if the domain name is **example.com**, the prefix can be as follows:                                             |                                                |
      |                       |                                                                                                                               |                                                |
      |                       | -  **www**: The domain name is www.example.com, which is usually used for a website.                                          |                                                |
      |                       |                                                                                                                               |                                                |
      |                       | -  Left blank: The domain name is example.com.                                                                                |                                                |
      |                       |                                                                                                                               |                                                |
      |                       |    The **Name** field cannot be set to an at sign (@). Just leave it blank.                                                   |                                                |
      |                       |                                                                                                                               |                                                |
      |                       | -  **abc**: The domain name is abc.example.com, a subdomain of example.com.                                                   |                                                |
      |                       |                                                                                                                               |                                                |
      |                       | -  **mail**: The domain name is mail.example.com, which is typically used for email servers.                                  |                                                |
      |                       |                                                                                                                               |                                                |
      |                       | -  **\***: The domain name is \*.example.com, which is a wildcard domain name, indicating all subdomains of example.com.      |                                                |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------+
      | Type                  | Type of the record set                                                                                                        | NS - Delegate subdomains to other name servers |
      |                       |                                                                                                                               |                                                |
      |                       | A message may be displayed indicating that the record set you are trying to add conflicts with an existing record set.        |                                                |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------+
      | TTL (s)               | Cache duration of the record set on a local DNS server, in seconds.                                                           | 300                                            |
      |                       |                                                                                                                               |                                                |
      |                       | The value ranges from **1** to **2147483647**, and the default is **300**.                                                    |                                                |
      |                       |                                                                                                                               |                                                |
      |                       | If your service address changes frequently, set TTL to a smaller value.                                                       |                                                |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------+
      | Value                 | DNS server address                                                                                                            | ns1.example.net                                |
      |                       |                                                                                                                               |                                                |
      |                       | You can enter a maximum of 50 record values, each on a separate line.                                                         | ns2.example.net                                |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------+
      | Tag                   | (Optional) Identifier of a record set. Each tag contains a key and a value. You can add a maximum of 20 tags to a record set. | example_key1                                   |
      |                       |                                                                                                                               |                                                |
      |                       | For details about tag key and value requirements, see :ref:`Table 2 <dns_usermanual_0009__table191971158112315>`.             | example_value1                                 |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------+
      | Description           | (Optional) Supplementary information about the record set.                                                                    | ``-``                                          |
      |                       |                                                                                                                               |                                                |
      |                       | You can enter a maximum of 255 characters.                                                                                    |                                                |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------+

   .. _dns_usermanual_0009__table191971158112315:

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

7. Switch back to the **Record Sets** tab.

   The added record set is in the **Normal** state.
