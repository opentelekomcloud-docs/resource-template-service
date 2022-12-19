:original_name: rts_02_0058.html

.. _rts_02_0058:

OS::Heat::StructuredConfig
==========================

A resource which has same logic with OS::Heat::SoftwareConfig.

This resource is like OS::Heat::SoftwareConfig except that the config property is represented by a Map rather than a String.

This is useful for configuration tools which use YAML or JSON as their configuration syntax. The resulting configuration is transferred, stored and returned by the software_configs API as parsed JSON.

Optional Properties
-------------------

+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                          |
+===================================+======================================================================================================================================================+
| config                            | Map representing the configuration data structure which will be serialized to JSON format.                                                           |
|                                   |                                                                                                                                                      |
|                                   | Map value expected.                                                                                                                                  |
|                                   |                                                                                                                                                      |
|                                   | Updates cause replacement.                                                                                                                           |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
| group                             | Namespace to group this software config by when delivered to a server. This may imply what configuration tool is going to perform the configuration. |
|                                   |                                                                                                                                                      |
|                                   | String value expected.                                                                                                                               |
|                                   |                                                                                                                                                      |
|                                   | Updates cause replacement.                                                                                                                           |
|                                   |                                                                                                                                                      |
|                                   | Defaults to "Heat::Ungrouped".                                                                                                                       |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
| inputs                            | Schema representing the inputs that this software config is expecting.                                                                               |
|                                   |                                                                                                                                                      |
|                                   | List value expected.                                                                                                                                 |
|                                   |                                                                                                                                                      |
|                                   | Updates cause replacement.                                                                                                                           |
|                                   |                                                                                                                                                      |
|                                   | *List contents:*                                                                                                                                     |
|                                   |                                                                                                                                                      |
|                                   | -  \*                                                                                                                                                |
|                                   |                                                                                                                                                      |
|                                   |    Map value expected.                                                                                                                               |
|                                   |                                                                                                                                                      |
|                                   |    Updates cause replacement.                                                                                                                        |
|                                   |                                                                                                                                                      |
|                                   |    *Map properties:*                                                                                                                                 |
|                                   |                                                                                                                                                      |
|                                   |    -  default                                                                                                                                        |
|                                   |                                                                                                                                                      |
|                                   |       Default value for the input if none is specified.                                                                                              |
|                                   |                                                                                                                                                      |
|                                   |       String value expected.                                                                                                                         |
|                                   |                                                                                                                                                      |
|                                   |       Updates cause replacement.                                                                                                                     |
|                                   |                                                                                                                                                      |
|                                   |    -  description                                                                                                                                    |
|                                   |                                                                                                                                                      |
|                                   |       Description of the input.                                                                                                                      |
|                                   |                                                                                                                                                      |
|                                   |       String value expected.                                                                                                                         |
|                                   |                                                                                                                                                      |
|                                   |       Updates cause replacement.                                                                                                                     |
|                                   |                                                                                                                                                      |
|                                   |    -  name                                                                                                                                           |
|                                   |                                                                                                                                                      |
|                                   |       Name of the input.                                                                                                                             |
|                                   |                                                                                                                                                      |
|                                   |       String value expected.                                                                                                                         |
|                                   |                                                                                                                                                      |
|                                   |       Updates cause replacement.                                                                                                                     |
|                                   |                                                                                                                                                      |
|                                   |    -  replace_on_change                                                                                                                              |
|                                   |                                                                                                                                                      |
|                                   |       Replace the deployment instead of updating it when the input value changes.                                                                    |
|                                   |                                                                                                                                                      |
|                                   |       Boolean value expected.                                                                                                                        |
|                                   |                                                                                                                                                      |
|                                   |       Updates cause replacement.                                                                                                                     |
|                                   |                                                                                                                                                      |
|                                   |       Defaults to "False".                                                                                                                           |
|                                   |                                                                                                                                                      |
|                                   |    -  type                                                                                                                                           |
|                                   |                                                                                                                                                      |
|                                   |       Type of the value of the input.                                                                                                                |
|                                   |                                                                                                                                                      |
|                                   |       String value expected.                                                                                                                         |
|                                   |                                                                                                                                                      |
|                                   |       Updates cause replacement.                                                                                                                     |
|                                   |                                                                                                                                                      |
|                                   |       Defaults to "String".                                                                                                                          |
|                                   |                                                                                                                                                      |
|                                   |       Allowed values: String, Number, CommaDelimitedList, Json, Boolean                                                                              |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
| options                           | Map containing options specific to the configuration management tool used by this resource.                                                          |
|                                   |                                                                                                                                                      |
|                                   | Map value expected.                                                                                                                                  |
|                                   |                                                                                                                                                      |
|                                   | Updates cause replacement.                                                                                                                           |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
| outputs                           | Schema representing the outputs that this software config will produce.                                                                              |
|                                   |                                                                                                                                                      |
|                                   | List value expected.                                                                                                                                 |
|                                   |                                                                                                                                                      |
|                                   | Updates cause replacement.                                                                                                                           |
|                                   |                                                                                                                                                      |
|                                   | *List contents:*                                                                                                                                     |
|                                   |                                                                                                                                                      |
|                                   | -  \*                                                                                                                                                |
|                                   |                                                                                                                                                      |
|                                   |    Map value expected.                                                                                                                               |
|                                   |                                                                                                                                                      |
|                                   |    Updates cause replacement.                                                                                                                        |
|                                   |                                                                                                                                                      |
|                                   |    *Map properties:*                                                                                                                                 |
|                                   |                                                                                                                                                      |
|                                   |    -  description                                                                                                                                    |
|                                   |                                                                                                                                                      |
|                                   |       Description of the output.                                                                                                                     |
|                                   |                                                                                                                                                      |
|                                   |       String value expected.                                                                                                                         |
|                                   |                                                                                                                                                      |
|                                   |       Updates cause replacement.                                                                                                                     |
|                                   |                                                                                                                                                      |
|                                   |    -  error_output                                                                                                                                   |
|                                   |                                                                                                                                                      |
|                                   |       Denotes that the deployment is in an error state if this output has a value.                                                                   |
|                                   |                                                                                                                                                      |
|                                   |       Boolean value expected.                                                                                                                        |
|                                   |                                                                                                                                                      |
|                                   |       Updates cause replacement.                                                                                                                     |
|                                   |                                                                                                                                                      |
|                                   |       Defaults to "False".                                                                                                                           |
|                                   |                                                                                                                                                      |
|                                   |    -  name                                                                                                                                           |
|                                   |                                                                                                                                                      |
|                                   |       Name of the output.                                                                                                                            |
|                                   |                                                                                                                                                      |
|                                   |       String value expected.                                                                                                                         |
|                                   |                                                                                                                                                      |
|                                   |       Updates cause replacement.                                                                                                                     |
|                                   |                                                                                                                                                      |
|                                   |    -  type                                                                                                                                           |
|                                   |                                                                                                                                                      |
|                                   |       Type of the value of the output.                                                                                                               |
|                                   |                                                                                                                                                      |
|                                   |       String value expected.                                                                                                                         |
|                                   |                                                                                                                                                      |
|                                   |       Updates cause replacement.                                                                                                                     |
|                                   |                                                                                                                                                      |
|                                   |       Defaults to "String".                                                                                                                          |
|                                   |                                                                                                                                                      |
|                                   |       Allowed values: String, Number, CommaDelimitedList, Json, Boolean                                                                              |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+

Attributes
----------

+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                                        |
+===================================+====================================================================================================================================================================================+
| config                            | The config value of the software config.                                                                                                                                           |
|                                   |                                                                                                                                                                                    |
|                                   | The config is generally read from a script file and often contains some parameter substitutions. The config value is the script content that actually runs in the virtual machine. |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Heat::StructuredConfig
       properties:
         config: {...}
         group: String
         inputs: [{"type": String, "default": String, "name": String, "replace_on_change": Boolean, "description": String}, {"type": String, "default": String, "name": String, "replace_on_change": Boolean, "description": String}, ...]
         options: {...}
         outputs: [{"type": String, "name": String, "error_output": Boolean, "description": String}, {"type": String, "name": String, "error_output": Boolean, "description": String}, ...]
