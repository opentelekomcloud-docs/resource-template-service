:original_name: rts_02_0002.html

.. _rts_02_0002:

Creating Resources Using a Template (Using the Heat Client)
===========================================================

After the Heat client is installed and configured, you can use this client to create an ECS.

The required operations are as follows:

#. :ref:`Compile a Template <rts_02_0002__section19689531174816>`: A template is a collection of resources and a blueprint for resource orchestration. Before creating a resource, compile a template according to syntax requirements.
#. :ref:`Create Resources <rts_02_0002__section13942639134816>`: To create an ECS, run commands on the Heat client to create an ECS stack.
#. :ref:`View Resources <rts_02_0002__section147919492487>`: To view resources, run commands on the Heat client to view all resource stacks and details of a specified resource stack.
#. :ref:`Delete Resources <rts_02_0002__section15014577483>`: To delete resources, run commands on the Heat client to delete the resource stack if the stack is no longer used.

.. _rts_02_0002__section19689531174816:

Compile a Template
------------------

Create a template and name it **server_instance.yaml**. The template content is as follows:

.. code-block::

   heat_template_version: 2014-10-16
   description: Create a simple ECS instance.
   parameters:
     name:
       type: string
       description: Specifies the ECS name.
     image:
       type: string
       description: Specifies the image used for creating ECS. The value can be the name or ID of the image.
     flavor:
       type: string
       description: Specifies the flavor used for creating ECS.
     key:
       type: string
       description: Specifies the key pair used for creating ECS. The value can be the name of the key pair.
     network_id:
       type: string
       description: Specifies the network used for creating ECS. The value can be the name or ID of the network.
     availability_zone:
       type: string
       description: Specifies the name of the AZ to which the ECS belong.

   resources:
     nova_serer:
       type: OS::Nova::Server
       properties:
         name: { get_param: name }
         image: { get_param: image }
         flavor: { get_param: flavor }
         key_name: { get_param: key }
         networks:
           - network: { get_param: network_id }
         availability_zone: { get_param: availability_zone }

This YAML file contains four first-level fields:

-  **heat_template_version**: indicates the template version. This field is mandatory.
-  **description**: provides a description for the template. This field is optional.
-  **parameters**: defines template parameters. In this example template, this field defines the ECS name, image name or ID, key pair, specifications, VPC, and AZ. All of these can be used by function **get_param** in **resources**.
-  **resources**: defines resources to be created by the template. In this example, the resources is an ECS.
-  **type**: defines the resource. You need to enter parameters in **properties** when creating a resource. For details, see :ref:`Create Resources <rts_02_0002__section13942639134816>`.

.. _rts_02_0002__section13942639134816:

Create Resources
----------------

Run the following command on the Heat client to create a resource stack:

**heat stack-create -f** *server_instance.yaml* **-P 'name=**\ *ecs_name*\ **;image=**\ *Redhat-6.9*\ **;flavor=**\ *m1.medium*\ **;key=**\ *keypair_name*\ **;network_id=**\ *external-network3*\ **;availability_zone=**\ *az_name*\ **'** *ecsStack*

In this command,

-  *server_instance.yaml*: indicates the name of the template file.
-  *ecsStack*: indicates the name of the resource stack to be created. The value can be user-defined.
-  Other variables are values of the parameters defined in the template.

.. _rts_02_0002__section147919492487:

View Resources
--------------

Perform the following operations to check whether the resource stack is created:

-  Run the following command to query all stacks and check whether the new stack is included:

   **heat stack-list**

-  (Optional) Run the following command to view details of the new stack:

   **heat stack-show** *ecsStack*

.. _rts_02_0002__section15014577483:

Delete Resources
----------------

If you do not need a resource stack any longer, run the following command to delete it:

**heat stack-delete** *ecsStack*
