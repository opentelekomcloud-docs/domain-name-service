:original_name: en-us_topic_0035467699.html

.. _en-us_topic_0035467699:

Configuring a Public Zone
=========================

Scenario
--------

After you register a domain name and set up a website, you can configure record sets to map the domain name to the public IP address of the web server so that end users can use the domain name to access your website over the Internet.

For example, you have already built a website on a web server with a public IPv4 address bound. To allow end users to access your website using domain name example.com and its subdomain www.example.com, perform the following operations:

-  Add an A record set that maps domain name example.com to the public IP address of the web server.
-  Add an A record set that maps subdomain www.example.com to the public IP address of the web server.

Prerequisites
-------------

-  You have registered domain name example.com.
-  You have deployed a web server and obtained its public IP address.

Process Flow
------------

:ref:`Figure 1 <en-us_topic_0035467699__fe4910c96160749349abf31cb88cfe52b>` shows the process of configuring a domain name for your website.

.. _en-us_topic_0035467699__fe4910c96160749349abf31cb88cfe52b:

.. figure:: /_static/images/en-us_image_0000001906813590.png
   :alt: **Figure 1** Process of configuring a domain name

   **Figure 1** Process of configuring a domain name

Procedure
---------

#. Create a public zone.

   Create a public zone for your domain name on the DNS console.

   a. Log in to the management console.

   b. In the service list, choose **Network** > **Domain Name Service**.

      The DNS console is displayed.

   c. In the navigation pane on the left, choose **Public Zones**.

      The **Public Zones** page is displayed.

   d. Click **Create Public Zone**.

   e. Set **Domain Name** to **example.com**.

      Configure other parameters by referring to :ref:`Creating a Public Zone <en-us_topic_0035467702>`.


      .. figure:: /_static/images/en-us_image_0000001906813570.png
         :alt: **Figure 2** Creating a public zone

         **Figure 2** Creating a public zone

   f. Click **OK**.

      You can view the created public zone in the public zone list.


      .. figure:: /_static/images/en-us_image_0000001906973418.png
         :alt: **Figure 3** Public zone list

         **Figure 3** Public zone list

      .. note::

         You can click the domain name to view SOA and NS record sets automatically generated for the zone.

         -  The NS record set defines the authoritative DNS servers for the domain name.

         -  .. _en-us_topic_0035467699__li6252195613418:

            The start of authority (SOA) record includes administrative information about your zone, as defined by the Domain Name System (DNS).

2. Add an A record set.

   Add an A record set to the created public zone to allow access to your website using example.com.

   a. On the **Public Zones** page, click the domain name (**example.com**) of the public zone you created.

      The **Record Sets** page is displayed.

   b. Click **Add Record Set**.

   c. Configure the parameters as follows:

      -  **Name**: Leave this parameter blank. The DNS service automatically considers example.com as the name, and requests are routed to example.com.
      -  **Type**: Retain the default setting **A - Map domains to IPv4 addresses**.
      -  **Value**: Enter the public IP address of your web server.

      Configure other parameters by referring to :ref:`Adding an A Record Set <dns_usermanual_0007>`.


      .. figure:: /_static/images/en-us_image_0000001906813542.png
         :alt: **Figure 4** Adding an A record set

         **Figure 4** Adding an A record set

   d. Click **OK**.

      The added record set is in the **Normal** state.

3. Add an A record set to a subdomain.

   Add another A record set to the created public zone to allow access to your website using www.example.com.

   a. On the **Public Zones** page, click the domain name (**example.com**) of the public zone you created.

      The **Record Sets** page is displayed.

   b. Click **Add Record Set**.

   c. Configure the parameters as follows:

      -  **Name**: Set it to **www**, indicating that the subdomain to be resolved is **www.example.com**.
      -  **Type**: Retain the default setting **A - Map domains to IPv4 addresses**.
      -  **Value**: Enter the public IP address of your web server.

      Configure other parameters by referring to :ref:`Adding an A Record Set <dns_usermanual_0007>`.


      .. figure:: /_static/images/en-us_image_0000001906973434.png
         :alt: **Figure 5** Adding an A record set

         **Figure 5** Adding an A record set

   d. Click **OK**.

      The added record set is in the **Normal** state.

4. Change the DNS server addresses.

   The DNS service provides authoritative DNS servers for domain resolution.

   After you create a public zone, an NS record set is generated, which specifies the DNS servers provided by the DNS service.

   If DNS server addresses of the public domain name are not the same as those in the NS record set, the DNS service will not be able to resolve the domain name. You must change the DNS server addresses of the domain name on the registrar's website.

   .. note::

      Generally, the changes to DNS server addresses take effect within 48 hours, but the time may vary depending on the domain name registrar's cache duration.

   **Query the DNS server addresses provided by the DNS service.**

   a. Log in to the management console.

   b. In the service list, choose **Network** > **Domain Name Service**.

      The DNS console is displayed.

   c. In the navigation pane on the left, choose **Public Zones**.

      The **Public Zones** page is displayed.

   d. Click the domain name of the public zone you created.

      Locate the NS record set and view the DNS server addresses under **Value**.


      .. figure:: /_static/images/en-us_image_0000001906813582.png
         :alt: **Figure 6** NS record set

         **Figure 6** NS record set

   **Change the DNS servers.**

   Log in to the domain name registrar's website and change the DNS server addresses to those provided by the DNS service. Refer to the domain name registrar's documentation for detailed operations.
