:original_name: rts_02_0053.html

.. _rts_02_0053:

OS::Heat::ScalingPolicy
=======================

A resource to manage scaling of OS::Heat::AutoScalingGroup.

Resource to manage scaling for OS::Heat::AutoScalingGroup, i.e. define which metric should be scaled and scaling adjustment, set cooldown etc.

Required Properties
-------------------

+-----------------------------------+--------------------------------------------------------------------------------+
| Name                              | Description                                                                    |
+===================================+================================================================================+
| adjustment_type                   | Type of adjustment (absolute or percentage).                                   |
|                                   |                                                                                |
|                                   | String value expected.                                                         |
|                                   |                                                                                |
|                                   | Can be updated without replacement.                                            |
|                                   |                                                                                |
|                                   | Allowed values: change_in_capacity, exact_capacity, percent_change_in_capacity |
+-----------------------------------+--------------------------------------------------------------------------------+
| auto_scaling_group_id             | AutoScaling group ID to apply policy to.                                       |
|                                   |                                                                                |
|                                   | String value expected.                                                         |
|                                   |                                                                                |
|                                   | Updates cause replacement.                                                     |
+-----------------------------------+--------------------------------------------------------------------------------+
| scaling_adjustment                | Size of adjustment.                                                            |
|                                   |                                                                                |
|                                   | Number value expected.                                                         |
|                                   |                                                                                |
|                                   | Can be updated without replacement.                                            |
+-----------------------------------+--------------------------------------------------------------------------------+

Optional Properties
-------------------

+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                                                            |
+===================================+========================================================================================================================================================================================================+
| cooldown                          | Cooldown period, in seconds.                                                                                                                                                                           |
|                                   |                                                                                                                                                                                                        |
|                                   | Number value expected.                                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                        |
|                                   | Can be updated without replacement.                                                                                                                                                                    |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| min_adjustment_step               | Minimum number of resources that are added or removed when the AutoScaling group scales up or down. This can be used only when specifying percent_change_in_capacity for the adjustment_type property. |
|                                   |                                                                                                                                                                                                        |
|                                   | Integer value expected.                                                                                                                                                                                |
|                                   |                                                                                                                                                                                                        |
|                                   | Can be updated without replacement.                                                                                                                                                                    |
|                                   |                                                                                                                                                                                                        |
|                                   | The value must be at least 0.                                                                                                                                                                          |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Attributes
----------

========= =================================
Name      Description
========= =================================
alarm_url A signed url to handle the alarm.
========= =================================

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Heat::ScalingPolicy
       properties:
         adjustment_type: String
         auto_scaling_group_id: String
         cooldown: Number
         min_adjustment_step: Integer
         scaling_adjustment: Number
