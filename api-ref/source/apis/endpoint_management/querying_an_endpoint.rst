:original_name: ShowEndpoint.html

.. _ShowEndpoint:

Querying an Endpoint
====================

Function
--------

This API is used to query an endpoint.

URI
---

GET /v2.1/endpoints/{endpoint_id}

.. table:: **Table 1** Path parameter

   =========== ========= ====== ===========
   Parameter   Mandatory Type   Description
   =========== ========= ====== ===========
   endpoint_id Yes       String Endpoint ID
   =========== ========= ====== ===========

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

.. table:: **Table 3** Response body parameter

   +-----------+-----------------------------------------------------------------------------------------------+-------------+
   | Parameter | Type                                                                                          | Description |
   +===========+===============================================================================================+=============+
   | endpoint  | :ref:`EndpointResp <showendpoint__en-us_topic_0000002244218612_response_endpointresp>` object | Endpoint    |
   +-----------+-----------------------------------------------------------------------------------------------+-------------+

.. _showendpoint__en-us_topic_0000002244218612_response_endpointresp:

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

Example Requests
----------------

None

Example Responses
-----------------

**Status code: 200**

Response to the request for querying an endpoint

.. code-block::

   {
     "endpoint" : {
       "id" : "ff80808169b445ab0169b541bc5c0000",
       "name" : "poi-17",
       "direction" : "inbound",
       "status" : "ACTIVE",
       "vpc_id" : "02443811-acf1-4c22-8f44-e3adf19f6097",
       "ipaddress_count" : 4,
       "resolver_rule_count" : 0,
       "create_time" : "2019-03-25T14:29:37.997",
       "update_time" : "2019-03-25T14:29:37.997"
     }
   }

Status Codes
------------

=========== ================================================
Status Code Description
=========== ================================================
200         Response to the request for querying an endpoint
=========== ================================================

Error Codes
-----------

For details, see :ref:`Error Code <dns_api_80003>`.
