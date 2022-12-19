:original_name: rts_02_0023.html

.. _rts_02_0023:

Creating a stack
================

With RTS, you can create a collection of cloud resources using a template. These resources are defined as a stack. This section uses creating a random string as an example to describe how to create a stack on the RTS console.

Prerequisite
------------

You have prepared a stack template.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner to select the desired region and project.

#. Under **Management & Deployment**, click **Resource Template Service**.

#. Click **Create Stack** in the upper right corner.

   The process of creating a stack is displayed.

#. Upload a template.

   -  For a single template, you can create a stack by entering template content online.

      a. **Template Source**: Select **Manually specify**.

      b. **Template Content**: Enter template content online or copy content of an existing template to the text box.

         .. note::

            The template must comply with the JSON or YAML format and uses the UTF-8 encoding format.

      c. Click **Next** to check syntax.

         If the syntax check succeeds, the **Specify Details** page is displayed. If the syntax check fails, modify the template as prompted.

   -  For a single or nested template, you can create a stack by uploading a template package.


      .. figure:: /_static/images/en-us_image_0165712169.png
         :alt: **Figure 1** Uploading a template file

         **Figure 1** Uploading a template file

      a. **Template Source**: Select **Upload template**.

      b. **Stack Template**: Click |image2|, select the prepared template package, and click **Upload**.

      c. **Main File**: Select a template file as the main file based on the resources you want to create. A template package may contain multiple template files.

      d. After selecting a main file, click **Next** to check the syntax.

         If the syntax check succeeds, the **Specify Details** page is displayed. If the syntax check fails, modify the template as prompted.

#. On the **Specify Details** page, enter a stack name, set parameters based on the required resource information, and click **Next**.

   .. note::

      The stack name:

      -  Contains 1 to 255 characters.
      -  Starts with a letter.
      -  Can contain digits, hyphens (-), dots (.), and underlines (_).

#. Confirm that stack configurations are correct and click **Submit**.

   It takes some time to complete the creation.

Result
------

You can view the stack creation result in the stack list or details or query events.

You can click **Events** on the **Specify Details** page to view each operation occurring during stack creation. All operations are displayed in the time sequence, and the latest operation is in the first row.

.. |image1| image:: /_static/images/en-us_image_0210485079.png
.. |image2| image:: /_static/images/en-us_image_0238393889.png
