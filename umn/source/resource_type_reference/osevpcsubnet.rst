:original_name: rts_02_0091.html

.. _rts_02_0091:

OSE::VPC::Subnet
================

A resource for managing subnets

Required Properties
-------------------

+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                         |
+===================================+=====================================================================================================================================================+
| name                              | Subnet name                                                                                                                                         |
|                                   |                                                                                                                                                     |
|                                   | String value expected.                                                                                                                              |
|                                   |                                                                                                                                                     |
|                                   | Can be updated without replacement.                                                                                                                 |
|                                   |                                                                                                                                                     |
|                                   | Value range: 1 to 64, which can contain digits, letters, underscores (_), and hyphens (-)                                                           |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
| cidr                              | Network segment of a subnet                                                                                                                         |
|                                   |                                                                                                                                                     |
|                                   | String value expected.                                                                                                                              |
|                                   |                                                                                                                                                     |
|                                   | Updates cause replacement.                                                                                                                          |
|                                   |                                                                                                                                                     |
|                                   | Value range: The value must be within the CIDR range of the VPC. The value must be in the CIDR format. The mask length cannot exceed 28 characters. |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
| gateway_ip                        | Gateway of a subnet                                                                                                                                 |
|                                   |                                                                                                                                                     |
|                                   | String value expected.                                                                                                                              |
|                                   |                                                                                                                                                     |
|                                   | Updates cause replacement.                                                                                                                          |
|                                   |                                                                                                                                                     |
|                                   | Value range: IP addresses in the subnet segment. The IP address must be valid.                                                                      |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
| vpc_id                            | ID of the VPC to which the subnet belongs                                                                                                           |
|                                   |                                                                                                                                                     |
|                                   | String value expected.                                                                                                                              |
|                                   |                                                                                                                                                     |
|                                   | Updates cause replacement.                                                                                                                          |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

Optional Properties
-------------------

+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                               |
+===================================+===========================================================================================================================================================+
| dhcp_enable                       | Whether the DHCP function is enabled on a subnet                                                                                                          |
|                                   |                                                                                                                                                           |
|                                   | String value expected.                                                                                                                                    |
|                                   |                                                                                                                                                           |
|                                   | Can be updated without replacement.                                                                                                                       |
|                                   |                                                                                                                                                           |
|                                   | Allowed value: true and false                                                                                                                             |
|                                   |                                                                                                                                                           |
|                                   | Default value: true                                                                                                                                       |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
| primary_dns                       | Subnet DNS server address 1                                                                                                                               |
|                                   |                                                                                                                                                           |
|                                   | String value expected.                                                                                                                                    |
|                                   |                                                                                                                                                           |
|                                   | Can be updated without replacement.                                                                                                                       |
|                                   |                                                                                                                                                           |
|                                   | The value must be a valid IP address.                                                                                                                     |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
| secondary_dns                     | Subnet DNS server address 2                                                                                                                               |
|                                   |                                                                                                                                                           |
|                                   | String value expected.                                                                                                                                    |
|                                   |                                                                                                                                                           |
|                                   | Can be updated without replacement.                                                                                                                       |
|                                   |                                                                                                                                                           |
|                                   | The value must be a valid IP address.                                                                                                                     |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
| dnsList                           | A set of subnet DNS server addresses                                                                                                                      |
|                                   |                                                                                                                                                           |
|                                   | Use this field if you want to use more than two DNS servers. This field is the parent set of subnet DNS server address 1 and subnet DNS server address 2. |
|                                   |                                                                                                                                                           |
|                                   | List value.                                                                                                                                               |
|                                   |                                                                                                                                                           |
|                                   | Can be updated without replacement.                                                                                                                       |
|                                   |                                                                                                                                                           |
|                                   | The value in the set must be a valid IP address.                                                                                                          |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
| availability_zone                 | ID of the AZ where the subnet is located                                                                                                                  |
|                                   |                                                                                                                                                           |
|                                   | String value expected.                                                                                                                                    |
|                                   |                                                                                                                                                           |
|                                   | Updates cause replacement.                                                                                                                                |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OSE::VPC::Subnet
       properties:
         name: String
         cidr: String
         gateway_ip: String
         vpc_id: String
         dhcp_enable: Boolean
         primary_dns: String
         secondary_dns: String
         dnsList: [...]
         availability_zone: String
