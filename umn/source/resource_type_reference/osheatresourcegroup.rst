:original_name: rts_02_0052.html

.. _rts_02_0052:

OS::Heat::ResourceGroup
=======================

Creates one or more identically configured nested resources.

In addition to the refs attribute, this resource implements synthetic attributes that mirror those of the resources in the group. When getting an attribute from this resource, however, a list of attribute values for each resource in the group is returned. To get attribute values for a single resource in the group, synthetic attributes of the form resource.{resource index}.{attribute name} can be used. The resource ID of a particular resource in the group can be obtained via the synthetic attribute resource.{resource index}. Note, that if you get attribute without {resource index}, e.g. [resource, {attribute_name}], you will get a list of this attributes value for all resources in group.

While each resource in the group will be identically configured, this resource does allow for some index-based customization of the properties of the resources in the group. For example:

.. code-block::

   resources:
     my_indexed_group:
       type: OS::Heat::ResourceGroup
       properties:
         count: 3
         resource_def:
           type: OS::Nova::Server
           properties:
             # create a unique name for each server
             # using its index in the group
             name: my_server_%index%
             image: CentOS 6.5
             flavor: 4GB Performance

would result in a group of three servers having the same image and flavor, but names of my_server_0, my_server_1, and my_server_2. The variable used for substitution can be customized by using the index_var property.

Required Properties
-------------------

+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                            |
+===================================+========================================================================================================================================================================+
| resource_def                      | Resource definition for the resources in the group. The value of this property is the definition of a resource just as if it had been declared in the template itself. |
|                                   |                                                                                                                                                                        |
|                                   | Map value expected.                                                                                                                                                    |
|                                   |                                                                                                                                                                        |
|                                   | Can be updated without replacement.                                                                                                                                    |
|                                   |                                                                                                                                                                        |
|                                   | *Map properties:*                                                                                                                                                      |
|                                   |                                                                                                                                                                        |
|                                   | -  metadata                                                                                                                                                            |
|                                   |                                                                                                                                                                        |
|                                   |    Supplied metadata for the resources in the group.                                                                                                                   |
|                                   |                                                                                                                                                                        |
|                                   |    Map value expected.                                                                                                                                                 |
|                                   |                                                                                                                                                                        |
|                                   |    Can be updated without replacement.                                                                                                                                 |
|                                   |                                                                                                                                                                        |
|                                   | -  properties                                                                                                                                                          |
|                                   |                                                                                                                                                                        |
|                                   |    Property values for the resources in the group.                                                                                                                     |
|                                   |                                                                                                                                                                        |
|                                   |    Map value expected.                                                                                                                                                 |
|                                   |                                                                                                                                                                        |
|                                   |    Can be updated without replacement.                                                                                                                                 |
|                                   |                                                                                                                                                                        |
|                                   | -  type                                                                                                                                                                |
|                                   |                                                                                                                                                                        |
|                                   |    The type of the resources in the group.                                                                                                                             |
|                                   |                                                                                                                                                                        |
|                                   |    String value expected.                                                                                                                                              |
|                                   |                                                                                                                                                                        |
|                                   |    Can be updated without replacement.                                                                                                                                 |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Optional Properties
-------------------

+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                                                                                                         |
+===================================+=====================================================================================================================================================================================================================================================+
| count                             | The number of resources to create.                                                                                                                                                                                                                  |
|                                   |                                                                                                                                                                                                                                                     |
|                                   | Integer value expected.                                                                                                                                                                                                                             |
|                                   |                                                                                                                                                                                                                                                     |
|                                   | Can be updated without replacement.                                                                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                                                                     |
|                                   | Defaults to "1".                                                                                                                                                                                                                                    |
|                                   |                                                                                                                                                                                                                                                     |
|                                   | The value must be at least 0.                                                                                                                                                                                                                       |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| index_var                         | A variable that this resource will use to replace with the current index of a given resource in the group. Can be used, for example, to customize the name property of grouped servers in order to differentiate them when listed with nova client. |
|                                   |                                                                                                                                                                                                                                                     |
|                                   | String value expected.                                                                                                                                                                                                                              |
|                                   |                                                                                                                                                                                                                                                     |
|                                   | Updates cause replacement.                                                                                                                                                                                                                          |
|                                   |                                                                                                                                                                                                                                                     |
|                                   | Defaults to "%index%".                                                                                                                                                                                                                              |
|                                   |                                                                                                                                                                                                                                                     |
|                                   | The length must be at least 3.                                                                                                                                                                                                                      |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Attributes
----------

+------------+-----------------------------------------------------------------------------------------------------------------------------+
| Name       | Description                                                                                                                 |
+============+=============================================================================================================================+
| attributes | A map of resource names to the specified attribute of each individual resource. Requires heat_template_version: 2014-10-16. |
+------------+-----------------------------------------------------------------------------------------------------------------------------+
| refs       | A list of resource IDs for the resources in the group.                                                                      |
+------------+-----------------------------------------------------------------------------------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Heat::ResourceGroup
       properties:
         count: Integer
         index_var: String
         removal_policies: [{"resource_list": [Value, Value, ...]}, {"resource_list": [Value, Value, ...]}, ...]
         resource_def: {"type": String, "properties": {...}, "metadata": {...}}
