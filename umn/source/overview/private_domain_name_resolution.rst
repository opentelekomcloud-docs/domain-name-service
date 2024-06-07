:original_name: dns_pd_0005.html

.. _dns_pd_0005:

Private Domain Name Resolution
==============================

Private Zone
------------

A private zone contains information about how to map a domain name (such as ecs.com) and its subdomains used within one or more VPCs to private IP addresses (such as 192.168.1.1). With private domain names, your ECSs can communicate with each other within a VPC without having to connect to the Internet. These ECSs can also access cloud services, such as OBS and SMN, over a private network.

:ref:`Figure 1 <dns_pd_0005__fig9226124091216>` shows how a private domain name is resolved by a private DNS server.

.. _dns_pd_0005__fig9226124091216:

.. figure:: /_static/images/en-us_image_0000001906813614.png
   :alt: **Figure 1** Process for resolving a private domain name

   **Figure 1** Process for resolving a private domain name

When an ECS in the VPC requests to access a private domain name, the private DNS server directly returns a private IP address mapped to the domain name.

Private zones allow you to:

-  Flexibly customize private domain names in your VPCs.
-  Associate one or more multiple VPCs with one domain name.
-  Use private DNS servers to prevent DNS spoofing and quickly respond to requests for accessing ECSs in VPCs as well as OBS and SMN resources.

You can use private domain names in the following scenarios:

-  :ref:`Managing ECS Host Names <dns_pd_0005__section147015342425>`
-  :ref:`Keeping Your Website Up and Running Even While Your Server Is Being Replaced <dns_pd_0005__section2827056164219>`
-  :ref:`Accessing Cloud Resources <dns_pd_0005__section1567083834313>`

.. _dns_pd_0005__section147015342425:

Managing ECS Host Names
-----------------------

You can plan host names based on the locations, usages, and account information of ECSs, and map the host names to private IP addresses, helping you manage ECSs more easily.

For example, if you have deployed 20 ECSs in an AZ, 10 for website A and 10 for website B, you can plan their host names (private domain names) as follows:

-  ECSs for website A: weba01.region1.az1.com - weba10.region1.az1.com
-  ECSs for website B: webb01.region1.az1.com - webb10.region1.az1.com

After you configure the host names, you will be able to quickly determine the locations and usages of ECSs during routine management and maintenance.

See :ref:`Configuring a Private Zone <dns_qs_0006>` for detailed operations.

.. _dns_pd_0005__section2827056164219:

Keeping Your Website Up and Running Even While Your Server Is Being Replaced
----------------------------------------------------------------------------

As the number of Internet users is continuously increasing, a website or web application deployed on a single server can hardly handle concurrent requests during peak hours. A common practice is to deploy the website or application on multiple servers and distribute the load across the servers.

These servers are in the same VPC and communicate with each other using private IP addresses that are coded into internal APIs called among the servers. If one of these servers is replaced, its private IP address changes. As a result, you need to change this IP address in the APIs and re-publish the website. This poses challenges for system maintenance.

If you create a private zone for each server and configure record sets to map their private domain names to the private IP addresses, they will be able to communicate using private domain names. When you replace any of the servers, you only need to change the private IP address in the record set, instead of modifying the code.

:ref:`Figure 2 <dns_pd_0005__fig8326104683415>` illustrates such use of private domain name resolution.

.. _dns_pd_0005__fig8326104683415:

.. figure:: /_static/images/en-us_image_0000001906973542.png
   :alt: **Figure 2** Configuring private DNS for cloud servers

   **Figure 2** Configuring private DNS for cloud servers

The ECSs and RDS instances are in the same VPC.

-  ECS0: primary service node
-  ECS1: public service node
-  RDS1: service database
-  ECS2 and RDS2: backup service node and backup database

When ECS1 becomes faulty, ECS2 must take over. However, if no private zones are configured for the two ECSs, you need to change the private IP addresses in the code for ECS0. This will interrupt services, and you will need to publish the website again.

Now assume that you have configured private zones for the ECSs and have included their private names in the code. If ECS1 becomes faulty, you only need to change the DNS records to direct traffic to ECS2. Services are not interrupted, and you do not need to publish the website again.

.. _dns_pd_0005__section1567083834313:

Accessing Cloud Resources
-------------------------

Configure private domain names for ECSs so that they can access other cloud services, such as SMN and OBS, without connecting to the Internet.

When you create an ECS, note the following:

-  If a public DNS server is configured for the VPC subnet where the ECS resides, requests to access cloud services will be routed over the Internet.

   :ref:`Figure 3 <dns_pd_0005__fig42701320112215>` shows the process for resolving a domain name when an ECS accesses cloud services such as OBS and SMN.

   Requests are routed over the Internet, resulting in an increase in network latency.

-  If a private DNS server is configured for the subnet, the private DNS server directly processes the requests to access cloud services.

   When the ECS accesses the cloud services, the private DNS server returns their private IP addresses, instead of routing requests over the Internet. This reduces network latency and improves access speed. Steps 1 to 4 on the left of :ref:`Figure 3 <dns_pd_0005__fig42701320112215>` shows the process.

.. _dns_pd_0005__fig42701320112215:

.. figure:: /_static/images/en-us_image_0000001942372841.png
   :alt: **Figure 3** Accessing cloud services

   **Figure 3** Accessing cloud services
