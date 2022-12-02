:original_name: rts_02_0047.html

.. _rts_02_0047:

OS::Cinder::VolumeAttachment
============================

Resource for associating volume to instance.

Resource for associating existing volume to instance. Also, the location where the volume is exposed on the instance can be specified.

.. note::

   Do not attach multiple volumes to one VM at the same time in the template.

Required Properties
-------------------

+-----------------------------------+----------------------------------------------------+
| Name                              | Description                                        |
+===================================+====================================================+
| instance_uuid                     | The ID of the server to which the volume attaches. |
|                                   |                                                    |
|                                   | String value expected.                             |
|                                   |                                                    |
|                                   | Can be updated without replacement.                |
+-----------------------------------+----------------------------------------------------+
| volume_id                         | The ID of the volume to be attached.               |
|                                   |                                                    |
|                                   | String value expected.                             |
|                                   |                                                    |
|                                   | Can be updated without replacement.                |
|                                   |                                                    |
|                                   | Value must be of type cinder.volume                |
+-----------------------------------+----------------------------------------------------+

Optional Properties
-------------------

+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                           |
+===================================+=======================================================================================================================================================================+
| mountpoint                        | The location where the volume is exposed on the instance. This assignment may not be honored and it is advised that the path /dev/disk/by-id/virtio- be used instead. |
|                                   |                                                                                                                                                                       |
|                                   | String value expected.                                                                                                                                                |
|                                   |                                                                                                                                                                       |
|                                   | Can be updated without replacement.                                                                                                                                   |
|                                   |                                                                                                                                                                       |
|                                   | Detailed information about resource.                                                                                                                                  |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Cinder::VolumeAttachment
       properties:
         instance_uuid: String
         mountpoint: String
         volume_id: String
