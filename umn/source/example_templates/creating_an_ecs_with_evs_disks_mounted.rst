:original_name: rts_02_0110.html

.. _rts_02_0110:

Creating an ECS with EVS Disks Mounted
======================================

Application Scenarios
---------------------

This template is used to create an ECS and EVS disk and attach the EVS disk to the ECS.

Example Template
----------------

.. code-block::

   heat_template_version: 2014-10-16
   description: Create an ECS and EVS disk and attach the EVS disk to the ECS.
   resources:
     neutron_port:
       type: OS::Neutron::Port
       properties:
         network: Network Name or ID
     data_volume:
       type: OS::Cinder::Volume
       properties:
         name: EVS Name
         size: Size of Volume
         availability_zone: AZ Name
     nova_server:
       type: OS::Nova::Server
       properties:
         name: ECS Name
         image: Image Name or ID
         flavor: Flavor Name
         key_name: Key Pair
         networks:
           - port: { get_resource: neutron_port }
         availability_zone: AZ Name
     volume_attach:
       type: OS::Cinder::VolumeAttachment
       properties:
         volume_id: { get_resource: data_volume }
         instance_uuid: { get_resource: nova_server }
