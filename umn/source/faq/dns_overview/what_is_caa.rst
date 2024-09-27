:original_name: dns_faq_032.html

.. _dns_faq_032:

What Is CAA?
============

Certification Authority Authorization (CAA) is to ensure that HTTPS certificates are issued by authorized certificate authorities (CAs). CAA complies with all IETF RFC 6844 requirements. As of September 8, 2017, all CAs are required to check CAA record sets before they can issue certificates.

CAA Specifications
------------------

Domain name owners can create CAA record sets to specify authorized CAs that can issue SSL certificates.

Only authorized CAs can issue SSL certificates for the domain names used by your website. Setting CAA record sets enhances security for your website.

CAs will perform a DNS lookup for CAA record sets when they issue certificates.

-  If a CA does not find a CAA record set, the CA can issue a certificate for the domain name.

   Other CAs can also issue certificates for this domain name, but these certificates may be insecure, and there will be messages indicating that your website is insecure when end users access your website.

-  If a CA finds a CAA record set that authorizes it to issue certificates, the CA will issue a certificate for the domain name.

-  If a CA finds a CAA record set that does not authorize it to issue certificates, the CA will not be able to issue SSL certificates for the domain name.

CAA Record Set
--------------

A CAA record set consists of a flag byte **[flag]**, a property tag, and a property value **[tag]-[value]**. You can create multiple CAA record sets for a domain name.

.. table:: **Table 1** Configuration of CAA record sets

   +-------------------------------------------------------------+------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Function                                                    | Example CAA Record Set             | Description                                                                                                                                                                                        |
   +=============================================================+====================================+====================================================================================================================================================================================================+
   | Configure a CAA record set for one domain name.             | 0 issue "ca.example.com"           | Only the specified CA (**ca.example.com**) can issue certificates for a particular domain name (**domain.com**). Requests to issue certificates for the domain name by other CAs will be rejected. |
   +-------------------------------------------------------------+------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                                                             | 0 issue ";"                        | No CA is allowed to issue certificates for the domain name (**domain.com**).                                                                                                                       |
   +-------------------------------------------------------------+------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Enable a CA to report violations to the domain name holder. | 0 iodef "mailto:admin@domain.com"  | If a certificate request violates the CAA record set, the CA will notify the domain name holder of the violation.                                                                                  |
   +-------------------------------------------------------------+------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                                                             | 0 iodef "http:// domain.com/log/"  | Requests to issue certificates by unauthorized CAs will be recorded.                                                                                                                               |
   |                                                             |                                    |                                                                                                                                                                                                    |
   |                                                             | 0 iodef "https:// domain.com/log/" |                                                                                                                                                                                                    |
   +-------------------------------------------------------------+------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Authorize a CA to issue wildcard certificates.              | 0 issuewild "ca.example.com"       | The authorized CA (**ca.example.com**) can issue wildcard certificates for the domain name.                                                                                                        |
   +-------------------------------------------------------------+------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Configuration example                                       | 0 issue "ca.abc.com"               | A CAA record set is configured for **domain.com**.                                                                                                                                                 |
   |                                                             |                                    |                                                                                                                                                                                                    |
   |                                                             | 0 issuewild "ca.def.com"           | -  Only CA **ca.abc.com** can issue certificates of all types.                                                                                                                                     |
   |                                                             |                                    | -  Only CA **ca.def.com** can issue wildcard certificates.                                                                                                                                         |
   |                                                             | 0 iodef "mailto:admin@domain.com"  | -  Any other CAs are not allowed to issue certificates.                                                                                                                                            |
   |                                                             |                                    | -  If a violation occurs, the CA sends a notification to **admin@domain.com**.                                                                                                                     |
   +-------------------------------------------------------------+------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Checking Whether a CAA Record Set Has Taken Effect
--------------------------------------------------

Use Domain Information Groper (dig) to check whether the CAA record set has taken effect. dig is a network administration command-line tool for querying the Domain Name System. If your OS does not support dig commands, install the dig tool.

Command format: **dig** [*Record set type*] [*Domain name*] **+trace**.

Example command:

**dig caa www.example.com +trace**
