:original_name: dns_api_63007.html

.. _dns_api_63007:

Querying Name Servers in a Private Zone
=======================================

Function
--------

Query name servers in a private zone.

URI
---

GET /v2/zones/{zone_id}/nameservers

For details, see :ref:`Table 1 <dns_api_63007__table14024165>`.

.. _dns_api_63007__table14024165:

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

-  Request parameters

   None

-  Example request

   Query name servers of the zone whose ID is ff8080825b8fc86c015b94bc6f8712c3:

   .. code-block:: text

      GET https://{DNS_Endpoint}/v2/zones/ff8080825b8fc86c015b94bc6f8712c3/nameservers

Response
--------

-  Parameter description

   .. table:: **Table 2** Parameter in the response

      +-----------------------+-----------------------+----------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                          |
      +=======================+=======================+======================================================================+
      | nameservers           | Array of object       | Name server list object                                              |
      |                       |                       |                                                                      |
      |                       |                       | For details, see :ref:`Table 3 <dns_api_63007__table3847447219326>`. |
      +-----------------------+-----------------------+----------------------------------------------------------------------+

   .. _dns_api_63007__table3847447219326:

   .. table:: **Table 3** Description of the **nameservers** field

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                   |
      +=======================+=======================+===============================================================================================================+
      | address               | String                | IP address of a DNS server                                                                                    |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+
      | priority              | Integer               | Priority of a name server                                                                                     |
      |                       |                       |                                                                                                               |
      |                       |                       | For example, if the priority of a name server is **1**, it is used to resolve domain names in first priority. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "nameservers": [
              {
                  "priority": 1,
                  "address": "100.125.0.81"
              },
              {
                  "priority": 2,
                  "address": "100.125.0.82"
              }
          ]
      }

Returned Value
--------------

If a 2xx status code is returned, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
