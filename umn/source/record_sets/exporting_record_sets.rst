:original_name: dns_usermanual_0024.html

.. _dns_usermanual_0024:

Exporting Record Sets
=====================

**Scenarios**
-------------

If you want to transfer your domain name to another cloud service provider for hosting, you can export all the record sets configured for the domain name in batches. This feature is available for both public and private zones.

Domain name example.com is used as an example to describe how you can export all its record sets.

.. _dns_usermanual_0024__section5370171114710:

**Procedure**
-------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane, choose **Public Zones** or **Private Zones**.

   The zone list is displayed.

#. (Optional) If you have selected **Private Zones**, click |image1| on the upper left corner to select the region and project.

#. In the zone list, click the domain name **example.com**.

#. Click **Export and Import**.

#. Click **Export Record Set**.

   An **example.com.xlsx** file is exported, which lists all record sets in the zone and their details, including the record set name, type, TTL, value, status, and description.

.. |image1| image:: /_static/images/en-us_image_0000001906653140.png
