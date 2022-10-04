:original_name: dns_faq_031.html

.. _dns_faq_031:

How Can I Configure a PTR Record to Map the IP Address of an ECS to a Domain Name?
==================================================================================

PTR records enable users to query domain names based on IP addresses.

To map the private IP address of an ECS to a domain name, you must create a private zone and create a PTR record in the zone.

To map the EIP of the ECS to a domain name, refer to :ref:`Creating a PTR Record <en-us_topic_0077500015>`.

.. note::

   The domain name in a PTR record must be in the *x.x.x.x*\ **.in-addr.arpa** format. **in-addr.arpa** is the domain name suffix used for reverse resolution.

   For example, if the private IP address is 192.168.1.10, the domain name in the PTR record must be **10.1.168.192.in-addr.arpa**.

   In this case, you must create a private zone named **192.in-addr.arpa** and add a PTR record with its value set to **10.1.168.192.in-addr.arpa**.

Creating a Private Zone
-----------------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane, choose **Private Zones**.

   The **Private Zones** page is displayed.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click **Create Private Zone**.


   .. figure:: /_static/images/en-us_image_0000001124472319.png
      :alt: **Figure 1** Create Private Zone


      **Figure 1** Create Private Zone

#. Set the parameters based on :ref:`Table 1 <dns_faq_031__en-us_topic_0089401572_table12455154165118>`.

   .. _dns_faq_031__en-us_topic_0089401572_table12455154165118:

   .. table:: **Table 1** Parameters for creating a private zone

      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | Parameter             | Description                                                                                                                        | Example Value           |
      +=======================+====================================================================================================================================+=========================+
      | Name                  | Domain name                                                                                                                        | 192.in-addr.arpa        |
      |                       |                                                                                                                                    |                         |
      |                       | Set the domain name suffix to **in-addr.arpa**.                                                                                    |                         |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | VPC                   | VPC to be associated with the private zone                                                                                         | N/A                     |
      |                       |                                                                                                                                    |                         |
      |                       | Select the VPC you want to associate with the private zone.                                                                        |                         |
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
      |                       | For details about tag key and value requirements, see :ref:`Table 2 <dns_faq_031__en-us_topic_0089401572_table114584301390>`.      |                         |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | Description           | (Optional)                                                                                                                         | This is a private zone. |
      |                       |                                                                                                                                    |                         |
      |                       | Supplementary information about the zone                                                                                           |                         |
      |                       |                                                                                                                                    |                         |
      |                       | You can enter a maximum of 255 characters.                                                                                         |                         |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------+

   .. _dns_faq_031__en-us_topic_0089401572_table114584301390:

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

#. Click **OK**.

#. Switch back to the **Private Zones** page.

   View the created private zone.

   .. note::

      Click the zone name to view zone details. You can view SOA and NS record sets automatically generated by the system.

      -  The SOA record set defines the DNS server that is the authoritative information source for a particular domain name.
      -  The NS record set defines authoritative DNS servers for a zone.

Adding a PTR Record
-------------------

#. On the **Private Zones** page, click the name of the private zone that you have created.

   The **Record Sets** page is displayed.

#. Click **Add Record Set**.

   The **Add Record Set** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0000001124472865.png
      :alt: **Figure 2** Add Record Set


      **Figure 2** Add Record Set

#. Set the parameters based on :ref:`Table 3 <dns_faq_031__en-us_topic_0089401572_table2068616914271>`.

   .. _dns_faq_031__en-us_topic_0089401572_table2068616914271:

   .. table:: **Table 3** Parameters for adding a PTR record

      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Description                                                                                                                   | Example Value                                                                                                           |
      +=======================+===============================================================================================================================+=========================================================================================================================+
      | Name                  | IP address in the PTR record (typed in reverse order)                                                                         | 10.1.168                                                                                                                |
      |                       |                                                                                                                               |                                                                                                                         |
      |                       |                                                                                                                               | For example, if the IP address is **192.168.1.10**, the domain name in the PTR record is **10.1.168.192.in-addr.arpa**. |
      |                       |                                                                                                                               |                                                                                                                         |
      |                       |                                                                                                                               | -  If the private zone name is **192.in-addr.arpa**, enter **10.1.168** in the box.                                     |
      |                       |                                                                                                                               | -  If the private zone name is **1.168.192.in-addr.arpa**, enter **10** in the box.                                     |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
      | Type                  | Type of the record set                                                                                                        | PTR – Map IP addresses to domains                                                                                       |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
      | TTL (s)               | Cache duration of the record set, in seconds                                                                                  | The default value is **300**, which is, 5 minutes.                                                                      |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
      | Value                 | Domain name mapped to the IP address                                                                                          | mail.example.com                                                                                                        |
      |                       |                                                                                                                               |                                                                                                                         |
      |                       | You can enter only one name.                                                                                                  |                                                                                                                         |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
      | Tags                  | (Optional) Identifier of a resource                                                                                           | example_key1                                                                                                            |
      |                       |                                                                                                                               |                                                                                                                         |
      |                       | Each tag contains a key and a value. You can add a maximum of 20 tags to a record set.                                        | example_value1                                                                                                          |
      |                       |                                                                                                                               |                                                                                                                         |
      |                       | For details about tag key and value requirements, see :ref:`Table 2 <dns_faq_031__en-us_topic_0089401572_table114584301390>`. |                                                                                                                         |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
      | Description           | (Optional) Supplementary information about the PTR record                                                                     | The PTR record is for reverse resolution.                                                                               |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

#. Switch back to the **Record Sets** page.

   View the added record set in the record set list of the zone and ensure that the status of the record set is **Normal**.

.. |image1| image:: /_static/images/en-us_image_0148391090.png
