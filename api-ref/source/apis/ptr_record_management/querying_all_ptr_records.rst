:original_name: dns_api_66004.html

.. _dns_api_66004:

Querying All PTR Records
========================

Function
--------

Query PTR records of EIPs.

URI
---

GET /v2/reverse/floatingips?limit={limit}&marker={marker}&offset={offset}&tags={tags}&status={status}

For details, see :ref:`Table 1 <dns_api_66004__table1562846014112>`.

.. _dns_api_66004__table1562846014112:

.. table:: **Table 1** Parameters in the URI

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                             |
   +=================+=================+=================+=========================================================================================================================================+
   | marker          | No              | String          | Start resource ID of pagination query                                                                                                   |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | If the parameter is left blank, only resources on the first page are queried.                                                           |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | The value is left blank by default.                                                                                                     |
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
   | status          | No              | String          | Resource status                                                                                                                         |
   |                 |                 |                 |                                                                                                                                         |
   |                 |                 |                 | For details, see :ref:`Resource Status <dns_api_80005__section33673592114748>`.                                                         |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

-  Example request

   List required PTR records.

   .. code-block:: text

      GET https://{DNS_Endpoint}/v2/reverse/floatingips

Response
--------

-  Parameter description

   .. table:: **Table 2** Parameters in the response

      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                                                                    |
      +=======================+=======================+================================================================================================================================================================+
      | links                 | Object                | Link to the current resource or other related resources.                                                                                                       |
      |                       |                       |                                                                                                                                                                |
      |                       |                       | When a response is broken into pages, a **next** link is provided to retrieve all results. For details, see :ref:`Table 5 <dns_api_66004__table354521744216>`. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | metadata              | Object                | Number of resources that meet the filter condition. For details, see :ref:`Table 4 <dns_api_66004__table16355953155210>`.                                      |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | floatingips           | Array of object       | PTR record object list. For details, see :ref:`Table 3 <dns_api_66004__table43740677113542>`.                                                                  |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_66004__table43740677113542:

   .. table:: **Table 3** Description of the **floatingips** field

      +-----------------------+-----------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                                                            | Description                                                                                                                                                    |
      +=======================+=================================================================+================================================================================================================================================================+
      | id                    | String                                                          | PTR record ID, which is in **{region}:{floatingip_id}** format                                                                                                 |
      +-----------------------+-----------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ptrdname              | String                                                          | Domain name of the PTR record                                                                                                                                  |
      +-----------------------+-----------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description           | String                                                          | PTR record description                                                                                                                                         |
      +-----------------------+-----------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ttl                   | Integer                                                         | PTR record cache duration (in seconds) on a local DNS server. The longer the duration is, the slower the update takes effect.                                  |
      |                       |                                                                 |                                                                                                                                                                |
      |                       |                                                                 | If your service address is frequently changed, set TTL to a smaller value.                                                                                     |
      |                       |                                                                 |                                                                                                                                                                |
      |                       |                                                                 | The value ranges from **1** to **2147483647**.                                                                                                                 |
      |                       |                                                                 |                                                                                                                                                                |
      |                       |                                                                 | The default value is **300**.                                                                                                                                  |
      +-----------------------+-----------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | address               | String                                                          | EIP                                                                                                                                                            |
      +-----------------------+-----------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                                                          | Resource status                                                                                                                                                |
      |                       |                                                                 |                                                                                                                                                                |
      |                       |                                                                 | For details, see :ref:`Resource Status <dns_api_80005__section33673592114748>`.                                                                                |
      +-----------------------+-----------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | action                | String                                                          | Requested operation on the resource                                                                                                                            |
      |                       |                                                                 |                                                                                                                                                                |
      |                       |                                                                 | The value can be **CREATE**, **UPDATE**, **DELETE**, or **NONE**.                                                                                              |
      |                       |                                                                 |                                                                                                                                                                |
      |                       |                                                                 | **NONE** indicates that no operation will be performed.                                                                                                        |
      +-----------------------+-----------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | links                 | Object                                                          | Link to the current resource or other related resources.                                                                                                       |
      |                       |                                                                 |                                                                                                                                                                |
      |                       |                                                                 | When a response is broken into pages, a **next** link is provided to retrieve all results. For details, see :ref:`Table 5 <dns_api_66004__table354521744216>`. |
      +-----------------------+-----------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tags                  | Array of :ref:`tag <dns_api_66004__table8387205213225>` objects | Resource tag.                                                                                                                                                  |
      |                       |                                                                 |                                                                                                                                                                |
      |                       |                                                                 | The format is as follows: **key1,value1|key2,value2**.                                                                                                         |
      |                       |                                                                 |                                                                                                                                                                |
      |                       |                                                                 | Multiple tags are separated by vertical bar (|). The key and value of each tag are separated by comma (,).                                                     |
      |                       |                                                                 |                                                                                                                                                                |
      |                       |                                                                 | The tags are in AND relationship.                                                                                                                              |
      |                       |                                                                 |                                                                                                                                                                |
      |                       |                                                                 | For details, see :ref:`Table 6 <dns_api_66004__table8387205213225>`.                                                                                           |
      |                       |                                                                 |                                                                                                                                                                |
      |                       |                                                                 | Exact matching will work. If the value starts with an asterisk (``*``), fuzzy matching will work for the string following the asterisk.                        |
      |                       |                                                                 |                                                                                                                                                                |
      |                       |                                                                 | The value is left blank by default.                                                                                                                            |
      +-----------------------+-----------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_66004__table16355953155210:

   .. table:: **Table 4** Description of the **metadata** field

      +-------------+---------+---------------------------------------------------------------------------------------------------------+
      | Parameter   | Type    | Description                                                                                             |
      +=============+=========+=========================================================================================================+
      | total_count | Integer | Number of resources that meet the filter criteria. The number is irrelevant to **limit** or **offset**. |
      +-------------+---------+---------------------------------------------------------------------------------------------------------+

   .. _dns_api_66004__table354521744216:

   .. table:: **Table 5** Parameters in the **links** field

      ========= ====== ============================
      Parameter Type   Description
      ========= ====== ============================
      self      String Link to the current resource
      next      String Link to the next page
      ========= ====== ============================

   .. _dns_api_66004__table8387205213225:

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
              "self": "https://Endpoint/v2/reverse/floatingips",
              "next": "https://Endpoint/v2/zones?id=&limit=1&marker=region_id:c5504932-bf23-4171-b655-b87a6bc59334"
          },
          "metadata": {
              "total_count": 1
          },
          "floatingips": [
              {
                  "id": "region_id:c5504932-bf23-4171-b655-b87a6bc59334",
                  "ptrdname": "www.example.com.",
                  "description": "Description for this PTR record",
                  "address": "10.154.52.138",
                  "action": "NONE",
                  "ttl": 300,
                  "status": "ACTIVE",
                  "links": {
                      "self": "https://Endpoint/v2/reverse/floatingips/region_id:c5504932-bf23-4171-b655-b87a6bc59334"
                  }
              }
          ]
      }

Returned Value
--------------

If a 2xx status code is returned, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
