:original_name: rts_02_0050.html

.. _rts_02_0050:

OS::Heat::MultipartMime
=======================

Assembles a collection of software configurations as a multi-part mime.

Parts in the message can be populated with inline configuration or references to other config resources. If the referenced resource is itself a valid multi-part mime message, that will be broken into parts and those parts appended to this message.

The resulting multi-part mime message will be stored by the configs API and can be referenced in properties such as OS::Nova::Server user_data.

This resource is generally used to build a list of cloud-init configuration elements including scripts and cloud-config. Since cloud-init is boot-only configuration, any changes to the definition will result in the replacement of all servers which reference it.

Optional Properties
-------------------

+-----------------------------------+--------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                  |
+===================================+==============================================================================================================+
| parts                             | Parts belonging to this message.                                                                             |
|                                   |                                                                                                              |
|                                   | List value expected.                                                                                         |
|                                   |                                                                                                              |
|                                   | Updates cause replacement.                                                                                   |
|                                   |                                                                                                              |
|                                   | Defaults to "[]".                                                                                            |
|                                   |                                                                                                              |
|                                   | List contents:                                                                                               |
|                                   |                                                                                                              |
|                                   | -  \*                                                                                                        |
|                                   |                                                                                                              |
|                                   |    Map value expected.                                                                                       |
|                                   |                                                                                                              |
|                                   |    Updates cause replacement.                                                                                |
|                                   |                                                                                                              |
|                                   |    Map properties:                                                                                           |
|                                   |                                                                                                              |
|                                   |    -  config                                                                                                 |
|                                   |                                                                                                              |
|                                   |       Content of part to attach, either inline or by referencing the ID of another software config resource. |
|                                   |                                                                                                              |
|                                   |       String value expected.                                                                                 |
|                                   |                                                                                                              |
|                                   |       Updates cause replacement.                                                                             |
|                                   |                                                                                                              |
|                                   |    -  filename                                                                                               |
|                                   |                                                                                                              |
|                                   |       Optional filename to associate with part.                                                              |
|                                   |                                                                                                              |
|                                   |       String value expected.                                                                                 |
|                                   |                                                                                                              |
|                                   |       Updates cause replacement.                                                                             |
|                                   |                                                                                                              |
|                                   |    -  subtype                                                                                                |
|                                   |                                                                                                              |
|                                   |       Optional subtype to specify with the type.\\                                                           |
|                                   |                                                                                                              |
|                                   |       String value expected.                                                                                 |
|                                   |                                                                                                              |
|                                   |       Updates cause replacement.                                                                             |
|                                   |                                                                                                              |
|                                   |    -  Type                                                                                                   |
|                                   |                                                                                                              |
|                                   |       Whether the part content is text or multipart.                                                         |
|                                   |                                                                                                              |
|                                   |       String value expected.                                                                                 |
|                                   |                                                                                                              |
|                                   |       Updates cause replacement.                                                                             |
|                                   |                                                                                                              |
|                                   |       Defaults to "text".                                                                                    |
|                                   |                                                                                                              |
|                                   |       Allowed values: text, multipart                                                                        |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Heat::MultipartMime
       properties:
         parts: [{"filename": String, "subtype": String, "config": String, "type": String}, {"filename": String, "subtype": String, "config": String, "type": String}, ...]
