:original_name: dns_api_62001.html

.. _dns_api_62001:

Creating a Public Zone
======================

Function
--------

Create a public zone.

URI
---

POST /v2/zones

Request
-------

-  Parameter description

   .. table:: **Table 1** Parameters in the request

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                                    |
      +=================+=================+=================+================================================================================================================================================================+
      | name            | Yes             | String          | Domain name registered with the domain name registrar                                                                                                          |
      |                 |                 |                 |                                                                                                                                                                |
      |                 |                 |                 | -  If a domain name is ended with a dot (.), it cannot exceed 254 characters.                                                                                  |
      |                 |                 |                 | -  If a domain name is not ended with a dot (.), it cannot exceed 253 characters.                                                                              |
      |                 |                 |                 | -  A domain name cannot exceed 63 characters. Multiple domain names are separated with dots (.).                                                               |
      |                 |                 |                 |                                                                                                                                                                |
      |                 |                 |                 | A domain name is case insensitive. Uppercase letters will also be converted into lowercase letters.                                                            |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description     | No              | String          | Description of the zone, which cannot exceed 255 characters                                                                                                    |
      |                 |                 |                 |                                                                                                                                                                |
      |                 |                 |                 | The value is left blank by default.                                                                                                                            |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | zone_type       | No              | String          | Zone type, which can be **public** or **private**                                                                                                              |
      |                 |                 |                 |                                                                                                                                                                |
      |                 |                 |                 | -  **public**: public zones accessible to hosts on the Internet                                                                                                |
      |                 |                 |                 | -  **private**: private zones accessible only to hosts in specified VPCs                                                                                       |
      |                 |                 |                 |                                                                                                                                                                |
      |                 |                 |                 | If the value is left blank, a public zone will be created. For details about how to create a private zone, see :ref:`Creating a Private Zone <dns_api_63002>`. |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | email           | No              | String          | Email address of the administrator managing the zone                                                                                                           |
      |                 |                 |                 |                                                                                                                                                                |
      |                 |                 |                 | The default value is the service email address.                                                                                                                |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ttl             | No              | Integer         | Caching period of the SOA record set (in seconds)                                                                                                              |
      |                 |                 |                 |                                                                                                                                                                |
      |                 |                 |                 | The value ranges from **1** to **2147483647**.                                                                                                                 |
      |                 |                 |                 |                                                                                                                                                                |
      |                 |                 |                 | The default value is **300**.                                                                                                                                  |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tags            | No              | Array of object | Resource tag. For details, see :ref:`Table 2 <dns_api_62001__table619059185111>`.                                                                              |
      |                 |                 |                 |                                                                                                                                                                |
      |                 |                 |                 | The value is left blank by default.                                                                                                                            |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_62001__table619059185111:

   .. table:: **Table 2** Description of the **tags** field

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

   Create a public zone named **example.com**.

   .. code-block:: text

      POST https://{DNS_Endpoint}/v2/zones

   .. code-block::

      {
          "name": "example.com.",
          "description": "This is an example zone.",
          "zone_type": "public",
          "email": "xx@example.org",
          "ttl": 300,
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

   .. table:: **Table 3** Parameters in the response

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                                                         |
      +=======================+=======================+=====================================================================================================================================================+
      | id                    | String                | Zone ID, which is a UUID used to identify the zone                                                                                                  |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Zone name                                                                                                                                           |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | description           | String                | Zone description                                                                                                                                    |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | email                 | String                | Email address of the administrator managing the zone                                                                                                |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | zone_type             | String                | Zone type, which can be **public** or **private**                                                                                                   |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | ttl                   | Integer               | TTL value of the SOA record set in the zone                                                                                                         |
      |                       |                       |                                                                                                                                                     |
      |                       |                       | The value ranges from **1** to **2147483647**.                                                                                                      |
      |                       |                       |                                                                                                                                                     |
      |                       |                       | The default value is **300**.                                                                                                                       |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | serial                | Integer               | Serial number in the SOA record set in a zone, which identifies the change on the primary DNS server                                                |
      |                       |                       |                                                                                                                                                     |
      |                       |                       | This parameter is not used currently.                                                                                                               |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Resource status                                                                                                                                     |
      |                       |                       |                                                                                                                                                     |
      |                       |                       | For details, see :ref:`Resource Status <dns_api_80005__section33673592114748>`.                                                                     |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | record_num            | Integer               | Number of record sets in the zone                                                                                                                   |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | pool_id               | String                | Pool ID of the zone, which is assigned by the system                                                                                                |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | project_id            | String                | Project ID of the zone                                                                                                                              |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | created_at            | String                | Time when the zone was created                                                                                                                      |
      |                       |                       |                                                                                                                                                     |
      |                       |                       | The UTC time format is used: YYYY-MM-DDTHH:MM:SSZ.                                                                                                  |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | updated_at            | String                | Time when the zone was updated                                                                                                                      |
      |                       |                       |                                                                                                                                                     |
      |                       |                       | The UTC time format is used: YYYY-MM-DDTHH:MM:SSZ.                                                                                                  |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | links                 | Object                | Link to the current resource or other related resources. When a response is broken into pages, a **next** link is provided to retrieve all results. |
      |                       |                       |                                                                                                                                                     |
      |                       |                       | For details, see :ref:`Table 4 <dns_api_62001__table0172144213344>`.                                                                                |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | masters               | Array of strings      | Master DNS servers, from which the slave servers get DNS information                                                                                |
      |                       |                       |                                                                                                                                                     |
      |                       |                       | This parameter is not used currently.                                                                                                               |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_62001__table0172144213344:

   .. table:: **Table 4** Description of the **links** field

      ========= ====== ============================
      Parameter Type   Description
      ========= ====== ============================
      self      String Link to the current resource
      next      String Link to the next page
      ========= ====== ============================

-  Example response

   .. code-block::

      {
          "id": "2c9eb155587194ec01587224c9f90149",
          "name": "example.com.",
          "description": "This is an example zone.",
          "email": "xx@example.com",
          "ttl": 300,
          "serial": 1,
          "masters": [],
          "status": "PENDING_CREATE",
          "links": {
              "self": "https://Endpoint/v2/zones/2c9eb155587194ec01587224c9f90149"
          },
          "pool_id": "00000000570e54ee01570e9939b20019",
          "project_id": "e55c6f3dc4e34c9f86353b664ae0e70c",
          "zone_type": "public",
          "created_at": "2016-11-17T11:56:03.439",
          "updated_at": null,
          "record_num": 0
      }

Returned Value
--------------

If a 2xx status code is returned, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
