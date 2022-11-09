:original_name: dns_usermanual_0013.html

.. _dns_usermanual_0013:

Adding an SRV Record Set
========================

**Scenarios**
-------------

To record services provided by a server, you can add SRV record sets for a domain name.

For details about other record set types, see :ref:`Record Set Types and Configuration Rules <dns_usermanual_0601>`.

**Procedure**
-------------

#. Log in to the management console.

#. In the service list, choose **Network** > **Domain Name Service**.

   The DNS console is displayed.

3. In the navigation pane, choose **Public Zones** or **Private Zones**.

   The zone list is displayed.

4. (Optional) If you have selected **Private Zones**, click |image1| on the upper left corner to select the region and project.

5. Click the zone name.

6. Click **Add Record Set**.

   The **Add Record Set** dialog box is displayed.

7. Set required parameters based on :ref:`Table 1 <dns_usermanual_0013__table28439303171815>`.

   .. _dns_usermanual_0013__table28439303171815:

   .. table:: **Table 1** Parameters for adding an SRV record set

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------+
      | Parameter             | Description                                                                                                                                            | Example Value                                                             |
      +=======================+========================================================================================================================================================+===========================================================================+
      | Name                  | Service (for example, FTP, SSH, or SIP) provided over the specified protocol (for example, TCP or UDP) on a host                                       | \_ftp._tcp                                                                |
      |                       |                                                                                                                                                        |                                                                           |
      |                       | The format is \_\ *Service name*.\_\ *Protocol*.                                                                                                       | **\_ftp._tcp** indicates that the host provides the FTP service over TCP. |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------+
      | Type                  | Type of the record set                                                                                                                                 | SRV - Record servers providing specific services                          |
      |                       |                                                                                                                                                        |                                                                           |
      |                       | If a message is displayed indicating that the record set you are trying to create exists, the record set conflicts with an existing record set.        |                                                                           |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------+
      | TTL (s)               | Cache duration of the record set on a local DNS server, in seconds                                                                                     | The default value is **300**, which is, 5 minutes.                        |
      |                       |                                                                                                                                                        |                                                                           |
      |                       | The value ranges from **1** to **2147483647**, and the default is **300**.                                                                             |                                                                           |
      |                       |                                                                                                                                                        |                                                                           |
      |                       | If your service address changes frequently, set TTL to a smaller value.                                                                                |                                                                           |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------+
      | Value                 | Server address                                                                                                                                         | 2 1 2355 example_server.test.com                                          |
      |                       |                                                                                                                                                        |                                                                           |
      |                       | You can enter a maximum of 50 record values, each on a separate line.                                                                                  |                                                                           |
      |                       |                                                                                                                                                        |                                                                           |
      |                       | The value format is **[priority] [weight] [port number] [server address]**.                                                                            |                                                                           |
      |                       |                                                                                                                                                        |                                                                           |
      |                       | Configuration rules:                                                                                                                                   |                                                                           |
      |                       |                                                                                                                                                        |                                                                           |
      |                       | -  The priority, weight, and port number range from 0 to 65535.                                                                                        |                                                                           |
      |                       |                                                                                                                                                        |                                                                           |
      |                       | -  A smaller priority value indicates a higher priority.                                                                                               |                                                                           |
      |                       |                                                                                                                                                        |                                                                           |
      |                       | -  A larger weight value indicates a larger weight.                                                                                                    |                                                                           |
      |                       |                                                                                                                                                        |                                                                           |
      |                       | -  The server address is the domain name of the target server.                                                                                         |                                                                           |
      |                       |                                                                                                                                                        |                                                                           |
      |                       |    Ensure that the domain name can be resolved.                                                                                                        |                                                                           |
      |                       |                                                                                                                                                        |                                                                           |
      |                       | .. note::                                                                                                                                              |                                                                           |
      |                       |                                                                                                                                                        |                                                                           |
      |                       |    The system checks the priority values first. If the priority values are the same, the system will check the weight values.                          |                                                                           |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------+
      | Tags                  | (Optional) Identifier of a resource                                                                                                                    | example_key1                                                              |
      |                       |                                                                                                                                                        |                                                                           |
      |                       | Each tag contains a key and a value. You can add a maximum of 20 tags to a record set. This parameter is displayed when you enable **Other Settings**. | example_value1                                                            |
      |                       |                                                                                                                                                        |                                                                           |
      |                       | For details about tag key and value requirements, see :ref:`Table 2 <dns_usermanual_0013__table191971158112315>`.                                      |                                                                           |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------+
      | Description           | (Optional) Supplementary information about the record set                                                                                              | ``-``                                                                     |
      |                       |                                                                                                                                                        |                                                                           |
      |                       | You can enter a maximum of 255 characters.                                                                                                             |                                                                           |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------+

   .. _dns_usermanual_0013__table191971158112315:

   .. table:: **Table 2** Tag key and value requirements

      +-----------------------+--------------------------------------------+-----------------------+
      | Parameter             | Requirements                               | Example Value         |
      +=======================+============================================+=======================+
      | Key                   | -  Cannot be left blank.                   | example_key1          |
      |                       | -  Must be unique for each resource.       |                       |
      |                       | -  Can contain a maximum of 36 characters. |                       |
      +-----------------------+--------------------------------------------+-----------------------+
      | Value                 | -  Cannot be left blank.                   | example_value1        |
      |                       | -  Can contain a maximum of 43 characters. |                       |
      +-----------------------+--------------------------------------------+-----------------------+

8. Click **OK**.

9. Switch back to the **Record Sets** page.

   View the added record set in the record set list of the zone and ensure that the status of the record set is **Normal**.

.. |image1| image:: /_static/images/en-us_image_0148391090.png
