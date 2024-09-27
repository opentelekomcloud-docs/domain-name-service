:original_name: dns_api_61002.html

.. _dns_api_61002:

Querying the DNS API Version
============================

Function
--------

Query a specified DNS API version.

To be interconnected with a third-party system, the current DNS version supports 1024- and 2048-bit DH key exchange algorithms, and the 2048-bit algorithm is recommended.

URI
---

GET /{version}

For details, see :ref:`Table 1 <dns_api_61002__table14024165>`.

.. _dns_api_61002__table14024165:

.. table:: **Table 1** Parameter in the URI

   +-----------+-----------+--------+---------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                         |
   +===========+===========+========+=====================================================================+
   | version   | Yes       | String | Version to be queried, which starts with **v**, for example, **v2** |
   +-----------+-----------+--------+---------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

-  Example request

   Query information about the v2 API version.

   .. code-block:: text

      GET https://{DNS_Endpoint}/v2

Response
--------

-  Parameter description

   .. table:: **Table 2** Parameter in the response

      +-----------+--------+--------------------------------------------------------------------------------------+
      | Parameter | Type   | Description                                                                          |
      +===========+========+======================================================================================+
      | version   | Object | Version object. For details, see :ref:`Table 3 <dns_api_61002__table3345872992049>`. |
      +-----------+--------+--------------------------------------------------------------------------------------+

   .. _dns_api_61002__table3345872992049:

   .. table:: **Table 3** Description of the **version** field

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                       |
      +=======================+=======================+===================================================================================================+
      | status                | String                | Version status, which can be:                                                                     |
      |                       |                       |                                                                                                   |
      |                       |                       | -  **CURRENT**: widely used version                                                               |
      |                       |                       | -  **SUPPORTED**: earlier version which is still supported                                        |
      |                       |                       | -  **DEPRECATED**: deprecated version which may be deleted later                                  |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------+
      | id                    | String                | Version number, for example, **v2**                                                               |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------+
      | updated               | String                | Time when the API version was released                                                            |
      |                       |                       |                                                                                                   |
      |                       |                       | The UTC time format is used: YYYY-MM-DDTHH:MM:SSZ.                                                |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------+
      | version               | String                | Maximum micro-version number. If the APIs do not support micro-versions, the value is left blank. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------+
      | min_version           | String                | Minimum micro-version number. If the APIs do not support micro-versions, the value is left blank. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------+
      | links                 | Array of object       | URL of the current version. For details, see :ref:`Table 4 <dns_api_61002__table0172144213344>`.  |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------+

   .. _dns_api_61002__table0172144213344:

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
              "version":
                  {
                      "status": "CURRENT",
                      "id": "v2",
                      "links": [
                          {
                              "href": "https://Endpoint/v2/",
                              "rel": "self"
                          }
                      ],
                  "min_version": "",
                  "updated": "2018-09-18T00:00:00Z",
                  "version": ""
                  }
      }

Returned Value
--------------

If a 2xx status code is returned, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
