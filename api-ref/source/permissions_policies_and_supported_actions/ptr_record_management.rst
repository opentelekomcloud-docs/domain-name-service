:original_name: dns_api_70004.html

.. _dns_api_70004:

PTR Record Management
=====================

.. table:: **Table 1** Actions for PTR record management

   +----------------------+--------------------------------------------------------+--------------+------------------+-------------+
   | Permission           | API                                                    | Action       | Dependencies     | IAM Project |
   +======================+========================================================+==============+==================+=============+
   | Create a PTR record. | PATCH /v2/reverse/floatingips/{region}:{floatingip_id} | dns:ptr:set  | vpc:``*``:get\*  | Supported   |
   |                      |                                                        |              |                  |             |
   |                      |                                                        |              | vpc:``*``:list\* |             |
   +----------------------+--------------------------------------------------------+--------------+------------------+-------------+
   | Modify a PTR record. | PATCH /v2/reverse/floatingips/{region}:{floatingip_id} | dns:ptr:set  | vpc:``*``:get\*  | Supported   |
   |                      |                                                        |              |                  |             |
   |                      |                                                        |              | vpc:``*``:list\* |             |
   +----------------------+--------------------------------------------------------+--------------+------------------+-------------+
   | Unset a PTR record.  | PATCH /v2/reverse/floatingips/{region}:{floatingip_id} | dns:ptr:set  | vpc:``*``:get\*  | Supported   |
   |                      |                                                        |              |                  |             |
   |                      |                                                        |              | vpc:``*``:list\* |             |
   +----------------------+--------------------------------------------------------+--------------+------------------+-------------+
   | Query a PTR record.  | GET /v2/reverse/floatingips/{region}:{floatingip_id}   | dns:ptr:get  | ``-``            | Supported   |
   +----------------------+--------------------------------------------------------+--------------+------------------+-------------+
   | Query PTR records.   | GET /v2/reverse/floatingips                            | dns:ptr:list | ``-``            | Supported   |
   +----------------------+--------------------------------------------------------+--------------+------------------+-------------+
