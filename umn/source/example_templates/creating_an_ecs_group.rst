:original_name: rts_02_0111.html

.. _rts_02_0111:

Creating an ECS Group
=====================

Application Scenarios
---------------------

This template is used to create a group of ECSs.

Example Template
----------------

.. code-block::

   heat_template_version: 2014-10-16
   description: Create a group of ECSs.
   resources:
     instance_group:
       type: OS::Heat::ResourceGroup
       properties:
         count: Number of resource
         resource_def:
           type: OS::Nova::Server
           properties:
             name: aaaa-%index%
             image: Image Name or ID
             flavor: Flavor Name
             key_name: Key Pair
             networks:
               - network: Network Name or ID
             availability_zone: AZ Name
