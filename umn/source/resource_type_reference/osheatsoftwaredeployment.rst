:original_name: rts_02_0056.html

.. _rts_02_0056:

OS::Heat::SoftwareDeployment
============================

This resource associates a server with some configuration.

The configuration is to be deployed to that server.

A deployment allows input values to be specified which map to the inputs schema defined in the config resource. These input values are interpreted by the configuration tool in a tool-specific manner.

Whenever this resource goes to an IN_PROGRESS state, it creates an ephemeral config that includes the inputs values plus a number of extra inputs which have names prefixed with `deploy\_ <http://docs.openstack.org/developer/heat/template_guide/openstack.html#id1>`__. The extra inputs relate to the current state of the stack, along with the information and credentials required to signal back the deployment results.

Unless signal_transport=NO_SIGNAL, this resource will remain in an IN_PROGRESS state until the server signals it with the output values for that deployment. Those output values are then available as resource attributes, along with the default attributes deploy_stdout, deploy_stderr and deploy_status_code.

Specifying actions other than the default CREATE and UPDATE will result in the deployment being triggered in those actions. For example this would allow cleanup configuration to be performed during action DELETE. A config could be designed to only work with some specific actions, or a config can read the value of the deploy_action input to allow conditional logic to perform different configuration for different actions.

.. note::

   If the software deployment function is used, the cloud-init, heat-config, os-collect-config, os-refresh-config, os-apply-config, and heat-config-script tools must be installed on images.

Optional Properties
-------------------

+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                  |
+===================================+==============================================================================================================================================================+
| actions                           | Which lifecycle actions of the deployment resource will result in this deployment being triggered.                                                           |
|                                   |                                                                                                                                                              |
|                                   | List value expected.                                                                                                                                         |
|                                   |                                                                                                                                                              |
|                                   | Can be updated without replacement.                                                                                                                          |
|                                   |                                                                                                                                                              |
|                                   | Defaults to "[CREATE, UPDATE]".                                                                                                                              |
|                                   |                                                                                                                                                              |
|                                   | Allowed values: CREATE, UPDATE, DELETE                                                                                                                       |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
| config                            | ID of software configuration resource to execute when applying to the server.                                                                                |
|                                   |                                                                                                                                                              |
|                                   | String value expected.                                                                                                                                       |
|                                   |                                                                                                                                                              |
|                                   | Can be updated without replacement.                                                                                                                          |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
| input_values                      | Input values to apply to the software configuration on this server.                                                                                          |
|                                   |                                                                                                                                                              |
|                                   | Map value expected.                                                                                                                                          |
|                                   |                                                                                                                                                              |
|                                   | Can be updated without replacement.                                                                                                                          |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
| server                            | ID of resource to apply configuration to. Normally this should be a Nova server ID.                                                                          |
|                                   |                                                                                                                                                              |
|                                   | String value expected.                                                                                                                                       |
|                                   |                                                                                                                                                              |
|                                   | Updates cause replacement.                                                                                                                                   |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
| name                              | Name of the derived config associated with this deployment. This is used to apply a sort order to the list of configurations currently deployed to a server. |
|                                   |                                                                                                                                                              |
|                                   | String value expected.                                                                                                                                       |
|                                   |                                                                                                                                                              |
|                                   | Can be updated without replacement.                                                                                                                          |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
| signal_transport                  | How the server should signal to heat with the deployment output values.                                                                                      |
|                                   |                                                                                                                                                              |
|                                   | -  TEMP_URL_SIGNAL will create a Swift TempURL to be signaled via HTTP PUT.                                                                                  |
|                                   | -  NO_SIGNAL will result in the resource going to the COMPLETE state without waiting for any signal.                                                         |
|                                   |                                                                                                                                                              |
|                                   | String value expected.                                                                                                                                       |
|                                   |                                                                                                                                                              |
|                                   | Updates cause replacement.                                                                                                                                   |
|                                   |                                                                                                                                                              |
|                                   | Defaults to "TEMP_URL_SIGNAL".                                                                                                                               |
|                                   |                                                                                                                                                              |
|                                   | Allowed values: TEMP_URL_SIGNAL, NO_SIGNAL                                                                                                                   |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

Attributes
----------

+--------------------+--------------------------------------------------------+
| Name               | Description                                            |
+====================+========================================================+
| deploy_status_code | Returned status code from the configuration execution. |
+--------------------+--------------------------------------------------------+
| deploy_stderr      | Captured stderr from the configuration execution.      |
+--------------------+--------------------------------------------------------+
| deploy_stdout      | Captured stdout from the configuration execution.      |
+--------------------+--------------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Heat::SoftwareDeployment
       properties:
         actions: [Value, Value, ...]
         config: String
         input_values: {...}
         name: String
         server: String
         signal_transport: String
