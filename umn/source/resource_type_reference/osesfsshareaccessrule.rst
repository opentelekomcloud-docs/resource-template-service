:original_name: rts_02_0093.html

.. _rts_02_0093:

OSE::SFS::ShareAccessRule
=========================

A resource for creating file sharing access rules

Required Properties
-------------------

+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                               |
+===================================+===========================================================================================================================================+
| share_id                          | Sharing ID of access rules                                                                                                                |
|                                   |                                                                                                                                           |
|                                   | String value expected.                                                                                                                    |
|                                   |                                                                                                                                           |
|                                   | Updates cause replacement.                                                                                                                |
|                                   |                                                                                                                                           |
|                                   | Value range: Valid shared ID, which is strictly checked using the UUID regular expression.                                                |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| allow_access                      | Sharing file system access policy                                                                                                         |
|                                   |                                                                                                                                           |
|                                   | Map value expected.                                                                                                                       |
|                                   |                                                                                                                                           |
|                                   | Map properties:                                                                                                                           |
|                                   |                                                                                                                                           |
|                                   | -  access_level                                                                                                                           |
|                                   |                                                                                                                                           |
|                                   |    Access pPermission level                                                                                                               |
|                                   |                                                                                                                                           |
|                                   |    String value expected.                                                                                                                 |
|                                   |                                                                                                                                           |
|                                   |    Allowed value: ro (read-only), rw (read/write)                                                                                         |
|                                   |                                                                                                                                           |
|                                   | -  access_type                                                                                                                            |
|                                   |                                                                                                                                           |
|                                   |    Specifies the type of a access rule. NFS sharing supports only the cert type.                                                          |
|                                   |                                                                                                                                           |
|                                   |    String value expected.                                                                                                                 |
|                                   |                                                                                                                                           |
|                                   |    .. note::                                                                                                                              |
|                                   |                                                                                                                                           |
|                                   |       If the NFS sharing access rule type is cert, set **access_to** to the VPC ID.                                                       |
|                                   |                                                                                                                                           |
|                                   | -  access_to                                                                                                                              |
|                                   |                                                                                                                                           |
|                                   |    Specifies the value of an access rule. Currently, only the VPC ID is supported.                                                        |
|                                   |                                                                                                                                           |
|                                   |    String value expected.                                                                                                                 |
|                                   |                                                                                                                                           |
|                                   |    Value range: The value cannot be empty. The length of the character string must be verified through the regular UUID check.            |
|                                   |                                                                                                                                           |
|                                   |    .. note::                                                                                                                              |
|                                   |                                                                                                                                           |
|                                   |       Only one VPC ID can be added to a sharing file system. If two or more VPC IDs are added, the sharing file system cannot be mounted. |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OSE::SFS::ShareAccessRule
       properties:
         share_id: String
         allow_access:
           access_level: String
           access_type: String
           access_to: String
