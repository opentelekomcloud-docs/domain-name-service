:original_name: dns_usermanual_0044.html

.. _dns_usermanual_0044:

Viewing Traces
==============

**Scenarios**
-------------

After CTS is enabled, the tracker starts recording operations on cloud resources. You can view operation records of the last 7 days on the CTS console.

This section describes how to query these records.

.. _dns_usermanual_0044__section960031713714:

**Procedure**
-------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. In the service list, choose **Management & Deployment** > **Cloud Trace Service**.

#. In the navigation pane on the left, choose **Trace List**.

#. Specify the filters used for querying traces. The following filters are available:


   .. figure:: /_static/images/en-us_image_0000001942372561.png
      :alt: **Figure 1** Filters

      **Figure 1** Filters

   -  **Trace Type**, **Trace Source**, **Resource Type**, and **Search By**

      Select a filter from the drop-down list.

      If you select **Trace name** for **Search By**, specify a trace name.

      If you select **Resource ID** for **Search By**, specify a resource ID.

      If you select **Resource name** for **Search By**, specify a resource name.

   -  **Operator**: Select a user who performs operations.

   -  **Trace Status**: Select **All trace statuses**, **Normal**, **Warning**, or **Incident**.

   -  Time range: Specify the start and end time to view traces generated during a time range of the last seven days.

#. Click |image2| on the left of the required trace to expand its details.

#. Click **View Trace**.

   A dialog box is displayed, in which the trace structure details are displayed.

.. |image1| image:: /_static/images/en-us_image_0000001942372557.png
.. |image2| image:: /_static/images/en-us_image_0000001906653316.png
