:original_name: rts_02_0086.html

.. _rts_02_0086:

OS::Neutron::LBaaS::LoadBalancer
================================

A resource for creating LBaaS v2 Load Balancers.

This resource creates and manages Neutron LBaaS v2 Load Balancers, which allows traffic to be directed between servers.

Required Properties
-------------------

+-----------------------------------+--------------------------------------------------------------------+
| Name                              | Description                                                        |
+===================================+====================================================================+
| vip_subnet                        | The name or ID of the subnet on which to allocate the VIP address. |
|                                   |                                                                    |
|                                   | String value expected.                                             |
|                                   |                                                                    |
|                                   | Updates cause replacement.                                         |
|                                   |                                                                    |
|                                   | Value must be of type neutron.subnet                               |
+-----------------------------------+--------------------------------------------------------------------+

Optional Properties
-------------------

+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                              |
+===================================+==========================================================================================================================+
| admin_state_up                    | The administrative state of this Load Balancer.                                                                          |
|                                   |                                                                                                                          |
|                                   | Boolean value expected.                                                                                                  |
|                                   |                                                                                                                          |
|                                   | Updates are not supported.                                                                                               |
|                                   |                                                                                                                          |
|                                   | Allowed values: True                                                                                                     |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------+
| description                       | Description of this Load Balancer.                                                                                       |
|                                   |                                                                                                                          |
|                                   | String value expected.                                                                                                   |
|                                   |                                                                                                                          |
|                                   | Can be updated without replacement.                                                                                      |
|                                   |                                                                                                                          |
|                                   | Defaults to " ".                                                                                                         |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------+
| name                              | Name of this Load Balancer.                                                                                              |
|                                   |                                                                                                                          |
|                                   | String value expected.                                                                                                   |
|                                   |                                                                                                                          |
|                                   | Can be updated without replacement.                                                                                      |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------+
| provider                          | Provider for this Load Balancer.                                                                                         |
|                                   |                                                                                                                          |
|                                   | String value expected.                                                                                                   |
|                                   |                                                                                                                          |
|                                   | Updates are not supported.                                                                                               |
|                                   |                                                                                                                          |
|                                   | Allowed values: vlb                                                                                                      |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------+
| tenant_id                         | The ID of the tenant who owns the Load Balancer. Only administrative users can specify a tenant ID other than their own. |
|                                   |                                                                                                                          |
|                                   | String value expected.                                                                                                   |
|                                   |                                                                                                                          |
|                                   | Updates cause replacement.                                                                                               |
|                                   |                                                                                                                          |
|                                   | Value must be of type keystone.project                                                                                   |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------+
| vip_address                       | IP address for the VIP.                                                                                                  |
|                                   |                                                                                                                          |
|                                   | String value expected.                                                                                                   |
|                                   |                                                                                                                          |
|                                   | Updates cause replacement.                                                                                               |
|                                   |                                                                                                                          |
|                                   | Value must be of type ip_addr                                                                                            |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------+

Attributes
----------

============= ====================================
Name          Description
============= ====================================
vip_address   The VIP address of the LoadBalancer.
vip_port_id   The VIP port of the LoadBalancer.
vip_subnet_id The VIP subnet of the LoadBalancer.
============= ====================================

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Neutron::LBaaS::LoadBalancer
       properties:
         admin_state_up: Boolean
         description: String
         name: String
         provider: String
         tenant_id: String
         vip_address: String
         vip_subnet: String
