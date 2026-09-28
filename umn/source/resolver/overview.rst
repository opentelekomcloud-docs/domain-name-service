:original_name: dns_usermanual_1030.html

.. _dns_usermanual_1030:

Overview
========

What Is a Resolver?
-------------------

DNS Resolver answers DNS queries to and from your on-premises data center after your data center is connected to the cloud over Direct Connect or VPN.

Generally, on-premises data centers can access cloud resources over a Direct Connect or VPN connection. However, for security purposes, on-premises servers are not allowed to access the DNS service on the cloud directly. If your on-premises servers need to access private domain names used within VPCs, or your cloud servers use private DNS to access an on-premises domain name, you need to set up DNS on your cloud servers for forwarding DNS queries between the cloud DNS and on-premises DNS. This increases management and maintenance costs and causes reliability risks.

Generally, cloud vendors use IP addresses starting with 100 for their cloud services and IP addresses starting with 10, 172, and 192 for compute resources. When a customer's on-premises network connects to multiple cloud vendor networks, there may be IP address conflicts. If an on-premises resource or a third-party cloud service also uses IP addresses starting with 100, it is necessary to add an exact route for each of such IP addresses on the on-premises network or third-party cloud network to prevent route conflicts. This significantly increases the maintenance workload. If there are IP address conflicts, the routes cannot be configured.

DNS Resolver translates IP addresses starting with 100 to private IP addresses used in VPCs. On-premises resources can directly access the private IP addresses used in VPCs, and they do not need to access IP addresses starting with 100, which greatly simplifies the networking architecture. If a customer uses Direct Connect or VPN to set up a hybrid cloud, they only need to create inbound and outbound endpoints and associate VPCs with these endpoints to resolve DNS queries between the on-premises network and VPCs. If a third-party cloud DNS requires access to a domain name hosted on a cloud, inbound endpoints allow DNS queries to the VPCs from that third-party cloud. Conversely, if a VM on the cloud seeks to access a third-party domain name, an outbound endpoint with rules configured can forward DNS queries to the on-premises network or that third-party cloud. In this way, on-premises and cloud services can easily communicate with each other in hybrid cloud scenarios.


.. figure:: /_static/images/en-us_image_0000002419406753.png
   :alt: **Figure 1** Networking of DNS Resolver

   **Figure 1** Networking of DNS Resolver

Notes and Constraints
---------------------

-  Both inbound and outbound endpoints do not support DNSSEC.
-  By default, cloud servers use private DNS for domain name resolution. Do not change private DNS addresses. Otherwise, forwarding rules will not take effect.

Where to Use
------------

-  On-premises servers access a cloud service domain name. For this to work, you need to create an inbound endpoint and configure forwarding rules on the on-premises DNS servers to forward the DNS queries for the cloud service domain name to the IP addresses specified the inbound endpoint.

   For details, see :ref:`Managing Inbound Endpoints <dns_usermanual_1032>`.

-  Cloud servers access an on-premises domain name. For this to work, you need to create an outbound endpoint, configure endpoint rules, and specify the on-premises domain name to be accessed and the IP addresses of on-premises DNS servers. Private DNS then forwards the DNS queries for the on-premises domain name to the on-premises DNS servers based on the endpoint rules.

   For details, see :ref:`Managing Outbound Endpoints <dns_usermanual_1031>`.
