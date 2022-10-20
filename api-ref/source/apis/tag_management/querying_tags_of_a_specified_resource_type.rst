:original_name: dns_api_67005.html

.. _dns_api_67005:

Querying Tags of a Specified Resource Type
==========================================

Function
--------

Query all tags of a resource type.

URI
---

GET /v2/{project_id}/{resource_type}/tags

For details, see :ref:`Table 1 <dns_api_67005__table6099729418149>`.

.. _dns_api_67005__table6099729418149:

.. table:: **Table 1** Parameters in the URI

   +---------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                                                                                                       |
   +===============+===========+========+===================================================================================================================================================+
   | project_id    | Yes       | String | Project ID. You can obtain it in :ref:`Obtaining a Project ID <dns_api_80007>`.                                                                   |
   +---------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource_type | Yes       | String | Resource type, which can be **DNS-public_zone**, **DNS-private_zone**, **DNS-public_recordset**, **DNS-private_recordset**, or **DNS-ptr_record** |
   +---------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

-  Parameter description

   None

-  Example request

   Query tags of all private zones in a project:

   .. code-block:: text

      GET https://{DNS_Endpoint}/v2/{project_id}/DNS-private_zone/tags

Response
--------

-  Parameter description

   .. table:: **Table 2** Parameters in the response

      +-----------+-----------------+---------------------------------------------------------------------------------+
      | Parameter | Type            | Description                                                                     |
      +===========+=================+=================================================================================+
      | tags      | Array of object | Tag list. For details, see :ref:`Table 3 <dns_api_67005__table19530794112436>`. |
      +-----------+-----------------+---------------------------------------------------------------------------------+

   .. _dns_api_67005__table19530794112436:

   .. table:: **Table 3** Description of the **tag** field

      +-----------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Type             | Description                                                                                                                                                |
      +===========+==================+============================================================================================================================================================+
      | key       | String           | Tag key. The key contains 36 Unicode characters at most and cannot be blank. It can contain only digits, letters, hyphens (-), and underscores (_).        |
      +-----------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | values    | Array of strings | Tag value, which contains 43 Unicode characters at most and can be an empty string. It can contain only digits, letters, hyphens (-), and underscores (_). |
      +-----------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "tags": [
              {
                  "key": "key1",
                  "values": [
                              "value1",
                              "value2"
                            ]
              },
              {
                  "key": "key2",
                  "values": [
                              "value1",
                              "value2"
                            ]
              }
          ]
      }

Returned Value
--------------

If the API call returns a code of 2\ *xx*, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
