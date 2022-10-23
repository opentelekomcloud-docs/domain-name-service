:original_name: en-us_topic_0040322596.html

.. _en-us_topic_0040322596:

Configuring a PTR Record
========================

**Scenarios**
-------------

PTR records are used to prove credibility of IP addresses and domain names of email servers. Most spam senders use email servers whose IP addresses are dynamically allocated or not mapped to registered domain names in order to avoid being tracked. If you do not want emails sent from your email server to be considered as spam, add a PTR record to map the email server IP address to a domain name. In this way, the email recipient can obtain the domain name by IP address and will know that the email server is trustworthy.

If you use an ECS as an email server, configure a PTR record to map the ECS IP address to a domain name.

.. note::

   After an ECS is successfully created and assigned with an EIP, a PTR record will be generated for the EIP by default in format of **ecs-xx-xx-xx-xx.compute.xxx.com**, where **xx-xx-xx-xx** is the EIP and **xxx** is the domain name provided by the cloud platform.

   You can use one of the following methods to query the default PTR record of an EIP:

   -  ping -a *EIP*
   -  nslookup [-qt=ptr] *EIP*
   -  dig -x *EIP*

   The default PTR record of the EIP may not be applicable in some scenarios. For example, it cannot be used as the domain name of an email server. In this case, create a PTR record for the EIP.

   After you create a PTR record, the default record will be overwritten.

This section describes how to add a PTR record for a cloud resource, such as ECS.

Constraints
-----------

Currently, you can configure PTR records only for IP addresses with a 32-bit subnet mask.

**Prerequisites**
-----------------

-  You have registered a domain name.
-  You have created an ECS and bound an EIP to it.

**Procedure**
-------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane, choose **PTR Records**.

   The **PTR Records** page is displayed.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click **Create PTR Record**.

   -  **EIP**: Select the EIP of the ECS.
   -  **Domain Name**: Enter the domain name that the EIP points to.

   Retain default settings for other parameters. For detailed descriptions of the parameters, see :ref:`Creating a PTR Record <en-us_topic_0077500015>`.


   .. figure:: /_static/images/en-us_image_0000001124586421.png
      :alt: **Figure 1** Creating a PTR record

      **Figure 1** Creating a PTR record

#. Click **OK**.

   View the created PTR record on the **PTR Records** page.


   .. figure:: /_static/images/en-us_image_0239453060.png
      :alt: **Figure 2** PTR Records

      **Figure 2** PTR Records

   .. note::

      If the domain name is mapped to multiple EIPs, you must create a PTR record for each EIP.

#. Verify that the PTR record has taken effect.

   Run the following DOS command on a PC connected to the Internet:

   **nslookup -qt=ptr** **IP address**

.. |image1| image:: /_static/images/en-us_image_0148391090.png
