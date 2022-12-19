:original_name: rts_02_0088.html

.. _rts_02_0088:

OS::Neutron::LBaaS::PoolMember
==============================

A resource for managing LBaaS v2 Pool Members.

A pool member represents a single backend node.

Required Properties
-------------------

+-----------------------------------+--------------------------------------------------------------------+
| Name                              | Description                                                        |
+===================================+====================================================================+
| address                           | IP address of the pool member on the pool network.                 |
|                                   |                                                                    |
|                                   | String value expected.                                             |
|                                   |                                                                    |
|                                   | Updates cause replacement.                                         |
|                                   |                                                                    |
|                                   | Value must be of type ip_addr                                      |
+-----------------------------------+--------------------------------------------------------------------+
| pool                              | Name or ID of the load balancing pool.                             |
|                                   |                                                                    |
|                                   | String value expected.                                             |
|                                   |                                                                    |
|                                   | Updates cause replacement.                                         |
|                                   |                                                                    |
|                                   | Value must be of type neutron.lbaas.pool                           |
+-----------------------------------+--------------------------------------------------------------------+
| protocol_port                     | Port on which the pool member listens for requests or connections. |
|                                   |                                                                    |
|                                   | Integer value expected.                                            |
|                                   |                                                                    |
|                                   | Updates cause replacement.                                         |
|                                   |                                                                    |
|                                   | The value must be in the range 1 to 65535, include 1 and 65535.    |
+-----------------------------------+--------------------------------------------------------------------+
| subnet                            | Subnet name or ID of this member.                                  |
|                                   |                                                                    |
|                                   | String value expected.                                             |
|                                   |                                                                    |
|                                   | Updates cause replacement.                                         |
|                                   |                                                                    |
|                                   | Value must be of type neutron.subnet                               |
+-----------------------------------+--------------------------------------------------------------------+

Optional Properties
-------------------

+-----------------------------------+-------------------------------------------------------------+
| Name                              | Description                                                 |
+===================================+=============================================================+
| admin_state_up                    | The administrative state of the pool member.                |
|                                   |                                                             |
|                                   | Boolean value expected.                                     |
|                                   |                                                             |
|                                   | Updates are not supported.                                  |
|                                   |                                                             |
|                                   | Allowed values: True                                        |
+-----------------------------------+-------------------------------------------------------------+
| weight                            | Weight of pool member in the pool (default to 1).           |
|                                   |                                                             |
|                                   | Integer value expected.                                     |
|                                   |                                                             |
|                                   | Can be updated without replacement.                         |
|                                   |                                                             |
|                                   | Defaults to "1".                                            |
|                                   |                                                             |
|                                   | The value must be in the range 0 to 256, include 0 and 256. |
+-----------------------------------+-------------------------------------------------------------+

Attributes
----------

======= ====================================================
Name    Description
======= ====================================================
address The IP address of the pool member.
pool_id The ID of the pool to which the pool member belongs.
======= ====================================================

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Neutron::LBaaS::PoolMember
       properties:
         address: String
         admin_state_up: Boolean
         pool: String
         protocol_port: Integer
         subnet: String
         weight: Integer
