:original_name: dns_usermanual_0030.html

.. _dns_usermanual_0030:

Overview
========

A public zone provides information to translate a domain name and its subdomains into IP addresses required for network communications over the Internet. Visitors can access your website by entering a domain name in the address box of a browser. To use DNS for public domain name resolution, create a public zone for your domain name, and add record sets to map your domain name to one or more IP addresses.

:ref:`Table 1 <dns_usermanual_0030__table977612405507>` describes the operations required for creating and managing public zones.

.. _dns_usermanual_0030__table977612405507:

.. table:: **Table 1** Public zone operations

   +--------------------------------------------------------+----------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation                                              | Scenario                               | Constraints                                                                                                                              |
   +========================================================+========================================+==========================================================================================================================================+
   | :ref:`Creating a Public Zone <en-us_topic_0035467702>` | Create a zone for your domain name.    | -  Public zones are global resources. You do not need to select a region or project.                                                     |
   |                                                        |                                        | -  Each account can have up to 50 public zones.                                                                                          |
   |                                                        |                                        | -  The domain name can be a second-level domain name (for example, example.com) or one of its subdomains (for example, abc.example.com). |
   +--------------------------------------------------------+----------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Managing Public Zones <dns_usermanual_0031>`     | Modify, delete, and view public zones. | -  The domain name of a created public zone cannot be modified.                                                                          |
   |                                                        |                                        | -  If a public zone is deleted, all its record sets will also be deleted.                                                                |
   +--------------------------------------------------------+----------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
