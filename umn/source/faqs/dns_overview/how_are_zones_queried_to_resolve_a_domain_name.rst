:original_name: dns_faq_011.html

.. _dns_faq_011:

How Are Zones Queried to Resolve a Domain Name?
===============================================

When a domain name resolution request is initiated, a matched subdomain is first queried.

-  If a zone is created for the subdomain, the system returns the result based on the zone configuration.
-  If a zone is not created for the subdomain, the system queries the domain name in the zone created for the domain name.

For example, suppose you have created one zone named **example.com** and added an A record set to it, with the **Name** field set to **www**, and you have also created another zone named **www.example.com** but have not added an A record set to this zone.

If a visitor accesses www.example.com, the domain name is first queried in the zone named **www.example.com**. However, no result will be returned because no record sets have been added to the zone.
