:original_name: DisassociateResolverRuleRouter.html

.. _DisassociateResolverRuleRouter:

Disassociating a VPC from an Endpoint Rule
==========================================

Function
--------

This API is used to disassociate a VPC from an endpoint rule.

URI
---

POST /v2.1/resolverrules/{resolverrule_id}/disassociaterouter

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

.. table:: **Table 3** Request body parameter

   +-----------+-----------+------------------------------------------------------------------------------------------------------------------+-------------+
   | Parameter | Mandatory | Type                                                                                                             | Description |
   +===========+===========+==================================================================================================================+=============+
   | router    | Yes       | :ref:`RouterForRule <disassociateresolverrulerouter__en-us_topic_0000002244058796_request_routerforrule>` object | VPC         |
   +-----------+-----------+------------------------------------------------------------------------------------------------------------------+-------------+

.. _disassociateresolverrulerouter__en-us_topic_0000002244058796_request_routerforrule:

.. table:: **Table 4** RouterForRule

   +-----------+-----------+--------+-------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                     |
   +===========+===========+========+=================================================+
   | router_id | Yes       | String | ID of the Router (VPC) associated with the zone |
   +-----------+-----------+--------+-------------------------------------------------+

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 5** Response body parameters

   ============= ====== ==========================================
   Parameter     Type   Description
   ============= ====== ==========================================
   router_id     String ID of the associated VPC
   router_region String Region where the associated VPC is located
   status        String Resource status
   ============= ====== ==========================================

Example Requests
----------------

Disassociating a VPC from an endpoint rule

.. code-block:: text

   POST https://{endpoint}/v2.1/resolverrules/{resolverrule_id}/disassociaterouter

   {
     "router" : {
       "router_id" : "f0791650-db8c-4a20-8a44-a06c6e24b15b"
     }
   }

Example Responses
-----------------

**Status code: 202**

Request accepted

.. code-block::

   {
     "status" : "PENDING_DELETE",
     "router_id" : "f0791650-db8c-4a20-8a44-a06c6e24b15b",
     "router_region" : "eu-de"
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
