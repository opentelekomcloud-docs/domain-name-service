:original_name: dns_api_63002.html

.. _dns_api_63002:

Creating a Private Zone
=======================

Function
--------

Create a private zone.

URI
---

POST /v2/zones

Request
-------

-  Parameter description

   .. table:: **Table 1** Parameters in the request

      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                         |
      +=================+=================+=================+=====================================================================================================================+
      | name            | Yes             | String          | Domain name of the zone to be created                                                                               |
      |                 |                 |                 |                                                                                                                     |
      |                 |                 |                 | -  If a domain name is ended with a period (.), it cannot exceed 254 characters.                                    |
      |                 |                 |                 | -  Otherwise, the domain name cannot exceed 253 characters.                                                         |
      |                 |                 |                 | -  A domain name cannot exceed 63 characters. Multiple domain names are separated with periods (.).                 |
      |                 |                 |                 |                                                                                                                     |
      |                 |                 |                 | A domain name is case insensitive. Uppercase letters will also be converted into lowercase letters.                 |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
      | description     | No              | String          | Description of the domain name, which cannot exceed 255 characters                                                  |
      |                 |                 |                 |                                                                                                                     |
      |                 |                 |                 | The value is left blank by default.                                                                                 |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
      | zone_type       | Yes             | String          | Zone type                                                                                                           |
      |                 |                 |                 |                                                                                                                     |
      |                 |                 |                 | The value must be **private**, indicating private zones accessible only to hosts in specified VPCs will be created. |
      |                 |                 |                 |                                                                                                                     |
      |                 |                 |                 | For details about creating a public zone, see section :ref:`Creating a Public Zone <dns_api_62001>`.                |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
      | email           | No              | String          | Email address of the administrator managing the zone                                                                |
      |                 |                 |                 |                                                                                                                     |
      |                 |                 |                 | The default value is the service email address.                                                                     |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
      | ttl             | No              | Integer         | Caching period of the SOA record set (in seconds)                                                                   |
      |                 |                 |                 |                                                                                                                     |
      |                 |                 |                 | The value ranges from **1** to **2147483647**.                                                                      |
      |                 |                 |                 |                                                                                                                     |
      |                 |                 |                 | The default value is **300**.                                                                                       |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
      | router          | Yes             | Object          | Router information (VPC associated with the private zone)                                                           |
      |                 |                 |                 |                                                                                                                     |
      |                 |                 |                 | For details, see :ref:`Table 2 <dns_api_63002__table4448008117179>`.                                                |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
      | tags            | No              | Array of object | Resource tag. For details, see :ref:`Table 3 <dns_api_63002__table58807309208>`.                                    |
      |                 |                 |                 |                                                                                                                     |
      |                 |                 |                 | The value is left blank by default.                                                                                 |
      +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_63002__table4448008117179:

   .. table:: **Table 2** Description of the **router** field

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                          |
      +=================+=================+=================+======================================================================================+
      | router_id       | Yes             | String          | ID of the associated VPC                                                             |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------+
      | router_region   | No              | String          | Region of the VPC                                                                    |
      |                 |                 |                 |                                                                                      |
      |                 |                 |                 | If it is left blank, the region of the project in the token takes effect by default. |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------+

   .. _dns_api_63002__table58807309208:

   .. table:: **Table 3** Description of the **tags** field

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                          |
      +=================+=================+=================+======================================================================================+
      | key             | Yes             | String          | Tag key                                                                              |
      |                 |                 |                 |                                                                                      |
      |                 |                 |                 | -  Cannot be left blank.                                                             |
      |                 |                 |                 | -  Must be unique for each resource.                                                 |
      |                 |                 |                 | -  Can contain a maximum of 128 Unicode characters.                                  |
      |                 |                 |                 | -  Can contain letters, digits, spaces, and the following characters: \_ . : = + - @ |
      |                 |                 |                 | -  Cannot start or end with a space, or cannot start with **\_sys\_**.               |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------+
      | value           | No              | String          | Tag value                                                                            |
      |                 |                 |                 |                                                                                      |
      |                 |                 |                 | -  Can be left blank.                                                                |
      |                 |                 |                 | -  Can contain a maximum of 255 Unicode characters.                                  |
      |                 |                 |                 | -  Can contain letters, digits, spaces, and the following characters: \_ . : = + - @ |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------+

-  Example request

   Create a private zone named **example.com**.

   .. code-block:: text

      POST https://{DNS_Endpoint}/v2/zones

   .. code-block::

      {
          "name": "example.com.",
          "description": "This is an example zone.",
          "zone_type": "private",
          "email": "xx@example.org",
          "router": {
              "router_id": "19664294-0bf6-4271-ad3a-94b8c79c6558",
              "router_region": "xx"
          },
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

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                              |
      +=======================+=======================+==========================================================================================================================+
      | id                    | String                | Zone ID, which is a UUID used to identify the zone                                                                       |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Zone name                                                                                                                |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | description           | String                | Zone description                                                                                                         |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | email                 | String                | Email address of the administrator managing the zone                                                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | zone_type             | String                | Zone type, which can be **public** or **private**                                                                        |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | ttl                   | Integer               | TTL value of the SOA record set in the zone                                                                              |
      |                       |                       |                                                                                                                          |
      |                       |                       | The value ranges from **1** to **2147483647**.                                                                           |
      |                       |                       |                                                                                                                          |
      |                       |                       | The default value is **300**.                                                                                            |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | serial                | Integer               | Serial number in the SOA record set in a zone, which identifies the change on the primary DNS server                     |
      |                       |                       |                                                                                                                          |
      |                       |                       | This parameter is not used currently.                                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Resource status                                                                                                          |
      |                       |                       |                                                                                                                          |
      |                       |                       | For details, see :ref:`Resource Status <dns_api_80005__section33673592114748>`.                                          |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | record_num            | Integer               | Number of record sets in the zone                                                                                        |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | pool_id               | String                | Pool ID of the zone, which is assigned by the system                                                                     |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | project_id            | String                | Project ID of the zone                                                                                                   |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | created_at            | String                | Time when the zone was created                                                                                           |
      |                       |                       |                                                                                                                          |
      |                       |                       | The UTC time format is used: YYYY-MM-DDTHH:MM:SSZ.                                                                       |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | updated_at            | String                | Time when the zone was updated                                                                                           |
      |                       |                       |                                                                                                                          |
      |                       |                       | The UTC time format is used: YYYY-MM-DDTHH:MM:SSZ.                                                                       |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | links                 | Object                | Link to the current resource or other related resources.                                                                 |
      |                       |                       |                                                                                                                          |
      |                       |                       | When a response is broken into pages, a **next** link is provided to retrieve all results.                               |
      |                       |                       |                                                                                                                          |
      |                       |                       | For details, see :ref:`Table 5 <dns_api_63002__table52442344175457>`.                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | masters               | Array of strings      | Master DNS servers, from which the slave servers get DNS information                                                     |
      |                       |                       |                                                                                                                          |
      |                       |                       | This parameter is not used currently.                                                                                    |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+
      | router                | Object                | Information about the VPC associated with the zone. For details, see :ref:`Table 6 <dns_api_63002__table4512106017551>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_63002__table52442344175457:

   .. table:: **Table 5** Parameters in the **links** field

      ========= ====== ============================
      Parameter Type   Description
      ========= ====== ============================
      self      String Link to the current resource
      next      String Link to the next page
      ========= ====== ============================

   .. _dns_api_63002__table4512106017551:

   .. table:: **Table 6** Description of the **router** field

      +-----------------------+-----------------------+---------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                     |
      +=======================+=======================+=================================================================================+
      | status                | String                | Resource status                                                                 |
      |                       |                       |                                                                                 |
      |                       |                       | For details, see :ref:`Resource Status <dns_api_80005__section33673592114748>`. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------+
      | router_id             | String                | Router ID (VPC ID)                                                              |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------+
      | router_region         | String                | Region of the VPC                                                               |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "id": "ff8080825b8fc86c015b94bc6f8712c3",
          "name": "example.com.",
          "description": "This is an example zone.",
          "email": "xx@example.com",
          "ttl": 300,
          "serial": 1,
          "masters": [],
          "status": "PENDING_CREATE",
          "links": {
              "self": "https://Endpoint/v2/zones/ff8080825b8fc86c015b94bc6f8712c3"
          },
          "pool_id": "ff8080825ab738f4015ab7513298010e",
          "project_id": "e55c6f3dc4e34c9f86353b664ae0e70c",
          "zone_type": "private",
          "created_at": "2017-04-22T08:17:08.997",
          "updated_at": null,
          "record_num": 0,
          "router": {
              "status": "PENDING_CREATE",
              "router_id": "19664294-0bf6-4271-ad3a-94b8c79c6558",
              "router_region": "xx"
          }
      }

Returned Value
--------------

If a 2xx status code is returned, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
