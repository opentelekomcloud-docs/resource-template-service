:original_name: rts_02_0090.html

.. _rts_02_0090:

OSE::VPC::Vpc
=============

A resource for managing Virtual Private Cloud (VPC) resources

A VPC can be used to build an isolated, user-configured, and managed virtual network environment for your ECSs.

Required Properties
-------------------

+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                                             |
+===================================+=========================================================================================================================================================================================+
| name                              | Name of a VPC                                                                                                                                                                           |
|                                   |                                                                                                                                                                                         |
|                                   | String value expected.                                                                                                                                                                  |
|                                   |                                                                                                                                                                                         |
|                                   | Can be updated without replacement.                                                                                                                                                     |
|                                   |                                                                                                                                                                                         |
|                                   | Value range: The value is a string of 1 to 64 characters, including digits, letters, underscores (_), and hyphens (-).                                                                  |
|                                   |                                                                                                                                                                                         |
|                                   | .. note::                                                                                                                                                                               |
|                                   |                                                                                                                                                                                         |
|                                   |    If the name is not empty, the name of a tenant must be unique.                                                                                                                       |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| cidr                              | Range of available subnets in a VPC                                                                                                                                                     |
|                                   |                                                                                                                                                                                         |
|                                   | String value expected.                                                                                                                                                                  |
|                                   |                                                                                                                                                                                         |
|                                   | Can be updated without replacement.                                                                                                                                                     |
|                                   |                                                                                                                                                                                         |
|                                   | The value can be updated without replacing the template.                                                                                                                                |
|                                   |                                                                                                                                                                                         |
|                                   | Value range: 10.0.0.0/8 to 10.255.255.0/24, 172.16.0.0/12 to 172.31.255.0/24, or 192.168.0.0/16 to 192.168.255.0/24. The value must be in the CIDR format. For example: 192.168.0.0/16. |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Attributes
----------

================= ===================================
Name              Description
================= ===================================
name              Name of a VPC
cidr              Range of available subnets in a VPC
status            Status of a VPC
neutron_router_id UUID of a router
================= ===================================

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OSE::VPC::Vpc
       properties:
         name: String
         cidr: String
