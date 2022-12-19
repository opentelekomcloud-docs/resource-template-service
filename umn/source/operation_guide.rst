:original_name: en-us_topic_0162985073.html

.. _en-us_topic_0162985073:

Operation Guide
===============

RTS helps you create and configure a collection of resources using a template and makes it easy to manage these resources.

Compile a Template
------------------

To create and manage a resource stack, you need to compile a template, and then RTS creates and configures a collection of resources based on the template.

During template compilation, you need to define and describe the required resources. For cloud resource types supported, you can log in to the RTS console and click **Resource Types** in the left pane to view cloud resource types that are supported. For more details, see :ref:`Supported Resources <rts_01_0004>`.

For template syntax, see the following references:

-  :ref:`Template Structure <rts_02_0009>`
-  :ref:`Template Version <rts_02_0010>`
-  :ref:`Template Description <rts_02_0011>`
-  :ref:`Parameters <rts_02_0012>`
-  :ref:`Resources <rts_02_0013>`
-  :ref:`Outputs <rts_02_0014>`
-  :ref:`Conditions <rts_02_0015>`
-  :ref:`Internal Function <rts_02_0016>`

We provide common templates in :ref:`Example Templates <rts_02_0037>` for your reference. These templates contain ECSs. If these templates meet your business scenarios, you can directly use them or modify some parameters.

Creating a Stack Using a Template
---------------------------------

If you have created a template, log in to the RTS console, click **Create Stack**, upload a template file or manually enter template content, and perform subsequent operations as needed. Then, the system orchestrates cloud resources defined in the template and dependencies between them.

.. note::

   Before uploading a template, you need to package the template according to the required rules.

The references are as follows:

-  :ref:`Preparing a Template or a Template Package <en-us_topic_0068576463>`
-  :ref:`Creating a stack <rts_02_0023>`

Managing Stacks Using the Console
---------------------------------

Except for creating stacks, you can also view all resources in your stack or update, re-create, or delete your stack based on your service requirements on the RTS console.

The references are as follows:

-  :ref:`Viewing Details of a Stack <rts_02_0029>`
-  :ref:`Updating a Stack <rts_02_0030>`
-  :ref:`Deleting a Stack <rts_02_0035>`
