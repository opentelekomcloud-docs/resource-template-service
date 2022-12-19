:original_name: rts_02_0087.html

.. _rts_02_0087:

OS::Neutron::LBaaS::Pool
========================

The resource is not allowed to be updated.

A resource for managing LBaaS v2 Pools.

This resources manages Neutron-LBaaS v2 Pools, which represent a group of nodes. Pools define the subnet where nodes reside, balancing algorithm, and the nodes themselves.

Required Properties
-------------------

+-----------------------------------+----------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                        |
+===================================+====================================================================================================+
| lb_algorithm                      | The algorithm used to distribute load between the members of the pool.                             |
|                                   |                                                                                                    |
|                                   | String value expected.                                                                             |
|                                   |                                                                                                    |
|                                   | Can be updated without replacement.                                                                |
|                                   |                                                                                                    |
|                                   | Allowed values: ROUND_ROBIN, LEAST_CONNECTIONS, SOURCE_IP                                          |
+-----------------------------------+----------------------------------------------------------------------------------------------------+
| listener                          | Listener name or ID to be associated with this pool.                                               |
|                                   |                                                                                                    |
|                                   | String value expected.                                                                             |
|                                   |                                                                                                    |
|                                   | Updates cause replacement.                                                                         |
|                                   |                                                                                                    |
|                                   | Value must be of type neutron.lbaas.listener                                                       |
+-----------------------------------+----------------------------------------------------------------------------------------------------+
| protocol                          | Protocol of the pool. It must be the same as the value of OS::Neutron::LBaaS::Listener's protocol. |
|                                   |                                                                                                    |
|                                   | String value expected.                                                                             |
|                                   |                                                                                                    |
|                                   | Can not be updated.                                                                                |
|                                   |                                                                                                    |
|                                   | Allowed values: TCP, HTTP                                                                          |
+-----------------------------------+----------------------------------------------------------------------------------------------------+

Optional Properties
-------------------

+-----------------------------------+--------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                  |
+===================================+==============================================================================================================+
| admin_state_up                    | The administrative state of this pool.                                                                       |
|                                   |                                                                                                              |
|                                   | Boolean value expected.                                                                                      |
|                                   |                                                                                                              |
|                                   | Updates are not supported.                                                                                   |
|                                   |                                                                                                              |
|                                   | Allowed values: True                                                                                         |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------+
| description                       | Description of this pool.                                                                                    |
|                                   |                                                                                                              |
|                                   | String value expected.                                                                                       |
|                                   |                                                                                                              |
|                                   | Can be updated without replacement.                                                                          |
|                                   |                                                                                                              |
|                                   | Defaults to " ".                                                                                             |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------+
| name                              | Name of this pool.                                                                                           |
|                                   |                                                                                                              |
|                                   | String value expected.                                                                                       |
|                                   |                                                                                                              |
|                                   | Can be updated without replacement.                                                                          |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------+
| session_persistence               | Configuration of session persistence.                                                                        |
|                                   |                                                                                                              |
|                                   | Map value expected.                                                                                          |
|                                   |                                                                                                              |
|                                   | Updates cause replacement.                                                                                   |
|                                   |                                                                                                              |
|                                   | *Map properties:*                                                                                            |
|                                   |                                                                                                              |
|                                   | -  cookie_name                                                                                               |
|                                   |                                                                                                              |
|                                   |    Name of the cookie, required if type is APP_COOKIE. It only support cookie_name in the 'APP_COOKIE' type. |
|                                   |                                                                                                              |
|                                   |    String value expected.                                                                                    |
|                                   |                                                                                                              |
|                                   |    Updates cause replacement.                                                                                |
|                                   |                                                                                                              |
|                                   | -  type                                                                                                      |
|                                   |                                                                                                              |
|                                   |    Method of implementation of session persistence feature.                                                  |
|                                   |                                                                                                              |
|                                   |    String value expected.                                                                                    |
|                                   |                                                                                                              |
|                                   |    Updates cause replacement.                                                                                |
|                                   |                                                                                                              |
|                                   |    Allowed values: SOURCE_IP, HTTP_COOKIE, APP_COOKIE                                                        |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------+

Attributes
----------

================ ===================================================
Name             Description
================ ===================================================
healthmonitor_id ID of the health monitor associated with this pool.
listeners        Listener associated with this pool.
members          Members associated with this pool.
================ ===================================================

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Neutron::LBaaS::Pool
       properties:
         admin_state_up: Boolean
         description: String
         lb_algorithm: String
         listener: String
         name: String
         protocol: String
         session_persistence: {"type": String, "cookie_name": String}
