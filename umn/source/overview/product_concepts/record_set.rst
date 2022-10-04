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

   +-----------------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | Type                  | Where to Use             | Usage                                                                                                                                      |
   +=======================+==========================+============================================================================================================================================+
   | A                     | Public and private zones | Maps domains to IPv4 addresses.                                                                                                            |
   +-----------------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | CNAME                 | Public and private zones | Maps one domain name to another or multiple domain names to one domain name.                                                               |
   +-----------------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | MX                    | Public and private zones | Maps domain names to email servers.                                                                                                        |
   +-----------------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | AAAA                  | Public and private zones | Maps domain names to IPv6 addresses.                                                                                                       |
   +-----------------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | TXT                   | Public and private zones | Specifies text records. TXT record sets are usually used in the following scenarios:                                                       |
   |                       |                          |                                                                                                                                            |
   |                       |                          | -  To record DKIM public keys to prevent email fraud.                                                                                      |
   |                       |                          | -  To record the identity of domain name owners to facilitate domain name retrieval.                                                       |
   +-----------------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | SRV                   | Public and private zones | Records servers providing specific services.                                                                                               |
   +-----------------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | NS                    | Public and private zones | Delegates subdomains to other name servers.                                                                                                |
   |                       |                          |                                                                                                                                            |
   |                       |                          | -  For public zones, an NS record set is automatically created, and you can add NS records for subdomains.                                 |
   |                       |                          | -  For private zones, an NS record set is automatically created, and you cannot add other NS record sets.                                  |
   +-----------------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | SOA                   | Public and private zones | Specifies the master authoritative DNS server for a domain name. The SOA record set is created by the system and cannot be added manually. |
   +-----------------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | CAA                   | Public zone              | Grants certificate issuing permissions to CAs. CAA record sets can be used to prevent the issuance of unauthorized HTTPS certificates.     |
   +-----------------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | PTR                   | Private zone             | Maps IP addresses to domain names.                                                                                                         |
   +-----------------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+

Usage
-----

Record sets are used in following scenarios:

-  Website domain name resolution

   A and AAAA record sets are usually used to build websites. They translate domain names into IP addresses.


   .. figure:: /_static/images/en-us_image_0201534885.png
      :alt: **Figure 1** Website domain name resolution


      **Figure 1** Website domain name resolution

-  Private domain name resolution

   On a private network, A and AAAA record sets translate private domain names into private IP addresses.


   .. figure:: /_static/images/en-us_image_0201578061.png
      :alt: **Figure 2** Private domain name resolution


      **Figure 2** Private domain name resolution

-  Email domain name resolution

   MX, CNAME, and TXT record sets are usually used for email services.


   .. figure:: /_static/images/en-us_image_0201534900.png
      :alt: **Figure 3** Email domain name resolution


      **Figure 3** Email domain name resolution

-  Reverse resolution on a private network

   You can use PTR records to translate private IP addresses into private domain names.


   .. figure:: /_static/images/en-us_image_0201534953.png
      :alt: **Figure 4** Reverse resolution on a private network


      **Figure 4** Reverse resolution on a private network

Helpful Links
-------------

For details, see :ref:`Overview <dns_usermanual_0035>`.
