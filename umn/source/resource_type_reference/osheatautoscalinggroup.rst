:original_name: rts_02_0048.html

.. _rts_02_0048:

OS::Heat::AutoScalingGroup
==========================

An autoscaling group that can scale arbitrary resources.

An autoscaling group allows the creation of a desired count of similar resources, which are defined with the resource property in HOT format. If there is a need to create many of the same resources (e.g. one hundred sets of Server, WaitCondition and WaitConditionHandle or even Neutron Nets), AutoScalingGroup is a convenient and easy way to do that.

.. note::

   -  During the scaling process, you are not allowed to create members. Otherwise, the scaling action fails.
   -  Cross-AZ automatic scaling is not supported.

Required Properties
-------------------

+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                                           |
+===================================+=======================================================================================================================================================================================+
| max_size                          | Maximum number of resources in the group.                                                                                                                                             |
|                                   |                                                                                                                                                                                       |
|                                   | Integer value expected.                                                                                                                                                               |
|                                   |                                                                                                                                                                                       |
|                                   | Can be updated without replacement.                                                                                                                                                   |
|                                   |                                                                                                                                                                                       |
|                                   | The value must be at least 0.                                                                                                                                                         |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| min_size                          | Minimum number of resources in the group.                                                                                                                                             |
|                                   |                                                                                                                                                                                       |
|                                   | Integer value expected.                                                                                                                                                               |
|                                   |                                                                                                                                                                                       |
|                                   | Can be updated without replacement.                                                                                                                                                   |
|                                   |                                                                                                                                                                                       |
|                                   | The value must be at least 0.                                                                                                                                                         |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| resource                          | Resource definition for the resources in the group, in HOT format. The value of this property is the definition of a resource just as if it had been declared in the template itself. |
|                                   |                                                                                                                                                                                       |
|                                   | Map value expected.                                                                                                                                                                   |
|                                   |                                                                                                                                                                                       |
|                                   | Can be updated without replacement.                                                                                                                                                   |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Optional Properties
-------------------

+-----------------------------------+-----------------------------------------------------------------------------------------+
| Name                              | Description                                                                             |
+===================================+=========================================================================================+
| cooldown                          | Cooldown period, in seconds.                                                            |
|                                   |                                                                                         |
|                                   | Integer value expected.                                                                 |
|                                   |                                                                                         |
|                                   | Can be updated without replacement.                                                     |
+-----------------------------------+-----------------------------------------------------------------------------------------+
| desired_capacity                  | Desired initial number of resources.                                                    |
|                                   |                                                                                         |
|                                   | Integer value expected.                                                                 |
|                                   |                                                                                         |
|                                   | Can be updated without replacement.                                                     |
+-----------------------------------+-----------------------------------------------------------------------------------------+
| rolling_updates                   | Policy for rolling updates for this scaling group.                                      |
|                                   |                                                                                         |
|                                   | Map value expected.                                                                     |
|                                   |                                                                                         |
|                                   | Can be updated without replacement.                                                     |
|                                   |                                                                                         |
|                                   | Defaults to "{max_batch_size: 1, min_in_service: 0, pause_time: 0}".                    |
|                                   |                                                                                         |
|                                   | Map properties:                                                                         |
|                                   |                                                                                         |
|                                   | -  max_batch_size                                                                       |
|                                   |                                                                                         |
|                                   |    The maximum number of resources to replace at once.                                  |
|                                   |                                                                                         |
|                                   |    Integer value expected.                                                              |
|                                   |                                                                                         |
|                                   |    Can be updated without replacement.                                                  |
|                                   |                                                                                         |
|                                   |    Defaults to "1".                                                                     |
|                                   |                                                                                         |
|                                   |    The value must be at least 1.                                                        |
|                                   |                                                                                         |
|                                   | -  min_in_service                                                                       |
|                                   |                                                                                         |
|                                   |    The minimum number of resources in service while rolling updates are being executed. |
|                                   |                                                                                         |
|                                   |    Integer value expected.                                                              |
|                                   |                                                                                         |
|                                   |    Can be updated without replacement.                                                  |
|                                   |                                                                                         |
|                                   |    Defaults to "0".                                                                     |
|                                   |                                                                                         |
|                                   |    The value must be at least 0.                                                        |
|                                   |                                                                                         |
|                                   | -  pause_time                                                                           |
|                                   |                                                                                         |
|                                   |    The number of seconds to wait between batches of updates.                            |
|                                   |                                                                                         |
|                                   |    Number value expected.                                                               |
|                                   |                                                                                         |
|                                   |    Can be updated without replacement.                                                  |
|                                   |                                                                                         |
|                                   |    Defaults to "0".                                                                     |
|                                   |                                                                                         |
|                                   |    The value must be at least 0.                                                        |
+-----------------------------------+-----------------------------------------------------------------------------------------+

Attributes
----------

+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name         | Description                                                                                                                                                                                                                                 |
+==============+=============================================================================================================================================================================================================================================+
| outputs      | A map of resource names to the specified attribute of each individual resource that is part of the AutoScalingGroup. This map specifies output parameters that are available once the AutoScalingGroup has been instantiated.               |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| outputs_list | A list of the specified attribute of each individual resource that is part of the AutoScalingGroup. This list of attributes is available as an output once the AutoScalingGroup has been instantiated. Detailed information about resource. |
+--------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Heat::AutoScalingGroup
       properties:
         cooldown: Integer
         desired_capacity: Integer
         max_size: Integer
         min_size: Integer
         resource: {...}
         rolling_updates: {"max_batch_size": Integer, "pause_time": Number, "min_in_service": Integer}
