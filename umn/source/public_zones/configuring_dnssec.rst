:original_name: dns_usermanual_00322.html

.. _dns_usermanual_00322:

Configuring DNSSEC
==================

What Is DNSSEC?
---------------

DNS Security Extensions (DNSSEC) provides digital signatures to ensure data integrity and authenticity of DNS requests and responses and to defend against common attacks such as DNS spoofing. This prevents you from being redirected to unexpected addresses and protects your core services.

Constraints
-----------

-  To use DNSSEC, both the domain name registrar and the DNS service provider must support DNSSEC.
-  DNSSEC supports only primary domain names.
-  Before disabling DNSSEC, you need to delete the DS record from the domain name service provider's system.
-  CNAME record sets cannot be configured for the second-level domain name, or the domain name cannot be resolved normally.

Process Flow
------------

:ref:`Figure 1 <dns_usermanual_00322__en-us_topic_0000001715570777_fig69042495113>` shows the process of configuring DNSSEC for a public zone

.. _dns_usermanual_00322__en-us_topic_0000001715570777_fig69042495113:

.. figure:: /_static/images/en-us_image_0000002194246985.png
   :alt: **Figure 1** DNSSEC configuration process

   **Figure 1** DNSSEC configuration process

Procedure
---------

#. Enable DNSSEC.

   a. Log in to the management console.

   b. In the service list, choose **Network** > **Domain Name Service**.

      The DNS console is displayed.

   c. In the navigation pane on the left, choose **Public Zones**.

      The **Public Zones** page is displayed.

   d. Locate the public zone for which you want to enable DNSSEC and click the domain name.

      The **Record Sets** tab is displayed.

   e. Click the **DNSSEC** tab.

   f. Click **Enable DNSSEC**.


      .. figure:: /_static/images/en-us_image_0000002194378913.png
         :alt: **Figure 2** Enabling DNSSEC

         **Figure 2** Enabling DNSSEC

   g. .. _dns_usermanual_00322__en-us_topic_0000001715570777_li287532972218:

      View and take a note of the following DNSSEC information:

      Key tag, digest algorithm, digest algorithm type, and digest.


      .. figure:: /_static/images/en-us_image_0000002159075694.png
         :alt: **Figure 3** Viewing DNSSEC details

         **Figure 3** Viewing DNSSEC details

   h. Go to the domain name registrar to configure a DS record.

#. .. _dns_usermanual_00322__en-us_topic_0000001715570777_li1282187111317:

   Configure a DS record.

   The following are operations for domain names that are registered with a domain name registrar and are only for reference. For details, see the operation guide on the official website of the domain name registrar.

   a. Please create a DS record for DNSSEC on your domain name registrar's website.
   b. Configure the parameters as prompted and enter the DNSSEC information recorded in :ref:`1.g <dns_usermanual_00322__en-us_topic_0000001715570777_li287532972218>`.

      -  **Key Tag**: Enter the recorded key tag.

      -  **Algorithm**: Enter the recorded signature algorithm type and signature algorithm.

         Format: Signature algorithm type-Signature algorithm

      -  **Digest Type**: Enter the recorded digest algorithm type and digest algorithm.

         Format: Digest algorithm type-Digest algorithm

      -  **Digest**: Enter the recorded digest.

Verification
------------

Use the `test tool <https://dnsviz.net/>`__ to verify that the configuration has taken effect.
