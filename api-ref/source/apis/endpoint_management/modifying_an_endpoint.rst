:original_name: UpdateEndpoint.html

.. _UpdateEndpoint:

Modifying an Endpoint
=====================

Function
--------

This API is used to modify an endpoint.

URI
---

PUT /v2.1/endpoints/{endpoint_id}

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

.. table:: **Table 3** Request body parameter

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                         |
   +=================+=================+=================+=====================================================================================================================+
   | name            | Yes             | String          | Endpoint name.                                                                                                      |
   |                 |                 |                 |                                                                                                                     |
   |                 |                 |                 | It can contain 1 to 64 characters. Only letters, digits, underscores (_), hyphens (-), and periods (.) are allowed. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 4** Response body parameter

   +-----------+-------------------------------------------------------------------------------------------------+-------------+
   | Parameter | Type                                                                                            | Description |
   +===========+=================================================================================================+=============+
   | endpoint  | :ref:`EndpointResp <updateendpoint__en-us_topic_0000002279297653_response_endpointresp>` object | Endpoint    |
   +-----------+-------------------------------------------------------------------------------------------------+-------------+

.. _updateendpoint__en-us_topic_0000002279297653_response_endpointresp:

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

Modifying the endpoint name

.. code-block:: text

   PUT https://{endpoint}/v2.1/endpoints/{endpoint_id}

   {
     "name" : "2118"
   }

Example Responses
-----------------

**Status code: 202**

Request accepted

.. code-block::

   {
     "endpoint" : {
       "id" : "ff80808169bf16c70169bf1d02270000",
       "name" : "2118",
       "direction" : "inbound",
       "status" : "ACTIVE",
       "vpc_id" : "02443811-acf1-4c22-8f44-e3adf19f6097",
       "ipaddress_count" : 6,
       "resolver_rule_count" : 0,
       "create_time" : "2019-03-27T12:25:43.181",
       "update_time" : "2019-03-27T12:25:43.181"
     }
   }

Status Codes
------------

=========== ================
Status Code Description
=========== ================
202         Request accepted
=========== ================

Error Codes
-----------

For details, see :ref:`Error Code <dns_api_80003>`.
