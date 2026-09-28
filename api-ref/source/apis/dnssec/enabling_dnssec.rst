:original_name: EnableDnssecConfig.html

.. _EnableDnssecConfig:

Enabling DNSSEC
===============

Function
--------

This API is used to enable DNSSEC for a public zone.

URI
---

POST /v2/zones/{zone_id}/enable-dnssec

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

.. table:: **Table 3** Response body parameters

   +-----------------------+-----------------------+-------------------------------------+
   | Parameter             | Type                  | Description                         |
   +=======================+=======================+=====================================+
   | zone_name             | String                | Domain name                         |
   +-----------------------+-----------------------+-------------------------------------+
   | key_tag               | Integer               | Key tag                             |
   +-----------------------+-----------------------+-------------------------------------+
   | flag                  | Integer               | Flag                                |
   +-----------------------+-----------------------+-------------------------------------+
   | digest_algorithm      | String                | Digest algorithm                    |
   +-----------------------+-----------------------+-------------------------------------+
   | digest_type           | Integer               | Digest algorithm type               |
   +-----------------------+-----------------------+-------------------------------------+
   | digest                | String                | Digest                              |
   +-----------------------+-----------------------+-------------------------------------+
   | signature             | String                | Signature algorithm                 |
   +-----------------------+-----------------------+-------------------------------------+
   | signature_type        | Integer               | Signature algorithm type            |
   +-----------------------+-----------------------+-------------------------------------+
   | ksk_public_key        | String                | Public key                          |
   +-----------------------+-----------------------+-------------------------------------+
   | ds_record             | String                | DS record                           |
   +-----------------------+-----------------------+-------------------------------------+
   | created_at            | String                | Creation time.                      |
   |                       |                       |                                     |
   |                       |                       | Format: *yyyy-MM-dd'T'HH:mm:ss.SSS* |
   +-----------------------+-----------------------+-------------------------------------+
   | updated_at            | String                | Update time.                        |
   |                       |                       |                                     |
   |                       |                       | Format: *yyyy-MM-dd'T'HH:mm:ss.SSS* |
   +-----------------------+-----------------------+-------------------------------------+
   | status                | String                | Status.                             |
   |                       |                       |                                     |
   |                       |                       | Value options:                      |
   |                       |                       |                                     |
   |                       |                       | **ENABLE**: DNSSEC is enabled.      |
   |                       |                       |                                     |
   |                       |                       | **DISABLE**: DNSSEC is disabled.    |
   +-----------------------+-----------------------+-------------------------------------+

Example Requests
----------------

None

Example Responses
-----------------

**Status code: 202**

Request accepted

.. code-block::

   {
     "zone_name" : "example.com.",
     "key_tag" : 46576,
     "flag" : 257,
     "digest" : "2cb6a21bc5ea1622a24d35b94d171dcc06523daf708f6eb08c3358608e84f51c",
     "digest_algorithm" : "SHA256",
     "digest_type" : 2,
     "signature" : "ECDSAP256SHA256",
     "signature_type" : 13,
     "ksk_public_key" : "M7/fjwRNXwWsBxjIMZ2KzxEQ+DnhZ8pbPTn8VCcPKdrDhvV750DkFdXhuXRMLFHrXI9xjIVUugtVKgmdPIEf8w==",
     "ds_record" : "example.com. 300 IN DS 46576 13 2 2cb6a21bc5ea1622a24d35b94d171dcc06523daf708f6eb08c3358608e84f51c",
     "created_at" : "2023-11-17T12:03:17.827",
     "updated_at" : "2023-11-17T12:03:17.827",
     "status" : "ENABLE"
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
