:original_name: dns_api_63004.html

.. _dns_api_63004:

Disassociating a VPC from a Private Zone
========================================

Function
--------

Disassociate a VPC from a private zone.

When a private zone is associated with only one VPC, you cannot disassociate it.

URI
---

POST /v2/zones/{zone_id}/disassociaterouter

For details, see :ref:`Table 1 <dns_api_63004__table14024165>`.

.. _dns_api_63004__table14024165:

.. table:: **Table 1** Parameter in the URI

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                   |
   +=================+=================+=================+===============================================================================================+
   | zone_id         | Yes             | String          | Zone ID                                                                                       |
   |                 |                 |                 |                                                                                               |
   |                 |                 |                 | You can obtain the value by calling the API in :ref:`Querying Private Zones <dns_api_63006>`. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter in the request

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                          |
      +=================+=================+=================+======================================================================+
      | router          | Yes             | Object          | Router information (VPC associated with the zone)                    |
      |                 |                 |                 |                                                                      |
      |                 |                 |                 | For details, see :ref:`Table 3 <dns_api_63004__table4448008117179>`. |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------+

   .. _dns_api_63004__table4448008117179:

   .. table:: **Table 3** Description of the **router** field

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                          |
      +=================+=================+=================+======================================================================================+
      | router_id       | Yes             | String          | ID of the associated VPC                                                             |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------+
      | router_region   | No              | String          | Region of the VPC                                                                    |
      |                 |                 |                 |                                                                                      |
      |                 |                 |                 | If it is left blank, the region of the project in the token takes effect by default. |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------+

-  Example request

   Disassociate a VPC from the zone whose ID is ff8080825b8fc86c015b94bc6f8712c3:

   .. code-block:: text

      POST https://{DNS_Endpoint}/v2/zones/ff8080825b8fc86c015b94bc6f8712c3/disassociaterouter

   .. code-block::

      {
          "router": {
              "router_id": "f0791650-db8c-4a20-8a44-a06c6e24b15b",
              "router_region": "xx"
          }
      }

Response
--------

-  Parameter description

   .. table:: **Table 4** Parameters in the response

      +-----------------------+-----------------------+---------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                     |
      +=======================+=======================+=================================================================================+
      | router_id             | String                | Router ID (VPC ID)                                                              |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------+
      | router_region         | String                | Region of the router (VPC)                                                      |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------+
      | status                | String                | Resource status                                                                 |
      |                       |                       |                                                                                 |
      |                       |                       | For details, see :ref:`Resource Status <dns_api_80005__section33673592114748>`. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "status": "PENDING_DELETE",
          "router_id": "f0791650-db8c-4a20-8a44-a06c6e24b15b",
          "router_region": "xx"
      }

Returned Value
--------------

If a 2xx status code is returned, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
