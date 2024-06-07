:original_name: dns_usermanual_0013.html

.. _dns_usermanual_0013:

Adding an SRV Record Set
========================

**Scenarios**
-------------

To tag a server to show what services it provides, you can add SRV record sets for a domain name.

For details about other record set types, see :ref:`Record Set Types and Configuration Rules <dns_usermanual_0601>`.

**Procedure**
-------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

#. In the navigation pane, choose **Public Zones** or **Private Zones**.

   The zone list is displayed.

#. (Optional) If you have selected **Private Zones**, click |image1| on the upper left corner to select the region and project.

#. Click the domain name.

#. Click **Add Record Set**.

   The **Add Record Set** dialog box is displayed.

#. Configure the parameters based on :ref:`Table 1 <dns_usermanual_0013__table28439303171815>`.

   .. _dns_usermanual_0013__table28439303171815:

   .. table:: **Table 1** Parameters for adding an SRV record set

      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------+
      | Parameter             | Description                                                                                                                   | Example Value                                                             |
      +=======================+===============================================================================================================================+===========================================================================+
      | Name                  | Service (for example, FTP, SSH, or SIP) provided over the specified protocol (for example, TCP or UDP) on a host              | \_ftp._tcp                                                                |
      |                       |                                                                                                                               |                                                                           |
      |                       | The format is \_\ *Service name*.\_\ *Protocol*.                                                                              | **\_ftp._tcp** indicates that the host provides the FTP service over TCP. |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------+
      | Type                  | Type of the record set                                                                                                        | SRV - Record servers providing specific services                          |
      |                       |                                                                                                                               |                                                                           |
      |                       | A message may be displayed indicating that the record set you are trying to add conflicts with an existing record set.        |                                                                           |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------+
      | TTL (s)               | Cache duration of the record set on a local DNS server, in seconds.                                                           | 300                                                                       |
      |                       |                                                                                                                               |                                                                           |
      |                       | The value ranges from **1** to **2147483647**, and the default is **300**.                                                    |                                                                           |
      |                       |                                                                                                                               |                                                                           |
      |                       | If your service address changes frequently, set TTL to a smaller value.                                                       |                                                                           |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------+
      | Value                 | Server address                                                                                                                | 2 1 2355 example_server.test.com                                          |
      |                       |                                                                                                                               |                                                                           |
      |                       | You can enter a maximum of 50 record values, each on a separate line.                                                         |                                                                           |
      |                       |                                                                                                                               |                                                                           |
      |                       | The value format is **[priority] [weight] [port number] [server address]**.                                                   |                                                                           |
      |                       |                                                                                                                               |                                                                           |
      |                       | Configuration rules:                                                                                                          |                                                                           |
      |                       |                                                                                                                               |                                                                           |
      |                       | -  The priority, weight, and port number range from 0 to 65535.                                                               |                                                                           |
      |                       |                                                                                                                               |                                                                           |
      |                       | -  A smaller value indicates a higher priority.                                                                               |                                                                           |
      |                       |                                                                                                                               |                                                                           |
      |                       | -  A larger value indicates a larger weight.                                                                                  |                                                                           |
      |                       |                                                                                                                               |                                                                           |
      |                       | -  The server address is the domain name of the target server.                                                                |                                                                           |
      |                       |                                                                                                                               |                                                                           |
      |                       |    Ensure that the domain name can be resolved.                                                                               |                                                                           |
      |                       |                                                                                                                               |                                                                           |
      |                       | .. note::                                                                                                                     |                                                                           |
      |                       |                                                                                                                               |                                                                           |
      |                       |    If the record set values have the same priority, requests to the domain name will be routed based on weights.              |                                                                           |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------+
      | Tag                   | (Optional) Identifier of a record set. Each tag contains a key and a value. You can add a maximum of 20 tags to a record set. | example_key1                                                              |
      |                       |                                                                                                                               |                                                                           |
      |                       | For details about tag key and value requirements, see :ref:`Table 2 <dns_usermanual_0013__table191971158112315>`.             | example_value1                                                            |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------+
      | Description           | (Optional) Supplementary information about the record set.                                                                    | ``-``                                                                     |
      |                       |                                                                                                                               |                                                                           |
      |                       | You can enter a maximum of 255 characters.                                                                                    |                                                                           |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------+

   .. _dns_usermanual_0013__table191971158112315:

   .. table:: **Table 2** Tag key and value requirements

      +-----------------------+--------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Requirements                                                                         | Example Value         |
      +=======================+======================================================================================+=======================+
      | Key                   | -  Cannot be left blank.                                                             | example_key1          |
      |                       | -  Must be unique for each resource.                                                 |                       |
      |                       | -  Can contain a maximum of 36 characters.                                           |                       |
      |                       | -  Can contain only letters, digits, hyphens (-), at signs (@), and underscores (_). |                       |
      +-----------------------+--------------------------------------------------------------------------------------+-----------------------+
      | Value                 | -  Cannot be left blank.                                                             | example_value1        |
      |                       | -  Can contain a maximum of 43 characters.                                           |                       |
      |                       | -  Can contain only letters, digits, hyphens (-), at signs (@), and underscores (_). |                       |
      +-----------------------+--------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

#. Switch back to the **Record Sets** tab.

   The added record set is in the **Normal** state.

.. |image1| image:: /_static/images/en-us_image_0000001906653140.png
