:original_name: dns_usermanual_0033.html

.. _dns_usermanual_0033:

Managing Private Zones
======================

**Scenarios**
-------------

You can view details of a private zone, modify a private zone, or delete a private zone.

Modifying a Private Zone
------------------------

Change the email address of the domain name administrator and description of the private zone.

.. note::

   For more information about the email address, see :ref:`Why Was the Email Address Format Changed in the SOA Record? <dns_faq_009>`

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane, choose **Private Zones**.

   The **Private Zones** page is displayed.

#. Click |image1| in the upper left corner and select the desired region and project.

5. Locate the private zone you want to modify and click **Modify** under **Operation**.

   The **Modify Private Zone** dialog box is displayed.

6. Change the email address or description of the zone as required.

7. Click **OK**.

Deleting a Private Zone
-----------------------

Delete a private zone when you no longer need it. After a private zone is deleted, the domain name and its subdomains cannot be resolved by the DNS service.

.. important::

   Before you delete a private zone, back up all record sets in the private zone.

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane, choose **Private Zones**.

   The **Private Zones** page is displayed.

#. Click |image2| in the upper left corner and select the desired region and project.

5. Locate the private zone you want to delete and click **Delete** under **Operation**.

   The **Delete Private Zone** dialog box is displayed.

6. Click **Yes**.

Viewing Details About a Private Zone
------------------------------------

View details about a private zone, such as zone ID, operation time, tag, and TTL, on the **Private Zones** page.

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

3. On the **Dashboard** page, click **Private Zones** under **My Resources**.
4. Click |image3| in the upper left corner and select the desired region and project.
5. Locate the private zone you want to view and click |image4| before the zone name to view its details.

.. |image1| image:: /_static/images/en-us_image_0148391090.png
.. |image2| image:: /_static/images/en-us_image_0148391090.png
.. |image3| image:: /_static/images/en-us_image_0148391090.png
.. |image4| image:: /_static/images/en-us_image_0210877115.png
