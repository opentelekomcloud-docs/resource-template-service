:original_name: rts_02_0065.html

.. _rts_02_0065:

OS::Neutron::Net
================

A resource for managing Neutron net.

A network is a virtual isolated layer-2 broadcast domain which is typically reserved to the tenant who created it, unless the network has been explicitly configured to be shared.

Optional Properties
-------------------

+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                       |
+===================================+===================================================================================================================================================================+
| admin_state_up                    | A boolean value specifying the administrative status of the network.                                                                                              |
|                                   |                                                                                                                                                                   |
|                                   | Boolean value expected.                                                                                                                                           |
|                                   |                                                                                                                                                                   |
|                                   | Can be updated without replacement.                                                                                                                               |
|                                   |                                                                                                                                                                   |
|                                   | Defaults to "True".                                                                                                                                               |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| dhcp_agent_ids                    | The IDs of the DHCP agent to schedule the network. Note that the default policy setting in Neutron restricts usage of this property to administrative users only. |
|                                   |                                                                                                                                                                   |
|                                   | List value expected.                                                                                                                                              |
|                                   |                                                                                                                                                                   |
|                                   | Can be updated without replacement.                                                                                                                               |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| name                              | A string specifying a symbolic name for the network, which is not required to be unique.                                                                          |
|                                   |                                                                                                                                                                   |
|                                   | String value expected.                                                                                                                                            |
|                                   |                                                                                                                                                                   |
|                                   | Can be updated without replacement.                                                                                                                               |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| shared                            | Whether this network should be shared across all tenants. Note that the default policy setting restricts usage of this attribute to administrative users only.    |
|                                   |                                                                                                                                                                   |
|                                   | Boolean value expected.                                                                                                                                           |
|                                   |                                                                                                                                                                   |
|                                   | Can be updated without replacement.                                                                                                                               |
|                                   |                                                                                                                                                                   |
|                                   | Defaults to "False".                                                                                                                                              |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| tenant_id                         | The ID of the tenant which will own the network. Only administrative users can set the tenant identifier; this cannot be changed using authorization policies.    |
|                                   |                                                                                                                                                                   |
|                                   | String value expected.                                                                                                                                            |
|                                   |                                                                                                                                                                   |
|                                   | Updates cause replacement.                                                                                                                                        |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| value_specs                       | Extra parameters to include in the request. Parameters are often specific to installed hardware or extensions.                                                    |
|                                   |                                                                                                                                                                   |
|                                   | Map value expected.                                                                                                                                               |
|                                   |                                                                                                                                                                   |
|                                   | Can be updated without replacement.                                                                                                                               |
|                                   |                                                                                                                                                                   |
|                                   | Defaults to "{}".                                                                                                                                                 |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Attributes
----------

============== =========================================
Name           Description
============== =========================================
admin_state_up The administrative status of the network.
name           The name of the network.
show           Detailed information about resource.
status         The status of the network.
subnets        Subnets of this network.
tenant_id      The tenant owning this network.
============== =========================================

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Neutron::Net
       properties:
         admin_state_up: Boolean
         dhcp_agent_ids: [Value, Value, ...]
         name: String
         shared: Boolean
         tenant_id: String
         value_specs: {...}
