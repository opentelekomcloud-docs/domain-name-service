:original_name: dns_api_614001.html

.. _dns_api_614001:

Querying Resource Quotas
========================

Function
--------

This API is used to query the DNS resource quotas of a specific tenant. The resources include:

-  Public zones
-  Private zones
-  Record sets
-  PTR records
-  Inbound endpoints
-  Outbound endpoints
-  Endpoint rules

URI
---

GET /v2/quotamg/dns/quotas

Request
-------

-  Parameter description

   .. table:: **Table 1** Parameters in the request

      ========= ========= ====== ========================
      Parameter Mandatory Type   Description
      ========= ========= ====== ========================
      domain_id Yes       String Specifies the tenant ID.
      ========= ========= ====== ========================

-  Example request

   Querying resource quotas of a tenant

   .. code-block:: text

      GET https://{DNS_Endpoint}/v2/quotamg/dns/quotas?domain_id=xxxx

Response
--------

-  Parameter description

   .. table:: **Table 2** Parameters in the response

      +-----------+-----------------+--------------------------------------------------------------------------------------------+
      | Parameter | Type            | Description                                                                                |
      +===========+=================+============================================================================================+
      | quotas    | Array of object | Resource quota list. For details, see :ref:`Table 3 <dns_api_614001__table6912840114213>`. |
      +-----------+-----------------+--------------------------------------------------------------------------------------------+

   .. _dns_api_614001__table6912840114213:

   .. table:: **Table 3** Description of the **quotas** field

      +-------------+---------+----------------------------------------------------------+
      | Parameter   | Type    | Description                                              |
      +=============+=========+==========================================================+
      | quota_key   | String  | Resource type.                                           |
      +-------------+---------+----------------------------------------------------------+
      | quota_limit | Integer | Maximum resource quota.                                  |
      +-------------+---------+----------------------------------------------------------+
      | used        | Integer | Used resource quota.                                     |
      +-------------+---------+----------------------------------------------------------+
      | unit        | String  | Quota measurement unit. The value is fixed at **count**. |
      +-------------+---------+----------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "quotas": [
              {
                  "quota_key": "zone",
                  "quota_limit": 50,
                  "used": 11,
                  "unit": "count"
              },
              {
                  "quota_key": "private_zone",
                  "quota_limit": 50,
                  "used": 17,
                  "unit": "count"
              },
              {
                  "quota_key": "record_set",
                  "quota_limit": 500,
                  "used": 98,
                  "unit": "count"
              },
              {
                  "quota_key": "ptr_record",
                  "quota_limit": 50,
                  "used": 1,
                  "unit": "count"
              },
              {
                  "quota_key": "inbound_endpoint",
                  "quota_limit": 50,
                  "used": 3,
                  "unit": "count"
              },
              {
                  "quota_key": "outbound_endpoint",
                  "quota_limit": 50,
                  "used": 1,
                  "unit": "count"
              },
              {
                  "quota_key": "resolver_rule",
                  "quota_limit": 50,
                  "used": 1,
                  "unit": "count"
              }
          ]
      }

Status Codes
------------

=========== ===================================================
Status Code Description
=========== ===================================================
200         Response to the request for querying tenant quotas.
=========== ===================================================

Error Codes
-----------

For details, see :ref:`Error Code <dns_api_80003>`.
