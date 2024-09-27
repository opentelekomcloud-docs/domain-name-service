:original_name: dns_api_61001.html

.. _dns_api_61001:

Listing All DNS API Versions
============================

Function
--------

List all DNS API versions.

To be interconnected with a third-party system, the current DNS version supports 1024- and 2048-bit DH key exchange algorithms, and the 2048-bit algorithm is recommended.

URI
---

GET /

Request
-------

-  Request parameters

   None

-  Example request

   List all DNS API versions.

   .. code-block:: text

      GET https://{DNS_Endpoint}/

Response
--------

-  Parameter description

   .. table:: **Table 1** Parameter in the response

      +-----------+--------+--------------------------------------------------------------------------------------+
      | Parameter | Type   | Description                                                                          |
      +===========+========+======================================================================================+
      | versions  | Object | Version object. For details, see :ref:`Table 2 <dns_api_61001__table2788528392049>`. |
      +-----------+--------+--------------------------------------------------------------------------------------+

   .. _dns_api_61001__table2788528392049:

   .. table:: **Table 2** Description of the **versions** field

      +-----------+-----------------+------------------------------------------------------------------------------------+
      | Parameter | Type            | Description                                                                        |
      +===========+=================+====================================================================================+
      | values    | Array of object | Version list. For details, see :ref:`Table 3 <dns_api_61001__table3345872992049>`. |
      +-----------+-----------------+------------------------------------------------------------------------------------+

   .. _dns_api_61001__table3345872992049:

   .. table:: **Table 3** Description of the **values** field

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                      |
      +=======================+=======================+==================================================================================================+
      | status                | String                | Version status, which can be:                                                                    |
      |                       |                       |                                                                                                  |
      |                       |                       | -  **CURRENT**: widely used version                                                              |
      |                       |                       | -  **SUPPORTED**: earlier version which is still supported                                       |
      |                       |                       | -  **DEPRECATED**: deprecated version which may be deleted later                                 |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | id                    | String                | Version number                                                                                   |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+
      | links                 | Array of object       | URL of the current version. For details, see :ref:`Table 4 <dns_api_61001__table0172144213344>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------+

   .. _dns_api_61001__table0172144213344:

   .. table:: **Table 4** Description of the **links** field

      ========= ====== ================
      Parameter Type   Description
      ========= ====== ================
      href      String Link address
      rel       String Link marker name
      ========= ====== ================

-  Example response

   .. code-block::

      {
          "versions": {
              "values": [
                  {
                      "status": "CURRENT",
                      "id": "v2",
                      "links": [
                          {
                              "href": "https://Endpoint/v2",
                              "rel": "self"
                          }
                      ]
                  }
              ]
          }
      }

Returned Value
--------------

If a 2xx status code is returned, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
