:original_name: rts_02_0062.html

.. _rts_02_0062:

OS::Heat::WaitConditionHandle
=============================

Resource for managing instance signals.

The main points of this resource are:

-  have no dependencies (so the instance can reference it).
-  create credentials to allow for signaling from the instance.
-  handle signals from the instance, validate and store result.

Optional Properties
-------------------

+-----------------------------------+-----------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                         |
+===================================+=====================================================================================================+
| signal_transport                  | How the client will signal the wait condition.                                                      |
|                                   |                                                                                                     |
|                                   | -  TOKEN_SIGNAL will allow and HTTP POST to a Heat API endpoint with the provided keystone token.   |
|                                   | -  NO_SIGNAL will result in the resource going to a signalled state without waiting for any signal. |
|                                   |                                                                                                     |
|                                   | String value expected.                                                                              |
|                                   |                                                                                                     |
|                                   | Updates cause replacement.                                                                          |
|                                   |                                                                                                     |
|                                   | Defaults to "TOKEN_SIGNAL".                                                                         |
|                                   |                                                                                                     |
|                                   | Allowed values: TOKEN_SIGNAL, NO_SIGNAL                                                             |
+-----------------------------------+-----------------------------------------------------------------------------------------------------+

Attributes
----------

+----------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name     | Description                                                                                                                                                                                                                                                                                                                                                              |
+==========+==========================================================================================================================================================================================================================================================================================================================================================================+
| curl_cli | Convenience attribute, provides curl CLI command prefix, which can be used for signaling handle completion or failure when signal_transport is set to TOKEN_SIGNAL. You can signal success by adding -data-binary {"status": "SUCCESS"} , or signal failure by adding -data-binary {"status": "FAILURE"}. This attribute is set to None for all other signal transports. |
+----------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| endpoint | Endpoint/url which can be used for signaling handle when signal_transport is set to TOKEN_SIGNAL. None for all other signal transports.                                                                                                                                                                                                                                  |
+----------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| token    | Token for stack-user which can be used for signaling handle when signal_transport is set to TOKEN_SIGNAL. None for all other signal transports.                                                                                                                                                                                                                          |
+----------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Heat::WaitConditionHandle
       properties:
         signal_transport: String
