:original_name: dns_api_70003.html

.. _dns_api_70003:

Record Set Management
=====================

.. table:: **Table 1** Actions for record set management

   +----------------------------------------+------------------------------------------------------+----------------------+-----------------------------------+-------------+
   | Permission                             | API                                                  | Action               | Dependencies                      | IAM Project |
   +========================================+======================================================+======================+===================================+=============+
   | Create a record set.                   | POST /v2/zones/{zone_id}/recordsets                  | dns:recordset:create | ``-``                             | Supported   |
   +----------------------------------------+------------------------------------------------------+----------------------+-----------------------------------+-------------+
   | Query a record set.                    | GET /v2/zones/{zone_id}/recordsets/{recordset_id}    | dns:recordset:get    | ``-``                             | Supported   |
   +----------------------------------------+------------------------------------------------------+----------------------+-----------------------------------+-------------+
   | Query record sets in a specified zone. | GET /v2/zones/{zone_id}/recordsets                   | dns:recordset:list   | ``-``                             | Supported   |
   +----------------------------------------+------------------------------------------------------+----------------------+-----------------------------------+-------------+
   | Query all record sets.                 | GET /v2/recordsets                                   | dns:recordset:list   | ``-``                             | Supported   |
   +----------------------------------------+------------------------------------------------------+----------------------+-----------------------------------+-------------+
   | Modify a record set.                   | PUT /v2/zones/{zone_id}/recordsets/{recordset_id}    | dns:recordset:update | ``-``                             | Supported   |
   +----------------------------------------+------------------------------------------------------+----------------------+-----------------------------------+-------------+
   | Delete a record set.                   | DELETE /v2/zones/{zone_id}/recordsets/{recordset_id} | dns:recordset:delete | ces:remoteChecks:list             | Supported   |
   |                                        |                                                      |                      |                                   |             |
   |                                        |                                                      |                      | ces:siteMonitorHealthCheck:get    |             |
   |                                        |                                                      |                      |                                   |             |
   |                                        |                                                      |                      | ces:siteMonitorHealthCheck:create |             |
   |                                        |                                                      |                      |                                   |             |
   |                                        |                                                      |                      | ces:siteMonitorRule:delete        |             |
   |                                        |                                                      |                      |                                   |             |
   |                                        |                                                      |                      | ces:siteMonitorRule:put           |             |
   +----------------------------------------+------------------------------------------------------+----------------------+-----------------------------------+-------------+
