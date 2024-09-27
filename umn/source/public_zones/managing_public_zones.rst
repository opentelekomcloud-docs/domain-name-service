:original_name: dns_usermanual_0031.html

.. _dns_usermanual_0031:

Managing Public Zones
=====================

.. _dns_usermanual_0031__section125317016203:

**Scenarios**
-------------

You can modify, delete public zones or view their details.

Modifying a Public Zone
-----------------------

Change the domain name administrator's email address and description of the public zone.

.. note::

   For more information about the email, see :ref:`Why Was the Email Address Format Changed in the SOA Record? <dns_faq_009>`

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Public Zones**.

   The **Public Zones** page is displayed.

#. Locate the public zone you want to modify and choose **More** > **Modify** under **Operation**.

   The **Modify Public Zone** dialog box is displayed.

#. Change the email address or description of the zone as required.

#. Click **OK**.

Deleting a Public Zone
----------------------

Delete a public zone when you no longer need it. After a public zone is deleted, the domain name and its subdomains cannot be resolved by the DNS service.

.. important::

   Before you delete a public zone, back up all its record sets.

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Public Zones**.

   The **Public Zones** page is displayed.

#. Locate the public zone you want to delete and click **Delete** under **Operation**.

   The **Delete Public Zone** dialog box is displayed.

#. Click **Yes**.

Viewing Details About a Public Zone
-----------------------------------

View details about a public zone, such as zone ID, operation time, tag, and TTL, on the **Public Zones** page.

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. On the **Dashboard** page, click **Public Zones** under **My Resources**.

#. In the public zone list, click the name of the public zone to view its details.
