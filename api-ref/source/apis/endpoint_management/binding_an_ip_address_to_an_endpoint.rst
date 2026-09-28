:original_name: AssociateEndpointIpaddress.html

.. _AssociateEndpointIpaddress:

Binding an IP Address to an Endpoint
====================================

Function
--------

This API is used to bind an IP address to an endpoint.

URI
---

POST /v2.1/endpoints/{endpoint_id}/ipaddresses

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

   +-----------+-----------+--------------------------------------------------------------------------------------------------------------+------------------------+
   | Parameter | Mandatory | Type                                                                                                         | Description            |
   +===========+===========+==============================================================================================================+========================+
   | ipaddress | Yes       | :ref:`IpaddressInfo <associateendpointipaddress__en-us_topic_0000002244058784_request_ipaddressinfo>` object | IP address to be bound |
   +-----------+-----------+--------------------------------------------------------------------------------------------------------------+------------------------+

.. _associateendpointipaddress__en-us_topic_0000002244058784_request_ipaddressinfo:

.. table:: **Table 4** IpaddressInfo

   +-----------+-----------+--------+----------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                        |
   +===========+===========+========+====================================================+
   | subnet_id | Yes       | String | Subnet ID                                          |
   +-----------+-----------+--------+----------------------------------------------------+
   | ip        | No        | String | Custom IP address, which must fall into the subnet |
   +-----------+-----------+--------+----------------------------------------------------+

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 5** Response body parameter

   +-----------+-------------------------------------------------------------------------------------------------------------+-------------+
   | Parameter | Type                                                                                                        | Description |
   +===========+=============================================================================================================+=============+
   | endpoint  | :ref:`EndpointResp <associateendpointipaddress__en-us_topic_0000002244058784_response_endpointresp>` object | Endpoint    |
   +-----------+-------------------------------------------------------------------------------------------------------------+-------------+

.. _associateendpointipaddress__en-us_topic_0000002244058784_response_endpointresp:

.. table:: **Table 6** EndpointResp

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

Binding an IP address to an endpoint

.. code-block:: text

   POST https://{endpoint}/v2.1/endpoints/{endpoint_id}/ipaddresses

   {
     "ipaddress" : {
       "subnet_id" : "3ee6107e-4188-4c4d-b453-80d6b9a147d5"
     }
   }

Example Responses
-----------------

**Status code: 202**

Request accepted

.. code-block::

   {
     "endpoint" : {
       "id" : "ff80808169bf16c70169bf1d02270000",
       "name" : "poi-666",
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

=========== ================
Status Code Description
=========== ================
202         Request accepted
=========== ================

Error Codes
-----------

For details, see :ref:`Error Code <dns_api_80003>`.
