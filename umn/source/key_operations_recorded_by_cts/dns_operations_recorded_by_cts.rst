:original_name: dns_usermanual_0043.html

.. _dns_usermanual_0043:

DNS Operations Recorded by CTS
==============================

CTS is interconnected with the DNS service to record operations performed by users in real time. Actions and results of the operations are stored in OBS buckets in the form of traces.

After you enable CTS, whenever a DNS API is called, the operation is recorded in a log file, which is then delivered to a specified OBS bucket for storage.

:ref:`Table 1 <dns_usermanual_0043__table149110413017>` and :ref:`Table 2 <dns_usermanual_0043__table155718451405>` list the DNS operations that will be recorded by CTS.

.. note::

   The DNS service involves resources both at the global and region levels. :ref:`Table 1 <dns_usermanual_0043__table149110413017>` lists DNS operations at the global level. Traces of these operations are displayed only in the primary region.

   :ref:`Table 2 <dns_usermanual_0043__table155718451405>` lists DNS operations at the region level. Traces of these operations are displayed in the regions where the operations are performed.

.. _dns_usermanual_0043__table149110413017:

.. table:: **Table 1** Global-level DNS operations that can be recorded by CTS

   +---------------------------------------------------+---------------------+---------------------------+
   | Operation                                         | Resource Type       | Trace Name                |
   +===================================================+=====================+===========================+
   | Creating a record set for a public zone           | publicRecordSet     | createPublicRecordSet     |
   +---------------------------------------------------+---------------------+---------------------------+
   | Deleting a record set of a public zone            | publicRecordSet     | deletePublicRecordSet     |
   +---------------------------------------------------+---------------------+---------------------------+
   | Modifying a record set of a public zone           | publicRecordSet     | updatePublicRecordSet     |
   +---------------------------------------------------+---------------------+---------------------------+
   | Creating a public zone                            | publicZone          | createPublicZone          |
   +---------------------------------------------------+---------------------+---------------------------+
   | Modifying a public zone                           | publicZone          | updatePublicZone          |
   +---------------------------------------------------+---------------------+---------------------------+
   | Deleting a public zone                            | publicZone          | deletePublicZone          |
   +---------------------------------------------------+---------------------+---------------------------+
   | Adding tags to a public zone                      | publicZoneTag       | createPublicZoneTag       |
   +---------------------------------------------------+---------------------+---------------------------+
   | Deleting tags from a public zone                  | publicZoneTag       | deletePublicZoneTag       |
   +---------------------------------------------------+---------------------+---------------------------+
   | Adding tags to a record set in a public zone      | publicRecordSetTag  | createPublicRecordSetTag  |
   +---------------------------------------------------+---------------------+---------------------------+
   | Deleting tags of a record set in a public zone    | publicRecordSetTag  | deletePublicRecordSetTag  |
   +---------------------------------------------------+---------------------+---------------------------+
   | Adding tags to a private zone                     | privateZoneTag      | createPrivateZoneTag      |
   +---------------------------------------------------+---------------------+---------------------------+
   | Deleting tags from a private zone                 | privateZoneTag      | deletePrivateZoneTag      |
   +---------------------------------------------------+---------------------+---------------------------+
   | Adding tags to a record set in a private zone     | privateRecordSetTag | createPrivateRecordSetTag |
   +---------------------------------------------------+---------------------+---------------------------+
   | Deleting tags from a record set in a private zone | privateRecordSetTag | deletePrivateRecordSetTag |
   +---------------------------------------------------+---------------------+---------------------------+
   | Adding tags to a PTR record                       | ptrRecordTag        | createPTRRecordSetTag     |
   +---------------------------------------------------+---------------------+---------------------------+
   | Deleting tags of a PTR record                     | ptrRecordTag        | deletePTRRecordTag        |
   +---------------------------------------------------+---------------------+---------------------------+

.. _dns_usermanual_0043__table155718451405:

.. table:: **Table 2** Region-level DNS operations that can be recorded by CTS

   +------------------------------------------+------------------+------------------------+
   | Operation                                | Resource Type    | Trace Name             |
   +==========================================+==================+========================+
   | Creating a record set in a private zone  | privateRecordSet | createPrivateRecordSet |
   +------------------------------------------+------------------+------------------------+
   | Deleting a record set in a private zone  | privateRecordSet | deletePrivateRecordSet |
   +------------------------------------------+------------------+------------------------+
   | Modifying a record set of a private zone | privateRecordSet | updatePrivateRecordSet |
   +------------------------------------------+------------------+------------------------+
   | Creating a private zone                  | privateZone      | createPrivateZone      |
   +------------------------------------------+------------------+------------------------+
   | Modifying a private zone                 | privateZone      | updatePrivateZone      |
   +------------------------------------------+------------------+------------------------+
   | Deleting a private zone                  | privateZone      | deletePrivateZone      |
   +------------------------------------------+------------------+------------------------+
   | Associating a VPC with a private zone    | privateZone      | associateRouter        |
   +------------------------------------------+------------------+------------------------+
   | Disassociating a VPC from a private zone | privateZone      | disassociateRouter     |
   +------------------------------------------+------------------+------------------------+
   | Configuring a PTR record                 | ptrRecord        | setPTRRecord           |
   +------------------------------------------+------------------+------------------------+
   | Deleting a PTR record                    | ptrRecord        | resetPTRRecord         |
   +------------------------------------------+------------------+------------------------+
