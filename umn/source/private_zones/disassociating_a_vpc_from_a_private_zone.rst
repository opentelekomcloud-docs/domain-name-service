:original_name: dns_usermanual_0004.html

.. _dns_usermanual_0004:

Disassociating a VPC from a Private Zone
========================================

Scenarios
---------

Disassociate a VPC from a private zone if you do not want the private domain name to be resolved in this VPC. If a private zone has only one VPC associated, you cannot disassociate the VPC.

.. note::

   If you do not intend to use private domain names, delete the private zone configured for it.

**Procedure**
-------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Private Zones**.

   The **Private Zones** page is displayed.

#. Click |image1| in the upper left corner and select the desired region and project.

5. Locate the private zone from which a VPC is to be disassociated, select the VPC to be disassociated under **Associated VPC**, and click |image2| on the right of the VPC.


   .. figure:: /_static/images/en-us_image_0000001906653264.png
      :alt: **Figure 1** Associated VPCs

      **Figure 1** Associated VPCs

6. In the **Disassociate VPC** dialog box, click **Yes**.


   .. figure:: /_static/images/en-us_image_0000001942372509.png
      :alt: **Figure 2** Disassociating a VPC

      **Figure 2** Disassociating a VPC

.. |image1| image:: /_static/images/en-us_image_0000001906973766.png
.. |image2| image:: /_static/images/en-us_image_0000001906653284.png
