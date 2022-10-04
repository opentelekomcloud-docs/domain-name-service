:original_name: dns_faq_032.html

.. _dns_faq_032:

What Is CAA?
============

Certification Authority Authorization (CAA) is a way to ensure that SSL certificates are issued by authorized certificate authorities (CAs). CAA complies with all RFC 6844 requirements. As of September 8, 2017, all CAs are required to check CAA records before they can issue certificates.

CAA Specifications
------------------

Domain name owners can create CAA records to specify authorized CAs that can issue SSL certificates.

For security reasons, only authorized CAs can issue SSL certificates for the domain names used by your website. Setting CAA records enhances security for your website.

CAs will perform a DNS lookup for CAA records when they issue certificates.

-  If a CA does not find a CAA record, it can issue a certificate for the domain name.

   Any other CAs can also issue certificates for this domain name. Insecure certificates may be issued, and messages indicating that your website is insecure when users access your website.

-  If the CA finds a CAA record that authorizes it to issue certificates, it will issue a certificate for the domain name.

-  If the CA finds a CAA record but the record does not authorize it to issue certificates, the CA will not be able to issue SSL certificates for the domain name.

CAA Record
----------

A CAA record consists of a flag byte **[flag]**, a property tag, and a property value **[tag]-[value]**. You can create multiple CAA records for a domain name.

.. table:: **Table 1** Configuration of CAA records

   +------------------------------------------------------------------+------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Function                                                         | Example                            | Description                                                                                                                                                                                        |
   +==================================================================+====================================+====================================================================================================================================================================================================+
   | Configure a CAA record for one domain name.                      | 0 issue "ca.example.com"           | Only the specified CA (**ca.example.com**) can issue certificates for a particular domain name (**domain.com**). Requests to issue certificates for the domain name by other CAs will be rejected. |
   +------------------------------------------------------------------+------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                                                                  | 0 issue ";"                        | No CA is allowed to issue certificates for the domain name **domain.com**.                                                                                                                         |
   +------------------------------------------------------------------+------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Configure the CA to report violations to the domain name holder. | 0 iodef "mailto:admin@domain.com"  | If a certificate request violates the CAA record, the CA will notify the domain name holder of the violation.                                                                                      |
   +------------------------------------------------------------------+------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                                                                  | 0 iodef "http:// domain.com/log/"  | Requests to issue certificates by unauthorized CAs will be recorded.                                                                                                                               |
   |                                                                  |                                    |                                                                                                                                                                                                    |
   |                                                                  | 0 iodef "https:// domain.com/log/" |                                                                                                                                                                                                    |
   +------------------------------------------------------------------+------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Authorize a CA to issue wildcard certificates.                   | 0 issuewild "ca.example.com"       | The specified CA (**ca.example.com**) can issue wildcard certificates for the domain name.                                                                                                         |
   +------------------------------------------------------------------+------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Configuration example                                            | 0 issue "ca.abc.com"               | The example configures a CAA record for the domain name **domain.com**.                                                                                                                            |
   |                                                                  |                                    |                                                                                                                                                                                                    |
   |                                                                  | 0 issuewild "ca.def.com"           | -  Only CA **ca.abc.com** can issue certificates of all types.                                                                                                                                     |
   |                                                                  |                                    | -  Only CA **ca.def.com** can issue wildcard certificates.                                                                                                                                         |
   |                                                                  | 0 iodef "mailto:admin@domain.com"  | -  Any other CAs are not allowed to issue certificates.                                                                                                                                            |
   |                                                                  |                                    | -  When a violation occurs, the CA sends a notification to **admin@domain.com**.                                                                                                                   |
   +------------------------------------------------------------------+------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Checking Whether a CAA Record Has Taken Effect
----------------------------------------------

Use Domain Information Groper (dig) to check whether the CAA record has taken effect. dig is a network administration command-line tool for querying the Domain Name System. If your OS does not support dig commands, install the dig tool.

Command format: **dig** [*Record set type*] [*Domain name*] **+trace**.

Example command:

**dig caa www.example.com +trace**
