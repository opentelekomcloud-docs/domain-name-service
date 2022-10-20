:original_name: dns_api_63006.html

.. _dns_api_63006:

Querying Private Zones
======================

Function
--------

Query private zones in list.

URI
---

GET /v2/zones?type={type}&limit={limit}&marker={marker}&offset={offset}&tags={tags}&name={name}&status={status}&enterprise_project_id={id}

For details, see :ref:`Table 1 <dns_api_63006__table36421405182556>`.

.. _dns_api_63006__table36421405182556:

.. table:: **Table 1** Parameters in the URI

   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type            | Description                                                                                                                 |
   +=======================+=================+=================+=============================================================================================================================+
   | type                  | Yes             | String          | Zone type                                                                                                                   |
   |                       |                 |                 |                                                                                                                             |
   |                       |                 |                 | The value is **private**, indicating that private zones are queried.                                                        |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+
   | marker                | No              | String          | Start resource ID of pagination query                                                                                       |
   |                       |                 |                 |                                                                                                                             |
   |                       |                 |                 | If the parameter is left blank, only resources on the first page are queried.                                               |
   |                       |                 |                 |                                                                                                                             |
   |                       |                 |                 | The value is left blank by default.                                                                                         |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+
   | limit                 | No              | Integer         | Number of resources on each page                                                                                            |
   |                       |                 |                 |                                                                                                                             |
   |                       |                 |                 | The value ranges from **0** to **500**.                                                                                     |
   |                       |                 |                 |                                                                                                                             |
   |                       |                 |                 | Commonly used values are **10**, **20**, and **50**. The default value is **500**.                                          |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+
   | offset                | No              | Integer         | Start offset of pagination query. The query will start from the next resource of the offset value.                          |
   |                       |                 |                 |                                                                                                                             |
   |                       |                 |                 | The value ranges from **0** to **2147483647**.                                                                              |
   |                       |                 |                 |                                                                                                                             |
   |                       |                 |                 | The default value is **0**.                                                                                                 |
   |                       |                 |                 |                                                                                                                             |
   |                       |                 |                 | If **marker** is not left blank, the query starts from the resource specified by **marker**.                                |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+
   | tags                  | No              | String          | Resource tag                                                                                                                |
   |                       |                 |                 |                                                                                                                             |
   |                       |                 |                 | The format is as follows: **key1,value1|key2,value2**.                                                                      |
   |                       |                 |                 |                                                                                                                             |
   |                       |                 |                 | Multiple tags are separated by vertical bar (|). The key and value of each tag are separated by comma (,).                  |
   |                       |                 |                 |                                                                                                                             |
   |                       |                 |                 | The tags are in AND relationship.                                                                                           |
   |                       |                 |                 |                                                                                                                             |
   |                       |                 |                 | For details, see :ref:`Adding Resource Tags <dns_api_67001>`.                                                               |
   |                       |                 |                 |                                                                                                                             |
   |                       |                 |                 | The value is left blank by default.                                                                                         |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+
   | name                  | No              | String          | Zone name                                                                                                                   |
   |                       |                 |                 |                                                                                                                             |
   |                       |                 |                 | A fuzzy search will be performed.                                                                                           |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+
   | status                | No              | String          | Resource status                                                                                                             |
   |                       |                 |                 |                                                                                                                             |
   |                       |                 |                 | For details, see :ref:`Resource Status <dns_api_80005__section33673592114748>`.                                             |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id | No              | String          | Specifies the ID of the enterprise project associated with the private zone. The value contains a maximum of 36 characters. |
   |                       |                 |                 |                                                                                                                             |
   |                       |                 |                 | The default value is **0**.                                                                                                 |
   +-----------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

-  Example request

   Query the first 10 private zones whose tag is <key1, value1>:

   .. code-block:: text

      GET https://{DNS_Endpoint}/v2/zones?type=private&limit=10&offset=0&tags=key1,value1

Response
--------

-  Parameter description

   .. table:: **Table 2** Parameters in the response

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                                  |
      +=======================+=======================+==============================================================================================================================+
      | links                 | Object                | Link to the current resource or other related resources.                                                                     |
      |                       |                       |                                                                                                                              |
      |                       |                       | When a response is broken into pages, a **next** link is provided to retrieve all results.                                   |
      |                       |                       |                                                                                                                              |
      |                       |                       | For details, see :ref:`Table 5 <dns_api_63006__table0172144213344>`.                                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | zones                 | Array of object       | Zone list. For details, see :ref:`Table 3 <dns_api_63006__table10871190151410>`.                                             |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+
      | metadata              | Object                | Total number of resources that meet the filter criteria. For details, see :ref:`Table 4 <dns_api_63006__table141615131414>`. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_63006__table10871190151410:

   .. table:: **Table 3** Description of the **zones** field

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                                 |
      +=======================+=======================+=============================================================================================================================+
      | id                    | String                | Zone ID, which is a UUID used to identify the zone                                                                          |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Zone name                                                                                                                   |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | description           | String                | Zone description                                                                                                            |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | email                 | String                | Email address of the administrator managing the zone                                                                        |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | zone_type             | String                | Zone type, which can be **public** or **private**                                                                           |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | ttl                   | Integer               | TTL value of the SOA record set in the zone                                                                                 |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | serial                | Integer               | Serial number in the SOA record set in a zone, which identifies the change on the primary DNS server                        |
      |                       |                       |                                                                                                                             |
      |                       |                       | This parameter is not used currently.                                                                                       |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Resource status                                                                                                             |
      |                       |                       |                                                                                                                             |
      |                       |                       | For details, see :ref:`Resource Status <dns_api_80005__section33673592114748>`.                                             |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | record_num            | Integer               | Number of record sets in the zone                                                                                           |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | pool_id               | String                | Pool ID of the zone, which is assigned by the system                                                                        |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | project_id            | String                | Project ID of the zone                                                                                                      |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | created_at            | String                | Time when the zone was created                                                                                              |
      |                       |                       |                                                                                                                             |
      |                       |                       | The UTC time format is used: YYYY-MM-DDTHH:MM:SSZ.                                                                          |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | updated_at            | String                | Time when the zone was updated                                                                                              |
      |                       |                       |                                                                                                                             |
      |                       |                       | The UTC time format is used: YYYY-MM-DDTHH:MM:SSZ.                                                                          |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | links                 | Object                | Link to the current resource or other related resources.                                                                    |
      |                       |                       |                                                                                                                             |
      |                       |                       | When a response is broken into pages, a **next** link is provided to retrieve all results.                                  |
      |                       |                       |                                                                                                                             |
      |                       |                       | For details, see :ref:`Table 5 <dns_api_63006__table0172144213344>`.                                                        |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | masters               | Array of strings      | Master DNS servers, from which the slave servers get DNS information                                                        |
      |                       |                       |                                                                                                                             |
      |                       |                       | This parameter is not used currently.                                                                                       |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | routers               | Array of object       | Routers (VPCs associated with the zone). For details, see :ref:`Table 6 <dns_api_63006__table4448008117179>`.               |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | enterprise_project_id | String                | Specifies the ID of the enterprise project associated with the private zone. The value contains a maximum of 36 characters. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_63006__table141615131414:

   .. table:: **Table 4** Description of the **metadata** field

      +-------------+---------+---------------------------------------------------------------------------------------------------------+
      | Parameter   | Type    | Description                                                                                             |
      +=============+=========+=========================================================================================================+
      | total_count | Integer | Number of resources that meet the filter criteria. The number is irrelevant to **limit** or **offset**. |
      +-------------+---------+---------------------------------------------------------------------------------------------------------+

   .. _dns_api_63006__table0172144213344:

   .. table:: **Table 5** Parameters in the **links** field

      ========= ====== ============================
      Parameter Type   Description
      ========= ====== ============================
      self      String Link to the current resource
      next      String Link to the next page
      ========= ====== ============================

   .. _dns_api_63006__table4448008117179:

   .. table:: **Table 6** Description of the **routers** field

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
          "links": {
              "self": "https://Endpoint/v2/zones?type=private&limit=11",
              "next": "https://Endpoint/v2/zones?type=private&limit=11&marker=ff8080825b8fc86c015b94bc6f8712c3"
          },
          "zones": [
              {
                  "id": "ff8080825b8fc86c015b94bc6f8712c3",
                  "name": "example.com.",
                  "description": "This is an example zone.",
                  "email": "xx@example.com",
                  "ttl": 300,
                  "serial": 0,
                  "masters": [],
                  "status": "ACTIVE",
                  "links": {
                      "self": "https://Endpoint/v2/zones/ff8080825b8fc86c015b94bc6f8712c3"
                  },
                  "pool_id": "ff8080825ab738f4015ab7513298010e",
                  "project_id": "e55c6f3dc4e34c9f86353b664ae0e70c",
                  "zone_type": "private",
                  "created_at": "2017-04-22T08:17:08.997",
                  "updated_at": "2017-04-22T08:17:09.997",
                  "record_num": 2,
                  "routers": [
                      {
                          "status": "ACTIVE",
                          "router_id": "19664294-0bf6-4271-ad3a-94b8c79c6558",
                          "router_region": "xx"
                      },
                      {
                          "status": "ACTIVE",
                          "router_id": "f0791650-db8c-4a20-8a44-a06c6e24b15b",
                          "router_region": "xx"
                      }
                  ]
              },
              {
                  "id": "ff8080825b95142f015b951f87280029",
                  "name": "example.org.",
                  "description": "This is an example zone.",
                  "email": "xx@example.org",
                  "ttl": 300,
                  "serial": 0,
                  "masters": [],
                  "status": "ACTIVE",
                  "links": {
                      "self": "https://Endpoint/v2/zones/ff8080825b95142f015b951f87280029"
                  },
                  "pool_id": "ff8080825ab738f4015ab7513298010e",
                  "project_id": "e55c6f3dc4e34c9f86353b664ae0e70c",
                  "zone_type": "private",
                  "created_at": "2017-04-22T08:17:08.997",
                  "updated_at": "2017-04-22T08:17:09.997",
                  "record_num": 2,
                  "routers": [
                      {
                          "status": "ACTIVE",
                          "router_id": "19664294-0bf6-4271-ad3a-94b8c79c6558",
                          "router_region": "xx"
                      },
                      {
                          "status": "ACTIVE",
                          "router_id": "f0791650-db8c-4a20-8a44-a06c6e24b15b",
                          "router_region": "xx"
                      }
                  ]

              }
          ],
          "metadata": {
              "total_count": 2
          }
      }

Returned Value
--------------

If the API call returns a code of 2\ *xx*, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
