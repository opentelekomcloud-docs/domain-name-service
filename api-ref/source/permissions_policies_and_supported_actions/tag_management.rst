:original_name: dns_api_70005.html

.. _dns_api_70005:

Tag Management
==============

.. table:: **Table 1** Actions for tag management

   +-----------------------------------------+------------------------------------------------------------------+-------------+----------------------+-------------+
   | Permission                              | API                                                              | Action      | Dependent Permission | IAM Project |
   |                                         |                                                                  |             |                      |             |
   |                                         |                                                                  |             |                      | (Project)   |
   +=========================================+==================================================================+=============+======================+=============+
   | Add a resource tag.                     | POST /v2/{project_id}/{resource_type}/{resource_id}/tags         | dns:tag:set | ``-``                | Y           |
   +-----------------------------------------+------------------------------------------------------------------+-------------+----------------------+-------------+
   | Add or delete resource tags in batches. | POST /v2/{project_id}/{resource_type}/{resource_id}/tags/action  | dns:tag:set | ``-``                | Y           |
   +-----------------------------------------+------------------------------------------------------------------+-------------+----------------------+-------------+
   | Delete a resource tag.                  | DELETE /v2/{project_id}/{resource_type}/{resource_id}/tags/{key} | dns:tag:set | ``-``                | Y           |
   +-----------------------------------------+------------------------------------------------------------------+-------------+----------------------+-------------+
   | Query tags of a resource.               | GET /v2/{project_id}/{resource_type}/{resource_id}/tags          | dns:tag:get | ``-``                | Y           |
   +-----------------------------------------+------------------------------------------------------------------+-------------+----------------------+-------------+
   | Query project tags.                     | GET /v2/{project_id}/{resource_type}/tags                        | dns:tag:get | ``-``                | Y           |
   +-----------------------------------------+------------------------------------------------------------------+-------------+----------------------+-------------+
   | Query resources by tag.                 | POST /v2/{project_id}/{resource_type}/resource_instances/action  | dns:tag:get | ``-``                | Y           |
   +-----------------------------------------+------------------------------------------------------------------+-------------+----------------------+-------------+
