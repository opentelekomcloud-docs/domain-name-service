:original_name: dns_api_66005.html

.. _dns_api_66005:

Unsetting a PTR Record
======================

Function
--------

Unset the PTR record to the default value.

URI
---

PATCH /v2/reverse/floatingips/{region}:{floatingip_id}

For details, see :ref:`Table 1 <dns_api_66005__table48883615>`.

.. _dns_api_66005__table48883615:

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

   .. table:: **Table 2** Parameter in the request

      +-----------------+-----------------+-----------------+------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                        |
      +=================+=================+=================+====================================+
      | ptrdname        | Yes             | String          | Domain name of the PTR record      |
      |                 |                 |                 |                                    |
      |                 |                 |                 | Set it to **null** in the request. |
      +-----------------+-----------------+-----------------+------------------------------------+

-  Example request

   Unset the PTR record whose EIP ID is **c5504932-bf23-4171-b655-b87a6bc59334** to the default value:

   .. code-block:: text

      PATCH https://{DNS_Endpoint}/v2/reverse/floatingips/region_id:c5504932-bf23-4171-b655-b87a6bc59334

   .. code-block::

      {
          "ptrdname": null
      }

Response
--------

None

Returned Value
--------------

If the API call returns a code of 2\ *xx*, for example, 200, 202, or 204, the request is successful.

For details, see :ref:`Status Code <dns_api_80002>`.
