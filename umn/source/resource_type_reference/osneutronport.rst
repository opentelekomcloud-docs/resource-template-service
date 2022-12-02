:original_name: rts_02_0066.html

.. _rts_02_0066:

OS::Neutron::Port
=================

A resource for managing Neutron ports.

A port represents a virtual switch port on a logical network switch. Virtual instances attach their interfaces into ports. The logical port also defines the MAC address and the IP address(es) to be assigned to the interfaces plugged into them. When IP addresses are associated to a port, this also implies the port is associated with a subnet, as the IP address was taken from the allocation pool for a specific subnet.

Required Properties
-------------------

+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                                                                   |
+===================================+===============================================================================================================================================================================================================+
| network                           | Network this port belongs to. If you plan to use current port to assign Floating IP, you should specify fixed_ips with subnet. Note if this changes to a different network update, the port will be replaced. |
|                                   |                                                                                                                                                                                                               |
|                                   | String value expected.                                                                                                                                                                                        |
|                                   |                                                                                                                                                                                                               |
|                                   | Updates cause replacement.                                                                                                                                                                                    |
+-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Optional Properties
-------------------

+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                                                                        |
+===================================+====================================================================================================================================================================================================================+
| admin_state_up                    | The administrative state of this port.                                                                                                                                                                             |
|                                   |                                                                                                                                                                                                                    |
|                                   | Boolean value expected.                                                                                                                                                                                            |
|                                   |                                                                                                                                                                                                                    |
|                                   | Can be updated without replacement.                                                                                                                                                                                |
|                                   |                                                                                                                                                                                                                    |
|                                   | Defaults to "True".                                                                                                                                                                                                |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| allowed_address_pairs             | Additional MAC/IP address pairs allowed to pass through the port.                                                                                                                                                  |
|                                   |                                                                                                                                                                                                                    |
|                                   | List value expected.                                                                                                                                                                                               |
|                                   |                                                                                                                                                                                                                    |
|                                   | Can be updated without replacement.                                                                                                                                                                                |
|                                   |                                                                                                                                                                                                                    |
|                                   | *List contents:*                                                                                                                                                                                                   |
|                                   |                                                                                                                                                                                                                    |
|                                   | -  \*                                                                                                                                                                                                              |
|                                   |                                                                                                                                                                                                                    |
|                                   |    Map value expected.                                                                                                                                                                                             |
|                                   |                                                                                                                                                                                                                    |
|                                   |    Can be updated without replacement.                                                                                                                                                                             |
|                                   |                                                                                                                                                                                                                    |
|                                   |    *Map properties:*                                                                                                                                                                                               |
|                                   |                                                                                                                                                                                                                    |
|                                   |    -  ip_address                                                                                                                                                                                                   |
|                                   |                                                                                                                                                                                                                    |
|                                   |       IP address to allow through this port.                                                                                                                                                                       |
|                                   |                                                                                                                                                                                                                    |
|                                   |       String value expected.                                                                                                                                                                                       |
|                                   |                                                                                                                                                                                                                    |
|                                   |       Can be updated without replacement.                                                                                                                                                                          |
|                                   |                                                                                                                                                                                                                    |
|                                   |    -  mac_address                                                                                                                                                                                                  |
|                                   |                                                                                                                                                                                                                    |
|                                   |       MAC address to allow through this port.                                                                                                                                                                      |
|                                   |                                                                                                                                                                                                                    |
|                                   |       String value expected.                                                                                                                                                                                       |
|                                   |                                                                                                                                                                                                                    |
|                                   |       Can be updated without replacement.                                                                                                                                                                          |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| device_id                         | Device ID of this port.                                                                                                                                                                                            |
|                                   |                                                                                                                                                                                                                    |
|                                   | String value expected.                                                                                                                                                                                             |
|                                   |                                                                                                                                                                                                                    |
|                                   | Can be updated without replacement.                                                                                                                                                                                |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| device_owner                      | Name of the network owning the port. The value is typically network:floatingip or network:router_interface or network:dhcp.                                                                                        |
|                                   |                                                                                                                                                                                                                    |
|                                   | String value expected.                                                                                                                                                                                             |
|                                   |                                                                                                                                                                                                                    |
|                                   | Can be updated without replacement.                                                                                                                                                                                |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| fixed_ips                         | Desired IP addresses for this port.                                                                                                                                                                                |
|                                   |                                                                                                                                                                                                                    |
|                                   | List value expected.                                                                                                                                                                                               |
|                                   |                                                                                                                                                                                                                    |
|                                   | Can be updated without replacement.                                                                                                                                                                                |
|                                   |                                                                                                                                                                                                                    |
|                                   | *List contents:*                                                                                                                                                                                                   |
|                                   |                                                                                                                                                                                                                    |
|                                   | -  \*                                                                                                                                                                                                              |
|                                   |                                                                                                                                                                                                                    |
|                                   |    Map value expected.                                                                                                                                                                                             |
|                                   |                                                                                                                                                                                                                    |
|                                   |    Can be updated without replacement.                                                                                                                                                                             |
|                                   |                                                                                                                                                                                                                    |
|                                   |    *Map properties:*                                                                                                                                                                                               |
|                                   |                                                                                                                                                                                                                    |
|                                   |    -  subnet                                                                                                                                                                                                       |
|                                   |                                                                                                                                                                                                                    |
|                                   |       Subnet in which to allocate the IP address for this port.                                                                                                                                                    |
|                                   |                                                                                                                                                                                                                    |
|                                   |       String value expected.                                                                                                                                                                                       |
|                                   |                                                                                                                                                                                                                    |
|                                   |       Can be updated without replacement.                                                                                                                                                                          |
|                                   |                                                                                                                                                                                                                    |
|                                   |    -  subnet_id                                                                                                                                                                                                    |
|                                   |                                                                                                                                                                                                                    |
|                                   |       String value expected.                                                                                                                                                                                       |
|                                   |                                                                                                                                                                                                                    |
|                                   |       Can be updated without replacement.                                                                                                                                                                          |
|                                   |                                                                                                                                                                                                                    |
|                                   |    -  ip_address                                                                                                                                                                                                   |
|                                   |                                                                                                                                                                                                                    |
|                                   |       IP address desired in the subnet for this port.                                                                                                                                                              |
|                                   |                                                                                                                                                                                                                    |
|                                   |       String value expected.                                                                                                                                                                                       |
|                                   |                                                                                                                                                                                                                    |
|                                   |       Can be updated without replacement.                                                                                                                                                                          |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| mac_address                       | MAC address to give to this port.                                                                                                                                                                                  |
|                                   |                                                                                                                                                                                                                    |
|                                   | String value expected.                                                                                                                                                                                             |
|                                   |                                                                                                                                                                                                                    |
|                                   | Updates cause replacement.                                                                                                                                                                                         |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| name                              | A symbolic name for this port.                                                                                                                                                                                     |
|                                   |                                                                                                                                                                                                                    |
|                                   | String value expected.                                                                                                                                                                                             |
|                                   |                                                                                                                                                                                                                    |
|                                   | Can be updated without replacement.                                                                                                                                                                                |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| network_id                        | Network ID this port belongs to.                                                                                                                                                                                   |
|                                   |                                                                                                                                                                                                                    |
|                                   | String value expected.                                                                                                                                                                                             |
|                                   |                                                                                                                                                                                                                    |
|                                   | Updates cause replacement.                                                                                                                                                                                         |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| security_groups                   | Security group IDs to associate with this port.                                                                                                                                                                    |
|                                   |                                                                                                                                                                                                                    |
|                                   | List value expected.                                                                                                                                                                                               |
|                                   |                                                                                                                                                                                                                    |
|                                   | Can be updated without replacement.                                                                                                                                                                                |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| value_specs                       | Extra parameters to include in the request.                                                                                                                                                                        |
|                                   |                                                                                                                                                                                                                    |
|                                   | Map value expected.                                                                                                                                                                                                |
|                                   |                                                                                                                                                                                                                    |
|                                   | Can be updated without replacement.                                                                                                                                                                                |
|                                   |                                                                                                                                                                                                                    |
|                                   | Defaults to "{}".                                                                                                                                                                                                  |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| replacement_policy                | Policy on how to respond to a stack-update for this resource. REPLACE_ALWAYS will replace the port regardless of any property changes. AUTO will update the existing port for any changed update-allowed property. |
|                                   |                                                                                                                                                                                                                    |
|                                   | String value expected.                                                                                                                                                                                             |
|                                   |                                                                                                                                                                                                                    |
|                                   | Can be updated without replacement.                                                                                                                                                                                |
|                                   |                                                                                                                                                                                                                    |
|                                   | Defaults to "AUTO".                                                                                                                                                                                                |
|                                   |                                                                                                                                                                                                                    |
|                                   | Allowed values: AUTO, REPLACE_ALWAYS                                                                                                                                                                               |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Attributes
----------

+-----------------------+-----------------------------------------------------------------+
| Name                  | Description                                                     |
+=======================+=================================================================+
| admin_state_up        | The administrative state of this port.                          |
+-----------------------+-----------------------------------------------------------------+
| allowed_address_pairs | Additional MAC/IP address pairs allowed to pass through a port. |
+-----------------------+-----------------------------------------------------------------+
| device_id             | Unique identifier for the device.                               |
+-----------------------+-----------------------------------------------------------------+
| device_owner          | Name of the network owning the port.                            |
+-----------------------+-----------------------------------------------------------------+
| fixed_ips             | Fixed IP addresses.                                             |
+-----------------------+-----------------------------------------------------------------+
| mac_address           | MAC address of the port.                                        |
+-----------------------+-----------------------------------------------------------------+
| name                  | Friendly name of the port.                                      |
+-----------------------+-----------------------------------------------------------------+
| network_id            | Unique identifier for the network owning the port.              |
+-----------------------+-----------------------------------------------------------------+
| security_groups       | A list of security groups for the port.                         |
+-----------------------+-----------------------------------------------------------------+
| show                  | Detailed information about resource.                            |
+-----------------------+-----------------------------------------------------------------+
| status                | The status of the port.                                         |
+-----------------------+-----------------------------------------------------------------+
| subnets               | A list of all subnet attributes for the port.                   |
+-----------------------+-----------------------------------------------------------------+
| tenant_id             | Tenant owning the port.                                         |
+-----------------------+-----------------------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Neutron::Port
       properties:
         admin_state_up: Boolean
         allowed_address_pairs: [{"mac_address": String, "ip_address": String}, {"mac_address": String, "ip_address": String}, ...]
         device_id: String
         device_owner: String
         fixed_ips: [{"subnet_id": String, "ip_address": String, "subnet": String}, {"subnet_id": String, "ip_address": String, "subnet": String}, ...]
         mac_address: String
         name: String
         network: String
         network_id: String
         security_groups: [Value, Value, ...]
         value_specs: {...}
         replacement_policy: String
