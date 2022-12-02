:original_name: rts_02_0046.html

.. _rts_02_0046:

OS::Cinder::Volume
==================

A resource that implements Cinder volumes.

Cinder volume is a storage in the form of block devices. It can be used, for example, for providing storage to instance. Volume supports creation from snapshot, backup or image. Also volume can be created only by size.

Optional Properties
-------------------

+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                               |
+===================================+===========================================================================================================================================+
| availability_zone                 | The availability zone in which the volume will be created.                                                                                |
|                                   |                                                                                                                                           |
|                                   | String value expected.                                                                                                                    |
|                                   |                                                                                                                                           |
|                                   | Updates cause replacement.                                                                                                                |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| backup_id                         | If specified, the volume to create from the backup.                                                                                       |
|                                   |                                                                                                                                           |
|                                   | The parameter **backup_restore** can specify how to restore the backup.                                                                   |
|                                   |                                                                                                                                           |
|                                   | String value expected.                                                                                                                    |
|                                   |                                                                                                                                           |
|                                   | Can be updated without replacement.                                                                                                       |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| backup_restore                    | The method of restoring a backup during the creation of a volume. The value is **heat** or **vbs**. The default value is **heat**.        |
|                                   |                                                                                                                                           |
|                                   | -  When specified as **heat**, the native recovery method is used, which is to restore a volume from backup.                              |
|                                   | -  When specified as **vbs**, after the volume is created, the API of the VBS service is called for recovery.                             |
|                                   |                                                                                                                                           |
|                                   | String value expected.                                                                                                                    |
|                                   |                                                                                                                                           |
|                                   | Updates cause replacement.                                                                                                                |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| description                       | A description of the volume.                                                                                                              |
|                                   |                                                                                                                                           |
|                                   | String value expected.                                                                                                                    |
|                                   |                                                                                                                                           |
|                                   | Can be updated without replacement.                                                                                                       |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| image                             | If specified, the name or ID of the image to create the volume from.                                                                      |
|                                   |                                                                                                                                           |
|                                   | String value expected.                                                                                                                    |
|                                   |                                                                                                                                           |
|                                   | Updates cause replacement.                                                                                                                |
|                                   |                                                                                                                                           |
|                                   | Value must be of type glance.image                                                                                                        |
|                                   |                                                                                                                                           |
|                                   | .. note::                                                                                                                                 |
|                                   |                                                                                                                                           |
|                                   |    **image**, **imageRef**, **snapshot_id** and **source_volid** cannot appear at the same time, otherwise the stack will fail to create. |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| imageRef                          | The ID of the image to create the volume from.                                                                                            |
|                                   |                                                                                                                                           |
|                                   | String value expected.                                                                                                                    |
|                                   |                                                                                                                                           |
|                                   | Updates cause replacement.                                                                                                                |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| metadata                          | Key/value pairs to associate with the volume.                                                                                             |
|                                   |                                                                                                                                           |
|                                   | Map value expected.                                                                                                                       |
|                                   |                                                                                                                                           |
|                                   | Can be updated without replacement.                                                                                                       |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| name                              | A name used to distinguish the volume.                                                                                                    |
|                                   |                                                                                                                                           |
|                                   | String value expected.                                                                                                                    |
|                                   |                                                                                                                                           |
|                                   | Can be updated without replacement.                                                                                                       |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| size                              | The size of the volume in GB. On update only increase in size is supported.                                                               |
|                                   |                                                                                                                                           |
|                                   | -  This parameter is ignored when **backup_id** is specified and **backup_restore** is set to **heat**.                                   |
|                                   | -  This parameter is not required when **source_volid** or **snapshot_id** is specified.                                                  |
|                                   |                                                                                                                                           |
|                                   | Integer value expected.                                                                                                                   |
|                                   |                                                                                                                                           |
|                                   | Can be updated without replacement.                                                                                                       |
|                                   |                                                                                                                                           |
|                                   | The value must be at least 1.                                                                                                             |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| snapshot_id                       | If specified, the snapshot to create the volume from.                                                                                     |
|                                   |                                                                                                                                           |
|                                   | String value expected.                                                                                                                    |
|                                   |                                                                                                                                           |
|                                   | Updates cause replacement.                                                                                                                |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| source_volid                      | If specified, the volume to use as source.                                                                                                |
|                                   |                                                                                                                                           |
|                                   | String value expected.                                                                                                                    |
|                                   |                                                                                                                                           |
|                                   | Updates cause replacement.                                                                                                                |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| volume_type                       | If specified, the type of volume to use, mapping to a specific backend.                                                                   |
|                                   |                                                                                                                                           |
|                                   | String value expected.                                                                                                                    |
|                                   |                                                                                                                                           |
|                                   | Can be updated without replacement.                                                                                                       |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| multiattach                       | Whether allow the volume to be attached more than once.                                                                                   |
|                                   |                                                                                                                                           |
|                                   | Boolean value expected.                                                                                                                   |
|                                   |                                                                                                                                           |
|                                   | Updates cause replacement.                                                                                                                |
|                                   |                                                                                                                                           |
|                                   | Defaults to "False".                                                                                                                      |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+

Attributes
----------

+---------------------+----------------------------------------------------------------------------+
| Name                | Description                                                                |
+=====================+============================================================================+
| availability_zone   | The availability zone in which the volume is located.                      |
+---------------------+----------------------------------------------------------------------------+
| bootable            | Boolean indicating if the volume can be booted or not.                     |
+---------------------+----------------------------------------------------------------------------+
| created_at          | The timestamp indicating volume creation.                                  |
+---------------------+----------------------------------------------------------------------------+
| display_description | Description of the volume.                                                 |
+---------------------+----------------------------------------------------------------------------+
| display_name        | Name of the volume.                                                        |
+---------------------+----------------------------------------------------------------------------+
| metadata            | Key/value pairs associated with the volume.                                |
+---------------------+----------------------------------------------------------------------------+
| metadata_values     | Key/value pairs associated with the volume in raw dict form.               |
+---------------------+----------------------------------------------------------------------------+
| multiattach         | Boolean indicating whether allow the volume to be attached more than once. |
+---------------------+----------------------------------------------------------------------------+
| size                | The size of the volume in GB.                                              |
+---------------------+----------------------------------------------------------------------------+
| snapshot_id         | The snapshot the volume was created from, if any.                          |
+---------------------+----------------------------------------------------------------------------+
| source_volid        | The volume used as source, if any.                                         |
+---------------------+----------------------------------------------------------------------------+
| status              | The current status of the volume.                                          |
+---------------------+----------------------------------------------------------------------------+
| volume_type         | The type of the volume mapping to a backend, if any.                       |
+---------------------+----------------------------------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Cinder::Volume
       properties:
         availability_zone: String
         backup_id: String
         description: String
         image: String
         metadata: {...}
         name: String
         size: Integer
         volume_type: String
