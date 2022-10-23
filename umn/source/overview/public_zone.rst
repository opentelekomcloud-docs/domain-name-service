:original_name: en-us_topic_0035920135.html

.. _en-us_topic_0035920135:

Public Zone
===========

What Is a Public Zone?
----------------------

A public zone contains information about how domain names are translated into IP addresses for routing traffic over the Internet. Your users can access your website or mailbox by using a domain name.

Accessing a Website Using a Domain Name
---------------------------------------

A domain name is required if you expect that your website is accessible on the Internet. To route traffic for the domain name, you must complete the following steps:

#. Register the domain name that your users can use to access your website.

#. Set up your website.

   You may need to purchase cloud resources.

#. Configure the DNS service to route Internet traffic for your domain name.

   Create a public zone to host the domain name on the DNS service and add record sets to map the domain name to the EIP bound to the web server where the website is deployed.

   For details, see :ref:`Routing Internet Traffic to a Website <en-us_topic_0035467699>`.

After you finish the above steps, end users will be able to access your website on the Internet with the registered domain name and its subdomains.


.. figure:: /_static/images/en-us_image_0221355590.png
   :alt: **Figure 1** How DNS routes Internet traffic to a website

   **Figure 1** How DNS routes Internet traffic to a website

-  Phase 1 shows how DNS resolves your domain name.
-  Phase 2 shows how a user accesses your website using your domain name.

Public domain name resolution depends on the DNS hierarchy. The following describes the hierarchies of domain names and how domain names are resolved.

DNS Hierarchy
-------------

Domain names are hierarchical, and domain resolution is a recursive lookup process. The following uses example.com to describe the hierarchies of domain names.

-  Root domain

   A dot (.) is the designation for the root domain.

   A fully qualified domain name (FQDN) ends with a dot (example.com.). When you enter a domain name (example.com) in the browser, the DNS system will automatically add a dot in the end.

   Root domain names are resolved by root DNS servers that hold the addresses of top-level DNS servers.

-  Top-level domain

   Below the root domain are top-level domains, which are categorized into two types:

   -  Generic top-level domain (gTLD), such as .com, .net, .org, and .top
   -  Country code top-level domain (ccTLD), such as .cn, .uk, and .de

   Top-level domains are resolved by top-level DNS servers that hold the addresses of second-level DNS servers. For example, the top-level DNS server of .com saves the addresses of all DNS servers of second-level domain names that end with .com.

-  Second-level domain

   Second-level domains (such as example.com) are subdomains of top-level domains and are resolved by second-level DNS servers, which provide authoritative domain name resolution services.

   For example, if you purchase example.com from a domain name registrar and set a DNS server for the domain name, the DNS server will provide authoritative resolution for example.com, and its address will be recorded by all top-level DNS servers.

   If you host domain names on the DNS service, authoritative DNS servers will be provided for your domain names.

Domain Name Resolution
----------------------

:ref:`Figure 2 <en-us_topic_0035920135__fig198648428615>` shows the process for accessing a website using the domain name www.example.com.

.. _en-us_topic_0035920135__fig198648428615:

.. figure:: /_static/images/en-us_image_0168004604.png
   :alt: **Figure 2** Domain name resolution

   **Figure 2** Domain name resolution

#. A user enters **www.example.com** in the address box of the browser.

#. The request for querying domain name www.example.com is then sent to the local DNS server.

   Local DNS servers are usually provided by the Internet service provider to cache domain name information and perform recursive lookup.

#. If the local DNS server does not find any records in the cache, it routes the request for www.example.com to the root DNS server.

#. The root DNS server returns the DNS server address of .com (because the domain name suffix is .com) to the local DNS server.

#. The local DNS server sends the query request to the DNS server of .com.

#. The .com DNS server returns the address of the second-level DNS server which provides authoritative records for example.com.

#. The local DNS server sends the request to the DNS server of example.com.

   If you have hosted www.example.com on the DNS service and set its DNS servers to the DNS servers provided by the DNS service, these DNS servers will provide authoritative records for the domain name.

#. The second-level DNS server returns the IP address mapped to www.example.com to the local DNS server.

#. The local DNS server returns the IP address to the web browser.

#. The web browser accesses the website server with the IP address.

#. The website server returns the web page to the browser.

#. The user views the web page using the browser.

For details, see :ref:`Routing Internet Traffic to a Website <en-us_topic_0035467699>`.
