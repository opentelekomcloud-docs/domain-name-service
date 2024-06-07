:original_name: dns_usermanual_0037.html

.. _dns_usermanual_0037:

Importing Record Sets
=====================

**Scenarios**
-------------

If you want to transfer your domain name from another cloud server provider to the DNS service for hosting, you can import existing record sets configured for the domain name in batches. This feature is available for both public and private zones.

You can import a maximum of 500 record sets at a time.

.. note::

   Before importing record sets, you have created public or private zones on the DNS console. For details, see :ref:`Creating a Public Zone <en-us_topic_0035467702>` or :ref:`Creating a Private Zone <en-us_topic_0057773658>`.

**Procedure**
-------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane, choose **Public Zones** or **Private Zones**.

   The zone list is displayed.

4. (Optional) If you have selected **Private Zones**, click |image1| on the upper left corner to select the region and project.

5. In the zone list, click the domain name **example.com** (an example domain name used in this topic).

6. Click **Export and Import**.

   a. Click **Download template**.
   b. Enter your record sets in the template as required.

      .. note::

         Ensure that the content is imported based on the format of the template, or the import will fail.

7. Click **Import Record Set** and select the record set file to import.

   After the import is complete, you can check whether record sets are successfully imported or not.

   -  **Successful Import**: The number of successfully imported record sets are displayed.
   -  **Failed Import**: All failed record sets are listed. You can resolve the problems based on the failure causes.

.. |image1| image:: /_static/images/en-us_image_0000001906653140.png
