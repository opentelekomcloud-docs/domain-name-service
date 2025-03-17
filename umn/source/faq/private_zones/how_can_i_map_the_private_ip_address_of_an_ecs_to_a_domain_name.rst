:original_name: dns_faq_031.html

.. _dns_faq_031:

How Can I Map the Private IP Address of an ECS to a Domain Name?
================================================================

You can configure PTR records to allow end users to query domain names based on IP addresses.

To map the private IP address of an ECS to a domain name, you must create a private zone and add a PTR record to the zone.

To add a PTR record, you may refer to :ref:`Creating a PTR Record <en-us_topic_0077500015>`.

.. note::

   The domain name for the PTR record must be in the *x.x.x.x*\ **.in-addr.arpa** format. **in-addr.arpa** is the domain name suffix used for reverse resolution.

   For example, if the private IP address is 192.168.1.10, the domain name is 10.1.168.192.in-addr.arpa.

   You need to create a private zone with the domain name set to 192.in-addr.arpa and add a PTR record with the **Name** field set to **10.1.168**.

Creating a Private Zone
-----------------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Private Zones**.

   The **Private Zones** page is displayed.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click **Create Private Zone**.


   .. figure:: /_static/images/en-us_image_0000001942372773.png
      :alt: **Figure 1** Create Private Zone

      **Figure 1** Create Private Zone

#. Configure the parameters based on :ref:`Table 1 <dns_faq_031__en-us_topic_0089401572_table12455154165118>`.

   .. _dns_faq_031__en-us_topic_0089401572_table12455154165118:

   .. table:: **Table 1** Parameters for creating a private zone

      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | Parameter             | Description                                                                                                                        | Example Value           |
      +=======================+====================================================================================================================================+=========================+
      | Domain Name           | Domain name you use to access the cloud servers or cloud services.                                                                 | 192.in-addr.arpa        |
      |                       |                                                                                                                                    |                         |
      |                       | Ensure that the domain name suffix is **in-addr.arpa**.                                                                            |                         |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | VPC                   | VPC to be associated with the private zone.                                                                                        | N/A                     |
      |                       |                                                                                                                                    |                         |
      |                       | Select the VPC you want to associate with the private zone.                                                                        |                         |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | Email                 | (Optional) Email address of the administrator managing the private zone.                                                           | HOSTMASTER@example.com  |
      |                       |                                                                                                                                    |                         |
      |                       | Recommended email address: **HOSTMASTER@\ Domain name**                                                                            |                         |
      |                       |                                                                                                                                    |                         |
      |                       | For more information about the email address, see :ref:`Why Was the Email Address Format Changed in the SOA Record? <dns_faq_009>` |                         |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
      | Tag                   | (Optional) Identifier of a resource                                                                                                | example_key1            |
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

#. .. _dns_faq_031__en-us_topic_0089401572_li16410118105310:

   Switch back to the **Private Zones** page.

   You can view the created private zone in the private zone list.

   .. note::

      Click the domain name to view SOA and NS record sets automatically generated for the zone.

      -  The start of authority (SOA) record includes administrative information about your zone, as defined by the Domain Name System (DNS).
      -  The NS record set defines the authoritative DNS servers for the domain name.

Adding a PTR Record
-------------------

#. On the **Private Zones** page, click the domain name of the private zone you created.

   The **Record Sets** page is displayed.

#. Click **Add Record Set**.

   The **Add Record Set** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0000001942372761.png
      :alt: **Figure 2** Add Record Set

      **Figure 2** Add Record Set

#. Configure the parameters based on :ref:`Table 3 <dns_faq_031__en-us_topic_0089401572_table2068616914271>`.

   .. _dns_faq_031__en-us_topic_0089401572_table2068616914271:

   .. table:: **Table 3** Parameters for adding a PTR record

      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Description                                                                                                                   | Example Value                                                                                                        |
      +=======================+===============================================================================================================================+======================================================================================================================+
      | Name                  | Part of the private IP address in reverse order.                                                                              | 10.1.168                                                                                                             |
      |                       |                                                                                                                               |                                                                                                                      |
      |                       |                                                                                                                               | For example, if the IP address is 192.168.1.10, the domain name in the PTR record must be 10.1.168.192.in-addr.arpa. |
      |                       |                                                                                                                               |                                                                                                                      |
      |                       |                                                                                                                               | -  If the domain name is 192.in-addr.arpa, enter **10.1.168**.                                                       |
      |                       |                                                                                                                               | -  If the domain name is 1.168.192.in-addr.arpa, enter **10**.                                                       |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
      | Type                  | Type of the record set.                                                                                                       | PTR - Map IP addresses to domains                                                                                    |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
      | TTL (s)               | Cache duration of the record set, in seconds.                                                                                 | Default value: 300                                                                                                   |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
      | Value                 | Domain name mapped to the IP address.                                                                                         | mail.example.com                                                                                                     |
      |                       |                                                                                                                               |                                                                                                                      |
      |                       | You can enter only one name.                                                                                                  |                                                                                                                      |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
      | Tag                   | (Optional) Identifier of a resource                                                                                           | example_key1                                                                                                         |
      |                       |                                                                                                                               |                                                                                                                      |
      |                       | Each tag contains a key and a value. You can add a maximum of 20 tags to a record set.                                        | example_value1                                                                                                       |
      |                       |                                                                                                                               |                                                                                                                      |
      |                       | For details about tag key and value requirements, see :ref:`Table 2 <dns_faq_031__en-us_topic_0089401572_table114584301390>`. |                                                                                                                      |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
      | Description           | (Optional) Supplementary information about the PTR record.                                                                    | The PTR record is for reverse resolution.                                                                            |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

#. Switch back to the **Record Sets** page.

   The added record set is in the **Normal** state.

.. |image1| image:: /_static/images/en-us_image_0000001906973766.png
