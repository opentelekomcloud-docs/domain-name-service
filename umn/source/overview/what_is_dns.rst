:original_name: en-us_topic_0035467691.html

.. _en-us_topic_0035467691:

What Is DNS?
============

Domain Name Service (DNS) is a highly available and scalable authoritative DNS service that translates domain names (such as www.example.com) into IP addresses (such as 192.1.2.3) required for network connection. The DNS service allows users to visit your websites or web applications with domain names.

Basic Functions
---------------

The DNS service provides the following functions:

-  :ref:`Public zone <en-us_topic_0035920135>`

   Maps domain names to public IP addresses so that your users can access your website or web applications over the Internet.

-  :ref:`Private zone <dns_pd_0005>`

   Translates private domain names into private IP addresses to facilitate access to cloud resources within VPCs.

-  :ref:`Reverse resolution <dns_pd_0006>`

   Obtains a domain name based on an IP address. Reverse resolution is typically used to improve credibility of email servers.

Product Advantages
------------------

The DNS service has the following advantages:

-  High performance

   DNS can handle millions of concurrent queries on a single node, allowing your end users to quickly access the closest application endpoints that are healthy.

-  Easy access to cloud resources

   You can host private domain names so that your ECSs can communicate with each other or with resources within VPCs using private domain names. Traffic is not directed to the Internet, and this reduces network latency and improves security.

-  Isolation of core data

   A private DNS server provides domain name resolution for ECSs carrying core data, enabling communications while safeguarding the core data. You do not need to bind EIPs to these ECSs.

How to Access
-------------

The cloud platform provides a web-based management console and REST APIs through which you can access the DNS service.

-  Management console

   A web-based management console enables you to access the DNS service.

   With a few steps, you can start using the DNS service for domain name resolution.

-  APIs

   REST APIs are provided for accessing the DNS service. You can also use the provided APIs to integrate DNS into a third-party system for secondary development. For details, see the `Domain Name Service API Reference <https://docs.otc.t-systems.com/en-us/api/dns/dns_api_50000.html>`__.
