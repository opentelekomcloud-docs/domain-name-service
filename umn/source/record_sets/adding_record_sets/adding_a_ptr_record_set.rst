:original_name: dns_usermanual_0015.html

.. _dns_usermanual_0015:

Adding a PTR Record Set
=======================

**Scenarios**
-------------

You can create PTR record sets to map private IP addresses to domain names.

For details about other record set types, see :ref:`Record Set Types and Configuration Rules <dns_usermanual_0601>`.

Constraints
-----------

-  You can create PTR record sets only in private zones.

-  PTR record sets can only be added to private zones whose domain name suffix is in-addr.arpa.

   For details about how to create a PTR record for a public domain name, see :ref:`Creating a PTR Record <en-us_topic_0077500015>`.

**Procedure**
-------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Private Zones**.

   The **Private Zones** page is displayed.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click the domain name.

#. Click **Add Record Set**.

   The **Add Record Set** dialog box is displayed.

#. Configure the parameters based on :ref:`Table 1 <dns_usermanual_0015__table6260239895544>`.

   .. _dns_usermanual_0015__table6260239895544:

   .. table:: **Table 1** Parameters for adding a PTR record set

      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Description                                                                                                                   | Example Value                                                                                                       |
      +=======================+===============================================================================================================================+=====================================================================================================================+
      | Name                  | Name of the PTR record set                                                                                                    | 10.1.168                                                                                                            |
      |                       |                                                                                                                               |                                                                                                                     |
      |                       |                                                                                                                               | For example, if the IP address is 192.168.1.10, the domain name in the PTR record is **10.1.168.192.in-addr.arpa**. |
      |                       |                                                                                                                               |                                                                                                                     |
      |                       |                                                                                                                               | -  If the private zone is 192.in-addr.arpa, enter **10.1.168** in the box.                                          |
      |                       |                                                                                                                               | -  If the private zone is 1.168.192.in-addr.arpa, enter **10** in the box.                                          |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Type                  | Type of the record set                                                                                                        | PTR - Map IP addresses to domains                                                                                   |
      |                       |                                                                                                                               |                                                                                                                     |
      |                       | A message may be displayed indicating that the record set you are trying to add conflicts with an existing record set.        |                                                                                                                     |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | TTL (s)               | Cache duration of the record set on a local DNS server, in seconds.                                                           | 300                                                                                                                 |
      |                       |                                                                                                                               |                                                                                                                     |
      |                       | The value ranges from **1** to **2147483647**, and the default is **300**.                                                    |                                                                                                                     |
      |                       |                                                                                                                               |                                                                                                                     |
      |                       | If your service address changes frequently, set TTL to a smaller value.                                                       |                                                                                                                     |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Value                 | Private domain name mapped to the private IP address. You can enter only one domain name.                                     | host.example.com.                                                                                                   |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Tag                   | (Optional) Identifier of a record set. Each tag contains a key and a value. You can add a maximum of 20 tags to a record set. | example_key1                                                                                                        |
      |                       |                                                                                                                               |                                                                                                                     |
      |                       | For details about tag key and value requirements, see :ref:`Table 2 <dns_usermanual_0015__table191971158112315>`.             | example_value1                                                                                                      |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Description           | (Optional) Supplementary information about the record set.                                                                    | ``-``                                                                                                               |
      |                       |                                                                                                                               |                                                                                                                     |
      |                       | You can enter a maximum of 255 characters.                                                                                    |                                                                                                                     |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+

   .. _dns_usermanual_0015__table191971158112315:

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

For more information, see :ref:`How Can I Map the Private IP Address of an ECS to a Domain Name? <dns_faq_031>`

.. |image1| image:: /_static/images/en-us_image_0000001942372381.png
