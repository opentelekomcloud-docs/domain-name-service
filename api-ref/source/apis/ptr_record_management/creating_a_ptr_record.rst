:original_name: dns_api_66002.html

.. _dns_api_66002:

Creating a PTR Record
=====================

Function
--------

Create a PTR record for an elastic IP address (EIP).

.. note::

   The same :ref:`URI <dns_api_66002__section53701671161015>` is used to :ref:`create <dns_api_66002>`, :ref:`modify <dns_api_66006>`, and :ref:`delete <dns_api_66005>` PTR records. Different request bodies are used to implement different functions.

.. _dns_api_66002__section53701671161015:

URI
---

PATCH /v2/reverse/floatingips/{region}:{floatingip_id}

For details, see :ref:`Table 1 <dns_api_66002__table6099729418149>`.

.. _dns_api_66002__table6099729418149:

.. table:: **Table 1** Parameters in the URI

   ============= ========= ====== =====================
   Parameter     Mandatory Type   Description
   ============= ========= ====== =====================
   region        Yes       String Region of the tenant.
   floatingip_id Yes       String EIP ID
   ============= ========= ====== =====================

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameters in the request

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                   |
      +=================+=================+=================+===============================================================================================================================+
      | ptrdname        | Yes             | String          | Domain name of the PTR record                                                                                                 |
      |                 |                 |                 |                                                                                                                               |
      |                 |                 |                 | A domain name is case insensitive. Uppercase letters will also be converted into lowercase letters.                           |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
      | description     | No              | String          | PTR record description                                                                                                        |
      |                 |                 |                 |                                                                                                                               |
      |                 |                 |                 | The value is left blank by default.                                                                                           |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
      | ttl             | No              | Integer         | PTR record cache duration (in seconds) on a local DNS server. The longer the duration is, the slower the update takes effect. |
      |                 |                 |                 |                                                                                                                               |
      |                 |                 |                 | If your service address is frequently changed, set TTL to a smaller value.                                                    |
      |                 |                 |                 |                                                                                                                               |
      |                 |                 |                 | The value ranges from **1** to **2147483647**.                                                                                |
      |                 |                 |                 |                                                                                                                               |
      |                 |                 |                 | The default value is **300**.                                                                                                 |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+
      | tags            | No              | Array of object | Resource tag. For details, see :ref:`Table 3 <dns_api_66002__table9752964195025>`.                                            |
      |                 |                 |                 |                                                                                                                               |
      |                 |                 |                 | The value is left blank by default.                                                                                           |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_66002__table9752964195025:

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

   Create a PTR record for the EIP whose ID is **c5504932-bf23-4171-b655-b87a6bc59334**:

   .. code-block:: text

      PATCH https://{DNS_Endpoint}/v2/reverse/floatingips/region_id:c5504932-bf23-4171-b655-b87a6bc59334

   .. code-block::

      {
          "ptrdname": "www.example.com",
          "description": "Description for this PTR record",
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

   .. table:: **Table 4** Parameters in the response

      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                                                                    |
      +=======================+=======================+================================================================================================================================================================+
      | id                    | String                | PTR record ID, which is in **{region}:{floatingip_id}** format                                                                                                 |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ptrdname              | String                | Domain name of the PTR record                                                                                                                                  |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description           | String                | PTR record description                                                                                                                                         |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ttl                   | Integer               | PTR record cache duration (in seconds) on a local DNS server. The longer the duration is, the slower the update takes effect.                                  |
      |                       |                       |                                                                                                                                                                |
      |                       |                       | If your service address is frequently changed, set TTL to a smaller value.                                                                                     |
      |                       |                       |                                                                                                                                                                |
      |                       |                       | The value ranges from **1** to **2147483647**.                                                                                                                 |
      |                       |                       |                                                                                                                                                                |
      |                       |                       | The default value is **300**.                                                                                                                                  |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | address               | String                | EIP                                                                                                                                                            |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Resource status                                                                                                                                                |
      |                       |                       |                                                                                                                                                                |
      |                       |                       | For details, see :ref:`Resource Status <dns_api_80005__section33673592114748>`.                                                                                |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | action                | String                | Requested operation on the resource                                                                                                                            |
      |                       |                       |                                                                                                                                                                |
      |                       |                       | The value can be **CREATE**, **UPDATE**, **DELETE**, or **NONE**.                                                                                              |
      |                       |                       |                                                                                                                                                                |
      |                       |                       | **NONE** indicates that no operation will be performed.                                                                                                        |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | links                 | Object                | Link to the current resource or other related resources.                                                                                                       |
      |                       |                       |                                                                                                                                                                |
      |                       |                       | When a response is broken into pages, a **next** link is provided to retrieve all results. For details, see :ref:`Table 5 <dns_api_66002__table354521744216>`. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_66002__table354521744216:

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
          "id": "region_id:c5504932-bf23-4171-b655-b87a6bc59334",
          "ptrdname": "www.example.com.",
          "description": "Description for this PTR record",
          "address": "10.154.52.138",
          "action": "CREATE",
          "ttl": 300,
          "status": "PENDING_CREATE",
          "links": {
              "self": "https://Endpoint/v2/reverse/floatingips/region_id:c5504932-bf23-4171-b655-b87a6bc59334"
          }
      }

Returned Value
--------------

If a 2xx status code is returned, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
