:original_name: dns_bestprac_0002.html

.. _dns_bestprac_0002:

Configuring Private Domain Names for ECSs
=========================================

Overview
--------

**Scenario**

If one of your ECSs is not working normally and you need to use the backup ECS to handle requests, but you have not configured private zones for the two ECSs, you need to change the private IP address in the code for the faulty ECS. This will interrupt your services and cause you to publish your website again, which is time- and labor-consuming.

Assume that you have configured private zones for the ECSs and have included their private domain names in the code. If one ECS is malfunctioning, you only need to change the DNS records to direct traffic to a normal ECS. Your services will not be interrupted, and you do not need to publish the website again.

**Architecture**

:ref:`Figure 1 <dns_bestprac_0002__fig182055712485>` shows the networking of a website where ECSs and RDS instances are deployed in a VPC.

-  ECS0: primary service node
-  ECS1: public service node
-  RDS1: service database
-  ECS2: backup service node
-  RDS2: backup database

.. _dns_bestprac_0002__fig182055712485:

.. figure:: /_static/images/en-us_image_0000001394829705.png
   :alt: **Figure 1** Networking example

   **Figure 1** Networking example

**Advantages**

-  **Higher efficiency and security**: You can use private domain names to access ECSs in the VPCs, without going through the Internet.
-  **Easier management**: Compared with IP addresses, domain names are easier to modify in the code. When an ECS is changed, you only need to change the DNS records without modifying the code.

Resource Planning
-----------------

This table lists private zones and record sets planned for the cloud servers.

.. _dns_bestprac_0002__table11364645122020:

.. table:: **Table 1** Private zones and record sets for each server

   +----------+--------------+----------------+--------------------+-----------------+------------------------------------+
   | Resource | Private Zone | Associated VPC | Private IP Address | Record Set Type | Description                        |
   +==========+==============+================+====================+=================+====================================+
   | ECS1     | api.ecs.com  | VPC_001        | 192.168.2.8        | A               | Public service node                |
   +----------+--------------+----------------+--------------------+-----------------+------------------------------------+
   | ECS2     | api.ecs.com  | VPC_001        | 192.168.3.8        | A               | Backup for the public service node |
   +----------+--------------+----------------+--------------------+-----------------+------------------------------------+
   | RDS1     | db.com       | VPC_001        | 192.168.2.5        | A               | Service database                   |
   +----------+--------------+----------------+--------------------+-----------------+------------------------------------+
   | RDS2     | db.com       | VPC_001        | 192.168.3.5        | A               | Backup database                    |
   +----------+--------------+----------------+--------------------+-----------------+------------------------------------+

.. _dns_bestprac_0002__table56883141317:

.. table:: **Table 2** Resource planning

   +--------------+-----------+-------------+---------------------------------------------------------------------------------------------------------------------------------------+-----------+--------------------------------------------------------------------------------------------------------------------+
   | Region       | Service   | Resource    | Description                                                                                                                           | Quantity  | Monthly Price                                                                                                      |
   +==============+===========+=============+=======================================================================================================================================+===========+====================================================================================================================+
   | eu-de        | VPC       | VPC_001     | The DNS server addresses must be the same as the private DNS server addresses of Open Telekom Cloud.                                  | 1         | Free                                                                                                               |
   |              |           |             |                                                                                                                                       |           |                                                                                                                    |
   |              |           |             | For details, see `Availability of secondary DNS <https://www.open-telekom-cloud.com/en/support/release-notes/secondary-dns>`__        |           |                                                                                                                    |
   +--------------+-----------+-------------+---------------------------------------------------------------------------------------------------------------------------------------+-----------+--------------------------------------------------------------------------------------------------------------------+
   |              | ECS       | ECS0        | -  Private domain name: api.ecs.com                                                                                                   | 3         | For details, see `ECS Product Pricing Details <https://open-telekom-cloud.com/en/prices/price-calculator>`__.      |
   |              |           |             |                                                                                                                                       |           |                                                                                                                    |
   |              |           | ECS1        | -  Associated VPC: VPC_001                                                                                                            |           |                                                                                                                    |
   |              |           |             |                                                                                                                                       |           |                                                                                                                    |
   |              |           | ECS2        | -  ECS1: public service node                                                                                                          |           |                                                                                                                    |
   |              |           |             |                                                                                                                                       |           |                                                                                                                    |
   |              |           |             |    Private IP address: 192.168.2.8                                                                                                    |           |                                                                                                                    |
   |              |           |             |                                                                                                                                       |           |                                                                                                                    |
   |              |           |             | -  ECS2: backup service node                                                                                                          |           |                                                                                                                    |
   |              |           |             |                                                                                                                                       |           |                                                                                                                    |
   |              |           |             | -  Private IP address: 192.168.3.8                                                                                                    |           |                                                                                                                    |
   +--------------+-----------+-------------+---------------------------------------------------------------------------------------------------------------------------------------+-----------+--------------------------------------------------------------------------------------------------------------------+
   |              | RDS       | RDS1        | -  Private domain name: db.com                                                                                                        | 2         | For details, see `RDS Product Pricing Details <https://open-telekom-cloud.com/en/prices/price-calculator>`__.      |
   |              |           |             |                                                                                                                                       |           |                                                                                                                    |
   |              |           | RDS2        | -  Associated VPC: VPC_001                                                                                                            |           |                                                                                                                    |
   |              |           |             |                                                                                                                                       |           |                                                                                                                    |
   |              |           |             | -  RDS1: service database                                                                                                             |           |                                                                                                                    |
   |              |           |             |                                                                                                                                       |           |                                                                                                                    |
   |              |           |             |    Private IP address: 192.168.2.5                                                                                                    |           |                                                                                                                    |
   |              |           |             |                                                                                                                                       |           |                                                                                                                    |
   |              |           |             | -  RDS2: backup database                                                                                                              |           |                                                                                                                    |
   |              |           |             |                                                                                                                                       |           |                                                                                                                    |
   |              |           |             |    Private IP address: 192.168.3.5                                                                                                    |           |                                                                                                                    |
   +--------------+-----------+-------------+---------------------------------------------------------------------------------------------------------------------------------------+-----------+--------------------------------------------------------------------------------------------------------------------+
   |              | DNS       | api.ecs.com | -  api.ecs.com:                                                                                                                       | 2         | Free                                                                                                               |
   |              |           |             |                                                                                                                                       |           |                                                                                                                    |
   |              |           | db.com      |    Associated VPC: VPC_001                                                                                                            |           |                                                                                                                    |
   |              |           |             |                                                                                                                                       |           |                                                                                                                    |
   |              |           |             |    Record set type: A                                                                                                                 |           |                                                                                                                    |
   |              |           |             |                                                                                                                                       |           |                                                                                                                    |
   |              |           |             |    Value: 192.168.2.8                                                                                                                 |           |                                                                                                                    |
   |              |           |             |                                                                                                                                       |           |                                                                                                                    |
   |              |           |             | -  db.com                                                                                                                             |           |                                                                                                                    |
   |              |           |             |                                                                                                                                       |           |                                                                                                                    |
   |              |           |             |    Associated VPC: VPC_001                                                                                                            |           |                                                                                                                    |
   |              |           |             |                                                                                                                                       |           |                                                                                                                    |
   |              |           |             |    Record set type: A                                                                                                                 |           |                                                                                                                    |
   |              |           |             |                                                                                                                                       |           |                                                                                                                    |
   |              |           |             |    Value: 192.168.2.5                                                                                                                 |           |                                                                                                                    |
   +--------------+-----------+-------------+---------------------------------------------------------------------------------------------------------------------------------------+-----------+--------------------------------------------------------------------------------------------------------------------+

Process for Configuring Private Zones
-------------------------------------

:ref:`Figure 2 <dns_bestprac_0002__f28bbf91c2c3e4b9c875c6375167fc7b1>` shows the process for configuring private zones.

.. _dns_bestprac_0002__f28bbf91c2c3e4b9c875c6375167fc7b1:

.. figure:: /_static/images/en-us_image_0173959206.png
   :alt: **Figure 2** Process for configuring private zones

   **Figure 2** Process for configuring private zones

Description:

#. (Optional) Create a VPC and a subnet on the VPC console. This operation is required when you are configuring private domain names for servers during website deployment.
#. Create private zones and associate them with the VPC and add a record set to each private zone on the DNS console.
#. (Optional) Change the DNS server addresses of the VPC subnet on the VPC console. This operation is required when you are configuring private domain names for servers where your website is running.

Procedure
---------

#. (Optional) Create a VPC and a subnet.

   Before configuring private domain names for the ECSs and databases required by your website, you need to create a VPC and a subnet.

   a. Log in to the management console.

   b. Click |image1| in the upper left corner and select the desired region and project.

   c. Choose **Network** > **Virtual Private Cloud**.

   d. In the navigation pane on the left, choose **Virtual Private Cloud**.

   e. Click **Create VPC** and configure the parameters based on :ref:`Table 3 <dns_bestprac_0002__table65603559163645>`.

      .. _dns_bestprac_0002__table65603559163645:

      .. table:: **Table 3** Parameters for creating a VPC

         +-----------------------------+--------------------------------------------------------------------------------------------------+-----------------------+
         | Parameter                   | Description                                                                                      | Example Value         |
         +=============================+==================================================================================================+=======================+
         | Region                      | Region of the VPC. For low network latency and quick resource access, select the nearest region. | eu-de                 |
         +-----------------------------+--------------------------------------------------------------------------------------------------+-----------------------+
         | Name                        | VPC name                                                                                         | VPC_001               |
         +-----------------------------+--------------------------------------------------------------------------------------------------+-----------------------+
         | CIDR Block                  | Network range of the VPC. All subnets must be within this range.                                 | 192.168.0.0/16        |
         |                             |                                                                                                  |                       |
         |                             | Choose one from the following CIDR blocks:                                                       |                       |
         |                             |                                                                                                  |                       |
         |                             | -  10.0.0.0/8-24                                                                                 |                       |
         |                             | -  172.16.0.0/12-24                                                                              |                       |
         |                             | -  192.168.0.0/16-24                                                                             |                       |
         +-----------------------------+--------------------------------------------------------------------------------------------------+-----------------------+
         | Name (default subnet)       | Subnet name                                                                                      | Subnet                |
         +-----------------------------+--------------------------------------------------------------------------------------------------+-----------------------+
         | CIDR Block (default subnet) | Network range of the subnet, which must be within the VPC                                        | 192.168.0.0/24        |
         +-----------------------------+--------------------------------------------------------------------------------------------------+-----------------------+
         | Gateway                     | Gateway address of the subnet                                                                    | 192.168.0.1           |
         +-----------------------------+--------------------------------------------------------------------------------------------------+-----------------------+
         | DNS Server Address          | Set the DNS server addresses of the VPC subnet to those provided by Open Teleom Cloud DNS.       | 100.125.1.250         |
         |                             |                                                                                                  |                       |
         |                             |                                                                                                  | 100.125.3.250         |
         +-----------------------------+--------------------------------------------------------------------------------------------------+-----------------------+

   f. Click **Create Now**.

#. Create private zones.

   Create private zones for the domain names used by ECS1 and RDS1.

   a. Choose **Network** > **Domain Name Service**.

      The DNS console is displayed.

   b. In the navigation pane on the left, choose **Private Zones**.

   c. .. _dns_bestprac_0002__en-us_topic_0035467699_li3668574216212:

      Click **Create Private Zone**.

   d. Configure the parameters based on :ref:`Table 4 <dns_bestprac_0002__en-us_topic_0035467699_table2052132816642>`.

      .. _dns_bestprac_0002__en-us_topic_0035467699_table2052132816642:

      .. table:: **Table 4** Parameters for creating a private zone

         +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
         | Parameter             | Description                                                                                                                                                                                                                                              | Example Value           |
         +=======================+==========================================================================================================================================================================================================================================================+=========================+
         | Name                  | Private domain name. You can customize any compliant domain names, even top-level ones.                                                                                                                                                                  | api.ecs.com             |
         +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
         | VPC                   | VPC to be associated with the private zone                                                                                                                                                                                                               | VPC_001                 |
         +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
         | Email                 | (Optional) Email address of the administrator managing the private zone. It is recommended that you set the email address to **HOSTMASTER@Domain name**.                                                                                                 | HOSTMASTER@ecs1.com     |
         |                       |                                                                                                                                                                                                                                                          |                         |
         |                       | For more details about the email address, see `Why Was the Email Address Format Changed in the SOA Record? <https://docs.otc.t-systems.com/domain-name-service/umn/faqs/dns_overview/why_was_the_email_address_format_changed_in_the_soa_record.html>`__ |                         |
         +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
         | Tag                   | (Optional) Identifier used to group and search for resources. A tag consists of a key and value. You can set tags when there are many zones in your account.                                                                                             | N/A                     |
         |                       |                                                                                                                                                                                                                                                          |                         |
         |                       | For details about tag key and value requirements, see :ref:`Table 5 <dns_bestprac_0002__table1393932617253>`.                                                                                                                                            |                         |
         +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+
         | Description           | (Optional) Description of a zone. The value cannot exceed 255 characters.                                                                                                                                                                                | This is a private zone. |
         +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------+

      .. _dns_bestprac_0002__table1393932617253:

      .. table:: **Table 5** Tag key and value requirements

         +-----------------------+--------------------------------------------------------------------------------+-----------------------+
         | Parameter             | Requirements                                                                   | Example Value         |
         +=======================+================================================================================+=======================+
         | Key                   | -  Cannot be left blank.                                                       | example_key1          |
         |                       | -  Must be unique for each resource.                                           |                       |
         |                       | -  Can contain a maximum of 36 characters.                                     |                       |
         |                       | -  Cannot start or end with a space or contain special characters ``=*<>\,|/`` |                       |
         +-----------------------+--------------------------------------------------------------------------------+-----------------------+
         | Value                 | -  Cannot be left blank.                                                       | example_value1        |
         |                       | -  Can contain a maximum of 43 characters.                                     |                       |
         |                       | -  Cannot start or end with a space or contain special characters ``=*<>\,|/`` |                       |
         +-----------------------+--------------------------------------------------------------------------------+-----------------------+

   e. .. _dns_bestprac_0002__en-us_topic_0035467699_li46536642161024:

      Click **OK**. Then check the private zone created for api.ecs.com.

      You can view details about this private zone on the **Private Zones** page.

      .. note::

         Click the domain name to view SOA and NS record sets automatically generated for the zone.

         -  The SOA record set identifies the base DNS information about the domain name.
         -  The NS record set defines authoritative DNS servers for the domain name.

   f. Repeat steps :ref:`3 <dns_bestprac_0002__en-us_topic_0035467699_li3668574216212>` to :ref:`5 <dns_bestprac_0002__en-us_topic_0035467699_li46536642161024>` to create a private zone for db.com.

      For details about private domain names, see :ref:`Table 1 <dns_bestprac_0002__table11364645122020>`.

3. Add a record set to each private zone.

   Add record sets to translate private domain names to private IP addresses of ECS1 and RDS1.

   a. .. _dns_bestprac_0002__en-us_topic_0035467699_li5958141402845:

      Click the domain name.

      The record set page is displayed.

   b. Click **Add Record Set**.

   c. Configure the parameters based on :ref:`Table 6 <dns_bestprac_0002__en-us_topic_0035467699_table6239446395216>`.

      .. _dns_bestprac_0002__en-us_topic_0035467699_table6239446395216:

      .. table:: **Table 6** Parameters for adding an A record set

         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
         | Parameter             | Description                                                                                                                                                        | Example Value                                   |
         +=======================+====================================================================================================================================================================+=================================================+
         | Name                  | Domain name prefix                                                                                                                                                 | N/A                                             |
         |                       |                                                                                                                                                                    |                                                 |
         |                       | If this parameter is left blank, the primary domain name is to be resolved, for example, api.ecs.com.                                                              |                                                 |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
         | Type                  | Type of the record set                                                                                                                                             | A - Map domains to IPv4 addresses               |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
         | TTL (s)               | Caching period of the record set on a DNS server                                                                                                                   | The default value is 300s, which is, 5 minutes. |
         |                       |                                                                                                                                                                    |                                                 |
         |                       | If your service address is frequently changed, set TTL to a small value.                                                                                           |                                                 |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
         | Value                 | IPv4 addresses mapped to the domain name. Every two IPv4 addresses are separated using a line break.                                                               | 192.168.2.8                                     |
         |                       |                                                                                                                                                                    |                                                 |
         |                       | Enter the private IP address of the ECS, for example, ECS1.                                                                                                        |                                                 |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
         | Tag                   | (Optional) Identifier used to group and search for resources. A tag consists of a key and value. You can set tags when there are many record sets in your account. | N/A                                             |
         |                       |                                                                                                                                                                    |                                                 |
         |                       | For details about tag key and value requirements, see :ref:`Table 5 <dns_bestprac_0002__table1393932617253>`.                                                      |                                                 |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+
         | Description           | (Optional) Description of the record set                                                                                                                           | N/A                                             |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------+

   d. .. _dns_bestprac_0002__en-us_topic_0035467699_li4923490010251:

      Click **OK**. An A record set is added for api.ecs.com.

   e. Repeat steps :ref:`1 <dns_bestprac_0002__en-us_topic_0035467699_li5958141402845>` to :ref:`4 <dns_bestprac_0002__en-us_topic_0035467699_li4923490010251>` to add an A record set for db.com.

      Set the record set value of **db.com** to **192.168.2.5**.

      For details, see :ref:`Table 2 <dns_bestprac_0002__table56883141317>`.

4. (Optional) Change the DNS server addresses of the VPC subnet.

   After you configure private domain names for nodes in the website application, you need to change the DNS servers of the VPC subnet to those provided by the DNS service so that the domain names can be resolved.

   For details, see `How Do I Change Default DNS Servers of an ECS to Huawei Cloud Private DNS Servers? <https://support.huaweicloud.com/intl/en-us/dns_faq/dns_faq_005.html>`__

5. Switch to the backup ECS.

   When ECS1 becomes faulty, you can switch services to ECS2 by changing the value of the record set added to private zone **api.ecs.com**.

   a. Log in to the management console.

   b. Click |image1| in the upper left and select **eu-de**.

   c. Choose **Network** > **Domain Name Service**.

      The DNS console is displayed.

   d. In the navigation pane on the left, choose **Private Zones**.

   e. In the private zone list, click the name of the zone **api.ecs.com**.

   f. Locate the A record set and click **Modify** under **Operation**.

   g. Change the value to **192.168.3.8**.

   h. Click **OK**.

   Traffic to ECS1 will be directed to ECS2 by the private DNS server.

.. |image1| image:: /_static/images/en-us_image_0131021386.png
.. |image2| image:: /_static/images/en-us_image_0000001343763404.png
