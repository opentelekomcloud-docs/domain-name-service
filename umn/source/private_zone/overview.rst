:original_name: dns_usermanual_0032.html

.. _dns_usermanual_0032:

Overview
========

Private zones provide configurations for private domain names that are only applicable within VPCs, and they map private domain names to private IP addresses and resolve domain names within VPCs.

-  You can create any domain names without registering them.
-  One private zone can be associated with multiple VPCs, and domain names are valid only in VPCs.

To use private domain names, you must first create a private zone and associate VPCs with it.

This chapter describes how to create and manage private zones.

.. table:: **Table 1** Private zone operations

   +-----------------------------------------------------------------------+------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | Operation                                                             | Description                              | Constraint                                                                                                                       |
   +=======================================================================+==========================================+==================================================================================================================================+
   | :ref:`Creating a Private Zone <en-us_topic_0057773658>`               | Create a zone for your domain name.      | -  Private zones are project-level resources. When you create a private zone, select a region and project.                       |
   |                                                                       |                                          | -  Each account can create a maximum of 50 private zones.                                                                        |
   |                                                                       |                                          | -  Private domain names must meet the following requirements:                                                                    |
   |                                                                       |                                          |                                                                                                                                  |
   |                                                                       |                                          |    -  Domain name labels are separated by dot (.), and each label does not exceed 63 characters.                                 |
   |                                                                       |                                          |    -  A domain name label can contain letters, digits, and hyphens (-) and cannot start or end with a hyphen.                    |
   |                                                                       |                                          |    -  The total length of a domain name cannot exceed 254 characters.                                                            |
   +-----------------------------------------------------------------------+------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Managing Private Zones <dns_usermanual_0033>`                   | Modify, delete, and query private zones. | -  The name of a private zone cannot be modified after the zone is created.                                                      |
   |                                                                       |                                          | -  After a private zone is deleted, all its record sets will also be deleted.                                                    |
   +-----------------------------------------------------------------------+------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Associating a VPC with a Private Zone <dns_usermanual_0003>`    | Configure private domain names for VPCs. | -  You can only associate VPCs that you have created using your own account.                                                     |
   |                                                                       |                                          | -  Each VPC can be associated only with one private zone. However, a private zone can have more than one VPC associated with it. |
   +-----------------------------------------------------------------------+------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Disassociating a VPC from a Private Zone <dns_usermanual_0004>` | Disassociate a VPC from a private zone.  | -  After the disassociation, private domain names will not take effect in the VPC.                                               |
   |                                                                       |                                          | -  If a private zone is only associated with one VPC, you cannot disassociate it.                                                |
   +-----------------------------------------------------------------------+------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------+
