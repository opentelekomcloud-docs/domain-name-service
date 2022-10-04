:original_name: dns_usermanual_0039.html

.. _dns_usermanual_0039:

Overview
========

Reverse resolution involves obtaining a domain name based on an IP address and is typically used to improve credibility of email servers.

After a recipient server receives an email, it checks whether the IP address and domain name of the sender server are trustworthy and determines whether the email is spam. If the recipient server fails to obtain the domain name mapped to the sender's IP address, it considers that the email is sent by a malicious host and rejects it. Therefore, it is necessary to map IP addresses of your email servers to domain names by adding PTR records.

.. table:: **Table 1** PTR record description

   +-------------------------------------------------------+-----------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Operation                                             | Scenario                                            | Constraint                                                                                                         |
   +=======================================================+=====================================================+====================================================================================================================+
   | :ref:`Creating a PTR Record <en-us_topic_0077500015>` | Create PTR records for cloud resources such as ECS. | -  PTR records are project-level resources. When you create a PTR record, you need to select a region and project. |
   |                                                       |                                                     | -  Each user can add a maximum of 50 PTR records.                                                                  |
   +-------------------------------------------------------+-----------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | :ref:`Managing PTR Records <dns_usermanual_0040>`     | Modify, delete, and query PTR records.              | -  After you created a PTR record, its EIP cannot be changed.                                                      |
   |                                                       |                                                     | -  After you delete a PTR record, the domain name mapped to your EIP will change to the default domain name.       |
   +-------------------------------------------------------+-----------------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
