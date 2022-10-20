:original_name: dns_api_63009.html

.. _dns_api_63009:

Modifying a Private Zone
========================

Function
--------

Modify a private zone.

URI
---

PATCH /v2/zones/{zone_id}

For details, see :ref:`Table 1 <dns_api_63009__tacd282d91a914e70a7e35f44180b61aa>`.

.. _dns_api_63009__tacd282d91a914e70a7e35f44180b61aa:

.. table:: **Table 1** Parameters in the URI

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                   |
   +=================+=================+=================+===============================================================================================+
   | zone_id         | Yes             | String          | ID of the zone to be modified                                                                 |
   |                 |                 |                 |                                                                                               |
   |                 |                 |                 | You can obtain the value by calling the API in :ref:`Querying Private Zones <dns_api_63006>`. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameters in the request

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                     |
      +=================+=================+=================+=================================================================+
      | description     | No              | String          | Description of the zone, which cannot exceed 255 characters     |
      |                 |                 |                 |                                                                 |
      |                 |                 |                 | If this parameter is left blank, the value will not be changed. |
      |                 |                 |                 |                                                                 |
      |                 |                 |                 | The value is left blank by default.                             |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------+
      | email           | No              | String          | Email address of the administrator managing the zone            |
      |                 |                 |                 |                                                                 |
      |                 |                 |                 | If this parameter is left blank, the value will not be changed. |
      |                 |                 |                 |                                                                 |
      |                 |                 |                 | The value is left blank by default.                             |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------+
      | ttl             | No              | Integer         | Caching period of the SOA record set (in seconds)               |
      |                 |                 |                 |                                                                 |
      |                 |                 |                 | The value ranges from 1 to **2147483647**.                      |
      |                 |                 |                 |                                                                 |
      |                 |                 |                 | If this parameter is left blank, the value will not be changed. |
      |                 |                 |                 |                                                                 |
      |                 |                 |                 | The value is left blank by default.                             |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------+

-  Example request

   Modify the zone whose ID is 2c9eb155587194ec01587224c9f90149:

   .. code-block:: text

      PATCH https://{DNS_Endpoint}/v2/zones/2c9eb155587194ec01587224c9f90149

   .. code-block::

      {
          "description": "This is an example zone.",
          "email": "xx@example.org",
          "ttl": 300
      }

Response
--------

-  Parameter description

   .. table:: **Table 3** Parameters in the response

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                              |
      +=======================+=======================+==========================================================================================================================+
      | id                    | String                | Zone ID, which is a UUID used to identify the zone                                                                       |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Zone name                                                                                                                |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | description           | String                | Zone description                                                                                                         |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | email                 | String                | Email address of the administrator managing the zone                                                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | zone_type             | String                | Zone type, which can be **public** or **private**                                                                        |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | ttl                   | Integer               | TTL value of the SOA record set in the zone                                                                              |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | serial                | Integer               | Serial number in the SOA record set in a zone, which identifies the change on the primary DNS server                     |
      |                       |                       |                                                                                                                          |
      |                       |                       | This parameter is not used currently.                                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Resource status                                                                                                          |
      |                       |                       |                                                                                                                          |
      |                       |                       | For details, see :ref:`Resource Status <dns_api_80005__section33673592114748>`.                                          |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | record_num            | Integer               | Number of record sets in the zone                                                                                        |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | pool_id               | String                | Pool ID of the zone, which is assigned by the system                                                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | project_id            | String                | Project ID of the zone                                                                                                   |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | created_at            | String                | Time when the zone was created                                                                                           |
      |                       |                       |                                                                                                                          |
      |                       |                       | The UTC time format is used: YYYY-MM-DDTHH:MM:SSZ.                                                                       |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | updated_at            | String                | Time when the zone was updated                                                                                           |
      |                       |                       |                                                                                                                          |
      |                       |                       | The UTC time format is used: YYYY-MM-DDTHH:MM:SSZ.                                                                       |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | links                 | Object                | Link to the current resource or other related resources.                                                                 |
      |                       |                       |                                                                                                                          |
      |                       |                       | When a response is broken into pages, a **next** link is provided to retrieve all results.                               |
      |                       |                       |                                                                                                                          |
      |                       |                       | For details, see :ref:`Table 4 <dns_api_63009__table52442344175457>`.                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | masters               | Array of strings      | Master DNS servers, from which the slave servers get DNS information                                                     |
      |                       |                       |                                                                                                                          |
      |                       |                       | This parameter is not used currently.                                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | routers               | Array of object       | Information about the VPC associated with the zone. For details, see :ref:`Table 5 <dns_api_63009__table4448008117179>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_63009__table52442344175457:

   .. table:: **Table 4** Parameters in the **links** field

      ========= ====== ============================
      Parameter Type   Description
      ========= ====== ============================
      self      String Link to the current resource
      next      String Link to the next page
      ========= ====== ============================

   .. _dns_api_63009__table4448008117179:

   .. table:: **Table 5** Description of the **routers** field

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                          |
      +=======================+=======================+======================================================================================+
      | status                | String                | Resource status                                                                      |
      |                       |                       |                                                                                      |
      |                       |                       | For details, see :ref:`Resource Status <dns_api_80005__section33673592114748>`.      |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------+
      | router_id             | String                | ID of the associated VPC                                                             |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------+
      | router_region         | String                | Region of the VPC                                                                    |
      |                       |                       |                                                                                      |
      |                       |                       | If it is left blank, the region of the project in the token takes effect by default. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "id": "ff8080825b8fc86c015b94bc6f8712c3",
          "name": "example.com.",
          "description": "This is an example zone.",
          "email": "xx@example.com",
          "ttl": 300,
          "serial": 1,
          "masters": [],
          "status": "ACTIVE",
          "links": {
              "self": "https://Endpoint/v2/zones/ff8080825b8fc86c015b94bc6f8712c3"
          },
          "pool_id": "ff8080825ab738f4015ab7513298010e",
          "project_id": "e55c6f3dc4e34c9f86353b664ae0e70c",
          "zone_type": "private",
          "created_at": "2017-04-22T08:17:08.997",
          "updated_at": "2017-04-22T08:17:10.849",
          "record_num": 2,
          "routers": [
            {
                "status": "ACTIVE",
                "router_id": "19664294-0bf6-4271-ad3a-94b8c79c6558",
                "router_region": "xx"
              }
          ]
      }

Returned Value
--------------

If the API call returns a code of 2\ *xx*, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
