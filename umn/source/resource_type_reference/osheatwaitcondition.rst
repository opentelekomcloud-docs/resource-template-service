:original_name: rts_02_0061.html

.. _rts_02_0061:

OS::Heat::WaitCondition
=======================

Resource for handling signals received by WaitConditionHandle.

Resource takes WaitConditionHandle and starts to create. Resource is in CREATE_IN_PROGRESS status until WaitConditionHandle doesnt receive sufficient number of successful signals (this number can be specified with count property) and successfully creates after that, or fails due to timeout.

Required Properties
-------------------

+-----------------------------------+------------------------------------------------------------------------------+
| Name                              | Description                                                                  |
+===================================+==============================================================================+
| handle                            | A reference to the wait condition handle used to signal this wait condition. |
|                                   |                                                                              |
|                                   | String value expected.                                                       |
|                                   |                                                                              |
|                                   | Updates cause replacement.                                                   |
+-----------------------------------+------------------------------------------------------------------------------+
| timeout                           | The number of seconds to wait for the correct number of signals to arrive.   |
|                                   |                                                                              |
|                                   | Number value expected.                                                       |
|                                   |                                                                              |
|                                   | Updates cause replacement.                                                   |
|                                   |                                                                              |
|                                   | The value must be in the range 1 to 43200, include 1 and 43200.              |
+-----------------------------------+------------------------------------------------------------------------------+

Optional Properties
-------------------

+-----------------------------------+--------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                      |
+===================================+==================================================================================================+
| count                             | The number of success signals that must be received before the stack creation process continues. |
|                                   |                                                                                                  |
|                                   | Integer value expected.                                                                          |
|                                   |                                                                                                  |
|                                   | Can be updated without replacement.                                                              |
|                                   |                                                                                                  |
|                                   | Defaults to "1".                                                                                 |
|                                   |                                                                                                  |
|                                   | The value must be at least 1.                                                                    |
+-----------------------------------+--------------------------------------------------------------------------------------------------+

Attributes
----------

+------+----------------------------------------------------------------------------------------+
| Name | Description                                                                            |
+======+========================================================================================+
| data | JSON string containing data associated with wait condition signals sent to the handle. |
+------+----------------------------------------------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Heat::WaitCondition
       properties:
         count: Integer
         handle: String
         timeout: Number
