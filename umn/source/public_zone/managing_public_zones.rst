:original_name: dns_usermanual_0031.html

.. _dns_usermanual_0031:

Managing Public Zones
=====================

**Scenarios**
-------------

You can view details of a public zone, modify a public zone, or delete a public zone.

Modifying a Public Zone
-----------------------

Change the email address of the domain name administrator and description of the public zone.

.. note::

   For more information about the email address, see :ref:`Why Was the Email Address Format Changed in the SOA Record? <dns_faq_009>`

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane, choose **Public Zones**.

   The **Public Zones** page is displayed.

4. Locate the public zone you want to modify and click **Modify** under **Operation**.

   The **Modify Public Zone** dialog box is displayed.

5. Change the email address or description of the zone as required.

6. Click **OK**.

Deleting a Public Zone
----------------------

Delete a public zone when you no longer need it. After a public zone is deleted, the domain name and its subdomains cannot be resolved by the DNS service.

.. important::

   Before you delete a public zone, back up all record sets in the public zone.

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane, choose **Public Zones**.

   The **Public Zones** page is displayed.

4. Locate the public zone you want to delete and click **Delete** under **Operation**.

   The **Delete Public Zone** dialog box is displayed.

5. Click **Yes**.

Viewing Details About a Public Zone
-----------------------------------

View details about a public zone, such as zone ID, operation time, tag, and TTL, on the **Public Zones** page.

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

3. On the **Dashboard** page, click **Public Zones** under **My Resources**.
4. Locate the public zone you want to view and click |image1| before the zone name to view its details.

.. |image1| image:: /_static/images/en-us_image_0210877115.png
