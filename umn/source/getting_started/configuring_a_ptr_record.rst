:original_name: en-us_topic_0040322596.html

.. _en-us_topic_0040322596:

Configuring a PTR Record
========================

Scenario
--------

PTR records are used to prove credibility of IP addresses and domain names of email servers. To avoid being tracked, most spam senders use email servers whose IP addresses are dynamically allocated or not mapped to registered domain names. If you want to keep the spam out of your recipients' inbox, add a PTR record to map the email server IP address to a domain name. In this way, the email recipients can obtain the domain name by IP address and will know that the email server is trustworthy.

If you use an ECS as an email server, configure a PTR record to map the EIP of the ECS to the domain name.

.. note::

   After an ECS is created and assigned with an EIP, a PTR record will be generated for the EIP by default in format of **ecs-xx-xx-xx-xx.compute.xxx.com**, where **xx-xx-xx-xx** indicates the EIP and **xxx** is the domain name provided by the cloud platform.

   You can use any of the following methods to query the default PTR record for the EIP:

   -  ping -a *EIP*
   -  nslookup [-qt=ptr] *EIP*
   -  dig -x *EIP*

   The default PTR record may not be applicable in some scenarios. For example, the PTR record cannot be used as the domain name of an email server. In this case, create a PTR record for the EIP.

   After the PTR record is created, the default record will be overwritten.

This following are operations for you to add a PTR record for a cloud resource, such as ECS.

Constraints
-----------

You can only configure PTR records for IP addresses with a 32-bit subnet mask.

Prerequisites
-------------

-  You have registered a domain name.
-  You have created an ECS and bound an EIP to it.

Procedure
---------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane on the left, choose **PTR Records**.

   The **PTR Records** page is displayed.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click **Create PTR Record** and configure the following parameters.

   -  **EIP**: Select the EIP of the ECS.
   -  **Domain Name**: Enter the domain name that the EIP points to.

   Configure other parameters by referring to :ref:`Creating a PTR Record <en-us_topic_0077500015>`.


   .. figure:: /_static/images/en-us_image_0000001906973554.png
      :alt: **Figure 1** Creating a PTR record

      **Figure 1** Creating a PTR record

#. Click **OK**.

   You can view the created PTR record on the **PTR Records** page.


   .. figure:: /_static/images/en-us_image_0000001906973550.png
      :alt: **Figure 2** PTR Records

      **Figure 2** PTR Records

   .. note::

      If a domain name is mapped to multiple EIPs, you must create a PTR record for each EIP.

#. Verify that the PTR record has taken effect by running the following command on a PC connected to the Internet:

   **nslookup -qt=ptr** *EIP*

.. |image1| image:: /_static/images/en-us_image_0000001906813654.png
