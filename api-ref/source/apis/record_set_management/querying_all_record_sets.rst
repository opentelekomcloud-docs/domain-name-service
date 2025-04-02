:original_name: dns_api_64003.html

.. _dns_api_64003:

Querying All Record Sets
========================

Function
--------

Query record sets in list.

URI
---

GET /v2/recordsets?zone_type={zone_type}&limit={limit}&marker={marker}&offset={offset}&tags={tags}&status={status}&type={type}&name={name}&id={id}&records={records}&sort_key={sort_key}&sort_dir={sort_dir}

For details, see :ref:`Table 1 <dns_api_64003__table40248354>`.

.. _dns_api_64003__table40248354:

.. table:: **Table 1** Parameters in the URI

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================================================+
   | zone_type       | No              | String          | Zone type of the record set to be queried, which can be **public** or **private**                                                                           |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | -  **public**: Record sets in public zones are queried.                                                                                                     |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | -  **private**: Record sets in private zones are queried.                                                                                                   |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 |    If the value is left blank, record sets in public zones are queried by default.                                                                          |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | A fuzzy search will be performed.                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | The default value is **public**.                                                                                                                            |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker          | No              | String          | Start resource ID of pagination query                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | If the parameter is left blank, only resources on the first page are queried.                                                                               |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | The value is left blank by default.                                                                                                                         |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Number of resources on each page                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | The value ranges from **0** to **500**.                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | Commonly used values are **10**, **20**, and **50**. The default value is **500**.                                                                          |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | Integer         | Start offset of pagination query. The query will start from the next resource of the offset value.                                                          |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | The value ranges from **0** to **2147483647**.                                                                                                              |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | The default value is **0**.                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | If **marker** is not left blank, the query starts from the resource specified by **marker**.                                                                |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags            | No              | String          | Resource tag                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | The format is as follows: **key1,value1|key2,value2**.                                                                                                      |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | Multiple tags are separated by vertical bar (|). The key and value of each tag are separated by comma (,).                                                  |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | The tags are in AND relationship.                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | For details, see :ref:`Adding Resource Tags <dns_api_67001>`.                                                                                               |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | Exact matching will work. If the value starts with an asterisk (``*``), fuzzy matching will work for the string following the asterisk.                     |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | The value is left blank by default.                                                                                                                         |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | No              | String          | Status of the record sets to be queried                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | The value can be **ACTIVE**, **ERROR**, **DISABLE**, **FREEZE**, **PENDING_CREATE**, **PENDING_UPDATE**, or **PENDING_DELETE**.                             |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | For details, see :ref:`Resource Status <dns_api_80005__section33673592114748>`.                                                                             |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | A fuzzy search will be performed.                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | The value is left blank by default.                                                                                                                         |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | No              | String          | Type of the record sets to be queried                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | The value can be **A**, **AAAA**, **MX**, **CNAME**, **TXT**, **NS**, **SOA**, **SRV**, **CAA** (only in public zones), or **PTR** (only in private zones). |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | For details, see :ref:`Record Set Type <dns_api_80005__section1188113824413>`.                                                                              |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | Exact matching will work.                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | The value is left blank by default.                                                                                                                         |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | Names of record sets to be queried                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | A fuzzy search will be performed.                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | The value is left blank by default.                                                                                                                         |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id              | No              | String          | IDs of record sets to be queried                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | A fuzzy search will be performed.                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | The value is left blank by default.                                                                                                                         |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | records         | No              | String          | Value included in the values of record sets to be queried                                                                                                   |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | A fuzzy search will be performed.                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | The value is left blank by default.                                                                                                                         |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sort_key        | No              | String          | Sorting condition of the record set list                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | The value can be:                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | -  **name**: domain name                                                                                                                                    |
   |                 |                 |                 | -  **type**: record set type                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | The default value is left blank, indicating that the records are not sorted.                                                                                |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sort_dir        | No              | String          | Sorting order of the record set list                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | The value can be:                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | -  **desc**: descending order                                                                                                                               |
   |                 |                 |                 | -  **asc**: ascending order                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | The default value is left blank, indicating that the records are not sorted.                                                                                |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

-  Example request

   Query A record sets whose name contains **www.example.com** in private zones:

   .. code-block:: text

      GET https://{DNS_Endpoint}/v2/recordsets?zone_type=private&type=A&name=www.example.com

Response
--------

-  Parameter description

   .. table:: **Table 2** Parameters in the response

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                                                         |
      +=======================+=======================+=====================================================================================================================================================+
      | links                 | Object                | Link to the current resource or other related resources. When a response is broken into pages, a **next** link is provided to retrieve all results. |
      |                       |                       |                                                                                                                                                     |
      |                       |                       | For details, see :ref:`Table 5 <dns_api_64003__table354521744216>`.                                                                                 |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | recordsets            | Array of object       | Record set list object. For details, see :ref:`Table 3 <dns_api_64003__table18580737>`.                                                             |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | metadata              | Object                | Total number of resources that meet the filter criteria. For details, see :ref:`Table 4 <dns_api_64003__table9971756154520>`.                       |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_64003__table18580737:

   .. table:: **Table 3** Description of the **recordsets** field

      +-----------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                                                          | Description                                                                                                                                                 |
      +=======================+===============================================================+=============================================================================================================================================================+
      | id                    | String                                                        | Record set ID                                                                                                                                               |
      +-----------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                                                        | Record set name                                                                                                                                             |
      +-----------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description           | String                                                        | Record set description                                                                                                                                      |
      +-----------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | zone_id               | String                                                        | Zone ID of the record set                                                                                                                                   |
      +-----------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | zone_name             | String                                                        | Zone name of the record set                                                                                                                                 |
      +-----------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | type                  | String                                                        | Record set type                                                                                                                                             |
      |                       |                                                               |                                                                                                                                                             |
      |                       |                                                               | The value can be **A**, **AAAA**, **MX**, **CNAME**, **TXT**, **NS**, **SOA**, **SRV**, **CAA** (only in public zones), or **PTR** (only in private zones). |
      |                       |                                                               |                                                                                                                                                             |
      |                       |                                                               | For details, see :ref:`Record Set Type <dns_api_80005__section1188113824413>`.                                                                              |
      +-----------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ttl                   | Integer                                                       | Record set cache duration (in seconds) on a local DNS server. The longer the duration is, the slower the update takes effect.                               |
      |                       |                                                               |                                                                                                                                                             |
      |                       |                                                               | If your service address is frequently changed, set TTL to a smaller value.                                                                                  |
      |                       |                                                               |                                                                                                                                                             |
      |                       |                                                               | Value range:                                                                                                                                                |
      |                       |                                                               |                                                                                                                                                             |
      |                       |                                                               | -  Public zone: **1**\ ``-``\ **2147483647**                                                                                                                |
      |                       |                                                               | -  Private zone: **1**\ ``-``\ **2147483647**                                                                                                               |
      |                       |                                                               |                                                                                                                                                             |
      |                       |                                                               | The default value is **300**.                                                                                                                               |
      +-----------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | records               | Array of strings                                              | Record set value                                                                                                                                            |
      +-----------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | create_at             | String                                                        | Time when the record set was created                                                                                                                        |
      |                       |                                                               |                                                                                                                                                             |
      |                       |                                                               | The value format is yyyy-MM-dd'T'HH:mm:ss.SSS.                                                                                                              |
      +-----------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | update_at             | String                                                        | Time when the record set was updated                                                                                                                        |
      |                       |                                                               |                                                                                                                                                             |
      |                       |                                                               | The value format is yyyy-MM-dd'T'HH:mm:ss.SSS.                                                                                                              |
      +-----------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                                                        | Resource status                                                                                                                                             |
      |                       |                                                               |                                                                                                                                                             |
      |                       |                                                               | For details, see :ref:`Resource Status <dns_api_80005__section33673592114748>`.                                                                             |
      +-----------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | default               | Boolean                                                       | Whether the record set is created by default                                                                                                                |
      |                       |                                                               |                                                                                                                                                             |
      |                       |                                                               | A default record set cannot be deleted.                                                                                                                     |
      +-----------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | project_id            | String                                                        | Project ID of the record set                                                                                                                                |
      +-----------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | links                 | Object                                                        | Link to the current resource or other related resources                                                                                                     |
      |                       |                                                               |                                                                                                                                                             |
      |                       |                                                               | When a response is broken into pages, a **next** link is provided to retrieve all results.                                                                  |
      |                       |                                                               |                                                                                                                                                             |
      |                       |                                                               | For details, see :ref:`Table 5 <dns_api_64003__table354521744216>`.                                                                                         |
      +-----------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tags                  | Array of :ref:`tag <dns_api_64003__table36911165107>` objects | Resource tag.                                                                                                                                               |
      |                       |                                                               |                                                                                                                                                             |
      |                       |                                                               | The format is as follows: **key1,value1|key2,value2**.                                                                                                      |
      |                       |                                                               |                                                                                                                                                             |
      |                       |                                                               | Multiple tags are separated by vertical bar (|). The key and value of each tag are separated by comma (,).                                                  |
      |                       |                                                               |                                                                                                                                                             |
      |                       |                                                               | The tags are in AND relationship.                                                                                                                           |
      |                       |                                                               |                                                                                                                                                             |
      |                       |                                                               | For details, see :ref:`Table 6 <dns_api_64003__table36911165107>`.                                                                                          |
      |                       |                                                               |                                                                                                                                                             |
      |                       |                                                               | Exact matching will work. If the value starts with an asterisk (``*``), fuzzy matching will work for the string following the asterisk.                     |
      |                       |                                                               |                                                                                                                                                             |
      |                       |                                                               | It is left blank by default.                                                                                                                                |
      +-----------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_64003__table9971756154520:

   .. table:: **Table 4** Description of the **metadata** field

      +-------------+---------+---------------------------------------------------------------------------------------------------------+
      | Parameter   | Type    | Description                                                                                             |
      +=============+=========+=========================================================================================================+
      | total_count | Integer | Number of resources that meet the filter criteria. The number is irrelevant to **limit** or **offset**. |
      +-------------+---------+---------------------------------------------------------------------------------------------------------+

   .. _dns_api_64003__table354521744216:

   .. table:: **Table 5** Parameters in the **links** field

      ========= ====== ============================
      Parameter Type   Description
      ========= ====== ============================
      self      String Link to the current resource
      next      String Link to the next page
      ========= ====== ============================

   .. _dns_api_64003__table36911165107:

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
              "self": "https://Endpoint/v2/recordsets",
              "next": "https://Endpoint/v2/recordsets?id=&limit=11&marker=2c9eb155587194ec01587224c9f9014a"
          },
          "recordsets": [
              {
                  "id": "2c9eb155587194ec01587224c9f9014a",
                  "name": "example.com.",
                  "type": "SOA",
                  "ttl": 300,
                  "records": [
                      "ns1.hotrot.de. xx.example.com. (1 7200 900 1209600 300)"
                  ],
                  "status": "ACTIVE",
                  "links": {
                      "self": "https://Endpoint/v2/zones/2c9eb155587194ec01587224c9f90149/recordsets/2c9eb155587194ec01587224c9f9014a"
                  },
                  "zone_id": "2c9eb155587194ec01587224c9f90149",
                  "zone_name": "example.com.",
                  "create_at": "2016-11-17T11:56:03.439",
                  "update_at": "2016-11-17T11:56:03.827",
                  "default": true,
                  "project_id": "e55c6f3dc4e34c9f86353b664ae0e70c"
              },
              {
                  "id": "2c9eb155587194ec01587224c9f9014c",
                  "name": "example.com.",
                  "type": "NS",
                  "ttl": 172800,
                  "records": [
                      "ns2.hotrot.de.",
                      "ns1.hotrot.de."
                  ],
                  "status": "ACTIVE",
                  "links": {
                      "self": "https://Endpoint/v2/zones/2c9eb155587194ec01587224c9f90149/recordsets/2c9eb155587194ec01587224c9f9014c"
                  },
                  "zone_id": "2c9eb155587194ec01587224c9f90149",
                  "zone_name": "example.com.",
                  "create_at": "2016-11-17T11:56:03.439",
                  "update_at": "2016-11-17T11:56:03.827",
                  "default": true,
                  "project_id": "e55c6f3dc4e34c9f86353b664ae0e70c"
              },
              {
                  "id": "2c9eb155587228570158722996ca0002",
                  "name": "example.org.",
                  "type": "SOA",
                  "ttl": 300,
                  "records": [
                      "ns1.hotrot.de. xx.example.org. (1 7200 900 1209600 300)"
                  ],
                  "status": "ACTIVE",
                  "links": {
                      "self": "https://Endpoint/v2/zones/2c9eb155587228570158722996c50001/recordsets/2c9eb155587228570158722996ca0002"
                  },
                  "zone_id": "2c9eb155587228570158722996c50001",
                  "zone_name": "example.org.",
                  "create_at": "2016-11-17T12:01:17.996",
                  "update_at": "2016-11-17T12:56:03.827",
                  "default": true,
                  "project_id": "e55c6f3dc4e34c9f86353b664ae0e70c"
              },
              {
                  "id": "2c9eb155587228570158722996ca0004",
                  "name": "example.org.",
                  "type": "NS",
                  "ttl": 172800,
                  "records": [
                      "ns2.hotrot.de.",
                      "ns1.hotrot.de."
                  ],
                  "status": "ACTIVE",
                  "links": {
                      "self": "https://Endpoint/v2/zones/2c9eb155587228570158722996c50001/recordsets/2c9eb155587228570158722996ca0004"
                  },
                  "zone_id": "2c9eb155587228570158722996c50001",
                  "zone_name": "example.org.",
                  "create_at": "2016-11-17T12:01:17.996",
                  "update_at": "2016-11-17T12:56:03.827",
                  "default": true,
                  "project_id": "e55c6f3dc4e34c9f86353b664ae0e70c"
              },
              {
                  "id": "2c9eb155587228570158722b6ac30007",
                  "name": "www.example.com.",
                  "description": "This is an example record set.",
                  "type": "A",
                  "ttl": 300,
                  "records": [
                      "192.168.10.2",
                      "192.168.10.1"
                  ],
                  "status": "ACTIVE",
                  "links": {
                      "self": "https://Endpoint/v2/zones/2c9eb155587194ec01587224c9f90149/recordsets/2c9eb155587228570158722b6ac30007"
                  },
                  "zone_id": "2c9eb155587194ec01587224c9f90149",
                  "zone_name": "example.com.",
                  "create_at": "2016-11-17T12:03:17.827",
                  "update_at": "2016-11-17T12:56:03.827",
                  "default": false,
                  "project_id": "e55c6f3dc4e34c9f86353b664ae0e70c"
              }
          ],
          "metadata": {
              "total_count": 5
          }
      }

Returned Value
--------------

If a 2xx status code is returned, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
