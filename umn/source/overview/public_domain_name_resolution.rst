:original_name: en-us_topic_0035920135.html

.. _en-us_topic_0035920135:

Public Domain Name Resolution
=============================

Public Zone
-----------

A public zone contains information about how a domain name and its subdomains are translated into IP addresses for routing traffic over the Internet. Public zones allow end users to access your website or application over the Internet using your domain name.

Accessing a Website Using a Domain Name
---------------------------------------

To make your website accessible on the Internet through a domain name, perform the following steps:

#. Register your domain name with a domain name registrar so that end users can use the domain name to access your website.

#. Set up your website.

   Purchase cloud resources.

#. Configure the DNS service to route Internet traffic for your domain name.

   Create a public zone to host the domain name on the DNS service and add a record set to map the domain name to the EIP of the server where the website is set up.

   For details, see :ref:`Configuring a Public Zone <en-us_topic_0035467699>`.

After you finish the above steps, end users will be able to access your website over the Internet with the registered domain name and its subdomains.


.. figure:: /_static/images/en-us_image_0000001906973482.png
   :alt: **Figure 1** How DNS routes Internet traffic to a website

   **Figure 1** How DNS routes Internet traffic to a website

-  Phase 1 shows how DNS resolves your domain name.
-  Phase 2 shows how the web page is returned to the user.

Public domain name resolution depends on the DNS hierarchy. The following describes the hierarchies of domain names and how domain names are resolved.

DNS Hierarchy
-------------

Domain names are hierarchical, and domain name resolution is a recursive lookup process. The following uses example.com to describe the hierarchies in domain names.

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

   If you host domain names on the DNS service, authoritative DNS servers will be provided for the domain names.

Domain Name Resolution
----------------------

:ref:`Figure 2 <en-us_topic_0035920135__fig8980728155012>` shows the process for accessing a website using the domain name www.example.com.

.. _en-us_topic_0035920135__fig8980728155012:

.. figure:: /_static/images/en-us_image_0000001942372793.png
   :alt: **Figure 2** Domain name resolution

   **Figure 2** Domain name resolution

#. An end user enters **www.example.com** in the address box of a browser.

#. The request for querying domain name www.example.com is routed to the local DNS server.

   Local DNS servers are usually provided by the Internet service provider to cache domain name information and perform recursive lookup.

#. If the local DNS server does not find any records in the cache, it routes the request for www.example.com to the root DNS server.

#. The root DNS server returns the DNS server address of .com (because the domain name suffix is .com) to the local DNS server.

#. The local DNS server sends the request to the top-level DNS server of .com.

#. The top-level DNS server of .com returns the address of the authoritative DNS server which provides authoritative records for example.com.

#. The local DNS server sends the request to the authoritative DNS server of example.com.

   If you have hosted www.example.com on the DNS service and configure the name servers provided by the DNS service, these name servers will provide authoritative DNS for the domain name.

#. The authoritative DNS server returns the IP address mapped to www.example.com to the local DNS server.

#. The local DNS server returns the IP address to the web browser.

#. The web browser accesses the web server with the IP address.

#. The web server returns the web page to the browser.

#. The end user views the web page using the browser.

For details, see :ref:`Configuring a Public Zone <en-us_topic_0035467699>`.
