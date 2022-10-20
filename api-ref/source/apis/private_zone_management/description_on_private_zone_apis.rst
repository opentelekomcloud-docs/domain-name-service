:original_name: dns_api_63001.html

.. _dns_api_63001:

Description on Private Zone APIs
================================

Private zones are region-level resources, which are isolated and managed based on projects.

Before creating, querying, or deleting private zones, specify a project in **X-Project-Id** in the request header to perform the operations. If you do not specify one, the default project of the token will be used.

.. note::

   For details about **X-Project-Id**, see `API Usage Guidelines <https://docs.otc.t-systems.com/en-us/api/apiug/apig-en-api-180328001.html?tag=API%20Documents>`__.
