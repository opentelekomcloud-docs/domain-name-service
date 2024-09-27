:original_name: en-us_topic_0035467692.html

.. _en-us_topic_0035467692:

Record Set
==========

Overview
--------

A record set is a collection of resource records that belong to the same domain name. A record set defines DNS record types and values.

If you have created a zone on the DNS console, you can create record sets to expand the domain name or record its detailed information.

:ref:`Table 1 <en-us_topic_0035467692__table352893684543>` describes the record set types and their application scenarios.

.. _en-us_topic_0035467692__table352893684543:

.. table:: **Table 1** Record set usages

   +-----------------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Type                  | Where to Use             | Description                                                                                                                                         |
   +=======================+==========================+=====================================================================================================================================================+
   | A                     | Public and private zones | Maps domains to IPv4 addresses.                                                                                                                     |
   +-----------------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | CNAME                 | Public and private zones | Maps one domain name to another domain name or multiple domain names to one domain name.                                                            |
   +-----------------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | MX                    | Public and private zones | Maps domain names to email servers.                                                                                                                 |
   +-----------------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | AAAA                  | Public and private zones | Maps domain names to IPv6 addresses.                                                                                                                |
   +-----------------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | TXT                   | Public and private zones | TXT record sets are usually used to record the following:                                                                                           |
   |                       |                          |                                                                                                                                                     |
   |                       |                          | -  DKIM public keys to prevent email fraud                                                                                                          |
   |                       |                          | -  The identity of domain name owners to facilitate domain name retrieval                                                                           |
   +-----------------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | SRV                   | Public and private zones | Records servers providing specific services.                                                                                                        |
   +-----------------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | NS                    | Public and private zones | Delegates subdomains to other name servers.                                                                                                         |
   |                       |                          |                                                                                                                                                     |
   |                       |                          | -  For public zones, an NS record set is automatically created, and you can add NS record sets for subdomains.                                      |
   |                       |                          | -  For private zones, an NS record set is automatically created, and you cannot add other NS record sets.                                           |
   +-----------------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | SOA                   | Public and private zones | Identifies the base information about a domain name. The SOA record set is automatically generated by the DNS service and cannot be added manually. |
   +-----------------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | CAA                   | Public zone              | Grants certificate issuing permissions to CAs. CAA record sets can prevent the issuance of unauthorized HTTPS certificates.                         |
   +-----------------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | PTR                   | Public and private zones | Maps IP addresses to domain names.                                                                                                                  |
   +-----------------------+--------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

Usage
-----

Record sets are used in following scenarios:

-  Routing Internet traffic to a website

   A and AAAA record sets are usually used to map domain names used by websites to IPv4 or IPv6 addresses of web servers where the websites are deployed.


   .. figure:: /_static/images/en-us_image_0000001942372585.png
      :alt: **Figure 1** Accessing a website over the Internet using domain name

      **Figure 1** Accessing a website over the Internet using domain name

-  Private domain name resolution

   On a private network, A and AAAA record sets translate private domain names into private IP addresses.


   .. figure:: /_static/images/en-us_image_0000001906653348.png
      :alt: **Figure 2** Private domain name resolution

      **Figure 2** Private domain name resolution

-  Email domain name resolution

   MX, CNAME, and TXT record sets are usually used for email services.


   .. figure:: /_static/images/en-us_image_0000001906813264.png
      :alt: **Figure 3** Email domain name resolution

      **Figure 3** Email domain name resolution

-  Reverse resolution on a private network

   PTR records translate private IP addresses into private domain names.


   .. figure:: /_static/images/en-us_image_0000001942372581.png
      :alt: **Figure 4** Reverse resolution on a private network

      **Figure 4** Reverse resolution on a private network

Helpful Links
-------------

For details, see :ref:`Record Set Overview <dns_usermanual_0035>`.
