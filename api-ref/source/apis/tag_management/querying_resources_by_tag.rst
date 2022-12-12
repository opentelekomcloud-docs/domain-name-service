:original_name: dns_api_67006.html

.. _dns_api_67006:

Querying Resources by Tag
=========================

Function
--------

Query DNS resources by tag.

Resources are sorted by creation time in descending order.

URI
---

POST /v2/{project_id}/{resource_type}/resource_instances/action

For details, see :ref:`Table 1 <dns_api_67006__ta232abacc5c94e828ce60c58a8982bee>`.

.. _dns_api_67006__ta232abacc5c94e828ce60c58a8982bee:

.. table:: **Table 1** Parameters in the URI

   +---------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                                                                                                       |
   +===============+===========+========+===================================================================================================================================================+
   | project_id    | Yes       | String | Project ID. You can obtain it in :ref:`Obtaining a Project ID <dns_api_80007>`.                                                                   |
   +---------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource_type | Yes       | String | Resource type, which can be **DNS-public_zone**, **DNS-private_zone**, **DNS-public_recordset**, **DNS-private_recordset**, or **DNS-ptr_record** |
   +---------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameters in the request

      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                           |
      +=================+=================+=================+=======================================================================================================================================================================================================================================================================================+
      | tags            | No              | Array of object | Includes specified tags. For details, see :ref:`Table 3 <dns_api_67006__tb2c210e5c1f44fad9eaeb485e2da1424>`.                                                                                                                                                                          |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | The structure body is mandatory. A maximum of 20 tag keys are allowed in each query operation. The tag key cannot be left blank or set to the empty string. One tag key can have up to 10 tag values. Each tag key must be unique, and the tag values of one key must also be unique. |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tags_any        | No              | Array of object | Includes any of the specified tags. For details, see :ref:`Table 3 <dns_api_67006__tb2c210e5c1f44fad9eaeb485e2da1424>`.                                                                                                                                                               |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | The structure body is mandatory. A maximum of 20 tag keys are allowed in each query operation. The tag key cannot be left blank or set to the empty string. One tag key can have up to 10 tag values. Each tag key must be unique, and the tag values of one key must also be unique. |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | not_tags        | No              | Array of object | Excludes specified tags. For details, see :ref:`Table 3 <dns_api_67006__tb2c210e5c1f44fad9eaeb485e2da1424>`.                                                                                                                                                                          |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | The structure body is mandatory. A maximum of 20 tag keys are allowed in each query operation. The tag key cannot be left blank or set to the empty string. One tag key can have up to 10 tag values. Each tag key must be unique, and the tag values of one key must also be unique. |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | not_tags_any    | No              | Array of object | Excludes any of the specified tags. For details, see :ref:`Table 3 <dns_api_67006__tb2c210e5c1f44fad9eaeb485e2da1424>`.                                                                                                                                                               |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | The structure body is mandatory. A maximum of 20 tag keys are allowed in each query operation. The tag key cannot be left blank or set to the empty string. One tag key can have up to 10 tag values. Each tag key must be unique, and the tag values of one key must also be unique. |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit           | No              | Integer         | Number of resources on each page                                                                                                                                                                                                                                                      |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | The value range is 1-1000.                                                                                                                                                                                                                                                            |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | -  If the value of **action** is set to **filter**, the default value is **1000**.                                                                                                                                                                                                    |
      |                 |                 |                 | -  If **action** is set to **count**, this parameter does not take effect.                                                                                                                                                                                                            |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | offset          | No              | Integer         | Start offset of pagination query. The query will start from the next resource of the offset value.                                                                                                                                                                                    |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | The value ranges from **0** to **2147483647**.                                                                                                                                                                                                                                        |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | The default value is 0.                                                                                                                                                                                                                                                               |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | -  You do not need to specify this parameter when querying resources on the first page.                                                                                                                                                                                               |
      |                 |                 |                 | -  When you query resources on subsequent pages, set the value of **offset** to the location returned in the response body for the previous query.                                                                                                                                    |
      |                 |                 |                 | -  If **action** is set to **filter**, this parameter takes effect. Its value can be 0 (default) or a positive integer.                                                                                                                                                               |
      |                 |                 |                 | -  If **action** is set to **count**, this parameter does not take effect.                                                                                                                                                                                                            |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | action          | Yes             | String          | Operation to be performed                                                                                                                                                                                                                                                             |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | The value can be:                                                                                                                                                                                                                                                                     |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | -  **filter**: queries resources in pages by filter condition.                                                                                                                                                                                                                        |
      |                 |                 |                 | -  **count**: queries the total number of resources.                                                                                                                                                                                                                                  |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | matches         | No              | Array of object | Field to be matched. For details, see :ref:`Table 4 <dns_api_67006__tddefa9c37bda4fab97a689a2dcf0ac0e>`.                                                                                                                                                                              |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | This parameter specifies the key-value pair to be matched in the query.                                                                                                                                                                                                               |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | If **value** is left blank, an exact match is performed. Otherwise, a fuzzy match is performed.                                                                                                                                                                                       |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_67006__tb2c210e5c1f44fad9eaeb485e2da1424:

   .. table:: **Table 3** Parameters in the **tags** field

      +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type             | Description                                                                                                                 |
      +=================+=================+==================+=============================================================================================================================+
      | key             | Yes             | String           | Tag key. A key contains 127 Unicode characters and cannot be blank. (This parameter is not verified in the search process.) |
      +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | values          | Yes             | Array of strings | Values of the tag.                                                                                                          |
      |                 |                 |                  |                                                                                                                             |
      |                 |                 |                  | A value contains a maximum of 255 Unicode characters.                                                                       |
      |                 |                 |                  |                                                                                                                             |
      |                 |                 |                  | The asterisk (``*``) is a reserved character.                                                                               |
      |                 |                 |                  |                                                                                                                             |
      |                 |                 |                  | If the value starts with an asterisk (``*``), fuzzy matching will work for the string following the asterisk.               |
      |                 |                 |                  |                                                                                                                             |
      |                 |                 |                  | If this parameter is not specified, any value is matched. The values are in OR relationship.                                |
      +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_67006__tddefa9c37bda4fab97a689a2dcf0ac0e:

   .. table:: **Table 4** Parameters in the **matches** field

      +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Mandatory | Type   | Description                                                                                                                   |
      +===========+===========+========+===============================================================================================================================+
      | key       | Yes       | String | Key to be matched. Currently, it can only be **resource_name**.                                                               |
      +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------+
      | value     | Yes       | String | Value to be matched. It contains a maximum of 255 Unicode characters and cannot contain underscores (_) and percent sign (%). |
      +-----------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   Query DNS resources by tag.

   .. code-block:: text

      POST https://{DNS_Endpoint}/v2/{project_id}/DNS-private_zone/resource_instances/action

   The following is a request example when **action** is set to **filter**:

   .. code-block::

      {
          "offset": "100",
          "limit": "100",
          "action": "filter",
          "matches": [
              {
                  "key": "resource_name",
                  "value": "resource1"
              }
          ],
          "not_tags": [
              {
                  "key": "key1",
                  "values": [
                      "*value1",
                      "value2"
                  ]
              }
          ],
          "tags": [
              {
                  "key": "key1",
                  "values": [
                      "*value1",
                      "value2"
                  ]
              }
          ],
          "tags_any": [
              {
                  "key": "key1",
                  "values": [
                      "value1",
                      "value2"
                  ]
              }
          ],
          "not_tags_any": [
              {
                  "key": "key1",
                  "values": [
                      "value1",
                      "value2"
                  ]
              }
          ]
      }

   The following is a request example when **action** is set to **count**:

   .. code-block::

      {
          "action": "count",
          "not_tags": [
              {
                  "key": "key1",
                  "values": [
                      "value1",
                      "*value2"
                  ]
              }
          ],
          "tags": [
              {
                  "key": "key1",
                  "values": [
                      "value1",
                      "value2"
                  ]
              },
              {
                  "key": "key2",
                  "values": [
                      "value1",
                      "value2"
                  ]
              }
          ],
          "tags_any": [
              {
                  "key": "key1",
                  "values": [
                      "value1",
                      "value2"
                  ]
              }
          ],
          "not_tags_any": [
              {
                  "key": "key1",
                  "values": [
                      "value1",
                      "value2"
                  ]
              }
          ],
          "matches": [
              {
                  "key": "resource_name",
                  "value": "resource1"
              }
          ]
      }

Response
--------

-  Parameter description

   .. table:: **Table 5** Parameters in the response

      +-------------+-----------------+---------------------------------------------------------------------------------------------------------+
      | Parameter   | Type            | Description                                                                                             |
      +=============+=================+=========================================================================================================+
      | resources   | Array of object | Resource list For details, see :ref:`Table 6 <dns_api_67006__t3e476a1cfb8049779a2717fcc171190c>`.       |
      +-------------+-----------------+---------------------------------------------------------------------------------------------------------+
      | total_count | Integer         | Number of resources that meet the filter criteria. The number is irrelevant to **limit** or **offset**. |
      +-------------+-----------------+---------------------------------------------------------------------------------------------------------+

   .. _dns_api_67006__t3e476a1cfb8049779a2717fcc171190c:

   .. table:: **Table 6** Parameters in the **resources** field

      +-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Type            | Description                                                                                                                                   |
      +=================+=================+===============================================================================================================================================+
      | resource_id     | String          | Resource ID                                                                                                                                   |
      +-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | resource_detail | String          | Resource details. This field is reserved for subsequent extension, and its value defaults to an empty string.                                 |
      +-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | tags            | Array of object | List of queried tags. If no tag is matched, an empty array is returned. For details, see :ref:`Table 2 <dns_api_80006__table19530794112436>`. |
      +-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | resource_name   | String          | Resource name. If no resource name is matched, the value is left blank.                                                                       |
      +-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   The following is a request example when **action** is set to **filter**:

   .. code-block::

      {
          "resources": [
              {
                  "resource_detail": null,
                  "resource_id": "cdfs_cefs_wesas_12_dsad",
                  "resource_name": "resouece1",
                  "tags": [
                      {
                          "key": "key1",
                          "value": "value1"
                      },
                      {
                          "key": "key2",
                          "value": "value1"
                      }
                  ]
              }
          ],
          "total_count": 1000
      }

   The following is a request example when **action** is set to **count**:

   .. code-block::

      {
          "total_count": 1000
      }

Returned Value
--------------

If the API call returns a code of 2\ *xx*, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
