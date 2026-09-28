:original_name: dns_api_63010.html

.. _dns_api_63010:

Setting a Recursive Resolution Proxy for Subdomains in a Private Zone
=====================================================================

Function
--------

This API is used to set a recursive resolution proxy for subdomains in a private zone.

URI
---

POST /v2/zones/{zone_id}/actions/set-proxy-pattern

.. table:: **Table 1** Path parameter

   ========= ========= ====== =======================================
   Parameter Mandatory Type   Description
   ========= ========= ====== =======================================
   zone_id   Yes       String ID of the private zone to be configured
   ========= ========= ====== =======================================

Request
-------

-  Request parameters

   .. table:: **Table 2** Request parameter

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                         |
      +=================+=================+=================+=====================================================================================================================================================+
      | proxy_pattern   | Yes             | String          | Recursive resolution proxy mode for subdomain names of private zones                                                                                |
      |                 |                 |                 |                                                                                                                                                     |
      |                 |                 |                 | The recursive resolution proxy mode can be set only for private zones created using the DNS service, not for those created by other cloud services. |
      |                 |                 |                 |                                                                                                                                                     |
      |                 |                 |                 | The value can be:                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                     |
      |                 |                 |                 | -  **AUTHORITY**: The recursive resolution proxy is disabled for the zone.                                                                          |
      |                 |                 |                 | -  **RECURSIVE**: The recursive resolution proxy is enabled for the zone.                                                                           |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   Setting the recursive resolution proxy for the subdomains of a private zone

   .. code-block:: text

      POST https://{endpoint}/v2/zones/{zone_id}/actions/set-proxy-pattern

   .. code-block::

      {
          "proxy_pattern": "RECURSIVE"
      }

Response
--------

None

Status Codes
------------

+-------------+----------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                        |
+=============+====================================================================================================+
| 202         | Response to the request for setting a recursive resolution proxy for subdomains in a private zone. |
+-------------+----------------------------------------------------------------------------------------------------+
| 400         | Error response.                                                                                    |
+-------------+----------------------------------------------------------------------------------------------------+
| 500         | Error response.                                                                                    |
+-------------+----------------------------------------------------------------------------------------------------+

Error Codes
-----------

For details, see :ref:`Error Code <dns_api_80003>`.
