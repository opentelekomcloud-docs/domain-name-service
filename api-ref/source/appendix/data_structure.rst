:original_name: dns_api_80006.html

.. _dns_api_80006:

Data Structure
==============

.. table:: **Table 1** Description of the **links** field

   ========= ====== ============================
   Parameter Type   Description
   ========= ====== ============================
   self      String Link to the current resource
   next      String Link to the next page
   ========= ====== ============================

.. _dns_api_80006__table19530794112436:

.. table:: **Table 2** Description of the **tag** field

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                          |
   +=======================+=======================+======================================================================================+
   | key                   | String                | Tag key                                                                              |
   |                       |                       |                                                                                      |
   |                       |                       | -  Cannot be left blank.                                                             |
   |                       |                       | -  Must be unique for each resource.                                                 |
   |                       |                       | -  Can contain a maximum of 128 Unicode characters.                                  |
   |                       |                       | -  Can contain letters, digits, spaces, and the following characters: \_ . : = + - @ |
   |                       |                       | -  Cannot start or end with a space, or cannot start with **\_sys\_**.               |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------+
   | value                 | String                | Tag value                                                                            |
   |                       |                       |                                                                                      |
   |                       |                       | -  Can be left blank.                                                                |
   |                       |                       | -  Can contain a maximum of 255 Unicode characters.                                  |
   |                       |                       | -  Can contain letters, digits, spaces, and the following characters: \_ . : = + - @ |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------+

.. table:: **Table 3** Description of the **routers** field

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                              |
   +=======================+=======================+==========================================================================================+
   | router_id             | String                | ID of the associated VPC                                                                 |
   |                       |                       |                                                                                          |
   |                       |                       | You can obtain the VPC ID using the following methods:                                   |
   |                       |                       |                                                                                          |
   |                       |                       | -  On the VPC console, obtain the VPC ID on the VPC details page.                        |
   |                       |                       | -  Obtain the VPC ID according to "Querying VPCs" in *Virtual Private Cloud User Guide*. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
   | router_region         | String                | Region of the VPC                                                                        |
   |                       |                       |                                                                                          |
   |                       |                       | If it is left blank, the region of the project in the token takes effect by default.     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------+

.. table:: **Table 4** Description of the **alias_target** field

   +-----------------------+-----------------------+-----------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                           |
   +=======================+=======================+=======================================================================+
   | resource_type         | String                | Service that support domain name aliases                              |
   |                       |                       |                                                                       |
   |                       |                       | The value can be **cloudsite** or **waf** (Web Application Firewall). |
   +-----------------------+-----------------------+-----------------------------------------------------------------------+
   | resource_domain_name  | String                | Domain name of the target service                                     |
   +-----------------------+-----------------------+-----------------------------------------------------------------------+
