:original_name: dns_usermanual_1032.html

.. _dns_usermanual_1032:

Managing Inbound Endpoints
==========================

Scenarios
---------

To enable on-premises servers to access a cloud service domain name, you need to create an inbound endpoint and configure forwarding rules on the on-premises DNS server to forward the DNS queries for the cloud service domain name to the IP addresses specified in the inbound endpoint.

Creating an Inbound Endpoint
----------------------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Resolvers**.

   The **Resolvers** page is displayed.

#. Click |image1| in the upper left corner and select the desired region and project.

#. In the upper right corner of the page, click **Create Endpoint**.

#. Configure the parameters based on :ref:`Table 1 <dns_usermanual_1032__en-us_topic_0138290753_en-us_topic_0035467699_table2052132816642>`.

   .. _dns_usermanual_1032__en-us_topic_0138290753_en-us_topic_0035467699_table2052132816642:

   .. table:: **Table 1** Parameters for creating an inbound endpoint

      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------+
      | Parameter             | Description                                                                                                                                        | Example Value               |
      +=======================+====================================================================================================================================================+=============================+
      | Endpoint Type         | Type of the endpoint. There are two options: **Inbound** and **Outbound**.                                                                         | Inbound                     |
      |                       |                                                                                                                                                    |                             |
      |                       | Select **Inbound**.                                                                                                                                |                             |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------+
      | Endpoint Name         | Name of the endpoint. The name can:                                                                                                                | inbound-test01              |
      |                       |                                                                                                                                                    |                             |
      |                       | -  Contain only letters, digits, underscores (_), hyphens (-), and periods (.).                                                                    |                             |
      |                       | -  Contain 1 to 64 characters.                                                                                                                     |                             |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------+
      | Region                | Region where the inbound endpoint works.                                                                                                           | eu-de                       |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------+
      | VPC                   | The VPC over which all inbound DNS queries are forwarded to cloud DNS servers.                                                                     | vpc-test                    |
      |                       |                                                                                                                                                    |                             |
      |                       | .. caution::                                                                                                                                       |                             |
      |                       |                                                                                                                                                    |                             |
      |                       |    CAUTION:                                                                                                                                        |                             |
      |                       |    The VPC cannot be changed after an endpoint is created.                                                                                         |                             |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------+
      | Subnet                | The subnet must have available IP addresses.                                                                                                       | Subnet-test(192.168.0.0/24) |
      |                       |                                                                                                                                                    |                             |
      |                       | Only IPv4 addresses are supported.                                                                                                                 |                             |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------+
      | IP Address            | There are two options: **Automatically assign** or **Specify**.                                                                                    | Automatically assign        |
      |                       |                                                                                                                                                    |                             |
      |                       | To improve reliability, you need to specify at least two IP addresses, with each in a different AZ. You can optionally add up to six IP addresses. |                             |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------+

#. Click **Create Now**.

Viewing an Inbound Endpoint
---------------------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Resolvers**.

   The **Resolvers** page is displayed.

#. Click |image2| in the upper left corner and select the desired region and project.

#. On the **Inbound Endpoints** tab, locate the inbound endpoint you want to view.

#. Click the name of the inbound endpoint and view its details, such as basic configuration and IP addresses.

Modifying an Inbound Endpoint
-----------------------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Resolvers**.

   The **Resolvers** page is displayed.

#. Click |image3| in the upper left corner and select the desired region and project.

#. On the **Inbound Endpoints** tab, locate the inbound endpoint you want to modify.

#. Click **Modify** in the **Operation** column.

   You can change the endpoint name, and add or delete IP addresses.

Deleting an Inbound Endpoint
----------------------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Resolvers**.

   The **Resolvers** page is displayed.

#. Click |image4| in the upper left corner and select the desired region and project.

#. On the **Inbound Endpoints** tab, locate the inbound endpoint you want to delete.

#. Click **Delete** in the **Operation** column.

#. Confirm the inbound endpoint and click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0000001906973658.png
.. |image2| image:: /_static/images/en-us_image_0000001906973658.png
.. |image3| image:: /_static/images/en-us_image_0000001906973658.png
.. |image4| image:: /_static/images/en-us_image_0000001906973658.png
