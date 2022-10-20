:original_name: dns_api_64006.html

.. _dns_api_64006:

Modifying a Record Set
======================

Function
--------

Modify a record set.

URI
---

PUT /v2/zones/{zone_id}/recordsets/{recordset_id}

For details, see :ref:`Table 1 <dns_api_64006__table52104579>`.

.. _dns_api_64006__table52104579:

.. table:: **Table 1** Parameters in the URI

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                           |
   +=================+=================+=================+=======================================================================================================+
   | zone_id         | Yes             | String          | Zone ID                                                                                               |
   |                 |                 |                 |                                                                                                       |
   |                 |                 |                 | Obtain the public zone ID according to :ref:`Querying Public Zones <dns_api_62003>`.                  |
   |                 |                 |                 |                                                                                                       |
   |                 |                 |                 | Obtain the private zone ID according to :ref:`Querying Private Zones <dns_api_63006>`.                |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------+
   | recordset_id    | Yes             | String          | ID of the record set to be modified                                                                   |
   |                 |                 |                 |                                                                                                       |
   |                 |                 |                 | You can obtain the value by calling the API in :ref:`Querying Record Sets in a Zone <dns_api_64004>`. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameters in the request

      +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                |
      +=================+=================+==================+============================================================================================================================================================================+
      | name            | No              | String           | Fully qualified domain name (FQDN) suffixed with a zone name, which is a complete host name ended with a dot                                                               |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | If it is a record set in a public zone, you can add five labels at most.                                                                                                   |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | A domain name is case insensitive. Uppercase letters will also be converted into lowercase letters.                                                                        |
      +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description     | No              | String           | (Optional) Description of the domain name                                                                                                                                  |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | The value cannot exceed 255 characters.                                                                                                                                    |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | If this parameter is left blank, the value will not be changed.                                                                                                            |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | The value is left blank by default.                                                                                                                                        |
      +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | type            | No              | String           | Record set type                                                                                                                                                            |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | The value can be **A**, **AAAA**, **MX**, **CNAME**, **TXT**, **NS** (only in public zones), **SRV**, **PTR** (only in private zones), and **CAA** (only in public zones). |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | The value can be **A**, **AAAA**, **MX**, **CNAME**, **TXT**, **SRV**, or **PTR** (only in private zones).                                                                 |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | For details, see :ref:`Record Set Type <dns_api_80005__section1188113824413>`.                                                                                             |
      +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ttl             | No              | Integer          | Record set cache duration (in second) on a local DNS server. The longer the duration is, the slower the update takes effect.                                               |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | If your service address is frequently changed, set TTL to a smaller value.                                                                                                 |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | The value ranges from **1** to **2147483647**.                                                                                                                             |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | If this parameter is left blank, the value will not be changed.                                                                                                            |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | The value is left blank by default.                                                                                                                                        |
      +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | records         | No              | Array of strings | Value of the record set. The value format varies depending on record set types.                                                                                            |
      |                 |                 |                  |                                                                                                                                                                            |
      |                 |                 |                  | For example, the value of an AAAA record set is the IPv6 address list mapped to the domain name.                                                                           |
      +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   Modify the record set whose ID is 2c9eb155587228570158722b6ac30007 in the zone whose ID is 2c9eb155587194ec01587224c9f90149:

   .. code-block:: text

      PUT https://{DNS_Endpoint}/v2/zones/2c9eb155587194ec01587224c9f90149/recordsets/2c9eb155587228570158722b6ac30007

   -  A type

      .. code-block::

         {
             "description": "This is an example record set.",
             "ttl": 3600,
             "records": [
                 "192.168.10.1",
                 "192.168.10.2"
             ]
         }

   -  AAAA type

      .. code-block::

         {
             "description": "This is an example record set.",
             "ttl": 3600,
             "records": [
                 "fe80:0:0:0:202:b3ff:fe1e:8329",
                 "ff03:0db8:85a3:0:0:8a2e:0370:7334"
             ]
         }

   -  MX type

      .. code-block::

         {
             "description": "This is an example record set.",
             "ttl": 3600,
             "records": [
                 "1 mail.example.com"
             ]
         }

   -  CNAME type

      .. code-block::

         {
             "description": "This is an example record set.",
             "ttl": 3600,
             "records": [
                 "server1.example.com"
             ]
         }

   -  TXT type

      .. code-block::

         {
             "description": "This is an example record set.",
             "ttl": 300,
             "records": [
                 "\"This host is used for sale.\""
             ]
         }

   -  NS type

      .. code-block::

         {
             "description": "This is an example record set.",
             "ttl": 300,
             "records": [
                 "node1.example.com.",
                 "node2.example.com."
             ]
         }

   -  SRV type

      .. code-block::

         {
             "description": "This is an example record set.",
             "ttl": 3600,
             "records": [
                 "3 60 2176 sipserver.example.com.",
                 "10 100 2176 sipserver.example.com."
             ]
         }

   -  PTR type

      .. code-block::

         {
             "description": "This is an example record set.",
             "ttl": 3600,
             "records": [
                 "host.example.com."

             ]
         }

   -  CAA type

      .. code-block::

         {
             "description": "This is an example record set.",
             "ttl": 300,
             "records": [
                 "0 issue \"example.com\"",
                 "0 issuewild \"www.certinomis.com\"",
                 "0 iodef \"mailto:xx@example.org\"",
                 "0 iodef \"http://iodef.example.com\""
             ]
         }

Response
--------

-  Parameter description

   .. table:: **Table 3** Parameters in the response

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
      | ttl                   | Integer               | Record set cache duration (in second) on a local DNS server. The longer the duration is, the slower the update takes effect.                                               |
      |                       |                       |                                                                                                                                                                            |
      |                       |                       | If your service address is frequently changed, set TTL to a smaller value.                                                                                                 |
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
      |                       |                       | For details, see :ref:`Table 4 <dns_api_64006__table354521744216>`.                                                                                                        |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_64006__table354521744216:

   .. table:: **Table 4** Parameters in the **links** field

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
          "ttl": 3600,
          "records": [
              "192.168.10.1",
              "192.168.10.2"
          ],
          "status": "PENDING_UPDATE",
          "links": {
              "self": "https://Endpoint/v2/zones/2c9eb155587194ec01587224c9f90149/recordsets/2c9eb155587228570158722b6ac30007"
          },
          "zone_id": "2c9eb155587194ec01587224c9f90149",
          "zone_name": "example.com.",
          "create_at": "2016-11-17T12:03:17.827",
          "update_at": "2016-11-17T12:56:03.827",
          "default": false,
          "project_id": "e55c6f3dc4e34c9f86353b664ae0e70c"
      }

Returned Value
--------------

If the API call returns a code of 2\ *xx*, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
