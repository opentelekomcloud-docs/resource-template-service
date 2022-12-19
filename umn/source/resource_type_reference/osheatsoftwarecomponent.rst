:original_name: rts_02_0054.html

.. _rts_02_0054:

OS::Heat::SoftwareComponent
===========================

A resource for describing and storing a software component.

This resource is similar to OS::Heat::SoftwareConfig. In contrast to SoftwareConfig which allows for storing only one configuration (e.g. one script), SoftwareComponent allows for storing multiple configurations to address handling of all lifecycle hooks (CREATE, UPDATE, DELETE) for a software component in one place.

This resource is backed by the persistence layer and the API of the SoftwareConfig resource, and only adds handling for the additional configs property and attribute.

Required Properties
-------------------

+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                                                      |
+===================================+==================================================================================================================================================================================================+
| configs                           | The list of configurations for the different lifecycle actions of the represented software component.                                                                                            |
|                                   |                                                                                                                                                                                                  |
|                                   | List value expected.                                                                                                                                                                             |
|                                   |                                                                                                                                                                                                  |
|                                   | Updates cause replacement.                                                                                                                                                                       |
|                                   |                                                                                                                                                                                                  |
|                                   | The length must be at least 1.                                                                                                                                                                   |
|                                   |                                                                                                                                                                                                  |
|                                   | List contents:                                                                                                                                                                                   |
|                                   |                                                                                                                                                                                                  |
|                                   | -  \*                                                                                                                                                                                            |
|                                   |                                                                                                                                                                                                  |
|                                   |    Map value expected.                                                                                                                                                                           |
|                                   |                                                                                                                                                                                                  |
|                                   |    Updates cause replacement.                                                                                                                                                                    |
|                                   |                                                                                                                                                                                                  |
|                                   |    Map properties:                                                                                                                                                                               |
|                                   |                                                                                                                                                                                                  |
|                                   |    -  actions                                                                                                                                                                                    |
|                                   |                                                                                                                                                                                                  |
|                                   |       Lifecycle actions to which the configuration applies. The string values provided for this property can include the standard resource actions CREATE, DELETE, and UPDATE supported by Heat. |
|                                   |                                                                                                                                                                                                  |
|                                   |       List value expected.                                                                                                                                                                       |
|                                   |                                                                                                                                                                                                  |
|                                   |       Updates cause replacement.                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                  |
|                                   |       Defaults to "[CREATE, UPDATE]".                                                                                                                                                            |
|                                   |                                                                                                                                                                                                  |
|                                   |       The length must be at least 1.                                                                                                                                                             |
|                                   |                                                                                                                                                                                                  |
|                                   |       List contents:                                                                                                                                                                             |
|                                   |                                                                                                                                                                                                  |
|                                   |       \*                                                                                                                                                                                         |
|                                   |                                                                                                                                                                                                  |
|                                   |       String value expected.                                                                                                                                                                     |
|                                   |                                                                                                                                                                                                  |
|                                   |       Updates cause replacement.                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                  |
|                                   |    -  config                                                                                                                                                                                     |
|                                   |                                                                                                                                                                                                  |
|                                   |       Configuration script or manifest which specifies what actual configuration is performed.                                                                                                   |
|                                   |                                                                                                                                                                                                  |
|                                   |       String value expected.                                                                                                                                                                     |
|                                   |                                                                                                                                                                                                  |
|                                   |       Updates cause replacement.                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                  |
|                                   |    -  tool                                                                                                                                                                                       |
|                                   |                                                                                                                                                                                                  |
|                                   |       The configuration tool used to actually apply the configuration on a server. This string property has to be understood by in-instance tools running inside deployed servers.               |
|                                   |                                                                                                                                                                                                  |
|                                   |       String value expected.                                                                                                                                                                     |
|                                   |                                                                                                                                                                                                  |
|                                   |       Updates cause replacement.                                                                                                                                                                 |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Optional Properties
-------------------

+-----------------------------------+---------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                 |
+===================================+=============================================================================================+
| inputs                            | Schema representing the inputs that this software config is expecting.                      |
|                                   |                                                                                             |
|                                   | List value expected.                                                                        |
|                                   |                                                                                             |
|                                   | Updates cause replacement.                                                                  |
|                                   |                                                                                             |
|                                   | *List contents:*                                                                            |
|                                   |                                                                                             |
|                                   | -  \*                                                                                       |
|                                   |                                                                                             |
|                                   |    Map value expected.                                                                      |
|                                   |                                                                                             |
|                                   |    Updates cause replacement.                                                               |
|                                   |                                                                                             |
|                                   |    *Map properties:*                                                                        |
|                                   |                                                                                             |
|                                   |    -  default                                                                               |
|                                   |                                                                                             |
|                                   |       Default value for the input if none is specified.                                     |
|                                   |                                                                                             |
|                                   |       String value expected.                                                                |
|                                   |                                                                                             |
|                                   |       Updates cause replacement.                                                            |
|                                   |                                                                                             |
|                                   |    -  description                                                                           |
|                                   |                                                                                             |
|                                   |       Description of the input.                                                             |
|                                   |                                                                                             |
|                                   |       String value expected.                                                                |
|                                   |                                                                                             |
|                                   |       Updates cause replacement.                                                            |
|                                   |                                                                                             |
|                                   |    -  name                                                                                  |
|                                   |                                                                                             |
|                                   |       Name of the input.                                                                    |
|                                   |                                                                                             |
|                                   |       String value expected.                                                                |
|                                   |                                                                                             |
|                                   |       Updates cause replacement.                                                            |
|                                   |                                                                                             |
|                                   |    -  replace_on_change                                                                     |
|                                   |                                                                                             |
|                                   |       Replace the deployment instead of updating it when the input value changes.           |
|                                   |                                                                                             |
|                                   |       Boolean value expected.                                                               |
|                                   |                                                                                             |
|                                   |       Updates cause replacement.                                                            |
|                                   |                                                                                             |
|                                   |       Defaults to "False".                                                                  |
|                                   |                                                                                             |
|                                   |    -  type                                                                                  |
|                                   |                                                                                             |
|                                   |       Type of the value of the input.                                                       |
|                                   |                                                                                             |
|                                   |       String value expected.                                                                |
|                                   |                                                                                             |
|                                   |       Updates cause replacement.                                                            |
|                                   |                                                                                             |
|                                   |       Defaults to "String".                                                                 |
|                                   |                                                                                             |
|                                   |       Allowed values: String, Number, CommaDelimitedList, Json, Boolean                     |
+-----------------------------------+---------------------------------------------------------------------------------------------+
| options                           | Map containing options specific to the configuration management tool used by this resource. |
|                                   |                                                                                             |
|                                   | Map value expected.                                                                         |
|                                   |                                                                                             |
|                                   | Updates cause replacement.                                                                  |
+-----------------------------------+---------------------------------------------------------------------------------------------+
| outputs                           | Schema representing the outputs that this software config will produce.                     |
|                                   |                                                                                             |
|                                   | List value expected.                                                                        |
|                                   |                                                                                             |
|                                   | Updates cause replacement.                                                                  |
|                                   |                                                                                             |
|                                   | *List contents:*                                                                            |
|                                   |                                                                                             |
|                                   | -  \*                                                                                       |
|                                   |                                                                                             |
|                                   |    Map value expected.                                                                      |
|                                   |                                                                                             |
|                                   |    Updates cause replacement.                                                               |
|                                   |                                                                                             |
|                                   |    *Map properties:*                                                                        |
|                                   |                                                                                             |
|                                   |    -  description                                                                           |
|                                   |                                                                                             |
|                                   |       Description of the output.                                                            |
|                                   |                                                                                             |
|                                   |       String value expected.                                                                |
|                                   |                                                                                             |
|                                   |       Updates cause replacement.                                                            |
|                                   |                                                                                             |
|                                   |    -  error_output                                                                          |
|                                   |                                                                                             |
|                                   |       Denotes that the deployment is in an error state if this output has a value.          |
|                                   |                                                                                             |
|                                   |       Boolean value expected.                                                               |
|                                   |                                                                                             |
|                                   |       Updates cause replacement.                                                            |
|                                   |                                                                                             |
|                                   |       Defaults to "False".                                                                  |
|                                   |                                                                                             |
|                                   |    -  name                                                                                  |
|                                   |                                                                                             |
|                                   |       Name of the output.                                                                   |
|                                   |                                                                                             |
|                                   |       String value expected.                                                                |
|                                   |                                                                                             |
|                                   |       Updates cause replacement.                                                            |
|                                   |                                                                                             |
|                                   |    -  type                                                                                  |
|                                   |                                                                                             |
|                                   |       Type of the value of the output.                                                      |
|                                   |                                                                                             |
|                                   |       String value expected.                                                                |
|                                   |                                                                                             |
|                                   |       Updates cause replacement.                                                            |
|                                   |                                                                                             |
|                                   |       Defaults to "String".                                                                 |
|                                   |                                                                                             |
|                                   |       Allowed values: String, Number, CommaDelimitedList, Json, Boolean                     |
+-----------------------------------+---------------------------------------------------------------------------------------------+

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
       type: OS::Heat::SoftwareComponent
       properties:
         configs: [{"config": String, "tool": String, "actions": [String, String, ...]}, {"config": String, "tool": String, "actions": [String, String, ...]}, ...]
         inputs: [{"type": String, "default": String, "name": String, "replace_on_change": Boolean, "description": String}, {"type": String, "default": String, "name": String, "replace_on_change": Boolean, "description": String}, ...]
         options: {...}
         outputs: [{"type": String, "name": String, "error_output": Boolean, "description": String}, {"type": String, "name": String, "error_output": Boolean, "description": String}, ...]
