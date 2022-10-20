:original_name: dns_api_50000.html

.. _dns_api_50000:

API Usage Guidelines
====================

Public cloud APIs comply with the RESTful API design principles. REST-based web services are organized into resources. Each resource is identified by one or more Uniform Resource Identifiers (URIs). An application accesses a resource based on the resource's Unified Resource Locator (URL). A URL is usually in the following format: https://*Endpoint/uri*. In the URL, *uri* indicates the resource path, that is, the API access path.

An endpoint is the **request address** for calling an API. Endpoints vary depending on services and regions. For DNS endpoints, see `Regions and Endpoints <https://docs.otc.t-systems.com/endpoint/index.html>`__.

-  Private zone APIs and related APIs call different endpoints based on the region.

   For example, call the API provided in :ref:`Private Zone Management <dns_api_63000>` to create a private zone, and call the API provided in :ref:`Record Set Management <dns_api_64000>` to add a record set to a private zone.

-  Public zone APIs, PTR record APIs, and related APIs call only endpoint dns.eu-de.otc.t-systems.com in the **eu-de** region.

   For example, call the API provided in :ref:`Public Zone Management <dns_api_62000>` to create a public zone, call the API provided in :ref:`Record Set Management <dns_api_64000>` to add a record set to a public zone, and call the API provided in :ref:`PTR Record Management <dns_api_66000>` to add a PTR record.

Public cloud APIs use HTTPS as the transmission protocol. Requests/Responses are transmitted using JSON messages, with the media type represented by **Application/json**.

For details about how to use APIs, see `API Usage Guidelines <https://docs.otc.t-systems.com/en-us/api/apiug/apig-en-api-180328001.html?tag=API%20Documents>`__.
