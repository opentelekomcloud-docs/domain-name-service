:original_name: CreateEndpoint.html

.. _CreateEndpoint:

Creating an Endpoint
====================

Function
--------

This API is used to create an endpoint.

URI
---

POST /v2.1/endpoints

Request Parameters
------------------

.. table:: **Table 1** Request header parameter

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token.                                                                                                                 |
   |                 |                 |                 |                                                                                                                             |
   |                 |                 |                 | The token can be obtained by calling an IAM API. The value of **X-Subject-Token** in the response header is the user token. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Request body parameters

   +-----------------+-----------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                                       | Description                                                                                                                 |
   +=================+=================+============================================================================================================+=============================================================================================================================+
   | name            | Yes             | String                                                                                                     | Endpoint name.                                                                                                              |
   |                 |                 |                                                                                                            |                                                                                                                             |
   |                 |                 |                                                                                                            | It can contain 1 to 64 characters. Only letters, digits, underscores (_), hyphens (-), and periods (.) are allowed.         |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | direction       | Yes             | String                                                                                                     | Endpoint direction.                                                                                                         |
   |                 |                 |                                                                                                            |                                                                                                                             |
   |                 |                 |                                                                                                            | The value can be:                                                                                                           |
   |                 |                 |                                                                                                            |                                                                                                                             |
   |                 |                 |                                                                                                            | **inbound**: indicates an inbound endpoint.                                                                                 |
   |                 |                 |                                                                                                            |                                                                                                                             |
   |                 |                 |                                                                                                            | **outbound**: indicates an outbound endpoint.                                                                               |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | region          | Yes             | String                                                                                                     | Region of the subnet                                                                                                        |
   |                 |                 |                                                                                                            |                                                                                                                             |
   |                 |                 |                                                                                                            | Example: eu-de                                                                                                              |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | ipaddresses     | Yes             | Array of :ref:`IpaddressInfo <createendpoint__en-us_topic_0000002279177753_request_ipaddressinfo>` objects | IP address and subnet of the endpoint. You need to add at least two IP addresses and can add a maximum of six IP addresses. |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------+

.. _createendpoint__en-us_topic_0000002279177753_request_ipaddressinfo:

.. table:: **Table 3** IpaddressInfo

   +-----------+-----------+--------+----------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                        |
   +===========+===========+========+====================================================+
   | subnet_id | Yes       | String | Subnet ID.                                         |
   +-----------+-----------+--------+----------------------------------------------------+
   | ip        | No        | String | Custom IP address, which must fall into the subnet |
   +-----------+-----------+--------+----------------------------------------------------+

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 4** Response body parameter

   +-----------+-------------------------------------------------------------------------------------------------+-------------+
   | Parameter | Type                                                                                            | Description |
   +===========+=================================================================================================+=============+
   | endpoint  | :ref:`EndpointResp <createendpoint__en-us_topic_0000002279177753_response_endpointresp>` object | Endpoint    |
   +-----------+-------------------------------------------------------------------------------------------------+-------------+

.. _createendpoint__en-us_topic_0000002279177753_response_endpointresp:

.. table:: **Table 5** EndpointResp

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

Creating an inbound endpoint, with the subnet ID of IP address 1 to **0463c8a5-fa49-441d-b28b-bc6c35ba04f8** and the custom IP address to **192.168.3.125**, and the subnet ID of IP address 2 to **0463c8a5-fa49-441d-b28b-bc6c35ba04f8** and the custom IP address to **192.168.3.126**

.. code-block:: text

   POST https://{endpoint}/v2.1/endpoints

   {
     "name" : "poi-1",
     "direction" : "inbound",
     "region" : "eu-de",
     "ipaddresses" : [ {
       "subnet_id" : "0463c8a5-fa49-441d-b28b-bc6c35ba04f8",
       "ip" : "192.168.3.125"
     }, {
       "subnet_id" : "0463c8a5-fa49-441d-b28b-bc6c35ba04f8",
       "ip" : "192.168.3.126"
     } ]
   }

Example Responses
-----------------

**Status code: 202**

Response to the request for creating an endpoint

.. code-block::

   {
     "endpoint" : {
       "id" : "ff80808169bf16c70169bf1d02270000",
       "name" : "poi-1",
       "direction" : "inbound",
       "status" : "PENDING_CREATE",
       "vpc_id" : null,
       "ipaddress_count" : 0,
       "resolver_rule_count" : 0,
       "create_time" : "2019-03-27T12:25:43.181",
       "update_time" : "2019-03-27T12:25:43.181"
     }
   }

Status Codes
------------

=========== ================================================
Status Code Description
=========== ================================================
202         Response to the request for creating an endpoint
=========== ================================================

Error Codes
-----------

For details, see :ref:`Error Code <dns_api_80003>`.
