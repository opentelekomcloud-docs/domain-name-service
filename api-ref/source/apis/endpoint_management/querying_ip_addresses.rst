:original_name: ListEndpointIpaddresses.html

.. _ListEndpointIpaddresses:

Querying IP Addresses
=====================

Function
--------

This API is used to query IP addresses of an endpoint.

URI
---

GET /v2.1/endpoints/{endpoint_id}/ipaddresses

.. table:: **Table 1** Path parameter

   =========== ========= ====== ===========
   Parameter   Mandatory Type   Description
   =========== ========= ====== ===========
   endpoint_id Yes       String Endpoint ID
   =========== ========= ====== ===========

.. _listendpointipaddresses__table140817549332:

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================================================+
   | limit           | No              | Integer         | Number of resources returned on each page.                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | Value range: 0 to 500                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | Commonly used values are **10**, **20**, and **50**. The default value is **500**.                                                                          |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | Integer         | The offset of pagination query. It specifies the number of rows or records to skip from the beginning of the result set before retrieving the desired data. |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | Value range: 0 to 2147483647                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | The default value is **0**.                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | If **marker** is not left blank, the query starts from the resource specified by **marker**.                                                                |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | No              | String          | Resource status.                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                             |
   |                 |                 |                 | For details, see :ref:`Enumeration Values <dns_api_80005>`.                                                                                                 |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameter

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

.. table:: **Table 4** Response body parameter

   +-------------+--------------------------------------------------------------------------------------------------------------------------+---------------------+
   | Parameter   | Type                                                                                                                     | Description         |
   +=============+==========================================================================================================================+=====================+
   | ipaddresses | Array of :ref:`IpaddressesData <listendpointipaddresses__en-us_topic_0000002244218616_response_ipaddressesdata>` objects | List data structure |
   +-------------+--------------------------------------------------------------------------------------------------------------------------+---------------------+

.. _listendpointipaddresses__en-us_topic_0000002244218616_response_ipaddressesdata:

.. table:: **Table 5** IpaddressesData

   +-----------------------+-----------------------+---------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                   |
   +=======================+=======================+===============================================================+
   | status                | String                | Resource status                                               |
   |                       |                       |                                                               |
   |                       |                       | The value can be:                                             |
   |                       |                       |                                                               |
   |                       |                       | -  **ACTIVE**: The resource is working normally.              |
   |                       |                       |                                                               |
   |                       |                       | -  **PENDING_CREATE**: The resource is being created.         |
   |                       |                       |                                                               |
   |                       |                       | -  **PENDING_DELETE**: The resource is being deleted.         |
   |                       |                       |                                                               |
   |                       |                       | -  **ERROR**: failed                                          |
   +-----------------------+-----------------------+---------------------------------------------------------------+
   | id                    | String                | IP address ID, which is a resource identifier in UUID format. |
   +-----------------------+-----------------------+---------------------------------------------------------------+
   | ip                    | String                | IP address                                                    |
   +-----------------------+-----------------------+---------------------------------------------------------------+
   | create_time           | String                | Creation time.                                                |
   |                       |                       |                                                               |
   |                       |                       | Format: *yyyy-MM-dd'T'HH:mm:ss.SSS*                           |
   +-----------------------+-----------------------+---------------------------------------------------------------+
   | update_time           | String                | Update time.                                                  |
   |                       |                       |                                                               |
   |                       |                       | Format: *yyyy-MM-dd'T'HH:mm:ss.SSS*                           |
   +-----------------------+-----------------------+---------------------------------------------------------------+
   | subnet_id             | String                | Subnet ID                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------+
   | error_info            | String                | Error message                                                 |
   +-----------------------+-----------------------+---------------------------------------------------------------+

Example Requests
----------------

None

Example Responses
-----------------

**Status code: 200**

Successful request

.. code-block::

   {
     "ipaddresses" : [ {
       "status" : "ACTIVE",
       "id" : "ff80808169be2efb0169bef85d740015",
       "ip" : "192.168.0.11",
       "create_time" : "2019-03-27T19:45:41.181",
       "update_time" : "2019-03-27T19:45:42.181",
       "subnet_id" : "485620bd-482a-43e7-9718-410079f860e2",
       "error_info" : null
     }, {
       "status" : "ACTIVE",
       "id" : "ff80808169be2efb0169bef85d740014",
       "ip" : "192.168.0.10",
       "create_time" : "2019-03-27T19:45:41.181",
       "update_time" : "2019-03-27T19:45:42.181",
       "subnet_id" : "485620bd-482a-43e7-9718-410079f860e2",
       "error_info" : null
     } ]
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
