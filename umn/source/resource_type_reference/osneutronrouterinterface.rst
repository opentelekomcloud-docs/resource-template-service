:original_name: rts_02_0069.html

.. _rts_02_0069:

OS::Neutron::RouterInterface
============================

A resource for managing Neutron router interfaces.

Router interfaces associate routers with existing subnets or ports.

Required Properties
-------------------

+-----------------------------------+-----------------------------------+
| Name                              | Description                       |
+===================================+===================================+
| router_id                         | The router id.                    |
|                                   |                                   |
|                                   | String value expected.            |
|                                   |                                   |
|                                   | Updates cause replacement.        |
+-----------------------------------+-----------------------------------+

Optional Properties
-------------------

+-----------------------------------+---------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                   |
+===================================+===============================================================================================================+
| port_id                           | The port id, either subnet or port_id should be specified.                                                    |
|                                   |                                                                                                               |
|                                   | String value expected.                                                                                        |
|                                   |                                                                                                               |
|                                   | Updates cause replacement.                                                                                    |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------+
| subnet                            | The subnet, either subnet or port should be specified.                                                        |
|                                   |                                                                                                               |
|                                   | String value expected.                                                                                        |
|                                   |                                                                                                               |
|                                   | Updates cause replacement.                                                                                    |
|                                   |                                                                                                               |
|                                   | Value must be of type neutron.subnet                                                                          |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------+
| subnet_id                         | String value expected.                                                                                        |
|                                   |                                                                                                               |
|                                   | Updates cause replacement.                                                                                    |
|                                   |                                                                                                               |
|                                   | .. note::                                                                                                     |
|                                   |                                                                                                               |
|                                   |    In the template,                                                                                           |
|                                   |                                                                                                               |
|                                   |    -  **subnet** and **subnet_id** cannot appear at the same time, otherwise the stack will fail to create.   |
|                                   |                                                                                                               |
|                                   |    -  At least one of the following properties must be specified: **port_id**, **subnet** (or **subnet_id**). |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Neutron::RouterInterface
       properties:
         port_id: String
         router_id: String
         subnet: String
         subnet_id: String
