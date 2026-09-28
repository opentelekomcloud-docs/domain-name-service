:original_name: CreateResolverRule.html

.. _CreateResolverRule:

Creating an Endpoint Rule
=========================

Function
--------

This API is used to create an endpoint rule.

URI
---

POST /v2.1/resolverrules

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

   +-----------------+-----------------+--------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                             | Description                                                                                                         |
   +=================+=================+==================================================================================================+=====================================================================================================================+
   | name            | Yes             | String                                                                                           | Rule name.                                                                                                          |
   |                 |                 |                                                                                                  |                                                                                                                     |
   |                 |                 |                                                                                                  | It can contain 1 to 64 characters. Only letters, digits, underscores (_), hyphens (-), and periods (.) are allowed. |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | domain_name     | Yes             | String                                                                                           | Domain name                                                                                                         |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | endpoint_id     | Yes             | String                                                                                           | ID of the endpoint to which the current rule belongs                                                                |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | ipaddresses     | Yes             | Array of :ref:`IpInfo <createresolverrule__en-us_topic_0000002244218620_request_ipinfo>` objects | Destination IP address added to a rule                                                                              |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+

.. _createresolverrule__en-us_topic_0000002244218620_request_ipinfo:

.. table:: **Table 3** IpInfo

   ========= ========= ====== ===========
   Parameter Mandatory Type   Description
   ========= ========= ====== ===========
   ip        No        String IP address
   ========= ========= ====== ===========

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 4** Response body parameter

   +---------------+---------------------------------------------------------------------------------------------------------------+---------------+
   | Parameter     | Type                                                                                                          | Description   |
   +===============+===============================================================================================================+===============+
   | resolver_rule | :ref:`ResolverRuleParam <createresolverrule__en-us_topic_0000002244218620_response_resolverruleparam>` object | Endpoint rule |
   +---------------+---------------------------------------------------------------------------------------------------------------+---------------+

.. _createresolverrule__en-us_topic_0000002244218620_response_resolverruleparam:

.. table:: **Table 5** ResolverRuleParam

   +-----------------------+-----------------------+---------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                   |
   +=======================+=======================+===============================================================+
   | id                    | String                | ID of an endpoint rule                                        |
   +-----------------------+-----------------------+---------------------------------------------------------------+
   | name                  | String                | Rule name                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------+
   | domain_name           | String                | Domain name                                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------+
   | endpoint_id           | String                | ID of the endpoint to which the current rule belongs          |
   +-----------------------+-----------------------+---------------------------------------------------------------+
   | status                | String                | Resource status.                                              |
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
   | rule_type             | String                | Rule type.                                                    |
   |                       |                       |                                                               |
   |                       |                       | This parameter is reserved. The default value is **FORWARD**. |
   +-----------------------+-----------------------+---------------------------------------------------------------+
   | ipaddress_count       | Integer               | Number of IP addresses in the endpoint rule                   |
   +-----------------------+-----------------------+---------------------------------------------------------------+
   | create_time           | String                | Creation time.                                                |
   |                       |                       |                                                               |
   |                       |                       | Format: *yyyy-MM-dd'T'HH:mm:ss.SSS*                           |
   +-----------------------+-----------------------+---------------------------------------------------------------+
   | update_time           | String                | Update time.                                                  |
   |                       |                       |                                                               |
   |                       |                       | Format: *yyyy-MM-dd'T'HH:mm:ss.SSS*                           |
   +-----------------------+-----------------------+---------------------------------------------------------------+

Example Requests
----------------

Creating an endpoint rule and setting the destination IP addresses to **1.1.1.1** and **2.2.2.2**

.. code-block:: text

   POST https://{endpoint}/v2.1/resolverrules

   {
     "name" : "rule-xxx",
     "domain_name" : "www.example.com",
     "endpoint_id" : "8a36f60a753badb401753bade3400001",
     "ipaddresses" : [ {
       "ip" : "1.1.1.1"
     }, {
       "ip" : "2.2.2.2"
     } ]
   }

Example Responses
-----------------

**Status code: 202**

Request accepted

.. code-block::

   {
     "resolver_rule" : {
       "id" : "8a36f60a753badb401753bade3400002",
       "name" : "rule-xxx",
       "domain_name" : "www.example.com",
       "endpoint_id" : "8a36f60a753badb401753bade3400001",
       "status" : "ACTIVE",
       "rule_type" : "FORWARD",
       "ipaddress_count" : 2,
       "create_time" : "2020-10-18T12:27:31.448",
       "update_time" : "2020-10-18T12:27:31.448"
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
