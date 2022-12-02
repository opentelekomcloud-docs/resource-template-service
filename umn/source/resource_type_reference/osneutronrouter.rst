:original_name: rts_02_0067.html

.. _rts_02_0067:

OS::Neutron::Router
===================

A resource that implements Neutron router.

Router is a physical or virtual network device that passes network traffic between different networks.

Optional Properties
-------------------

+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                                                    |
+===================================+================================================================================================================================================================================================+
| admin_state_up                    | The administrative state of the router.                                                                                                                                                        |
|                                   |                                                                                                                                                                                                |
|                                   | Boolean value expected.                                                                                                                                                                        |
|                                   |                                                                                                                                                                                                |
|                                   | Can be updated without replacement.                                                                                                                                                            |
|                                   |                                                                                                                                                                                                |
|                                   | Defaults to "True".                                                                                                                                                                            |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| external_gateway_info             | External network gateway configuration for a router.                                                                                                                                           |
|                                   |                                                                                                                                                                                                |
|                                   | You can use **GET /v2.0/networks?router:external=True** or **neutron net-external-list** to query the network information.                                                                     |
|                                   |                                                                                                                                                                                                |
|                                   | Map value expected.                                                                                                                                                                            |
|                                   |                                                                                                                                                                                                |
|                                   | Can be updated without replacement.                                                                                                                                                            |
|                                   |                                                                                                                                                                                                |
|                                   | *Map properties:*                                                                                                                                                                              |
|                                   |                                                                                                                                                                                                |
|                                   | -  enable_snat                                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                |
|                                   |    Enables Source NAT on the router gateway. NOTE: The default policy setting in Neutron restricts usage of this property to administrative users only.                                        |
|                                   |                                                                                                                                                                                                |
|                                   |    Boolean value expected.                                                                                                                                                                     |
|                                   |                                                                                                                                                                                                |
|                                   |    Can be updated without replacement.                                                                                                                                                         |
|                                   |                                                                                                                                                                                                |
|                                   | -  network                                                                                                                                                                                     |
|                                   |                                                                                                                                                                                                |
|                                   |    ID or name of the external network for the gateway.                                                                                                                                         |
|                                   |                                                                                                                                                                                                |
|                                   |    String value expected.                                                                                                                                                                      |
|                                   |                                                                                                                                                                                                |
|                                   |    Can be updated without replacement.                                                                                                                                                         |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| l3_agent_ids                      | ID list of the L3 agent. User can specify multi-agents for highly available router. NOTE: The default policy setting in Neutron restricts usage of this property to administrative users only. |
|                                   |                                                                                                                                                                                                |
|                                   | String value expected.                                                                                                                                                                         |
|                                   |                                                                                                                                                                                                |
|                                   | Can be updated without replacement.                                                                                                                                                            |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| name                              | The name of the router.                                                                                                                                                                        |
|                                   |                                                                                                                                                                                                |
|                                   | String value expected.                                                                                                                                                                         |
|                                   |                                                                                                                                                                                                |
|                                   | Can be updated without replacement.                                                                                                                                                            |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| value_specs                       | Extra parameters to include in the creation request.                                                                                                                                           |
|                                   |                                                                                                                                                                                                |
|                                   | Map value expected.                                                                                                                                                                            |
|                                   |                                                                                                                                                                                                |
|                                   | Can be updated without replacement.                                                                                                                                                            |
|                                   |                                                                                                                                                                                                |
|                                   | Defaults to "{}".                                                                                                                                                                              |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Attributes
----------

===================== ====================================
Name                  Description
===================== ====================================
admin_state_up        Administrative state of the router.
external_gateway_info Gateway network for the router.
name                  Friendly name of the router.
show                  Detailed information about resource.
status                The status of the router.
tenant_id             Tenant owning the router.
===================== ====================================

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Neutron::Router
       properties:
         admin_state_up: Boolean
         external_gateway_info: {"network": String, "enable_snat": Boolean}
         l3_agent_ids: String
         name: String
         value_specs: {...}
