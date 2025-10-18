:original_name: dns_usermanual_05046.html

.. _dns_usermanual_05046:

Configuring Recursive Resolution for Subdomains
===============================================

Scenarios
---------

The recursive resolution proxy function can be configured for private zones.

If you select this option, when you query subdomains that are not configured in the zone namespace, DNS will recursively resolve the subdomains on the Internet and use the result from authoritative DNS servers.

Recursive Resolution Example of a Subdomain in a Private Zone
-------------------------------------------------------------

For example.com, the following record sets have been added to the private zone:

.. table:: **Table 1** Record sets

   ==== ==== =======
   Name Type Value
   ==== ==== =======
   a1   A    1.2.3.4
   ==== ==== =======

When you access a1.example.com, the DNS server returns 1.2.3.4 based on the configured private zone record set.

When you access www.example.com, no record sets are configured in the private zone. In this case, the authoritative DNS server resolves the domain name and returns the result.

Enabling Recursive Resolution for Subdomains
--------------------------------------------

You can enable recursive subdomain resolution when creating or modifying a private zone.

-  **Enabling recursive subdomain resolution when creating a private zone**

   When you are creating a private zone, select **Recursive subdomain resolution proxy** to enable recursive subdomain resolution. For details about how to create a private zone, see :ref:`Creating a Private Zone <en-us_topic_0057773658>`.

-  **Enabling or disabling recursive subdomain resolution when modifying a private zone**

   When you are modifying a private zone, select or deselect **Recursive subdomain resolution proxy** to enable or disable recursive subdomain resolution. For details about how to modify a private zone, see :ref:`Managing Private Zones <dns_usermanual_0033>`.
