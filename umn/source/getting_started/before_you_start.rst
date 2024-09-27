:original_name: dns_qs_0001.html

.. _dns_qs_0001:

Before You Start
================

DNS provides a set of functions for different scenarios.

When DNS Is Required
--------------------

You can select a type of function based on :ref:`Table 1 <dns_qs_0001__table977612405507>` to suit your network scenario.

.. _dns_qs_0001__table977612405507:

.. table:: **Table 1** Scenarios where DNS is required

   +--------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------+
   | Function                       | Scenario                                                                                                                                                           | Reference                                                 |
   +================================+====================================================================================================================================================================+===========================================================+
   | Public domain name resolution  | Domain names are mapped to the public IP addresses of web servers or web applications on the Internet so that end users are routed to your website or application. | :ref:`Configuring a Public Zone <en-us_topic_0035467699>` |
   +--------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------+
   | Private domain name resolution | Domain names are mapped to the private IP addresses within the VPCs for accessing cloud resources or cloud services over a private network.                        | :ref:`Configuring a Private Zone <dns_qs_0006>`           |
   +--------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------+
   | Reverse resolution             | EIPs are mapped to domain names, which is often used by email servers against spammers.                                                                            | :ref:`Configuring a PTR Record <en-us_topic_0040322596>`  |
   +--------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------+
