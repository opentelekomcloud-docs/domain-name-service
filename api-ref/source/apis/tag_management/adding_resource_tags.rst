:original_name: dns_api_67001.html

.. _dns_api_67001:

Adding Resource Tags
====================

Function
--------

Add tags to a specified resource.

You can add up to 20 tags to a resource.

The API is idempotent.

If a to-be-created tag has the same key as an existing tag, the tag will be created and overwrite the existing one.

URI
---

POST /v2/{project_id}/{resource_type}/{resource_id}/tags

For details, see :ref:`Table 1 <dns_api_67001__table6099729418149>`.

.. _dns_api_67001__table6099729418149:

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

   .. table:: **Table 2** Parameter in the request

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                         |
      +=================+=================+=================+=====================================================================================+
      | tag             | Yes             | Object          | Tag                                                                                 |
      |                 |                 |                 |                                                                                     |
      |                 |                 |                 | For details, see :ref:`Table 3 <dns_api_67001__t055aabf9d8484a0d922846610305b7f9>`. |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------+

   .. _dns_api_67001__t055aabf9d8484a0d922846610305b7f9:

   .. table:: **Table 3** Parameters in the tag list

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

   Add tags for the private zone whose ID is ff8080825b8fc86c015b94bc6f8712c3:

   .. code-block:: text

      POST https://{DNS_Endpoint}/v2/{project_id}/DNS-private_zone/ff8080825b8fc86c015b94bc6f8712c3/tags

   .. code-block::

      {
          "tag": {
              "key": "key1",
              "value": "value1"
          }
      }

Response
--------

None

Returned Value
--------------

If a 2xx status code is returned, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
