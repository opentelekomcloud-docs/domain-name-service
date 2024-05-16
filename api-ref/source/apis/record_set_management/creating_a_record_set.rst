:original_name: dns_api_64001.html

.. _dns_api_64001:

Creating a Record Set
=====================

Function
--------

Create a record set.

URI
---

POST /v2/zones/{zone_id}/recordsets

For details, see :ref:`Table 1 <dns_api_64001__table30807893173129>`.

.. _dns_api_64001__table30807893173129:

.. table:: **Table 1** Parameters in the URI

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                            |
   +=================+=================+=================+========================================================================================+
   | zone_id         | Yes             | String          | Zone ID                                                                                |
   |                 |                 |                 |                                                                                        |
   |                 |                 |                 | Obtain the public zone ID according to :ref:`Querying Public Zones <dns_api_62003>`.   |
   |                 |                 |                 |                                                                                        |
   |                 |                 |                 | Obtain the private zone ID according to :ref:`Querying Private Zones <dns_api_63006>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameters in the request

      +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                |
      +=================+=================+==================+============================================================================================================================================================================+
      | name            | Yes             | String           | Fully qualified domain name (FQDN) suffixed with a zone name, which is a complete host name ended with a dot                                                               |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | A domain name is case insensitive. Uppercase letters will also be converted into lowercase letters.                                                                        |
      +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description     | No              | String           | (Optional) Description of the domain name                                                                                                                                  |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | The value cannot exceed 255 characters.                                                                                                                                    |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | The value is left blank by default.                                                                                                                                        |
      +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | type            | Yes             | String           | Record set type                                                                                                                                                            |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | The value can be **A**, **AAAA**, **MX**, **CNAME**, **TXT**, **NS** (only in public zones), **SRV**, **CAA** (only in public zones), and **PTR** (only in private zones). |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | For details, see :ref:`Record Set Type <dns_api_80005__section1188113824413>`.                                                                                             |
      +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ttl             | No              | Integer          | Caching period of the record set on a local DNS server                                                                                                                     |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | If your service address is frequently changed, set TTL to a smaller value.                                                                                                 |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | Value range:                                                                                                                                                               |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | -  Public zone: **1**\ ``-``\ **2147483647**                                                                                                                               |
      |                 |                 |                  | -  Private zone: **1**\ ``-``\ **2147483647**                                                                                                                              |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | The default value is **300**.                                                                                                                                              |
      +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | records         | Yes             | Array of strings | Value of the record set. The value format varies depending on record set types.                                                                                            |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | For example, the value of an AAAA record set is the IPv6 address list mapped to the domain name.                                                                           |
      +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tags            | No              | Array of object  | Resource tag. For details, see :ref:`Table 3 <dns_api_64001__table7518152113230>`.                                                                                         |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | The value is left blank by default.                                                                                                                                        |
      +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_64001__table7518152113230:

   .. table:: **Table 3** Description of the **tags** field

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                                    |
      +=================+=================+=================+================================================================================================================================================================+
      | key             | Yes             | String          | Tag key                                                                                                                                                        |
      |                 |                 |                 |                                                                                                                                                                |
      |                 |                 |                 | A key can contain up to 36 Unicode characters. **key** must be specified. It can contain only digits, letters, hyphens (-), underscores (_), and at signs (@). |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | value           | No              | String          | Tag value                                                                                                                                                      |
      |                 |                 |                 |                                                                                                                                                                |
      |                 |                 |                 | Each value can contain up to 43 Unicode characters and can be an empty string.                                                                                 |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   Add record sets for the zone whose ID is 2c9eb155587194ec01587224c9f90149:

   .. code-block:: text

      POST https://{DNS_Endpoint}/v2/zones/2c9eb155587194ec01587224c9f90149/recordsets

   -  A type

      .. code-block::

         {
             "name": "www.example.com.",
             "description": "This is an example record set.",
             "type": "A",
             "ttl": 3600,
             "records": [
                 "192.168.10.1",
                 "192.168.10.2"
             ],
             "tags": [
                 {
                   "key": "key1",
                   "value": "value1"
                 }
             ]
         }

   -  AAAA type

      .. code-block::

         {
             "name": "www.example.com.",
             "description": "This is an example record set.",
             "type": "AAAA",
             "ttl": 3600,
             "records": [
                 "fe80:0:0:0:202:b3ff:fe1e:8329",
                 "ff03:0db8:85a3:0:0:8a2e:0370:7334"
             ],
             "tags": [
                 {
                   "key": "key1",
                   "value": "value1"
                 }
             ]
         }

   -  MX type

      .. code-block::

         {
             "name": "www.example.com.",
             "description": "This is an example record set.",
             "type": "MX",
             "ttl": 3600,
             "records": [
                 "1 mail.example.com"
             ],
             "tags": [
                 {
                   "key": "key1",
                   "value": "value1"
                 }
             ]
         }

   -  CNAME type

      .. code-block::

         {
             "name": "sale.example.com.",
             "description": "This is an example record set.",
             "type": "CNAME",
             "ttl": 3600,
             "records": [
                 "server1.example.com"
             ],
             "tags": [
                 {
                   "key": "key1",
                   "value": "value1"
                 }
             ]
         }

   -  TXT type

      .. code-block::

         {
             "name": "server1.example.com.",
             "description": "This is an example record set.",
             "type": "TXT",
             "ttl": 300,
             "records": [
                 "\"This host is used for sale.\""
             ],
             "tags": [
                 {
                   "key": "key1",
                   "value": "value1"
                 }
             ]
         }

   -  NS type

      .. code-block::

         {
             "name": "server1.example.com.",
             "description": "This is an example record set.",
             "type": "NS",
             "ttl": 300,
             "records": [
                 "node1.example.com.",
                 "node2.example.com."
             ],
             "tags": [
                 {
                   "key": "key1",
                   "value": "value1"
                 }
             ]
         }

   -  SRV type

      .. code-block::

         {
             "name": "_sip._tcp.example.com.",
             "description": "This is an example record set.",
             "type": "SRV",
             "ttl": 300,
             "records": [
                 "3 60 2176 sipserver.example.com.",
                 "10 100 2176 sipserver.example.com."
             ],
             "tags": [
                 {
                   "key": "key1",
                   "value": "value1"
                 }
             ]
         }

   -  PTR type

      .. code-block::

         {
             "name": "1.1.168.192.in-addr.arpa.",
             "description": "This is an example record set.",
             "type": "PTR",
             "ttl": 300,
             "records": [
                 "webserver.example.com."
             ],
             "tags": [
                 {
                   "key": "key1",
                   "value": "value1"
                 }
             ]
         }

   -  CAA type

      .. code-block::

         {
             "name": "www.example.com.",
             "description": "This is an example record set.",
             "type": "CAA",
             "ttl": 300,
             "records": [
                 "0 issue \"example.com\"",
                 "0 issuewild \"www.certinomis.com\"",
                 "0 iodef \"mailto:xx@example.org\"",
                 "0 iodef \"http://iodef.example.com\""
             ],
             "tags": [
                 {
                   "key": "key1",
                   "value": "value1"
                 }
             ]
         }

Response
--------

-  Parameter description

   .. table:: **Table 4** Parameters in the response

      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                                                                                |
      +=======================+=======================+============================================================================================================================================================================+
      | id                    | String                | Record set ID                                                                                                                                                              |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Record set name                                                                                                                                                            |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description           | String                | Record set description                                                                                                                                                     |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | zone_id               | String                | Zone ID of the record set                                                                                                                                                  |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | zone_name             | String                | Zone name of the record set                                                                                                                                                |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | type                  | String                | Record set type                                                                                                                                                            |
      |                       |                       |                                                                                                                                                                            |
      |                       |                       | The value can be **A**, **AAAA**, **MX**, **CNAME**, **TXT**, **NS** (only in public zones), **SRV**, **CAA** (only in public zones), and **PTR** (only in private zones). |
      |                       |                       |                                                                                                                                                                            |
      |                       |                       | For details, see :ref:`Record Set Type <dns_api_80005__section1188113824413>`.                                                                                             |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ttl                   | Integer               | Record set cache duration (in seconds) on a local DNS server. The longer the duration is, the slower the update takes effect.                                              |
      |                       |                       |                                                                                                                                                                            |
      |                       |                       | If your service address is frequently changed, set TTL to a smaller value.                                                                                                 |
      |                       |                       |                                                                                                                                                                            |
      |                       |                       | Value range:                                                                                                                                                               |
      |                       |                       |                                                                                                                                                                            |
      |                       |                       | -  Public zone: **1**\ ``-``\ **2147483647**                                                                                                                               |
      |                       |                       | -  Private zone: **1**\ ``-``\ **2147483647**                                                                                                                              |
      |                       |                       |                                                                                                                                                                            |
      |                       |                       | The default value is **300**.                                                                                                                                              |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | records               | Array of strings      | Record set value                                                                                                                                                           |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | create_at             | String                | Time when the record set was created                                                                                                                                       |
      |                       |                       |                                                                                                                                                                            |
      |                       |                       | The value format is yyyy-MM-dd'T'HH:mm:ss.SSS.                                                                                                                             |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | update_at             | String                | Time when the record set was updated                                                                                                                                       |
      |                       |                       |                                                                                                                                                                            |
      |                       |                       | The value format is yyyy-MM-dd'T'HH:mm:ss.SSS.                                                                                                                             |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Resource status                                                                                                                                                            |
      |                       |                       |                                                                                                                                                                            |
      |                       |                       | For details, see :ref:`Resource Status <dns_api_80005__section33673592114748>`.                                                                                            |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | default               | Boolean               | Whether the record set is created by default. A default record set cannot be deleted.                                                                                      |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | project_id            | String                | Project ID of the record set                                                                                                                                               |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | links                 | Object                | Link to the current resource or other related resources. When a response is broken into pages, a **next** link is provided to retrieve all results.                        |
      |                       |                       |                                                                                                                                                                            |
      |                       |                       | For details, see :ref:`Table 5 <dns_api_64001__table52442344175457>`.                                                                                                      |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_64001__table52442344175457:

   .. table:: **Table 5** Parameters in the **links** field

      ========= ====== ============================
      Parameter Type   Description
      ========= ====== ============================
      self      String Link to the current resource
      next      String Link to the next page
      ========= ====== ============================

-  Example response

   .. code-block::

      {
          "id": "2c9eb155587228570158722b6ac30007",
          "name": "www.example.com.",
          "description": "This is an example record set.",
          "type": "A",
          "ttl": 300,
          "records": [
              "192.168.10.1",
              "192.168.10.2"
          ],
          "status": "PENDING_CREATE",
          "links": {
              "self": "https://Endpoint/v2/zones/2c9eb155587194ec01587224c9f90149/recordsets/2c9eb155587228570158722b6ac30007"
          },
          "zone_id": "2c9eb155587194ec01587224c9f90149",
          "zone_name": "example.com.",
          "create_at": "2016-11-17T12:03:17.827",
          "update_at": null,
          "default": false,
          "project_id": "e55c6f3dc4e34c9f86353b664ae0e70c"
      }

Returned Value
--------------

If a 2xx status code is returned, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
