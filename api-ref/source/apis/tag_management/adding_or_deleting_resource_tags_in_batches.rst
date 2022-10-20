:original_name: dns_api_67003.html

.. _dns_api_67003:

Adding or Deleting Resource Tags in Batches
===========================================

Function
--------

Add or delete tags for a specified resource in batches.

You can add a maximum of 20 tags to a resource.

The API is idempotent.

-  When you are to create tags, if there are duplicate keys in the request body, an error is reported.

   If a to-be-created tag has the same key as an existing tag, the tag will be created and overwrite the existing one.

-  When tags are being deleted and some tags do not exist, the operation is considered successful by default. The character set of the tags will not be checked.

URI
---

POST /v2/{project_id}/{resource_type}/{resource_id}/tags/action

For details, see :ref:`Table 1 <dns_api_67003__table6099729418149>`.

.. _dns_api_67003__table6099729418149:

.. table:: **Table 1** Parameters in the URI

   +---------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                                                                                                       |
   +===============+===========+========+===================================================================================================================================================+
   | project_id    | Yes       | String | Project ID. You can obtain it in :ref:`Obtaining a Project ID <dns_api_80007>`.                                                                   |
   +---------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource_type | Yes       | String | Resource type, which can be **DNS-public_zone**, **DNS-private_zone**, **DNS-public_recordset**, **DNS-private_recordset**, or **DNS-ptr_record** |
   +---------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource_id   | Yes       | String | Resource ID                                                                                                                                       |
   +---------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameters in the request

      +-----------+-----------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Mandatory | Type            | Description                                                                                                                                                |
      +===========+===========+=================+============================================================================================================================================================+
      | tags      | Yes       | Array of object | Tag list. The tag list structure cannot be empty when you delete tags. For details, see :ref:`Table 3 <dns_api_67003__t4b1b8c5089e8440eb9e241650e1b469f>`. |
      +-----------+-----------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | action    | Yes       | String          | Operation, which can be **create** or **delete** (case sensitive)                                                                                          |
      +-----------+-----------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _dns_api_67003__t4b1b8c5089e8440eb9e241650e1b469f:

   .. table:: **Table 3** Parameters in the **tags** field

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                                     |
      +=================+=================+=================+=================================================================================================================================================================+
      | key             | Yes             | String          | Tag key, which cannot be left blank or be an empty string. It can contain only digits, letters, hyphens (-), and underscores (_).                               |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | -  When **action** is set to **create**, the key contains 36 Unicode characters at most.                                                                        |
      |                 |                 |                 | -  When **action** is set to **delete**, the key contains 127 Unicode characters at most.                                                                       |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | value           | No              | String          | Tag value, which can be an empty string. It can contain only digits, letters, hyphens (-), and underscores (_).                                                 |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | -  When **action** is set to **create**, the tag value is mandatory and contains 43 Unicode characters at most.                                                 |
      |                 |                 |                 | -  When **action** is set to **delete**, the tag value is optional and contains 255 Unicode characters at most. If you leave it blank, tags are deleted by key. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   Add and delete tags for the private zone whose ID is ff8080825b8fc86c015b94bc6f8712c3:

   .. code-block:: text

      POST https://{DNS_Endpoint}/v2/{project_id}/DNS-private_zone/ff8080825b8fc86c015b94bc6f8712c3/tags/action

   .. code-block::

      {
          "action": "create",
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
      or
      {
          "action": "delete",
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

Response
--------

None

Returned Value
--------------

If the API call returns a code of 2\ *xx*, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
