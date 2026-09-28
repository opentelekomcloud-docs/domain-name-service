:original_name: DisassociateEndpointIpaddress.html

.. _DisassociateEndpointIpaddress:

Unbinding an IP Address from an Endpoint
========================================

Function
--------

This API is used to unbind an IP address from an endpoint.

URI
---

DELETE /v2.1/endpoints/{endpoint_id}/ipaddresses/{ipaddress_id}

.. table:: **Table 1** Path parameter

   ============ ========= ====== =============
   Parameter    Mandatory Type   Description
   ============ ========= ====== =============
   endpoint_id  Yes       String Endpoint ID
   ipaddress_id Yes       String IP address ID
   ============ ========= ====== =============

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

**Status code: 202**

.. table:: **Table 3** Response body parameter

   +-----------+----------------------------------------------------------------------------------------------------------------+-------------+
   | Parameter | Type                                                                                                           | Description |
   +===========+================================================================================================================+=============+
   | endpoint  | :ref:`EndpointResp <disassociateendpointipaddress__en-us_topic_0000002279297657_response_endpointresp>` object | Endpoint    |
   +-----------+----------------------------------------------------------------------------------------------------------------+-------------+

.. _disassociateendpointipaddress__en-us_topic_0000002279297657_response_endpointresp:

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
   | status                | String                | Resource status                                            |
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

**Status code: 202**

Request accepted

.. code-block::

   {
     "endpoint" : {
       "id" : "ff80808169be2efb0169bef85d720013",
       "name" : "NULL",
       "direction" : "inbound",
       "status" : "ACTIVE",
       "vpc_id" : "dd2a1ce7-fa36-48d1-b6ac-6623bc7c306b",
       "ipaddress_count" : 3,
       "resolver_rule_count" : 0,
       "create_time" : "2019-03-27T11:45:41.724",
       "update_time" : "2019-03-27T11:45:41.724"
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
