:original_name: dns_faq_009.html

.. _dns_faq_009:

Why Was the Email Address Format Changed in the SOA Record?
===========================================================

When you add a record set, you can enter an email address to receive error information and problem reports of the domain name. However, based on RFC 2142, we strongly recommend that you use **HOSTMASTER@**\ *Domain name* as the email address.

Because the at sign (@) has a special meaning in the SOA record set, the system replaces it with a period (.) and includes a backslash (\\) before the period in the label before the at sign, but emails are still sent to the email address you specify. For more information, see RFC 1035.

For example, if you enter **test.hostmaster@example.com** when you create the zone, the email address displayed in the SOA record set is **test\\.hostmaster.example.com**.
