:original_name: rts_02_0108_0.html

.. _rts_02_0108_0:

Creating an ECS
===============

Application Scenarios
---------------------

This template is used to create an ECS.

Example Template
----------------

.. code-block::

   heat_template_version: 2014-10-16
   description: Create a simple ECS instance.
   resources:
     nova_serer:
       type: OS::Nova::Server
       properties:
         name: ECS Name
         image: Image Name or ID
         flavor: Flavor Name
         key_name: Key Pair
         networks:
           - network: Network Name or ID
         availability_zone: AZ Name
