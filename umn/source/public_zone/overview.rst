:original_name: dns_usermanual_0030.html

.. _dns_usermanual_0030:

Overview
========

A public zone provides information to translate a domain name and its subdomains into IP addresses required for network communications on the Internet. Visitors can access your website by entering a domain name in the address box of a browser. DNS provides public domain names resolution. To resolve public domain names, you must host the registered domain names on the DNS service.

This chapter describes how to create and manage public zones.

.. table:: **Table 1** Public zone operations

   +--------------------------------------------------------+----------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | Operation                                              | Scenario                               | Remarks                                                                                                      |
   +========================================================+========================================+==============================================================================================================+
   | :ref:`Creating a Public Zone <en-us_topic_0035467702>` | Create a zone for your domain name.    | -  Public zones are global resources. You do not need to set a region or project.                            |
   |                                                        |                                        | -  Each user can add a maximum of 50 public zones.                                                           |
   |                                                        |                                        | -  The domain name can be a second-level domain name or one of its subdomains, for example, abc.example.com. |
   +--------------------------------------------------------+----------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | :ref:`Managing Public Zones <dns_usermanual_0031>`     | Modify, delete, and view public zones. | -  Once a public zone is created, its name cannot be modified.                                               |
   |                                                        |                                        | -  After a public zone is deleted, all its record sets will also be deleted.                                 |
   +--------------------------------------------------------+----------------------------------------+--------------------------------------------------------------------------------------------------------------+
