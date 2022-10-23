:original_name: dns_usermanual_0015.html

.. _dns_usermanual_0015:

Adding a PTR Record
===================

**Scenarios**
-------------

You can create PTR records to map private IP addresses to private domain names.

For details about other record set types, see :ref:`Overview <dns_usermanual_0035>`.

Constraints
-----------

-  You can create PTR records only in private zones.

-  PTR records take effect only in a private zone whose domain name suffix is in-addr.arpa.

   For details about how to add a PTR record for a public domain name, see :ref:`Creating a PTR Record <en-us_topic_0077500015>`.

**Procedure**
-------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

3. In the navigation pane, choose **Private Zones**.

   The **Private Zones** page is displayed.

4. Click |image1| in the upper left corner and select the desired region and project.

5. Click the zone name.

6. Click **Add Record Set**.

   The **Add Record Set** dialog box is displayed.

7. Set required parameters based on :ref:`Table 1 <dns_usermanual_0015__table6260239895544>`.

   .. _dns_usermanual_0015__table6260239895544:

   .. table:: **Table 1** Parameters for adding a PTR record

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Description                                                                                                                                            | Example Value                                                                                                       |
      +=======================+========================================================================================================================================================+=====================================================================================================================+
      | Name                  | Name of the PTR record                                                                                                                                 | 10.1.168                                                                                                            |
      |                       |                                                                                                                                                        |                                                                                                                     |
      |                       |                                                                                                                                                        | For example, if the IP address is 192.168.1.10, the domain name in the PTR record is **10.1.168.192.in-addr.arpa**. |
      |                       |                                                                                                                                                        |                                                                                                                     |
      |                       |                                                                                                                                                        | -  If the private zone name is 192.in-addr.arpa, enter **10.1.168** in the box.                                     |
      |                       |                                                                                                                                                        | -  If the private zone name is 1.168.192.in-addr.arpa, enter **10** in the box.                                     |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Type                  | Type of the record set                                                                                                                                 | PTR - Map IP addresses to domains                                                                                   |
      |                       |                                                                                                                                                        |                                                                                                                     |
      |                       | If a message is displayed indicating that the record set you are trying to create exists, the record set conflicts with an existing record set.        |                                                                                                                     |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | TTL (s)               | Cache duration of the record set on a local DNS server, in seconds                                                                                     | The default value is **300**, which is, 5 minutes.                                                                  |
      |                       |                                                                                                                                                        |                                                                                                                     |
      |                       | The value ranges from **1** to **2147483647**, and the default is **300**.                                                                             |                                                                                                                     |
      |                       |                                                                                                                                                        |                                                                                                                     |
      |                       | If your service address changes frequently, set TTL to a smaller value.                                                                                |                                                                                                                     |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Value                 | Private domain name mapped to the private IP address. You can enter only one domain name.                                                              | host.example.com.                                                                                                   |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Tags                  | (Optional) Identifier of a resource                                                                                                                    | example_key1                                                                                                        |
      |                       |                                                                                                                                                        |                                                                                                                     |
      |                       | Each tag contains a key and a value. You can add a maximum of 20 tags to a record set. This parameter is displayed when you enable **Other Settings**. | example_value1                                                                                                      |
      |                       |                                                                                                                                                        |                                                                                                                     |
      |                       | For details about tag key and value requirements, see :ref:`Table 2 <dns_usermanual_0015__table191971158112315>`.                                      |                                                                                                                     |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
      | Description           | (Optional) Supplementary information about the record set                                                                                              | -                                                                                                                   |
      |                       |                                                                                                                                                        |                                                                                                                     |
      |                       | You can enter a maximum of 255 characters.                                                                                                             |                                                                                                                     |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+

   .. _dns_usermanual_0015__table191971158112315:

   .. table:: **Table 2** Tag key and value requirements

      +-----------------------+--------------------------------------------+-----------------------+
      | Parameter             | Requirements                               | Example Value         |
      +=======================+============================================+=======================+
      | Key                   | -  Cannot be left blank.                   | example_key1          |
      |                       | -  Must be unique for each resource.       |                       |
      |                       | -  Can contain a maximum of 36 characters. |                       |
      +-----------------------+--------------------------------------------+-----------------------+
      | Value                 | -  Cannot be left blank.                   | example_value1        |
      |                       | -  Can contain a maximum of 43 characters. |                       |
      +-----------------------+--------------------------------------------+-----------------------+

8. Click **OK**.

9. Switch back to the **Record Sets** page.

   View the added record set in the record set list of the zone and ensure that the status of the record set is **Normal**.

Related Operations
------------------

For more information, see :ref:`How Can I Configure a PTR Record to Map the IP Address of an ECS to a Domain Name? <dns_faq_031>`

.. |image1| image:: /_static/images/en-us_image_0148391090.png
