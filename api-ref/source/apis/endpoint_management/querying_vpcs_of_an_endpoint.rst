:original_name: ListEndpointVpcs.html

.. _ListEndpointVpcs:

Querying VPCs of an Endpoint
============================

Function
--------

This API is used to query VPCs of an endpoint.

URI
---

GET /v2.1/vpcs

.. table:: **Table 1** Query parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                            |
   +=================+=================+=================+========================================================================================================+
   | limit           | No              | Integer         | Number of resources on each page.                                                                      |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | The value ranges from **0** to **500**.                                                                |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | Commonly used values are **10**, **20**, and **50**. The default value is **500**.                     |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+
   | offset          | No              | Integer         | Start offset of the pagination query. The query will start from the next resource of the offset value. |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | The value ranges from **0** to **2147483647**.                                                         |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | The default value is **0**.                                                                            |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | If **marker** is not left blank, the query starts from the resource specified by **marker**.           |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+
   | vpc_id          | No              | String          | ID of the VPC to be queried                                                                            |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameter

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token.                                                                                                                 |
   |                 |                 |                 |                                                                                                                             |
   |                 |                 |                 | The token can be obtained by calling an IAM API. The value of **X-Subject-Token** in the response header is the user token. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+-----------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | Parameter | Type                                                                                                | Description                                       |
   +===========+=====================================================================================================+===================================================+
   | vpcs      | Array of :ref:`VpcsData <listendpointvpcs__en-us_topic_0000002279177765_response_vpcsdata>` objects | VPCs of an endpoint                               |
   +-----------+-----------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | metadata  | :ref:`metadata <listendpointvpcs__en-us_topic_0000002279177765_response_metadata>` object           | Number of resources that meet the query condition |
   +-----------+-----------------------------------------------------------------------------------------------------+---------------------------------------------------+

.. _listendpointvpcs__en-us_topic_0000002279177765_response_vpcsdata:

.. table:: **Table 4** VpcsData

   +-------------------------+---------+--------------------------------------------------+
   | Parameter               | Type    | Description                                      |
   +=========================+=========+==================================================+
   | id                      | String  | VPC ID, which is a UUID used to identify the VPC |
   +-------------------------+---------+--------------------------------------------------+
   | inbound_endpoint_count  | Integer | Number of inbound endpoints in a VPC             |
   +-------------------------+---------+--------------------------------------------------+
   | outbound_endpoint_count | Integer | Number of outbound endpoints in a VPC            |
   +-------------------------+---------+--------------------------------------------------+

.. _listendpointvpcs__en-us_topic_0000002279177765_response_metadata:

.. table:: **Table 5** metadata

   +-------------+---------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Type    | Description                                                                                             |
   +=============+=========+=========================================================================================================+
   | total_count | Integer | Number of resources that meet the filter criteria. The number is irrelevant to **limit** or **offset**. |
   +-------------+---------+---------------------------------------------------------------------------------------------------------+

Example Requests
----------------

None

Example Responses
-----------------

**Status code: 200**

Successful request

.. code-block::

   {
     "vpcs" : [ {
       "id" : "02443811-acf1-4c22-8f44-e3adf19f6097",
       "inbound_endpoint_count" : 32
     } ],
     "metadata" : {
       "total_count" : 1
     }
   }

Status Codes
------------

=========== ==================
Status Code Description
=========== ==================
200         Successful request
=========== ==================

Error Codes
-----------

For details, see :ref:`Error Code <dns_api_80003>`.
