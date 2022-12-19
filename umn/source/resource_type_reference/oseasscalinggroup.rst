:original_name: rts_02_0076.html

.. _rts_02_0076:

OSE::AS::ScalingGroup
=====================

A resource for managing autoscaling group.

Required Properties
-------------------

+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                                                            |
+===================================+========================================================================================================================================================================================================+
| scaling_group_name                | Autoscaling group name.                                                                                                                                                                                |
|                                   |                                                                                                                                                                                                        |
|                                   | String value expected.                                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                        |
|                                   | Can be updated without replacement.                                                                                                                                                                    |
|                                   |                                                                                                                                                                                                        |
|                                   | It is allowed to start with **numbers**, **letters**, \_, and **-** characters. It is allowed to include **numbers**, **letters**, \_, and **-** characters, and the string length is **1** to **64**. |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| scaling_configuration_id          | AS configuration ID.                                                                                                                                                                                   |
|                                   |                                                                                                                                                                                                        |
|                                   | String value expected.                                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                        |
|                                   | Can be updated without replacement.                                                                                                                                                                    |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| networks                          | An ordered list of networks used to create instances, which are in same VPC defined in the vpc_id parameter.                                                                                           |
|                                   |                                                                                                                                                                                                        |
|                                   | List value expected.                                                                                                                                                                                   |
|                                   |                                                                                                                                                                                                        |
|                                   | Can be updated without replacement.                                                                                                                                                                    |
|                                   |                                                                                                                                                                                                        |
|                                   | *List contents:*                                                                                                                                                                                       |
|                                   |                                                                                                                                                                                                        |
|                                   | -  \*                                                                                                                                                                                                  |
|                                   |                                                                                                                                                                                                        |
|                                   |    Map value expected.                                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                        |
|                                   |    Can be updated without replacement.                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                        |
|                                   |    *Map properties:*                                                                                                                                                                                   |
|                                   |                                                                                                                                                                                                        |
|                                   |    -  id                                                                                                                                                                                               |
|                                   |                                                                                                                                                                                                        |
|                                   |       The ID of network.                                                                                                                                                                               |
|                                   |                                                                                                                                                                                                        |
|                                   |       String value expected.                                                                                                                                                                           |
|                                   |                                                                                                                                                                                                        |
|                                   |       Can be updated without replacement.                                                                                                                                                              |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| security_groups                   | An ordered list of security groups used to create instances.                                                                                                                                           |
|                                   |                                                                                                                                                                                                        |
|                                   | List value expected.                                                                                                                                                                                   |
|                                   |                                                                                                                                                                                                        |
|                                   | Can be updated without replacement.                                                                                                                                                                    |
|                                   |                                                                                                                                                                                                        |
|                                   | *List contents:*                                                                                                                                                                                       |
|                                   |                                                                                                                                                                                                        |
|                                   | -  \*                                                                                                                                                                                                  |
|                                   |                                                                                                                                                                                                        |
|                                   |    Map value expected.                                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                        |
|                                   |    Can be updated without replacement.                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                        |
|                                   |    *Map properties:*                                                                                                                                                                                   |
|                                   |                                                                                                                                                                                                        |
|                                   |    -  id                                                                                                                                                                                               |
|                                   |                                                                                                                                                                                                        |
|                                   |       The ID of security group.                                                                                                                                                                        |
|                                   |                                                                                                                                                                                                        |
|                                   |       String value expected.                                                                                                                                                                           |
|                                   |                                                                                                                                                                                                        |
|                                   |       Can be updated without replacement.                                                                                                                                                              |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| vpc_id                            | Virtual private cloud ID.                                                                                                                                                                              |
|                                   |                                                                                                                                                                                                        |
|                                   | String value expected.                                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                        |
|                                   | Updates cause replacement.                                                                                                                                                                             |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Optional Properties
-------------------

+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                     |
+===================================+=================================================================================================================================================================+
| desire_instance_number            | Desired instance number allowed in autoscaling group.                                                                                                           |
|                                   |                                                                                                                                                                 |
|                                   | Integer value expected.                                                                                                                                         |
|                                   |                                                                                                                                                                 |
|                                   | Can be updated without replacement.                                                                                                                             |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
| min_instance_number               | The minimum instance number allowed in autoscaling group.                                                                                                       |
|                                   |                                                                                                                                                                 |
|                                   | Integer value expected.                                                                                                                                         |
|                                   |                                                                                                                                                                 |
|                                   | Can be updated without replacement.                                                                                                                             |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
| max_instance_number               | The max instance number allowed in autoscaling group.                                                                                                           |
|                                   |                                                                                                                                                                 |
|                                   | Integer value expected.                                                                                                                                         |
|                                   |                                                                                                                                                                 |
|                                   | Can be updated without replacement.                                                                                                                             |
|                                   |                                                                                                                                                                 |
|                                   | .. note::                                                                                                                                                       |
|                                   |                                                                                                                                                                 |
|                                   |    The max instance number can not be smaller than the minimum instance number, can be equal. The value must be greater than 0.                                 |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
| cool_down_time                    | Cool down period, in seconds.                                                                                                                                   |
|                                   |                                                                                                                                                                 |
|                                   | Integer value expected.                                                                                                                                         |
|                                   |                                                                                                                                                                 |
|                                   | Can be updated without replacement.                                                                                                                             |
|                                   |                                                                                                                                                                 |
|                                   | Range from 0 to 86400, include 0 and 86400.                                                                                                                     |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
| lb_listener_id                    | ELB listener ID.                                                                                                                                                |
|                                   |                                                                                                                                                                 |
|                                   | String value expected.                                                                                                                                          |
|                                   |                                                                                                                                                                 |
|                                   | Can be updated without replacement.                                                                                                                             |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
| lbaas_listeners                   | Lbaas listener, which is mutually exclusive with lb_listener_id.                                                                                                |
|                                   |                                                                                                                                                                 |
|                                   | List value expected.                                                                                                                                            |
|                                   |                                                                                                                                                                 |
|                                   | Can be updated without replacement.                                                                                                                             |
|                                   |                                                                                                                                                                 |
|                                   | *List contents:*                                                                                                                                                |
|                                   |                                                                                                                                                                 |
|                                   | -  \*                                                                                                                                                           |
|                                   |                                                                                                                                                                 |
|                                   |    Map value expected.                                                                                                                                          |
|                                   |                                                                                                                                                                 |
|                                   |    Can be updated without replacement.                                                                                                                          |
|                                   |                                                                                                                                                                 |
|                                   |    *Map properties:*                                                                                                                                            |
|                                   |                                                                                                                                                                 |
|                                   |    -  listener_id                                                                                                                                               |
|                                   |                                                                                                                                                                 |
|                                   |       The listener id of the elastic load balancer.                                                                                                             |
|                                   |                                                                                                                                                                 |
|                                   |       String value expected.                                                                                                                                    |
|                                   |                                                                                                                                                                 |
|                                   |       Can be updated without replacement.                                                                                                                       |
|                                   |                                                                                                                                                                 |
|                                   |    -  protocol_port                                                                                                                                             |
|                                   |                                                                                                                                                                 |
|                                   |       The port that backend server listens.                                                                                                                     |
|                                   |                                                                                                                                                                 |
|                                   |       Integer value expected.                                                                                                                                   |
|                                   |                                                                                                                                                                 |
|                                   |       Can be updated without replacement.                                                                                                                       |
|                                   |                                                                                                                                                                 |
|                                   |       Range from 1 to 65535, include 1 and 65535.                                                                                                               |
|                                   |                                                                                                                                                                 |
|                                   |    -  weight                                                                                                                                                    |
|                                   |                                                                                                                                                                 |
|                                   |       The request rate that backend server receive.                                                                                                             |
|                                   |                                                                                                                                                                 |
|                                   |       Integer value expected.                                                                                                                                   |
|                                   |                                                                                                                                                                 |
|                                   |       Can be updated without replacement.                                                                                                                       |
|                                   |                                                                                                                                                                 |
|                                   |       Range from 0 to 256, include 0 and 256.                                                                                                                   |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
| available_zones                   | An ordered list of available zones used to create instances.                                                                                                    |
|                                   |                                                                                                                                                                 |
|                                   | List value expected.                                                                                                                                            |
|                                   |                                                                                                                                                                 |
|                                   | Can be updated without replacement.                                                                                                                             |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
| health_periodic_audit_method      | The health periodic audit method, when the lb_listener_id and lbaas_listeners parameter is set, the default is ELB_AUDIT, otherwise, it defaults to NOVA_AUDIT. |
|                                   |                                                                                                                                                                 |
|                                   | String value expected.                                                                                                                                          |
|                                   |                                                                                                                                                                 |
|                                   | Can be updated without replacement.                                                                                                                             |
|                                   |                                                                                                                                                                 |
|                                   | Allowed values: ELB_AUDIT, NOVA_AUDIT                                                                                                                           |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
| health_periodic_audit_time        | The health periodic audit time, in minutes.                                                                                                                     |
|                                   |                                                                                                                                                                 |
|                                   | Integer value expected.                                                                                                                                         |
|                                   |                                                                                                                                                                 |
|                                   | Can be updated without replacement.                                                                                                                             |
|                                   |                                                                                                                                                                 |
|                                   | Allowed values: 5, 15, 60, 180                                                                                                                                  |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
| instance_terminate_policy         | The policy of terminating instances.                                                                                                                            |
|                                   |                                                                                                                                                                 |
|                                   | String value expected.                                                                                                                                          |
|                                   |                                                                                                                                                                 |
|                                   | Can be updated without replacement.                                                                                                                             |
|                                   |                                                                                                                                                                 |
|                                   | Allowed values: OLD_CONFIG_OLD_INSTANCE, OLD_CONFIG_NEW_INSTANCE, OLD_INSTANCE, NEW_INSTANCE                                                                    |
|                                   |                                                                                                                                                                 |
|                                   | -  OLD_CONFIG_OLD_INSTANCE: The oldest instance created based on the oldest configuration is removed from the AS group first.                                   |
|                                   | -  OLD_CONFIG_NEW_INSTANCE: The latest instance created based on the oldest configuration is removed from the AS group first.                                   |
|                                   | -  OLD_INSTANCE: The oldest instance is removed from the AS group first.                                                                                        |
|                                   | -  NEW_INSTANCE: The latest instance is removed from the AS group first.                                                                                        |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
| delete_publicip                   | Whether to delete the elastic ip when terminating instances.                                                                                                    |
|                                   |                                                                                                                                                                 |
|                                   | Boolean value expected.                                                                                                                                         |
|                                   |                                                                                                                                                                 |
|                                   | Can be updated without replacement.                                                                                                                             |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+

Attributes
----------

+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name      | Description                                                                                                                                                                         |
+===========+=====================================================================================================================================================================================+
| instances | A list of all instances information. The information of instances may be obtained through the following expression: "{ get_attr: [<autoscaling_group_resource_name>, instances] }". |
+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OSE::AS::ScalingGroup
       properties:
         scaling_group_name: String
         scaling_configuration_id: String
         desire_instance_number: Integer
         min_instance_number: Integer
         max_instance_number: Integer
         cool_down_time: Integer
         lb_listener_id: String
         available_zones: [String, String,…]
         networks: [String, String,…]
         security_groups: [{"id": String}, {"id":  String},…]
         vpc_id: String
         health_periodic_audit_method: String
         health_periodic_audit_time: Integer
         instance_terminate_policy: String
         notifications: [String, String,…]
         delete_publicip: Boolean
