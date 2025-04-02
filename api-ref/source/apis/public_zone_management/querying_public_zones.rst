:original_name: dns_api_62003.html

.. _dns_api_62003:

Querying Public Zones
=====================

Function
--------

Query public zones in list.

URI
---

GET /v2/zones?type={type}&limit={limit}&marker={marker}&offset={offset}&tags={tags}&name={name}&status={status}

For details, see :ref:`Table 1 <dns_api_62003__table36421405182556>`.

.. _dns_api_62003__table36421405182556:

.. table:: **Table 1** Parameters in the URI

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                             |
   +=================+=================+=================+=========================================================================================================================================+
   | type            | No              | String          | Zone type, which can be **public** or **private**                                                                                       |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | -  **public**: Public zones are queried.                                                                                                |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | -  **private**: Private zones are queried.                                                                                              |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 |    If the value is left blank, public zones are queried by default.                                                                     |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | A fuzzy search will be performed.                                                                                                       |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | The value is left blank by default.                                                                                                     |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String          | Start resource ID of pagination query. If the parameter is left blank, only resources on the first page are queried.                    |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Number of resources on each page                                                                                                        |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | The value ranges from **0** to **500**.                                                                                                 |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | Commonly used values are **10**, **20**, and **50**. The default value is **500**.                                                      |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | Integer         | Start offset of pagination query. The query will start from the next resource of the offset value.                                      |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | The value ranges from **0** to **2147483647**.                                                                                          |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | The default value is 0.                                                                                                                 |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | If **marker** is not left blank, the query starts from the resource specified by **marker**.                                            |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | tags            | No              | String          | Resource tag                                                                                                                            |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | The format is as follows: **key1,value1|key2,value2**.                                                                                  |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | Multiple tags are separated by vertical bar (|). The key and value of each tag are separated by comma (,).                              |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | The tags are in AND relationship.                                                                                                       |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | For details, see :ref:`Adding Resource Tags <dns_api_67001>`.                                                                           |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | Exact matching will work. If the value starts with an asterisk (``*``), fuzzy matching will work for the string following the asterisk. |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | The value is left blank by default.                                                                                                     |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | Zone name                                                                                                                               |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | A fuzzy search will be performed.                                                                                                       |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | status          | No              | String          | Resource status                                                                                                                         |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | For details, see :ref:`Resource Status <dns_api_80005__section33673592114748>`.                                                         |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

-  Example request

   Query the first 10 public zones whose tag is <key1, value1>:

   .. code-block:: text

      GET https://{DNS_Endpoint}/v2/zones?type=public&limit=10&offset=0&tags=key1,value1

Response
--------

-  Parameter description

   .. table:: **Table 2** Parameters in the response

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                                                         |
      +=======================+=======================+=====================================================================================================================================================+
      | links                 | Object                | Link to the current resource or other related resources. When a response is broken into pages, a **next** link is provided to retrieve all results. |
      |                       |                       |                                                                                                                                                     |
      |                       |                       | For details, see :ref:`Table 5 <dns_api_62003__table0172144213344>`.                                                                                |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | zones                 | Array of object       | Zone list. For details, see :ref:`Table 3 <dns_api_62003__table6348803417233>`.                                                                     |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | metadata              | Object                | Total number of resources that meet the filter criteria. For details, see :ref:`Table 4 <dns_api_62003__table52442344175457>`.                      |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_62003__table6348803417233:

   .. table:: **Table 3** Description of the **zones** field

      +-----------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                                                           | Description                                                                                                                             |
      +=======================+================================================================+=========================================================================================================================================+
      | id                    | String                                                         | Zone ID, which is a UUID used to identify the zone                                                                                      |
      +-----------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                                                         | Zone name                                                                                                                               |
      +-----------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | description           | String                                                         | Zone description                                                                                                                        |
      +-----------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | email                 | String                                                         | Email address of the administrator managing the zone                                                                                    |
      +-----------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | zone_type             | String                                                         | Zone type, which can be **public** or **private**                                                                                       |
      +-----------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | ttl                   | Integer                                                        | TTL value of the SOA record set in the zone                                                                                             |
      |                       |                                                                |                                                                                                                                         |
      |                       |                                                                | The value ranges from **1** to **2147483647**.                                                                                          |
      |                       |                                                                |                                                                                                                                         |
      |                       |                                                                | The default value is **300**.                                                                                                           |
      +-----------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | serial                | Integer                                                        | Serial number in the SOA record set in a zone, which identifies the change on the primary DNS server                                    |
      |                       |                                                                |                                                                                                                                         |
      |                       |                                                                | This parameter is not used currently.                                                                                                   |
      +-----------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                                                         | Resource status                                                                                                                         |
      |                       |                                                                |                                                                                                                                         |
      |                       |                                                                | For details, see :ref:`Resource Status <dns_api_80005__section33673592114748>`.                                                         |
      +-----------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | record_num            | Integer                                                        | Number of record sets in the zone                                                                                                       |
      +-----------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | pool_id               | String                                                         | Pool ID of the zone, which is assigned by the system                                                                                    |
      +-----------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | project_id            | String                                                         | Project ID of the zone                                                                                                                  |
      +-----------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | created_at            | String                                                         | Time when the zone was created                                                                                                          |
      |                       |                                                                |                                                                                                                                         |
      |                       |                                                                | The UTC time format is used: YYYY-MM-DDTHH:MM:SSZ.                                                                                      |
      +-----------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | updated_at            | String                                                         | Time when the zone was updated                                                                                                          |
      |                       |                                                                |                                                                                                                                         |
      |                       |                                                                | The UTC time format is used: YYYY-MM-DDTHH:MM:SSZ.                                                                                      |
      +-----------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | links                 | Object                                                         | Link to the current resource or other related resources                                                                                 |
      |                       |                                                                |                                                                                                                                         |
      |                       |                                                                | When a response is broken into pages, a **next** link is provided to retrieve all results.                                              |
      |                       |                                                                |                                                                                                                                         |
      |                       |                                                                | For details, see :ref:`Table 5 <dns_api_62003__table0172144213344>`.                                                                    |
      +-----------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | tags                  | Array of :ref:`tag <dns_api_62003__table619059185111>` objects | Resource tag.                                                                                                                           |
      |                       |                                                                |                                                                                                                                         |
      |                       |                                                                | The format is as follows: **key1,value1|key2,value2**.                                                                                  |
      |                       |                                                                |                                                                                                                                         |
      |                       |                                                                | Multiple tags are separated by vertical bar (|). The key and value of each tag are separated by comma (,).                              |
      |                       |                                                                |                                                                                                                                         |
      |                       |                                                                | The tags are in AND relationship.                                                                                                       |
      |                       |                                                                |                                                                                                                                         |
      |                       |                                                                | For details about resource tags, see :ref:`Table 6 <dns_api_62003__table619059185111>`.                                                 |
      |                       |                                                                |                                                                                                                                         |
      |                       |                                                                | Exact matching will work. If the value starts with an asterisk (``*``), fuzzy matching will work for the string following the asterisk. |
      |                       |                                                                |                                                                                                                                         |
      |                       |                                                                | The value is left blank by default.                                                                                                     |
      +-----------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
      | masters               | Array of strings                                               | Master DNS servers, from which the slave servers get DNS information                                                                    |
      |                       |                                                                |                                                                                                                                         |
      |                       |                                                                | This parameter is not used currently.                                                                                                   |
      +-----------------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_62003__table52442344175457:

   .. table:: **Table 4** Description of the **metadata** field

      +-------------+---------+---------------------------------------------------------------------------------------------------------+
      | Parameter   | Type    | Description                                                                                             |
      +=============+=========+=========================================================================================================+
      | total_count | Integer | Number of resources that meet the filter criteria. The number is irrelevant to **limit** or **offset**. |
      +-------------+---------+---------------------------------------------------------------------------------------------------------+

   .. _dns_api_62003__table0172144213344:

   .. table:: **Table 5** Parameters in the **links** field

      ========= ====== ============================
      Parameter Type   Description
      ========= ====== ============================
      self      String Link to the current resource
      next      String Link to the next page
      ========= ====== ============================

   .. _dns_api_62003__table619059185111:

   .. table:: **Table 6** Description of the **tag** field

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                          |
      +=======================+=======================+======================================================================================+
      | key                   | String                | Tag key                                                                              |
      |                       |                       |                                                                                      |
      |                       |                       | -  Cannot be left blank.                                                             |
      |                       |                       | -  Must be unique for each resource.                                                 |
      |                       |                       | -  Can contain a maximum of 128 Unicode characters.                                  |
      |                       |                       | -  Can contain letters, digits, spaces, and the following characters: \_ . : = + - @ |
      |                       |                       | -  Cannot start or end with a space, or cannot start with **\_sys\_**.               |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------+
      | value                 | String                | Tag value                                                                            |
      |                       |                       |                                                                                      |
      |                       |                       | -  Can be left blank.                                                                |
      |                       |                       | -  Can contain a maximum of 255 Unicode characters.                                  |
      |                       |                       | -  Can contain letters, digits, spaces, and the following characters: \_ . : = + - @ |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "links": {
              "self": "https://Endpoint/v2/zones?type=public&limit=11",
              "next": "https://Endpoint/v2/zones?type=public&limit=11&marker=2c9eb155587194ec01587224c9f90149"
          },
          "zones": [
              {
                  "id": "2c9eb155587194ec01587224c9f90149",
                  "name": "example.com.",
                  "description": "This is an example zone.",
                  "email": "xx@example.com",
                  "ttl": 300,
                  "serial": 0,
                  "masters": [],
                  "status": "ACTIVE",
                  "links": {
                      "self": "https://Endpoint/v2/zones/2c9eb155587194ec01587224c9f90149"
                  },
                  "pool_id": "00000000570e54ee01570e9939b20019",
                  "project_id": "e55c6f3dc4e34c9f86353b664ae0e70c",
                  "zone_type": "public",
                  "created_at": "2016-11-17T11:56:03.439",
                  "updated_at": "2016-11-17T11:56:05.528",
                  "record_num": 2
              },
              {
                  "id": "2c9eb155587228570158722996c50001",
                  "name": "example.org.",
                  "description": "This is an example zone.",
                  "email": "xx@example.org",
                  "ttl": 300,
                  "serial": 0,
                  "masters": [],
                  "status": "PENDING_CREATE",
                  "links": {
                      "self": "https://Endpoint/v2/zones/2c9eb155587228570158722996c50001"
                  },
                  "pool_id": "00000000570e54ee01570e9939b20019",
                  "project_id": "e55c6f3dc4e34c9f86353b664ae0e70c",
                  "zone_type": "public",
                  "created_at": "2016-11-17T12:01:17.996",
                  "updated_at": "2016-11-17T12:01:18.528",
                  "record_num": 2
              }
          ],
          "metadata": {
              "total_count": 2
          }
      }

Returned Value
--------------

If a 2xx status code is returned, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
