:original_name: dns_usermanual_1033.html

.. _dns_usermanual_1033:

Managing Endpoint Rules
=======================

Scenarios
---------

To allow cloud servers to access an on-premises domain name, you need to create an outbound endpoint and configure endpoint rules to specify the on-premises domain name to be accessed and the IP addresses of the on-premises DNS servers. Private DNS then forwards the DNS queries for the on-premises domain name to the on-premises DNS servers based on the endpoint rules.

An endpoint rule can have more than one VPC associated. After a VPC is associated with an endpoint rule, DNS queries for the on-premises domain name from the cloud servers in the VPC will be forwarded to the on-premises DNS servers.

Prerequisites
-------------

An outbound endpoint has been created.

For details about how to create an outbound endpoint, see :ref:`Creating an Outbound Endpoint <dns_usermanual_1031__section921157130>`.

.. _dns_usermanual_1033__section343146174210:

Adding an Endpoint Rule
-----------------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Resolvers**.

   The **Resolvers** page is displayed.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click the **Endpoint Rules** tab.

#. Click **Add Rule**.

#. Configure the parameters based on :ref:`Table 1 <dns_usermanual_1033__en-us_topic_0138290753_en-us_topic_0035467699_table2052132816642>`.

   .. _dns_usermanual_1033__en-us_topic_0138290753_en-us_topic_0035467699_table2052132816642:

   .. table:: **Table 1** Parameters for adding an endpoint rule

      +-----------------------+--------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                  | Example Value         |
      +=======================+==============================================================================================================+=======================+
      | Name                  | Name of the endpoint rule added to an outbound endpoint.                                                     | rule-test01           |
      +-----------------------+--------------------------------------------------------------------------------------------------------------+-----------------------+
      | Domain Name           | Domain name used by on-premises servers.                                                                     | example.com           |
      |                       |                                                                                                              |                       |
      |                       | The domain name cannot be changed after an endpoint rule is created.                                         |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------+-----------------------+
      | Type                  | By default, **Resolvers** is selected.                                                                       | Resolvers             |
      +-----------------------+--------------------------------------------------------------------------------------------------------------+-----------------------+
      | Outbound Endpoint     | Select the outbound endpoint that you want to add to this endpoint rule to.                                  | outbound-test01       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------+-----------------------+
      | Associate VPC         | Whether to associate VPCs with the endpoint rule.                                                            | Select it.            |
      |                       |                                                                                                              |                       |
      |                       | If this option is selected, you need to select one or more VPCs.                                             |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------+-----------------------+
      | Region                | Region that the VPCs belong to.                                                                              | eu-de                 |
      |                       |                                                                                                              |                       |
      |                       | This parameter is displayed after **Associate VPC** is selected. The current region is displayed by default. |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------+-----------------------+
      | VPC                   | Select the VPCs to be associated with the endpoint rule.                                                     | vpc-test              |
      |                       |                                                                                                              |                       |
      |                       | This parameter is displayed after **Associate VPC** is selected.                                             |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------+-----------------------+
      | IP Addresses          | IP address of a DNS server in the on-premises data center.                                                   | 192.168.1.1           |
      |                       |                                                                                                              |                       |
      |                       | A maximum of five IP addresses can be added.                                                                 |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

Viewing an Endpoint Rule
------------------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Resolvers**.

   The **Resolvers** page is displayed.

#. Click |image2| in the upper left corner and select the desired region and project.

#. Click the **Endpoint Rules** tab to view the endpoint rule list.

   You can view the endpoint rules you created or other users shared with you.

#. Click the name of the endpoint rule to view its details, such as basic configuration, VPCs, and IP addresses.

Modifying an Endpoint Rule
--------------------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Resolvers**.

   The **Resolvers** page is displayed.

#. Click |image3| in the upper left corner and select the desired region and project.

#. Click the **Endpoint Rules** tab to view the endpoint rule list.

#. Locate the endpoint rule and click **Modify** in the **Operation** column.

   You can change the rule name, associating other VPCs, disassociating from VPCs, and add, delete, or modify IP addresses.

Deleting an Endpoint Rule
-------------------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Resolvers**.

   The **Resolvers** page is displayed.

#. Click |image4| in the upper left corner and select the desired region and project.

#. Click the **Endpoint Rules** tab to view the endpoint rule list.

#. Locate the endpoint rule, click **More** in the **Operation** column, and select **Delete**.

#. Confirm the endpoint rule and click **Yes**.

Disassociating a VPC from an Endpoint Rule
------------------------------------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **Resolvers**.

   The **Resolvers** page is displayed.

#. Click |image5| in the upper left corner and select the desired region and project.

#. Click the **Endpoint Rules** tab to view the endpoint rule list.

#. Locate the endpoint rule and click |image6| in the **VPCs** column.

#. In the **Disassociate VPC** dialog box, click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001906973658.png
.. |image2| image:: /_static/images/en-us_image_0000001906973658.png
.. |image3| image:: /_static/images/en-us_image_0000001906973658.png
.. |image4| image:: /_static/images/en-us_image_0000001906973658.png
.. |image5| image:: /_static/images/en-us_image_0000001884579401.png
.. |image6| image:: /_static/images/en-us_image_0000002326810157.png
