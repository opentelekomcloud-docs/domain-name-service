:original_name: en-us_topic_0035467691.html

.. _en-us_topic_0035467691:

What Is DNS?
============

Domain Name Service (DNS) is a highly available and scalable authoritative Domain Name System (DNS) web service that translates domain names (such as www.example.com) into IP addresses (such as 192.1.2.3) required for network connection. The DNS service allows end users to visit your websites or web applications with domain names.

Basic Functions
---------------

The DNS service provides the following functions:

-  :ref:`Public domain name resolution <en-us_topic_0035920135>`

   Maps domain names to public IP addresses so that end users can access your website or web applications over the Internet.

-  :ref:`Private domain name resolution <dns_pd_0005>`

   Translates private domain names into private IP addresses to facilitate access to cloud resources within VPCs.

-  :ref:`Reverse resolution <dns_pd_0006>`

   Obtains a domain name based on an IP address. Reverse resolution, or reverse DNS lookup, is typically used to affirm the credibility of email servers.

Product Advantages
------------------

The DNS service has the following advantages:

-  High performance

   A single DNS node can handle millions of concurrent queries, allowing end users to access your website or application much faster.

-  Easy access to cloud resources

   Your ECSs can communicate with each other and with other resources within VPCs using private domain names. Traffic is kept within your internal network, which reduces network latency and improves security.

-  Isolation of core data

   A private DNS server provides domain name resolution for ECSs carrying core data, enabling secure, controlled access to such data. You do not need to bind EIPs to these ECSs.

Accessing the DNS Service
-------------------------

The cloud platform provides a web-based management console as well as REST APIs through which you can access the DNS service.

-  Management console

   A web-based management console enables you to access the DNS service.

   With a few steps, you can start using the DNS service for domain name resolution.

-  APIs

   REST APIs are provided for accessing the DNS service. You can also use the provided APIs to integrate DNS into a third-party system for secondary development. For details, see the `Domain Name Service API Reference <https://docs.otc.t-systems.com/en-us/api/dns/dns_api_50000.html>`__.
