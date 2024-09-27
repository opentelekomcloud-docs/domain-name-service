:original_name: dns_qs_0006.html

.. _dns_qs_0006:

Configuring a Private Zone
==========================

Scenario
--------

If you have deployed ECSs and other cloud services within VPCs, you can configure private domain names for the ECSs so that they can communicate with each other or access the cloud services over a private network.

You can create any private zones that are unique within VPCs. You do not need to register the domain names.

Prerequisites
-------------

You have created an ECS and obtained its VPC name and private IP address.

Process Flow
------------

:ref:`Figure 1 <dns_qs_0006__f28bbf91c2c3e4b9c875c6375167fc7b1>` shows the process of configuring a private zone for routing traffic within VPCs.

.. _dns_qs_0006__f28bbf91c2c3e4b9c875c6375167fc7b1:

.. figure:: /_static/images/en-us_image_0000001906813850.png
   :alt: **Figure 1** Configuring a private zone for routing traffic within VPCs

   **Figure 1** Configuring a private zone for routing traffic within VPCs

.. note::

   To ensure that the private domain name can be resolved in the associated VPC, verify that the DNS server addresses for the VPC subnet are those provided by the DNS service. If the DNS server addresses are not those provided by the DNS service, change them.

   You can also :ref:`change the DNS server addresses of the VPC subnet <dns_qs_0006__li05488293265>` where the domain name is used.

Creating a Private Zone
-----------------------

#. Create a private zone.

   Create a private zone to allow access to your ECS using a private domain name example.com.

   a. Log in to the management console.

   b. In the service list, choose **Network** > **Domain Name Service**.

      The DNS console is displayed.

   c. In the navigation pane on the left, choose **Private Zones**.

      The **Private Zones** page is displayed.

   d. Click |image1| in the upper left corner and select the desired region and project.

   e. Click **Create Private Zone**.

   f. Set **Domain Name** to **example.com** and select the VPC where the ECS resides.

      Set other parameters by referring to :ref:`Creating a Private Zone <en-us_topic_0057773658>`.


      .. figure:: /_static/images/en-us_image_0000001906813838.png
         :alt: **Figure 2** Creating a private zone

         **Figure 2** Creating a private zone

   g. Click **OK**.

   h. Switch back to the **Private Zones** page.

      You can view the created private zone in the private zone list.

      .. note::

         Click the domain name to view SOA and NS record sets automatically generated for the zone.

         -  .. _dns_qs_0006__li27116903191010:

            The start of authority (SOA) record includes administrative information about your zone, as defined by the Domain Name System (DNS).

         -  The NS record set defines the authoritative DNS servers for the domain name.

#. Add an A record set to the domain name.

   To access the ECS using example.com, add an A record set.

   a. On the **Private Zones** page, click the domain name of the private zone you created.

      The **Record Sets** page is displayed.

   b. Click **Add Record Set**.

   c. Configure the parameters as follows:

      -  **Name**: Leave this parameter blank. The DNS service automatically considers example.com as the name, and requests are routed to example.com.
      -  **Type**: Retain the default setting **A - Map domains to IPv4 addresses**.
      -  **Value**: Enter the private IP address of the ECS.

      Configure other parameters by referring to :ref:`Adding an A Record Set <dns_usermanual_0007>`.


      .. figure:: /_static/images/en-us_image_0000001942373065.png
         :alt: **Figure 3** Add Record Set

         **Figure 3** Add Record Set

   d. Click **OK**.

   e. Switch back to the **Record Sets** tab.

      The added record set is in the **Normal** state.

#. .. _dns_qs_0006__li05488293265:

   Change the DNS server addresses of the VPC subnet.

   To ensure that the private domain name can be resolved in the associated VPC, verify that the DNS server addresses for the VPC subnet are those provided by the DNS service. If the DNS server addresses are not those provided by the DNS service, change them.

   **Query the private DNS server addresses provided by the DNS service.**

   a. Log in to the management console.

   b. In the service list, choose **Network** > **Domain Name Service**.

      The DNS console is displayed.

   c. In the navigation pane on the left, choose **Private Zones**.

      The **Private Zones** page is displayed.

   d. Click |image2| in the upper left corner and select the desired region and project.

   e. In the private zone list, click the domain name of the zone and view the DNS server addresses.

   **Change the DNS server addresses.**

   a. Go to the private zone list.

   b. Click the VPC name under **Associated VPC**.

      On the VPC console, change the DNS server addresses for the VPC subnet.

      For details, see `Modifying a Subnet <https://docs.otc.t-systems.com/usermanual/vpc/vpc_vpc_0001.html>`__.

.. |image1| image:: /_static/images/en-us_image_0000001906973766.png
.. |image2| image:: /_static/images/en-us_image_0000001906973766.png
