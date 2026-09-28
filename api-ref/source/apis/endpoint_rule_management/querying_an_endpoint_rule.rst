:original_name: ShowResolverRule.html

.. _ShowResolverRule:

Querying an Endpoint Rule
=========================

Function
--------

This API is used to query an endpoint rule.

URI
---

GET /v2.1/resolverrules/{resolverrule_id}

.. table:: **Table 1** Path parameter

   =============== ========= ====== ======================
   Parameter       Mandatory Type   Description
   =============== ========= ====== ======================
   resolverrule_id Yes       String ID of an endpoint rule
   =============== ========= ====== ======================

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

   +---------------+-----------------------------------------------------------------------------------------------------------------------------+---------------+
   | Parameter     | Type                                                                                                                        | Description   |
   +===============+=============================================================================================================================+===============+
   | resolver_rule | :ref:`ShowResolverRuleRespParam <showresolverrule__en-us_topic_0000002244218624_response_showresolverrulerespparam>` object | Endpoint rule |
   +---------------+-----------------------------------------------------------------------------------------------------------------------------+---------------+

.. _showresolverrule__en-us_topic_0000002244218624_response_showresolverrulerespparam:

.. table:: **Table 4** ShowResolverRuleRespParam

   +-----------------------+---------------------------------------------------------------------------------------------------+---------------------------------------------------------------+
   | Parameter             | Type                                                                                              | Description                                                   |
   +=======================+===================================================================================================+===============================================================+
   | id                    | String                                                                                            | Endpoint rule ID, which is a UUID used to identify the rule   |
   +-----------------------+---------------------------------------------------------------------------------------------------+---------------------------------------------------------------+
   | name                  | String                                                                                            | Rule name                                                     |
   +-----------------------+---------------------------------------------------------------------------------------------------+---------------------------------------------------------------+
   | domain_name           | String                                                                                            | Domain name                                                   |
   +-----------------------+---------------------------------------------------------------------------------------------------+---------------------------------------------------------------+
   | endpoint_id           | String                                                                                            | ID of the endpoint to which the current rule belongs          |
   +-----------------------+---------------------------------------------------------------------------------------------------+---------------------------------------------------------------+
   | status                | String                                                                                            | Resource status.                                              |
   |                       |                                                                                                   |                                                               |
   |                       |                                                                                                   | The value can be:                                             |
   |                       |                                                                                                   |                                                               |
   |                       |                                                                                                   | -  **ACTIVE**: The resource is working normally.              |
   |                       |                                                                                                   |                                                               |
   |                       |                                                                                                   | -  **PENDING_CREATE**: The resource is being created.         |
   |                       |                                                                                                   |                                                               |
   |                       |                                                                                                   | -  **PENDING_DELETE**: The resource is being deleted.         |
   |                       |                                                                                                   |                                                               |
   |                       |                                                                                                   | -  **ERROR**: failed                                          |
   +-----------------------+---------------------------------------------------------------------------------------------------+---------------------------------------------------------------+
   | rule_type             | String                                                                                            | Rule type.                                                    |
   |                       |                                                                                                   |                                                               |
   |                       |                                                                                                   | This parameter is reserved. The default value is **FORWARD**. |
   +-----------------------+---------------------------------------------------------------------------------------------------+---------------------------------------------------------------+
   | ipaddress_count       | Integer                                                                                           | Number of IP addresses in the endpoint rule                   |
   +-----------------------+---------------------------------------------------------------------------------------------------+---------------------------------------------------------------+
   | ipaddresses           | Array of :ref:`IpValue <showresolverrule__en-us_topic_0000002244218624_response_ipvalue>` objects | Destination IP address added to a rule                        |
   +-----------------------+---------------------------------------------------------------------------------------------------+---------------------------------------------------------------+
   | routers               | Array of :ref:`Router <showresolverrule__en-us_topic_0000002244218624_response_router>` objects   | VPC associated with the endpoint rule                         |
   +-----------------------+---------------------------------------------------------------------------------------------------+---------------------------------------------------------------+
   | create_time           | String                                                                                            | Creation time.                                                |
   |                       |                                                                                                   |                                                               |
   |                       |                                                                                                   | Format: *yyyy-MM-dd'T'HH:mm:ss.SSS*                           |
   +-----------------------+---------------------------------------------------------------------------------------------------+---------------------------------------------------------------+
   | update_time           | String                                                                                            | Update time.                                                  |
   |                       |                                                                                                   |                                                               |
   |                       |                                                                                                   | Format: *yyyy-MM-dd'T'HH:mm:ss.SSS*                           |
   +-----------------------+---------------------------------------------------------------------------------------------------+---------------------------------------------------------------+

.. _showresolverrule__en-us_topic_0000002244218624_response_ipvalue:

.. table:: **Table 5** IpValue

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   ip        String IP address
   ========= ====== ===========

.. _showresolverrule__en-us_topic_0000002244218624_response_router:

.. table:: **Table 6** Router

   ============= ====== ==========================================
   Parameter     Type   Description
   ============= ====== ==========================================
   router_id     String ID of the associated VPC
   router_region String Region where the associated VPC is located
   status        String Resource status
   ============= ====== ==========================================

Example Requests
----------------

None

Example Responses
-----------------

**Status code: 200**

Successful request

.. code-block::

   {
     "resolver_rule" : {
       "id" : "8a36f60a753badb401753bade3400002",
       "name" : "rule-xxx",
       "domain_name" : "www.example.com",
       "endpoint_id" : "8a36f60a753badb401753bade3400001",
       "status" : "ACTIVE",
       "rule_type" : "FORWARD",
       "ipaddress_count" : 0,
       "ipaddresses" : [ {
         "ip" : "1.1.1.1"
       }, {
         "ip" : "2.2.2.2"
       } ],
       "routers" : [ {
         "router_id" : "ff7bd47f-3f12-4f24-a078-e6064abaa670",
         "router_region" : "eu-de",
         "status" : "ACTIVE"
       }, {
         "router_id" : "ff7bd47f-3f12-4f24-a078-e6064abaa671",
         "router_region" : "eu-de",
         "status" : "ACTIVE"
       } ],
       "create_time" : "2020-10-18T12:27:31.448",
       "update_time" : "2020-10-18T12:27:31.448"
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
