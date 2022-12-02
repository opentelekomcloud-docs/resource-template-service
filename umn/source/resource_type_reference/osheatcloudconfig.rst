:original_name: rts_02_0049.html

.. _rts_02_0049:

OS::Heat::CloudConfig
=====================

A configuration resource for representing cloud-init cloud-config.

This resource allows cloud-config YAML to be defined and stored by the config API. Any intrinsic functions called in the config will be resolved before storing the result.

This resource will generally be referenced by OS::Nova::Server user_data, or OS::Heat::MultipartMime parts config. Since cloud-config is boot-only configuration, any changes to the definition will result in the replacement of all servers which reference it.

Optional Properties
-------------------

+-----------------------------------+-----------------------------------------------------------------------------------+
| Name                              | Description                                                                       |
+===================================+===================================================================================+
| cloud_config                      | Map representing the cloud-config data structure which will be formatted as YAML. |
|                                   |                                                                                   |
|                                   | Map value expected.                                                               |
|                                   |                                                                                   |
|                                   | Updates cause replacement.                                                        |
+-----------------------------------+-----------------------------------------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Heat::CloudConfig
       properties:
         cloud_config: {...}
