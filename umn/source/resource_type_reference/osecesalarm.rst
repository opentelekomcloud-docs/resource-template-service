:original_name: rts_02_0078.html

.. _rts_02_0078:

OSE::CES::Alarm
===============

A resource of CES.

Required Properties
-------------------

+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                                               |
+===================================+===========================================================================================================================================================================================+
| evaluation_periods                | Consecutive count.                                                                                                                                                                        |
|                                   |                                                                                                                                                                                           |
|                                   | Integer value expected.                                                                                                                                                                   |
|                                   |                                                                                                                                                                                           |
|                                   | Can be updated without replacement.                                                                                                                                                       |
|                                   |                                                                                                                                                                                           |
|                                   | Allowed values: from 1 to 5, include 1 and 5.                                                                                                                                             |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| comparison_operator               | Operator used to compare specified statistic with threshold.                                                                                                                              |
|                                   |                                                                                                                                                                                           |
|                                   | String value expected.                                                                                                                                                                    |
|                                   |                                                                                                                                                                                           |
|                                   | Can be updated without replacement.                                                                                                                                                       |
|                                   |                                                                                                                                                                                           |
|                                   | Allowed values: gt, lt, ge, le, eq                                                                                                                                                        |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| meter_name                        | Metric name.                                                                                                                                                                              |
|                                   |                                                                                                                                                                                           |
|                                   | String value expected.                                                                                                                                                                    |
|                                   |                                                                                                                                                                                           |
|                                   | Updates cause replacement.                                                                                                                                                                |
|                                   |                                                                                                                                                                                           |
|                                   | Allowed values: **cpu_util**, **mem_util**, **network_incoming_bytes_rate_inband**, and **network_outgoing_bytes_rate_inband**.                                                           |
|                                   |                                                                                                                                                                                           |
|                                   | -  cpu_util: CPU Usage.                                                                                                                                                                   |
|                                   | -  mem_util: Memory Usage.                                                                                                                                                                |
|                                   | -  network_incoming_bytes_rate_inband: Inband Incoming Rate.                                                                                                                              |
|                                   | -  network_outgoing_bytes_rate_inband: Inband Outgoing Rate.                                                                                                                              |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| period                            | Period (seconds) to evaluate over.                                                                                                                                                        |
|                                   |                                                                                                                                                                                           |
|                                   | Integer value expected.                                                                                                                                                                   |
|                                   |                                                                                                                                                                                           |
|                                   | Can be updated without replacement.                                                                                                                                                       |
|                                   |                                                                                                                                                                                           |
|                                   | Allowed values: 300, 1200, 3600, 14400, 86400                                                                                                                                             |
|                                   |                                                                                                                                                                                           |
|                                   | During alarm interconnection with CES, the native attribute **period** can be any value. However, CES supports only the preceding fixed values. Otherwise, alarm resource creation fails. |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| resource_id                       | ID of the group.                                                                                                                                                                          |
|                                   |                                                                                                                                                                                           |
|                                   | String value expected.                                                                                                                                                                    |
|                                   |                                                                                                                                                                                           |
|                                   | Updates cause replacement.                                                                                                                                                                |
|                                   |                                                                                                                                                                                           |
|                                   | This attributed is required by Cloud Eye (CES) for filtering.                                                                                                                             |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| statistic                         | Way to data aggregation.                                                                                                                                                                  |
|                                   |                                                                                                                                                                                           |
|                                   | String value expected.                                                                                                                                                                    |
|                                   |                                                                                                                                                                                           |
|                                   | Updates cause replacement.                                                                                                                                                                |
|                                   |                                                                                                                                                                                           |
|                                   | Allowed values: avg, min, max, variance.                                                                                                                                                  |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| threshold                         | Threshold value of the alarm.                                                                                                                                                             |
|                                   |                                                                                                                                                                                           |
|                                   | Integer value expected.                                                                                                                                                                   |
|                                   |                                                                                                                                                                                           |
|                                   | Can be updated without replacement.                                                                                                                                                       |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Optional Properties
-------------------

+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                                                             |
+===================================+=========================================================================================================================================================================================================+
| action_enabled                    | Whether to enable this alarm to trigger actions.                                                                                                                                                        |
|                                   |                                                                                                                                                                                                         |
|                                   | Boolean value expected.                                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                         |
|                                   | Can be updated without replacement.                                                                                                                                                                     |
|                                   |                                                                                                                                                                                                         |
|                                   | Defaults to "True".                                                                                                                                                                                     |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| alarm_actions                     | A list of URLs (webhooks) to invoke when state transitions to alarm.                                                                                                                                    |
|                                   |                                                                                                                                                                                                         |
|                                   | List value expected.                                                                                                                                                                                    |
|                                   |                                                                                                                                                                                                         |
|                                   | Can be updated without replacement.                                                                                                                                                                     |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| description                       | Description for the alarm.                                                                                                                                                                              |
|                                   |                                                                                                                                                                                                         |
|                                   | String value expected.                                                                                                                                                                                  |
|                                   |                                                                                                                                                                                                         |
|                                   | Can be updated without replacement.                                                                                                                                                                     |
|                                   |                                                                                                                                                                                                         |
|                                   | Allowed pattern: ``^[^\&\"\'\(\)]{``\ 0,256}$                                                                                                                                                           |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| enabled                           | Whether to enable alarm.                                                                                                                                                                                |
|                                   |                                                                                                                                                                                                         |
|                                   | Boolean value expected.                                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                         |
|                                   | Can be updated without replacement.                                                                                                                                                                     |
|                                   |                                                                                                                                                                                                         |
|                                   | Defaults to "True".                                                                                                                                                                                     |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| name                              | Name of the alarm.                                                                                                                                                                                      |
|                                   |                                                                                                                                                                                                         |
|                                   | String value expected.                                                                                                                                                                                  |
|                                   |                                                                                                                                                                                                         |
|                                   | Can be updated without replacement.                                                                                                                                                                     |
|                                   |                                                                                                                                                                                                         |
|                                   | It is allowed to start with **numbers**, **letters**, \_, and **-** characters. It is allowed to include **numbers**, **letters**, \_, and **-** characters, and the string length is **1** to **128**. |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| unit                              | Unit of data.                                                                                                                                                                                           |
|                                   |                                                                                                                                                                                                         |
|                                   | String value expected.                                                                                                                                                                                  |
|                                   |                                                                                                                                                                                                         |
|                                   | Can be updated without replacement.                                                                                                                                                                     |
|                                   |                                                                                                                                                                                                         |
|                                   | The string length allowed is **0** to **32**.                                                                                                                                                           |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| matching_metadata                 | Meter should match this resource metadata (key=value) additionally to the meter_name.                                                                                                                   |
|                                   |                                                                                                                                                                                                         |
|                                   | Map value expected.                                                                                                                                                                                     |
|                                   |                                                                                                                                                                                                         |
|                                   | Can be updated without replacement.                                                                                                                                                                     |
|                                   |                                                                                                                                                                                                         |
|                                   | Defaults to "{}".                                                                                                                                                                                       |
|                                   |                                                                                                                                                                                                         |
|                                   | .. note::                                                                                                                                                                                               |
|                                   |                                                                                                                                                                                                         |
|                                   |    This parameter is invalid in the current version.                                                                                                                                                    |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| resource_type                     | Alarm type of resource.                                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                         |
|                                   | String value expected.                                                                                                                                                                                  |
|                                   |                                                                                                                                                                                                         |
|                                   | Updates cause replacement.                                                                                                                                                                              |
|                                   |                                                                                                                                                                                                         |
|                                   | Defaults to "RTS.Group".                                                                                                                                                                                |
|                                   |                                                                                                                                                                                                         |
|                                   | Allowed values: RTS.Group, AS.Group                                                                                                                                                                     |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OSE::CES::Alarm
       properties:
         action_enabled: Boolean
         alarm_actions: […]
         comparison_operator: String
         description: String
         enabled: Boolean
         evaluation_periods: Integer
         meter_name: String
         name: String
         period: Integer
         resource_id: String
         statistic: String
         threshold: Integer
         unit: String
