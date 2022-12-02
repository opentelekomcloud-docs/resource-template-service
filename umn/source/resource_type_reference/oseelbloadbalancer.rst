:original_name: rts_02_0079.html

.. _rts_02_0079:

OSE::ELB::LoadBalancer
======================

A resource for ELB Loadbalancer.

.. note::

   In later version, the API for using the LBaaS v2 load balancers will be provided, and you can create native LBaaS v2 load balancers. However, created load balancer cannot be changed to LBaaS v2 load balancers.

Required Properties
-------------------

+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                                                            |
+===================================+========================================================================================================================================================================================================+
| admin_state_up                    | The admin state of the load balancer.                                                                                                                                                                  |
|                                   |                                                                                                                                                                                                        |
|                                   | Boolean value expected.                                                                                                                                                                                |
|                                   |                                                                                                                                                                                                        |
|                                   | Can be updated without replacement.                                                                                                                                                                    |
|                                   |                                                                                                                                                                                                        |
|                                   | Defaults to "True".                                                                                                                                                                                    |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| name                              | The name of the load balancer.                                                                                                                                                                         |
|                                   |                                                                                                                                                                                                        |
|                                   | String value expected.                                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                        |
|                                   | Can be updated without replacement.                                                                                                                                                                    |
|                                   |                                                                                                                                                                                                        |
|                                   | It is allowed to start with **numbers**, **letters**, \_, and **-** characters. It is allowed to include **numbers**, **letters**, \_, and **-** characters, and the string length is **1** to **64**. |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| type                              | The type of the load balancer.                                                                                                                                                                         |
|                                   |                                                                                                                                                                                                        |
|                                   | String value expected.                                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                        |
|                                   | Updates cause replacement.                                                                                                                                                                             |
|                                   |                                                                                                                                                                                                        |
|                                   | Allowed values: External, Internal                                                                                                                                                                     |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| vpc_id                            | The ID of vpc.                                                                                                                                                                                         |
|                                   |                                                                                                                                                                                                        |
|                                   | String value expected.                                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                        |
|                                   | Updates cause replacement.                                                                                                                                                                             |
|                                   |                                                                                                                                                                                                        |
|                                   | .. note::                                                                                                                                                                                              |
|                                   |                                                                                                                                                                                                        |
|                                   |    You must specify the VPC ID when using the RTS to perform operations on ELB.                                                                                                                        |
|                                   |                                                                                                                                                                                                        |
|                                   |    -  Only one VPC is supported for each tenant.                                                                                                                                                       |
|                                   |    -  You must add the VPC ID in the Heat template. (You can query the VPC using the API.)                                                                                                             |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Optional Properties
-------------------

+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                                                             |
+===================================+=========================================================================================================================================================================================================+
| az                                | The ID or name of the availability zone.                                                                                                                                                                |
|                                   |                                                                                                                                                                                                         |
|                                   | String value expected.                                                                                                                                                                                  |
|                                   |                                                                                                                                                                                                         |
|                                   | Updates cause replacement.                                                                                                                                                                              |
|                                   |                                                                                                                                                                                                         |
|                                   | .. note::                                                                                                                                                                                               |
|                                   |                                                                                                                                                                                                         |
|                                   |    -  The AZ attribute is mandatory, and you need to specify it.                                                                                                                                        |
|                                   |    -  If the AZ attribute is not specified, calls are made to the Nova API to randomly select an AZ.                                                                                                    |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| bandwidth                         | The bandwidth of the load balancer, in Mbit/s.                                                                                                                                                          |
|                                   |                                                                                                                                                                                                         |
|                                   | Integer value expected.                                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                         |
|                                   | Can be updated without replacement.                                                                                                                                                                     |
|                                   |                                                                                                                                                                                                         |
|                                   | Allowed values: from 1 to 300, include 1 and 300                                                                                                                                                        |
|                                   |                                                                                                                                                                                                         |
|                                   | .. note::                                                                                                                                                                                               |
|                                   |                                                                                                                                                                                                         |
|                                   |    The default bandwidth size value of an ELB listener is 300, and you can use only the default value.                                                                                                  |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| description                       | The description of the load balancer.                                                                                                                                                                   |
|                                   |                                                                                                                                                                                                         |
|                                   | String value expected.                                                                                                                                                                                  |
|                                   |                                                                                                                                                                                                         |
|                                   | Can be updated without replacement.                                                                                                                                                                     |
|                                   |                                                                                                                                                                                                         |
|                                   | It is allowed to start with **numbers**, **letters**, \_, and **-** characters. It is allowed to include **numbers**, **letters**, \_, and **-** characters, and the string length is **1** to **128**. |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| security_group                    | The ID of the security group.                                                                                                                                                                           |
|                                   |                                                                                                                                                                                                         |
|                                   | String value expected.                                                                                                                                                                                  |
|                                   |                                                                                                                                                                                                         |
|                                   | Updates cause replacement.                                                                                                                                                                              |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| vip_subnet_id                     | The ID of the network on which to allocate the VIP.                                                                                                                                                     |
|                                   |                                                                                                                                                                                                         |
|                                   | String value expected.                                                                                                                                                                                  |
|                                   |                                                                                                                                                                                                         |
|                                   | Updates cause replacement.                                                                                                                                                                              |
|                                   |                                                                                                                                                                                                         |
|                                   | Value must be of type neutron.network                                                                                                                                                                   |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Attributes
----------

============= =====================================
Name          Description
============= =====================================
status        The status of the load balancer.
vip_address   The VIP address of the load balancer.
vip_subnet_id The VIP subnet of the load balancer.
============= =====================================

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OSE::ELB::LoadBalancer
       properties:
         admin_state_up: Boolean
         az: String
         bandwidth: Integer
         description: String
         name: String
         security_group: String
         type: String
         vip_subnet_id: String
         vpc_id: String
