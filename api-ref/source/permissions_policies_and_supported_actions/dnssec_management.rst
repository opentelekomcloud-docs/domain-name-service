:original_name: dns_api_70008.html

.. _dns_api_70008:

DNSSEC Management
=================

.. table:: **Table 1** Actions for DNSSEC management

   +-----------------+-----------------------------------------+------------------------------+--------------+-------------+
   | Permission      | API                                     | Action                       | Dependencies | IAM Project |
   +=================+=========================================+==============================+==============+=============+
   | Enable DNSSEC.  | POST /v2/zones/{zone_id}/enable-dnssec  | dns:zone:enableDnssecConfig  | ``-``        | Supported   |
   +-----------------+-----------------------------------------+------------------------------+--------------+-------------+
   | Disable DNSSEC. | POST /v2/zones/{zone_id}/disable-dnssec | dns:zone:disableDnssecConfig | ``-``        | Supported   |
   +-----------------+-----------------------------------------+------------------------------+--------------+-------------+
   | Query DNSSEC.   | GET /v2/zones/{zone_id}/dnssec          | dns:zone:getDnssecConfig     | ``-``        | Supported   |
   +-----------------+-----------------------------------------+------------------------------+--------------+-------------+
