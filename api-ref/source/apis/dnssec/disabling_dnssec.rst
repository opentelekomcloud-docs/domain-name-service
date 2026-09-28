:original_name: DisableDnssecConfig.html

.. _DisableDnssecConfig:

Disabling DNSSEC
================

Function
--------

This API is used to disable DNSSEC for a public zone.

URI
---

POST /v2/zones/{zone_id}/disable-dnssec

.. table:: **Table 1** Path parameter

   ========= ========= ====== ==============
   Parameter Mandatory Type   Description
   ========= ========= ====== ==============
   zone_id   Yes       String Public zone ID
   ========= ========= ====== ==============

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

   +-----------------------+-----------------------+----------------------------------+
   | Parameter             | Type                  | Description                      |
   +=======================+=======================+==================================+
   | status                | String                | Status.                          |
   |                       |                       |                                  |
   |                       |                       | Value options:                   |
   |                       |                       |                                  |
   |                       |                       | **DISABLE**: DNSSEC is disabled. |
   +-----------------------+-----------------------+----------------------------------+

Example Requests
----------------

None

Example Responses
-----------------

**Status code: 202**

Request accepted

.. code-block::

   {
     "status" : "DISABLE"
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
