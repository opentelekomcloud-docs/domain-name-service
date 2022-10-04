:original_name: dns_pd_0009.html

.. _dns_pd_0009:

Domain Name Format and Structure
================================

A valid domain name meets the following requirements:

-  A domain name is segmented using dots (.) into multiple labels.
-  A domain name label can contain letters, digits, and hyphens (-) and cannot start or end with a hyphen.
-  A label cannot exceed 63 characters.
-  The total length of a domain name, including the dot at the end, cannot exceed 254 characters.

Domain names are classified into the following levels based on their structure:

-  Root domain: . (a dot)
-  Top-level domain: for example, .com, .net, .org, and .cn
-  Second-level domain: subdomains of the top-level domain names, such as example.com, example.net, and example.org
-  Third-level domain: subdomains of the second-level domain names, such as abc.example.com, abc.example.net, and abc.example.org
-  The next-level domain names are similarly expanded by adding prefixes to the previous-level domain names, such as def.abc.example.com, def.abc.example.net, and def.abc.example.org.
