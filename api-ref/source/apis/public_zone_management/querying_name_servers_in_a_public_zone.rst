:original_name: dns_api_62004.html

.. _dns_api_62004:

Querying Name Servers in a Public Zone
======================================

Function
--------

Query name servers in a public zone.

URI
---

GET /v2/zones/{zone_id}/nameservers

For details, see :ref:`Table 1 <dns_api_62004__table14024165>`.

.. _dns_api_62004__table14024165:

.. table:: **Table 1** Parameter in the URI

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                  |
   +=================+=================+=================+==============================================================================================+
   | zone_id         | Yes             | String          | Zone ID                                                                                      |
   |                 |                 |                 |                                                                                              |
   |                 |                 |                 | You can obtain the value by calling the API in :ref:`Querying Public Zones <dns_api_62003>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

-  Example request

   Query name servers of the zone whose ID is 2c9eb155587194ec01587224c9f90149:

   .. code-block:: text

      GET https://{DNS_Endpoint}/v2/zones/2c9eb155587194ec01587224c9f90149/nameservers

Response
--------

-  Parameter description

   .. table:: **Table 2** Parameter in the response

      +-------------+-----------------+----------------------------------------------------------------------------------------+
      | Parameter   | Type            | Description                                                                            |
      +=============+=================+========================================================================================+
      | nameservers | Array of object | Name server list. For details, see :ref:`Table 3 <dns_api_62004__table3847447219326>`. |
      +-------------+-----------------+----------------------------------------------------------------------------------------+

   .. _dns_api_62004__table3847447219326:

   .. table:: **Table 3** Description of the **nameservers** field

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                   |
      +=======================+=======================+===============================================================================================================+
      | hostname              | String                | Host name of a name server                                                                                    |
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
                  "hostname": "ns1.example.com.",
                  "priority": 1
              },
              {
                  "hostname": "ns2.example.com.",
                  "priority": 2
              }
          ]
      }

Returned Value
--------------

If the API call returns a code of 2\ *xx*, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
