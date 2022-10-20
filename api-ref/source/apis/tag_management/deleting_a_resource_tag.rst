:original_name: dns_api_67002.html

.. _dns_api_67002:

Deleting a Resource Tag
=======================

Function
--------

Delete a resource tag.

The API is idempotent.

When you delete a tag that does not exist, the system reports that the tag does not exist.

URI
---

DELETE /v2/{project_id}/{resource_type}/{resource_id}/tags/{key}

For details, see :ref:`Table 1 <dns_api_67002__table6099729418149>`.

.. _dns_api_67002__table6099729418149:

.. table:: **Table 1** Parameters in the URI

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                       |
   +=================+=================+=================+===================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. You can obtain it in :ref:`Obtaining a Project ID <dns_api_80007>`.                                                                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource_type   | Yes             | String          | Resource type, which can be **DNS-public_zone**, **DNS-private_zone**, **DNS-public_recordset**, **DNS-private_recordset**, or **DNS-ptr_record** |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource_id     | Yes             | String          | Resource ID                                                                                                                                       |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | key             | Yes             | String          | Tag key                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | The key cannot be left blank or be an empty string.                                                                                               |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   None

-  Example request

   Delete tags for the private zone whose ID is ff8080825b8fc86c015b94bc6f8712c3:

   .. code-block:: text

      DELETE https://{DNS_Endpoint}/v2/{project_id}/DNS-private_zone/ff8080825b8fc86c015b94bc6f8712c3/tags/{key}

Response
--------

None

Returned Value
--------------

If the API call returns a code of 2\ *xx*, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
