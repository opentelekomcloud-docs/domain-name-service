:original_name: DeleteResolverRule.html

.. _DeleteResolverRule:

Deleting an Endpoint Rule
=========================

Function
--------

This API is used to delete an endpoint rule.

URI
---

DELETE /v2.1/resolverrules/{resolverrule_id}

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

**Status code: 202**

.. table:: **Table 3** Response body parameter

   +---------------+---------------------------------------------------------------------------------------------------------------+---------------+
   | Parameter     | Type                                                                                                          | Description   |
   +===============+===============================================================================================================+===============+
   | resolver_rule | :ref:`ResolverRuleParam <deleteresolverrule__en-us_topic_0000002279177777_response_resolverruleparam>` object | Endpoint rule |
   +---------------+---------------------------------------------------------------------------------------------------------------+---------------+

.. _deleteresolverrule__en-us_topic_0000002279177777_response_resolverruleparam:

.. table:: **Table 4** ResolverRuleParam

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

None

.. _deleteresolverrule__section91061138133411:

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
       "status" : "PENDING_DELETE",
       "rule_type" : "FORWARD",
       "ipaddress_count" : 0,
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
