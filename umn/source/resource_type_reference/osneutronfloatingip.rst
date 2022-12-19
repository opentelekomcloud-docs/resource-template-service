:original_name: rts_02_0063.html

.. _rts_02_0063:

OS::Neutron::FloatingIP
=======================

A resource for managing Neutron floating IP addresses.

Floating IP addresses can change their association between routers by action of the user. One of the most common use cases for floating IP addresses is to provide public IP addresses to a private cloud, where there are a limited number of IP addresses available. Another is for a cloud system user to have a "static" IP address that can be reassigned when an instance is upgraded or moved.

Optional Properties
-------------------

+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                        |
+===================================+====================================================================================================================================================+
| floating_network                  | Network to allocate floating IP from.                                                                                                              |
|                                   |                                                                                                                                                    |
|                                   | String value expected.                                                                                                                             |
|                                   |                                                                                                                                                    |
|                                   | Updates cause replacement.                                                                                                                         |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
| fixed_ip_address                  | IP address to use if the port has multiple addresses.                                                                                              |
|                                   |                                                                                                                                                    |
|                                   | String value expected.                                                                                                                             |
|                                   |                                                                                                                                                    |
|                                   | Can be updated without replacement.                                                                                                                |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
| port_id                           | ID of an existing port with at least one IP address to associate with this floating IP. The port must be associated to a Nova instance.            |
|                                   |                                                                                                                                                    |
|                                   | String value expected.                                                                                                                             |
|                                   |                                                                                                                                                    |
|                                   | Can be updated without replacement.                                                                                                                |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
| value_specs                       | Extra parameters to include in the "floatingip" object in the creation request. Parameters are often specific to installed hardware or extensions. |
|                                   |                                                                                                                                                    |
|                                   | Map value expected.                                                                                                                                |
|                                   |                                                                                                                                                    |
|                                   | Updates cause replacement.                                                                                                                         |
|                                   |                                                                                                                                                    |
|                                   | Defaults to "{}".                                                                                                                                  |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+

Attributes
----------

+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                                                                                    |
+===================================+================================================================================================================================================================================================================================+
| fixed_ip_address                  | IP address of the associated port, if specified.                                                                                                                                                                               |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| floating_ip_address               | The allocated address of this IP.                                                                                                                                                                                              |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| floating_network_id               | ID of the network in which this IP is allocated.                                                                                                                                                                               |
|                                   |                                                                                                                                                                                                                                |
|                                   | The network ID used during floating IP address assignment is a fixed external network ID. You can use **GET /v2.0/networks?router:external=True** or **neutron net-external-list** to obtain the external network information. |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| port_id                           | ID of the port associated with this IP.                                                                                                                                                                                        |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| router_id                         | ID of the router used as gateway, set when associated with a port.                                                                                                                                                             |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| show                              | Detailed information about resource.                                                                                                                                                                                           |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| tenant_id                         | The tenant owning this floating IP.                                                                                                                                                                                            |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Neutron::FloatingIP
       properties:
         fixed_ip_address: String
         floating_ip_address: String
         floating_network: String
         port_id: String
         value_specs: {...}
