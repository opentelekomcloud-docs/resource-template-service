:original_name: rts_02_0085.html

.. _rts_02_0085:

OS::Neutron::LBaaS::Listener
============================

A resource for managing LBaaS v2 Listeners.

This resource creates and manages Neutron LBaaS v2 Listeners, which represent a listening endpoint for the vip.

Required Properties
-------------------

+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                  |
+===================================+==============================================================================================================================+
| loadbalancer                      | ID or name of the load balancer with which listener is associated.                                                           |
|                                   |                                                                                                                              |
|                                   | String value expected.                                                                                                       |
|                                   |                                                                                                                              |
|                                   | Updates cause replacement.                                                                                                   |
|                                   |                                                                                                                              |
|                                   | Value must be of type neutron.lbaas.loadbalancer                                                                             |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+
| protocol                          | Protocol on which to listen for the client traffic. It must be the same as the value of OS::Neutron::LBaaS::Pool's protocol. |
|                                   |                                                                                                                              |
|                                   | String value expected.                                                                                                       |
|                                   |                                                                                                                              |
|                                   | Updates cause replacement.                                                                                                   |
|                                   |                                                                                                                              |
|                                   | Allowed values: TCP, HTTP                                                                                                    |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+
| protocol_port                     | TCP or UDP port on which to listen for client traffic.                                                                       |
|                                   |                                                                                                                              |
|                                   | Integer value expected.                                                                                                      |
|                                   |                                                                                                                              |
|                                   | Updates cause replacement.                                                                                                   |
|                                   |                                                                                                                              |
|                                   | The value must be in the range 1 to 65535, include 1 and 65535.                                                              |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+

Optional Properties
-------------------

+-----------------------------------+--------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                            |
+===================================+========================================================================================================+
| admin_state_up                    | The administrative state of this listener.                                                             |
|                                   |                                                                                                        |
|                                   | Boolean value expected.                                                                                |
|                                   |                                                                                                        |
|                                   | Updates are not supported.                                                                             |
|                                   |                                                                                                        |
|                                   | Allowed values: True                                                                                   |
+-----------------------------------+--------------------------------------------------------------------------------------------------------+
| connection_limit                  | The maximum number of connections permitted for this load balancer. Defaults to -1, which is infinite. |
|                                   |                                                                                                        |
|                                   | Integer value expected.                                                                                |
|                                   |                                                                                                        |
|                                   | Can be updated without replacement.                                                                    |
|                                   |                                                                                                        |
|                                   | Defaults to "-1".                                                                                      |
|                                   |                                                                                                        |
|                                   | The value must be in the range -1 to 2147483647, include -1 and 2147483647.                            |
+-----------------------------------+--------------------------------------------------------------------------------------------------------+
| description                       | Description of this listener.                                                                          |
|                                   |                                                                                                        |
|                                   | String value expected.                                                                                 |
|                                   |                                                                                                        |
|                                   | Can be updated without replacement.                                                                    |
|                                   |                                                                                                        |
|                                   | Defaults to " ".                                                                                       |
+-----------------------------------+--------------------------------------------------------------------------------------------------------+
| name                              | Name of this listener.                                                                                 |
|                                   |                                                                                                        |
|                                   | String value expected.                                                                                 |
|                                   |                                                                                                        |
|                                   | Can be updated without replacement.                                                                    |
+-----------------------------------+--------------------------------------------------------------------------------------------------------+
| tenant_id                         | The ID of the tenant who owns the listener.                                                            |
|                                   |                                                                                                        |
|                                   | String value expected.                                                                                 |
|                                   |                                                                                                        |
|                                   | Updates cause replacement.                                                                             |
+-----------------------------------+--------------------------------------------------------------------------------------------------------+

Attributes
----------

=============== =======================================================
Name            Description
=============== =======================================================
default_pool_id ID of the default pool this listener is associated to.
loadbalancers   ID of the load balancer this listener is associated to.
=============== =======================================================

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Neutron::LBaaS::Listener
       properties:
         admin_state_up: Boolean
         connection_limit: Integer
         default_tls_container_ref: String
         description: String
         loadbalancer: String
         name: String
         protocol: String
         protocol_port: Integer
         sni_container_refs: [Value, Value, ...]
         tenant_id: String
