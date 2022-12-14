:original_name: dns_qs_0006.html

.. _dns_qs_0006:

Configuring a Private Zone
==========================

**Scenarios**
-------------

If you have deployed ECSs and other cloud services on the cloud, you can configure private domain names for the ECSs so that they can communicate using domain names within VPCs.

You can create any private zones for domain names that are unique within VPCs. You do not need to register the domain names.

This section describes how to configure a private zone for a private domain name and add an A record set.

**Prerequisites**
-----------------

You have created an ECS and obtained its VPC name and private IP address.

Process
-------

:ref:`Figure 1 <dns_qs_0006__f28bbf91c2c3e4b9c875c6375167fc7b1>` shows the process for configuring a private zone for a domain name.

.. _dns_qs_0006__f28bbf91c2c3e4b9c875c6375167fc7b1:

.. figure:: /_static/images/en-us_image_0202562548.png
   :alt: **Figure 1** Process for configuring a private zone

   **Figure 1** Process for configuring a private zone

Create a Private Zone
---------------------

Create a private zone to allow access to your ECS using a private domain name.

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane, choose **Private Zones**.

   The **Private Zones** page is displayed.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click **Create Private Zone**.

#. Set **Name** to **example.com** and select the VPC where the ECS resides.

   For details about more parameters, see :ref:`Creating a Private Zone <en-us_topic_0057773658>`.


   .. figure:: /_static/images/en-us_image_0000001124782805.png
      :alt: **Figure 2** Creating a private zone

      **Figure 2** Creating a private zone

#. Click **OK**.

#. Switch back to the **Private Zones** page.

   View the created private zone.

   .. note::

      Click the zone name to view zone details. You can view SOA and NS record sets automatically generated by the system.

      -  The SOA record set defines the DNS server that is the authoritative information source for a particular domain name.
      -  The NS record set defines authoritative DNS servers for a zone.

Add an A Record Set
-------------------

To access the ECS using example.com, add an A record set.

#. On the **Private Zones** page, click the name of the private zone you created.

   The **Record Sets** page is displayed.

#. Click **Add Record Set**.

#. Set the parameters as follows:

   -  **Name**: Leave this parameter blank. The system automatically considers example.com to be the name, and requests are routed to example.com.
   -  **Type**: Set it to **A - Map domains to IPv4 addresses**.
   -  **Value**: Enter the private IP address of the ECS.

   Retain the default values for other parameters. For details, see :ref:`Adding an A Record Set <dns_usermanual_0007>`.


   .. figure:: /_static/images/en-us_image_0000001124468095.png
      :alt: **Figure 3** Add Record Set

      **Figure 3** Add Record Set

#. Click **OK**.

#. Switch back to the **Record Sets** page.

   View the added record set in the record set list of the zone and ensure that the status of the record set is **Normal**.

(Optional) Configure DNS Servers for the VPC Subnet
---------------------------------------------------

To ensure that private domain names can be resolved in a VPC, change the DNS servers for the VPC subnet to those provided by the DNS service.

**Query the private DNS servers provided by the DNS service**

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane, choose **Private Zones**.

   The **Private Zones** page is displayed.

#. Click |image2| in the upper left corner and select the desired region and project.

#. In the private zone list, click the name of the zone and view the DNS servers.

**Change the DNS servers**

#. Go to the private zone list.

#. Click the VPC name under **Associated VPC**.

   On the VPC console, change the DNS servers of the VPC subnet.

   For details, see `Modifying a Subnet <https://docs.otc.t-systems.com/usermanual/vpc/vpc_vpc_0001.html>`__.

.. |image1| image:: /_static/images/en-us_image_0148391090.png
.. |image2| image:: /_static/images/en-us_image_0148391090.png
