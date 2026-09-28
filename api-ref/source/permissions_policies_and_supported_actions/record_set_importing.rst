:original_name: dns_api_70006.html

.. _dns_api_70006:

Record Set Importing
====================

.. table:: **Table 1** Actions for record set importing

   +--------------------------------------------------------------------------+-------+-----------------------------------+--------------+-------------+
   | Permission                                                               | API   | Action                            | Dependencies | IAM Project |
   +==========================================================================+=======+===================================+==============+=============+
   | Download the template for importing public zone record sets in batches.  | ``-`` | dns:publicRecordset:getImport     | ``-``        | Supported   |
   +--------------------------------------------------------------------------+-------+-----------------------------------+--------------+-------------+
   | Create a task to import public zone record sets.                         | ``-`` | dns:publicRecordset:createImport  | ``-``        | Supported   |
   +--------------------------------------------------------------------------+-------+-----------------------------------+--------------+-------------+
   | Query a task to import public zone record sets.                          | ``-`` | dns:publicRecordset:getImport     | ``-``        | Supported   |
   +--------------------------------------------------------------------------+-------+-----------------------------------+--------------+-------------+
   | Delete a task to import public zone record sets.                         | ``-`` | dns:publicRecordset:deleteImport  | ``-``        | Supported   |
   +--------------------------------------------------------------------------+-------+-----------------------------------+--------------+-------------+
   | Download the template for importing private zone record sets in batches. | ``-`` | dns:privateRecordset:getImport    | ``-``        | Supported   |
   +--------------------------------------------------------------------------+-------+-----------------------------------+--------------+-------------+
   | Create a task to import private zone record sets.                        | ``-`` | dns:privateRecordset:createImport | ``-``        | Supported   |
   +--------------------------------------------------------------------------+-------+-----------------------------------+--------------+-------------+
   | Query a task to import private zone record sets.                         | ``-`` | dns:privateRecordset:getImport    | ``-``        | Supported   |
   +--------------------------------------------------------------------------+-------+-----------------------------------+--------------+-------------+
   | Delete a task to import private zone record sets.                        | ``-`` | dns:privateRecordset:deleteImport | ``-``        | Supported   |
   +--------------------------------------------------------------------------+-------+-----------------------------------+--------------+-------------+
