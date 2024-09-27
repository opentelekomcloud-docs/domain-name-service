:original_name: dns_api_66003.html

.. _dns_api_66003:

Querying a PTR Record
=====================

Function
--------

Query the PTR record of an EIP.

URI
---

GET /v2/reverse/floatingips/{region}:{floatingip_id}

For details, see :ref:`Table 1 <dns_api_66003__table21421675>`.

.. _dns_api_66003__table21421675:

.. table:: **Table 1** Parameters in the URI

   ============= ========= ====== ====================
   Parameter     Mandatory Type   Description
   ============= ========= ====== ====================
   region        Yes       String Region of the tenant
   floatingip_id Yes       String EIP ID
   ============= ========= ====== ====================

Request
-------

-  Request parameters

   None

-  Example request

   Query the PTR record whose EIP ID is **c5504932-bf23-4171-b655-b87a6bc59334**:

   .. code-block:: text

      GET https://{DNS_Endpoint}/v2/reverse/floatingips/region_id:c5504932-bf23-4171-b655-b87a6bc59334

Response
--------

-  Parameter description

   .. table:: **Table 2** Parameters in the response

      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                                                                    |
      +=======================+=======================+================================================================================================================================================================+
      | id                    | String                | PTR record ID, which is in **{region}:{floatingip_id}** format                                                                                                 |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ptrdname              | String                | Domain name of the PTR record                                                                                                                                  |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description           | String                | PTR record description                                                                                                                                         |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ttl                   | Integer               | PTR record cache duration (in seconds) on a local DNS server. The longer the duration is, the slower the update takes effect.                                  |
      |                       |                       |                                                                                                                                                                |
      |                       |                       | If your service address is frequently changed, set TTL to a smaller value.                                                                                     |
      |                       |                       |                                                                                                                                                                |
      |                       |                       | The value ranges from **1** to **2147483647**.                                                                                                                 |
      |                       |                       |                                                                                                                                                                |
      |                       |                       | The default value is **300**.                                                                                                                                  |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | address               | String                | EIP                                                                                                                                                            |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Resource status                                                                                                                                                |
      |                       |                       |                                                                                                                                                                |
      |                       |                       | For details, see :ref:`Resource Status <dns_api_80005__section33673592114748>`.                                                                                |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | action                | String                | Requested operation on the resource                                                                                                                            |
      |                       |                       |                                                                                                                                                                |
      |                       |                       | The value can be **CREATE**, **UPDATE**, **DELETE**, or **NONE**.                                                                                              |
      |                       |                       |                                                                                                                                                                |
      |                       |                       | **NONE** indicates that no operation will be performed.                                                                                                        |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | links                 | Object                | Link to the current resource or other related resources                                                                                                        |
      |                       |                       |                                                                                                                                                                |
      |                       |                       | When a response is broken into pages, a **next** link is provided to retrieve all results. For details, see :ref:`Table 3 <dns_api_66003__table354521744216>`. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_66003__table354521744216:

   .. table:: **Table 3** Parameters in the **links** field

      ========= ====== ============================
      Parameter Type   Description
      ========= ====== ============================
      self      String Link to the current resource
      next      String Link to the next page
      ========= ====== ============================

-  Example response

   .. code-block::

      {
          "id": "region_id:c5504932-bf23-4171-b655-b87a6bc59334",
          "ptrdname": "www.example.com.",
          "description": "Description for this PTR record",
          "address": "10.154.52.138",
          "action": "CREATE",
          "ttl": 300,
          "status": "ACTIVE",
          "links": {
              "self": "https://Endpoint/v2/reverse/floatingips/region_id:c5504932-bf23-4171-b655-b87a6bc59334"
          }
      }

Returned Value
--------------

If a 2xx status code is returned, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
