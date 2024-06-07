:original_name: dns_usermanual_0033.html

.. _dns_usermanual_0033:

Managing Private Zones
======================

.. _dns_usermanual_0033__section125317016203:

Scenarios
---------

You can modify, delete private zones or view their details.

.. _dns_usermanual_0033__section10328742215619:

Modifying a Private Zone
------------------------

Change the domain name administrator's email address and description of the private zone.

.. note::

   For more information about the email, see :ref:`Why Was the Email Address Format Changed in the SOA Record? <dns_faq_009>`

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Private Zones**.

   The **Private Zones** page is displayed.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Locate the private zone you want to modify and choose **More** > **Modify** under **Operation**.

   The **Modify Private Zone** dialog box is displayed.

#. Change the email address or description of the zone as required.

#. Click **OK**.

.. _dns_usermanual_0033__section5576188803045:

Deleting a Private Zone
-----------------------

Delete a private zone when you no longer need it. After a private zone is deleted, the domain name and its subdomains cannot be resolved by the DNS service.

.. important::

   Before you delete a private zone, back up all record sets in the private zone.

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Private Zones**.

   The **Private Zones** page is displayed.

#. Click |image2| in the upper left corner and select the desired region and project.

#. Locate the private zone you want to delete and choose **More** > **Delete** in the **Operation** column.

   The **Delete Private Zone** dialog box is displayed.

#. Click **Yes**.

Viewing Details About a Private Zone
------------------------------------

View details about a private zone, such as zone ID, operation time, tag, and TTL, on the **Private Zones** page.

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. On the **Dashboard** page, click **Private Zones** under **My Resources**.

#. Click |image3| in the upper left corner and select the desired region and project.

#. In the private zone list, click the name of the private zone to view its details.

.. |image1| image:: /_static/images/en-us_image_0000001906973766.png
.. |image2| image:: /_static/images/en-us_image_0000001906973766.png
.. |image3| image:: /_static/images/en-us_image_0000001906973766.png
