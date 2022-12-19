:original_name: rts_02_0007.html

.. _rts_02_0007:

Creating Resources Using a Template (Using the Console)
=======================================================

With RTS, you can orchestrate a stack that contains a collection of resources using a template and maintain these resources by managing stacks on the console. This section describes how to orchestrate a complex application with RTS by creating an example Elastic Cloud Server (ECS). After the operations in this section are complete, you can view a created ECS on the ECS console.

The required operations are as follows:

#. :ref:`Create a Key Pair <rts_02_0007__section14934257541>`: Create a key pair for logging in to an ECS through SSH. If you already have a key pair, skip this step.
#. :ref:`Create an ECS Stack <rts_02_0007__section955894365412>`: Compile a template for creating an ECS.

.. _rts_02_0007__section14934257541:

Create a Key Pair
-----------------

To create an ECS using RTS, you need to create a key pair first for identity authentication during SSH login.

.. note::

   If you already have a key pair, skip this step.

#. Log in to the management console.

#. Click |image1| in the upper left corner to select the desired region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

#. In the navigation tree on the left, choose **Key Pairs** and click **Create Key Pair**.

#. Enter a key pair name and click **OK**.

   A key pair name consists of two parts: **KeyPair** and four random digits. You can enter an easy-to-remember name, for example, **KeyPair-xxxx_ecs**.

#. Manually or automatically download the private key file. The file name is a specified key pair name with a suffix of .pem. Securely store the private key file. In the displayed dialog box, click **OK**.

   .. important::

      This is the only opportunity for you to save the private key file. Keep it secure. When creating an ECS stack, provide the name of your desired key pair. Each time you log in to the ECS using SSH, provide the private key.

.. _rts_02_0007__section955894365412:

Create an ECS Stack
-------------------

#. Log in to the management console.

#. Click |image2| in the upper left corner to select the desired region and project.

#. Under **Management & Deployment**, click **Resource Template Service**.

#. Click **Create Stack**.


   .. figure:: /_static/images/en-us_image_0162741682.png
      :alt: **Figure 1** Create Stack

      **Figure 1** Create Stack

#. Confirm the desired region and project.

   If the region or project is incorrect, click the drop-down list for correction.

#. Select **Manually specify** to enter the template content.

   The details of an example ECS template are as follows:

   .. code-block::

      heat_template_version: 2014-10-16

      description: Create a simple ECS instance.

      parameters:
        name:
          type: string
          label: ECS Name
          description: Specifies the ECS name.
        image:
          type: string
          label: Image Name or ID
          description: Specifies the image used for creating ECS. The value can be the name or ID of the image.
          constraints:
            - custom_constraint: glance.image
        key_name:
          type: string
          label: Key Pair
          description: Specifies the key pair used for creating ECS. The value can be the name of the key pair.
          constraints:
            - custom_constraint: nova.keypair
        flavor:
          type: string
          label: Flavor Name
          description: Specifies the flavor used for creating ECS.
          constraints:
            - custom_constraint: nova.flavor
        networks:
          type: string
          label: Network Name or ID
          description: Specifies the network used for creating ECS. The value can be the name or ID of the network.
          constraints:
            - custom_constraint: neutron.network
        availability_zone:
          type: string
          label: AZ Name
          description: Specifies the name of the AZ to which the ECS belong.

      parameter_groups:
        - label: ECS
          parameters:
            - name
            - image
            - key_name
            - flavor
            - networks
            - availability_zone

      resources:
        nova_serer:
          type: OS::Nova::Server
          properties:
            name: { get_param: name }
            image: { get_param: image }
            flavor: { get_param: flavor }
            key_name: { get_param: key_name }
            networks:
              - network: { get_param: networks }
            availability_zone: { get_param: availability_zone }

   This YAML file contains five first-level fields:

   -  **heat_template_version**: indicates the template version.
   -  **description**: provides a description for the template.
   -  **parameters**: defines template parameters. In this example template, this field defines the ECS name, image name or ID, key pair, specifications, VPC, and AZ. All of these can be used by function **get_param** in **resources**.
   -  **parameter_groups**: indicates the parameter groups and the parameter sequence.
   -  **resources**: defines resources to be created by the template. In this example, the resources is an ECS. **type** defines the resource type. Function **get_param** in **properties** directly uses parameters defined in **parameters**.

   .. note::

      For more information about resource templates, see :ref:`Template Structure <rts_02_0009>`.

   Enter and verify template content and click **Next**.

#. Specify details. Enter the stack name, ECS name, image, key pair, specifications, VPC, and AZ. Click **Next**.


   .. figure:: /_static/images/en-us_image_0129631902.png
      :alt: **Figure 2** Specifying details

      **Figure 2** Specifying details

#. Confirm the information and create **Next**.

   It takes some time to complete the creation. After the stack is created, click **Stack Management** in the left pane to view the stack status. You can also access the ECS console to view the created ECS.

For more information about stack management and templates, see :ref:`Stack Management <rts_02_0017>` and :ref:`Example Templates <rts_02_0037>`.

.. |image1| image:: /_static/images/en-us_image_0210485079.png
.. |image2| image:: /_static/images/en-us_image_0210485079.png
