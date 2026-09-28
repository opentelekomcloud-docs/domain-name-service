:original_name: ListEndpoints.html

.. _ListEndpoints:

Querying Endpoints
==================

Function
--------

This API is used to query endpoints.

URI
---

GET /v2.1/endpoints

.. table:: **Table 1** Query parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                            |
   +=================+=================+=================+========================================================================================================+
   | direction       | Yes             | String          | Endpoint direction.                                                                                    |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | The value can be:                                                                                      |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | **inbound**: indicates an inbound endpoint.                                                            |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | **outbound**: indicates an outbound endpoint.                                                          |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+
   | vpc_id          | No              | String          | ID of the VPC to which the endpoint to be queried belongs                                              |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | Endpoint name                                                                                          |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+
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

   +-----------+----------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | Parameter | Type                                                                                                     | Description                                       |
   +===========+==========================================================================================================+===================================================+
   | endpoints | Array of :ref:`EndpointResp <listendpoints__en-us_topic_0000002244058776_response_endpointresp>` objects | Returned endpoints                                |
   +-----------+----------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | metadata  | :ref:`metadata <listendpoints__en-us_topic_0000002244058776_response_metadata>` object                   | Number of resources that meet the query condition |
   +-----------+----------------------------------------------------------------------------------------------------------+---------------------------------------------------+

.. _listendpoints__en-us_topic_0000002244058776_response_endpointresp:

.. table:: **Table 4** EndpointResp

   +-----------------------+-----------------------+------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                |
   +=======================+=======================+============================================================+
   | id                    | String                | Endpoint ID, which is a UUID used to identify the endpoint |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | name                  | String                | Endpoint name                                              |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | direction             | String                | Endpoint direction.                                        |
   |                       |                       |                                                            |
   |                       |                       | The value can be:                                          |
   |                       |                       |                                                            |
   |                       |                       | **inbound**: indicates an inbound endpoint.                |
   |                       |                       |                                                            |
   |                       |                       | **outbound**: indicates an outbound endpoint.              |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | status                | String                | Resource status.                                           |
   |                       |                       |                                                            |
   |                       |                       | The value can be:                                          |
   |                       |                       |                                                            |
   |                       |                       | -  **ACTIVE**: The resource is working normally.           |
   |                       |                       |                                                            |
   |                       |                       | -  **PENDING_CREATE**: The resource is being created.      |
   |                       |                       |                                                            |
   |                       |                       | -  **PENDING_DELETE**: The resource is being deleted.      |
   |                       |                       |                                                            |
   |                       |                       | -  **ERROR**: failed                                       |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | vpc_id                | String                | ID of the VPC to which the endpoint belongs                |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | ipaddress_count       | Integer               | Number of IP addresses of the endpoint                     |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | resolver_rule_count   | Integer               | Number of endpoint rules in the endpoint.                  |
   |                       |                       |                                                            |
   |                       |                       | This parameter is returned only for outbound endpoints.    |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | create_time           | String                | Creation time.                                             |
   |                       |                       |                                                            |
   |                       |                       | Format: *yyyy-MM-dd'T'HH:mm:ss.SSS*                        |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | update_time           | String                | Update time.                                               |
   |                       |                       |                                                            |
   |                       |                       | Format: *yyyy-MM-dd'T'HH:mm:ss.SSS*                        |
   +-----------------------+-----------------------+------------------------------------------------------------+

.. _listendpoints__en-us_topic_0000002244058776_response_metadata:

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

Response to the request for querying the endpoints

.. code-block::

   {
     "endpoints" : [ {
       "id" : "ff80808169bf16c70169bf1d02270000",
       "name" : "poi-666",
       "direction" : "inbound",
       "status" : "ACTIVE",
       "vpc_id" : "02443811-acf1-4c22-8f44-e3adf19f6097",
       "ipaddress_count" : 6,
       "resolver_rule_count" : 0,
       "create_time" : "2019-03-27T12:25:43.181",
       "update_time" : "2019-03-27T12:25:43.181"
     }, {
       "id" : "ff80808169be28130169be2e9dc40004",
       "name" : "poi-667",
       "direction" : "inbound",
       "status" : "ACTIVE",
       "vpc_id" : "02443811-acf1-4c22-8f44-e3adf19f6097",
       "ipaddress_count" : 6,
       "resolver_rule_count" : 0,
       "create_time" : "2019-03-27T08:05:19.916",
       "update_time" : "2019-03-27T08:05:19.916"
     } ],
     "metadata" : {
       "total_count" : 2
     }
   }

Status Codes
------------

=========== ==================================================
Status Code Description
=========== ==================================================
200         Response to the request for querying the endpoints
=========== ==================================================

Error Codes
-----------

For details, see :ref:`Error Code <dns_api_80003>`.
