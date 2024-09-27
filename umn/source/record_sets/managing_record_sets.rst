:original_name: en-us_topic_0035467703.html

.. _en-us_topic_0035467703:

Managing Record Sets
====================

.. _en-us_topic_0035467703__section125317016203:

**Scenarios**
-------------

You can modify, delete record sets or view their details.

Modifying a Record Set
----------------------

Change the TTL, value, and description of a record set to better address your service requirements.

.. note::

   SOA and NS record sets are automatically generated and cannot be modified.

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane, choose **Public Zones** or **Private Zones**.

   The zone list is displayed.

#. (Optional) If you have selected **Private Zones**, click |image1| on the upper left corner to select the region and project.

#. Click the domain name.

   The **Record Sets** page is displayed.

#. Locate the record set you want to modify and click **Modify** under **Operation**.

   The **Modify Record Set** dialog box is displayed.

#. Modify the parameters.

   You can change only the TTL, value, and description of a record set.

#. Click **OK**.

Deleting a Record Set
---------------------

.. note::

   SOA and NS record sets are automatically generated and cannot be deleted.

Record sets that are no longer required can be deleted. After a record set is deleted, it will become unavailable. For example, if an A record set is deleted, the domain name cannot be resolved into the IPv4 address specified in the record set. If a CNAME record set is deleted, the domain alias cannot be mapped to the domain name.

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. On the **Dashboard** page, click **Public Zones** or **Private Zones**.

   The zone list is displayed.

#. (Optional) If you have selected **Private Zones**, click |image2| on the upper left corner to select the region and project.

#. Click the domain name.

   The **Record Sets** page is displayed.

#. Locate the record set you want to delete and click **Delete** under **Operation**.

#. In the **Delete Record Set** dialog box, click **Yes**.

Viewing Details About a Record Set
----------------------------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane, choose **Public Zones** or **Private Zones**.

   The zone list is displayed.

#. (Optional) If you have selected **Private Zones**, click |image3| on the upper left corner to select the region and project.

#. Click the domain name.

   The **Record Sets** page is displayed.

#. Locate the record set you want to view and click its name to view the details.

.. |image1| image:: /_static/images/en-us_image_0000001906653140.png
.. |image2| image:: /_static/images/en-us_image_0000001906653140.png
.. |image3| image:: /_static/images/en-us_image_0000001906653140.png
