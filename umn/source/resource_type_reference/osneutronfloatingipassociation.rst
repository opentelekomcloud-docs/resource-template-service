:original_name: rts_02_0064.html

.. _rts_02_0064:

OS::Neutron::FloatingIPAssociation
==================================

A resource for associating floating IP addresses and ports.

This resource allows associating a floating IP to a port with at least one IP address to associate with this floating IP.

Required Properties
-------------------

+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                             |
+===================================+=========================================================================================================================================+
| floatingip_id                     | ID of the floating IP to associate.                                                                                                     |
|                                   |                                                                                                                                         |
|                                   | String value expected.                                                                                                                  |
|                                   |                                                                                                                                         |
|                                   | Can be updated without replacement.                                                                                                     |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| port_id                           | ID of an existing port with at least one IP address to associate with this floating IP. The port must be associated to a Nova instance. |
|                                   |                                                                                                                                         |
|                                   | String value expected.                                                                                                                  |
|                                   |                                                                                                                                         |
|                                   | Can be updated without replacement.                                                                                                     |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

Optional Properties
-------------------

+-----------------------------------+-------------------------------------------------------+
| Name                              | Description                                           |
+===================================+=======================================================+
| fixed_ip_address                  | IP address to use if the port has multiple addresses. |
|                                   |                                                       |
|                                   | String value expected.                                |
|                                   |                                                       |
|                                   | Can be updated without replacement.                   |
+-----------------------------------+-------------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Neutron::FloatingIPAssociation
       properties:
         fixed_ip_address: String
         floatingip_id: String
         port_id: String
