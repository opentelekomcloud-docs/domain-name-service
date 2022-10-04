:original_name: dns_usermanual_0003.html

.. _dns_usermanual_0003:

Associating a VPC with a Private Zone
=====================================

**Scenarios**
-------------

Associate a VPC with a private zone so that the private domain name can work in this VPC.

.. note::

   This VPC must be the same as the VPC where the servers are deployed. Otherwise, the domain name cannot be resolved.

**Procedure**
-------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane, choose **Private Zones**.

   The **Private Zones** page is displayed.

#. Click |image1| in the upper left corner and select the desired region and project.

5. Locate the private zone with which you want to associate the VPC and click **Associate VPC** under **Operation**.

6. Select the VPC you want to associate.

   If no VPCs are available, create one on the VPC console and then associate the private zone with it.


   .. figure:: /_static/images/en-us_image_0198815181.png
      :alt: **Figure 1** Associating a VPC


      **Figure 1** Associating a VPC

7. Click **OK**.

   The VPC is displayed under **Associated VPC**.

.. |image1| image:: /_static/images/en-us_image_0148391090.png
