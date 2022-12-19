:original_name: rts_02_0092.html

.. _rts_02_0092:

OSE::SFS::Share
===============

A resource for creating file sharing resources

Scalable File Service (SFS) provides users with a fully hosted shared file storage, which can be scaled to PB scale, providing high availability and durability, and providing powerful support for massive data and high-bandwidth applications. SFS applies to various application scenarios, including media processing, file sharing, content management, and web services.

Required Properties
-------------------

+-----------------------------------+------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                          |
+===================================+======================================================================================================+
| share_proto                       | File system sharing protocol                                                                         |
|                                   |                                                                                                      |
|                                   | String value expected.                                                                               |
|                                   |                                                                                                      |
|                                   | Updates cause replacement.                                                                           |
|                                   |                                                                                                      |
|                                   | Allowed value: NFS                                                                                   |
+-----------------------------------+------------------------------------------------------------------------------------------------------+
| size                              | Shared capacity                                                                                      |
|                                   |                                                                                                      |
|                                   | Integer value expected.                                                                              |
|                                   |                                                                                                      |
|                                   | Can be updated without replacement.                                                                  |
|                                   |                                                                                                      |
|                                   | Unit: GB                                                                                             |
|                                   |                                                                                                      |
|                                   | .. note::                                                                                            |
|                                   |                                                                                                      |
|                                   |    The size cannot exceed the quota. Otherwise, the shared storage fails to be created.              |
+-----------------------------------+------------------------------------------------------------------------------------------------------+
| name                              | Name of the sharing storage                                                                          |
|                                   |                                                                                                      |
|                                   | String value expected.                                                                               |
|                                   |                                                                                                      |
|                                   | Can be updated without replacement.                                                                  |
|                                   |                                                                                                      |
|                                   | Value range: 1 to 255. The value can contain only digits, letters, underscores (_), and hyphens (-). |
+-----------------------------------+------------------------------------------------------------------------------------------------------+

Optional Properties
-------------------

+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                          |
+===================================+======================================================================================================================================================+
| description                       | Description for a sharing file system                                                                                                                |
|                                   |                                                                                                                                                      |
|                                   | String value expected.                                                                                                                               |
|                                   |                                                                                                                                                      |
|                                   | Can be updated without replacement.                                                                                                                  |
|                                   |                                                                                                                                                      |
|                                   | Length: 0 to 255                                                                                                                                     |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
| is_public                         | Sharing range                                                                                                                                        |
|                                   |                                                                                                                                                      |
|                                   | Boolean value expected.                                                                                                                              |
|                                   |                                                                                                                                                      |
|                                   | Updates cause replacement.                                                                                                                           |
|                                   |                                                                                                                                                      |
|                                   | The default value is false.                                                                                                                          |
|                                   |                                                                                                                                                      |
|                                   | .. note::                                                                                                                                            |
|                                   |                                                                                                                                                      |
|                                   |    The Boolean value can be true/false, yes/no, or on/off.                                                                                           |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
| availability_zone                 | AZ name                                                                                                                                              |
|                                   |                                                                                                                                                      |
|                                   | String value expected.                                                                                                                               |
|                                   |                                                                                                                                                      |
|                                   | Updates cause replacement.                                                                                                                           |
|                                   |                                                                                                                                                      |
|                                   | Length: 0 to 255.                                                                                                                                    |
|                                   |                                                                                                                                                      |
|                                   | .. note::                                                                                                                                            |
|                                   |                                                                                                                                                      |
|                                   |    If no AZ information is entered, the default AZ is used. If no storage resource is available in the default AZ, creating a sharing storage fails. |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
| metadata                          | Key-value pair of one to more dictionary form                                                                                                        |
|                                   |                                                                                                                                                      |
|                                   | Map value expected.                                                                                                                                  |
|                                   |                                                                                                                                                      |
|                                   | Updates cause replacement.                                                                                                                           |
|                                   |                                                                                                                                                      |
|                                   | The default value is {}.                                                                                                                             |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+

Attributes
----------

=============== =============================================
Name            Description
=============== =============================================
name            Sharing file system name
export_location Sharing file system mount path
metadata        Key-value pair of one to more dictionary form
host            Shared host name
=============== =============================================

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OSE::SFS::Share
       properties:
         share_proto: String
         size: Integer
         name: String
         description: String
         availability_zone: String
         metadata:
           key1: value1
           key2: value2
