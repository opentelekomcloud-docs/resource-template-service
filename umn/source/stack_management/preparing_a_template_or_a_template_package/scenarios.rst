:original_name: rts_02_0018.html

.. _rts_02_0018:

Scenarios
=========

-  To perform operations on a stack using the Heat client, you only need to compile a template file.
-  To perform operations on a stack using the RTS console, you need to not only compile a template file, but also package the file in the required format if you create a stack by uploading a template. However, packaging the template file is not required if you choose to compile a template online. Compiling a template online is suitable if only one template is required. Uploading a template fits a wider range of templates: a single template or nested templates.

.. table:: **Table 1** Scenario description

   +--------------------+---------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Method             |                           | How to Prepare a Template                                                                                                                                                                                               |
   +====================+===========================+=========================================================================================================================================================================================================================+
   | Heat client        |                           | Use a text editor (like Notepad++) to compile a template and save it in the YAML format.                                                                                                                                |
   +--------------------+---------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Management console | Entering template content | Compile a template using a text editor and copy template content to the text box when creating a stack.                                                                                                                 |
   +--------------------+---------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                    | Uploading a file          | Compile a template using a text editor and then pack it in the format provided in :ref:`Template Package Structure <rts_02_0020>`. :ref:`Example Template Packages <rts_02_0022>` provides examples for your reference. |
   +--------------------+---------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   Template files can be in the YAML or JSON format.

   You can compile a template by following instructions in :ref:`Template Syntax <rts_02_0008>`. If you are not familiar with how to compile a template, you can refer to our examples.
