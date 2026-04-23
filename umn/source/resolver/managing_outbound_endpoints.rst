:original_name: dns_usermanual_1031.html

.. _dns_usermanual_1031:

Managing Outbound Endpoints
===========================

Scenarios
---------

To allow cloud servers to access an on-premises domain name, you need to create an outbound endpoint and configure endpoint rules to specify the on-premises domain name to be accessed and the IP addresses of the on-premises DNS servers. Private DNS then forwards the DNS queries for the on-premises domain name to the on-premises DNS servers based on the endpoint rules.

Process for Configuring an Outbound Endpoint
--------------------------------------------

:ref:`Figure 1 <dns_usermanual_1031__fig16930182510230>` shows how you can configure an outbound endpoint to forward DNS queries for an on-premises domain name to the on-premises DNS servers.

.. _dns_usermanual_1031__fig16930182510230:

.. figure:: /_static/images/en-us_image_0000001906813276.png
   :alt: **Figure 1** Configuring an outbound endpoint

   **Figure 1** Configuring an outbound endpoint

.. _dns_usermanual_1031__section921157130:

Creating an Outbound Endpoint
-----------------------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Resolvers**.

   The **Resolvers** page is displayed.

#. Click |image1| in the upper left corner and select the desired region and project.

#. In the upper right corner of the page, click **Create Endpoint**.

#. Configure the parameters based on :ref:`Table 1 <dns_usermanual_1031__en-us_topic_0138290753_en-us_topic_0035467699_table2052132816642>`.

   .. _dns_usermanual_1031__en-us_topic_0138290753_en-us_topic_0035467699_table2052132816642:

   .. table:: **Table 1** Parameters for creating an outbound endpoint

      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------+
      | Parameter             | Description                                                                                                                                        | Example Value               |
      +=======================+====================================================================================================================================================+=============================+
      | Endpoint Type         | Type of the endpoint. There are two options: **Inbound** and **Outbound**.                                                                         | Outbound                    |
      |                       |                                                                                                                                                    |                             |
      |                       | Select **Outbound**.                                                                                                                               |                             |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------+
      | Endpoint Name         | Name of the endpoint. The name can:                                                                                                                | outbound-test01             |
      |                       |                                                                                                                                                    |                             |
      |                       | -  Contain only letters, digits, underscores (_), hyphens (-), and periods (.).                                                                    |                             |
      |                       | -  Contain 1 to 64 characters.                                                                                                                     |                             |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------+
      | Region                | Region where the outbound endpoint works.                                                                                                          | eu-de                       |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------+
      | VPC                   | The VPC over which all outbound DNS requires are forwarded to the IP addresses specified in the endpoint rules.                                    | vpc-test                    |
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

.. note::

   After an outbound endpoint is created, you need to configure endpoint rules. For details, see :ref:`Modifying an Outbound Endpoint <dns_usermanual_1031__section95303119312>` or :ref:`Adding an Endpoint Rule <dns_usermanual_1033__section343146174210>`.

Viewing an Outbound Endpoint
----------------------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Resolvers**.

   The **Resolvers** page is displayed.

#. Click |image2| in the upper left corner and select the desired region and project.

#. On the **Outbound Endpoints** tab, locate the outbound endpoint you want to view.

#. Click the name of the outbound endpoint and view its details, such as basic configuration, IP addresses, and endpoint rules.

.. _dns_usermanual_1031__section95303119312:

Modifying an Outbound Endpoint
------------------------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Resolvers**.

   The **Resolvers** page is displayed.

#. Click |image3| in the upper left corner and select the desired region and project.

#. On the **Outbound Endpoints** tab, locate the outbound endpoint you want to modify.

#. Click **Modify** in the **Operation** column.

   You can change the endpoint name, add or delete IP addresses, and add or delete endpoint rules.

Deleting an Outbound Endpoint
-----------------------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Resolvers**.

   The **Resolvers** page is displayed.

#. Click |image4| in the upper left corner and select the desired region and project.

#. On the **Outbound Endpoints** tab, locate the outbound endpoint you want to delete.

#. Click **Delete** in the **Operation** column.

#. Confirm the outbound endpoint and click **Yes**.

Related Operations
------------------

:ref:`Adding an Endpoint Rule <dns_usermanual_1033__section343146174210>`

.. |image1| image:: /_static/images/en-us_image_0000001906973658.png
.. |image2| image:: /_static/images/en-us_image_0000001906973658.png
.. |image3| image:: /_static/images/en-us_image_0000001906973658.png
.. |image4| image:: /_static/images/en-us_image_0000001906973658.png
