:original_name: dns_api_67004.html

.. _dns_api_67004:

Querying Tags of a Resource
===========================

Function
--------

Query tags of a specified resource.

URI
---

GET /v2/{project_id}/{resource_type}/{resource_id}/tags

For details, see :ref:`Table 1 <dns_api_67004__table6099729418149>`.

.. _dns_api_67004__table6099729418149:

.. table:: **Table 1** Parameters in the URI

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                     |
   +=================+=================+=================+=================================================================================+
   | project_id      | Yes             | String          | Project ID. You can obtain it in :ref:`Obtaining a Project ID <dns_api_80007>`. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------+
   | resource_type   | Yes             | String          | Resource type.                                                                  |
   |                 |                 |                 |                                                                                 |
   |                 |                 |                 | -  DNS-public_zone                                                              |
   |                 |                 |                 | -  DNS-private_zone                                                             |
   |                 |                 |                 | -  DNS-public_recordset                                                         |
   |                 |                 |                 | -  DNS-private_recordset                                                        |
   |                 |                 |                 | -  DNS-ptr_record                                                               |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------+
   | resource_id     | Yes             | String          | Resource ID                                                                     |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   None

-  Example request

   Query tags of the private zone whose ID is ff8080825b8fc86c015b94bc6f8712c3:

   .. code-block:: text

      GET https://{DNS_Endpoint}/v2/{project_id}/DNS-private_zone/ff8080825b8fc86c015b94bc6f8712c3/tags

Response
--------

-  Parameter description

   .. table:: **Table 2** Parameter in the response

      +-----------+-----------------+---------------------------------------------------------------------------------+
      | Parameter | Type            | Description                                                                     |
      +===========+=================+=================================================================================+
      | tags      | Array of object | Tag list. For details, see :ref:`Table 2 <dns_api_80006__table19530794112436>`. |
      +-----------+-----------------+---------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "tags": [
              {
                  "key": "key1",
                  "value": "value1"
              },
              {
                  "key": "key2",
                  "value": "value2"
              }
          ]
      }

Returned Value
--------------

If a 2xx status code is returned, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
