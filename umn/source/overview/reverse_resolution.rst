:original_name: dns_pd_0006.html

.. _dns_pd_0006:

Reverse Resolution
==================

Reverse resolution involves obtaining a domain name based on an IP address and is typically used to improve credibility of email servers.

After a recipient server receives an email, it checks whether the IP address and domain name of the sender server are trustworthy and determines whether the email is spam. If the recipient server cannot obtain the domain name mapped to the IP address of the sender server, it considers that the email is sent by a malicious host and rejects it. It is necessary to configure pointer records (PTR) to point the IP addresses of your email servers to domain names.

In the following figure, an ECS serves as an email server, and a PTR record is configured to map the EIP of the ECS to the domain name configured for accessing the email server.

.. _dns_pd_0006__fig272143141518:

.. figure:: /_static/images/en-us_image_0165559749.png
   :alt: **Figure 1** Reverse resolution


   **Figure 1** Reverse resolution

.. note::

   :ref:`Figure 1 <dns_pd_0006__fig272143141518>` shows only the process for reverse resolution. Information about how an email server checks the credibility of the sender's IP address and whether domain name is available on the Internet is not provided here.

If no PTR records are configured, the recipient server will treat emails from the email server as spam or malicious and discard them.

See :ref:`Configuring a PTR Record <en-us_topic_0040322596>` for detailed operations.
