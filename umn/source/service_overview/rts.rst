:original_name: en-us_topic_0039055697.html

.. _en-us_topic_0039055697:

RTS
===

Resource Template Service (RTS) helps you simplify cloud computing resource management and automate O&M. You can compile a template file and define a collection of cloud computing resources, dependencies between resources, and resource configurations based on the template specifications defined in the RTS service. Then you can automatically create and configure all resources in the template using the orchestration engine to simplify deployment and O&M. The RTS service supports most APIs of the native OpenStack Heat component and templates in the HOT (Heat Orchestration Template) format.


.. figure:: /_static/images/en-us_image_0162983502.png
   :alt: **Figure 1** Resource template

   **Figure 1** Resource template

You can use the RTS service with methods in :ref:`Table 1 <en-us_topic_0039055697__table1162712315426>`.

.. _en-us_topic_0039055697__table1162712315426:

.. table:: **Table 1** Methods of using RTS

   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Method                            | Description                                                                                                                                                                                                   |
   +===================================+===============================================================================================================================================================================================================+
   | Management console                | The management console is a web-based visualized user interface, which is helpful for beginners to learn.                                                                                                     |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Heat client                       | The Heat client is a subproject of OpenStack Client, functioning as a command line client targeted for Heat. You can use this client to access cloud services by running commands.                            |
   |                                   |                                                                                                                                                                                                               |
   |                                   | For details, see :ref:`Heat Client <rts_01_0007>`.                                                                                                                                                            |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | API                               | The API (Application Programming Interface) management mode is based on HTTPS requests. If you need to integrate RTS into a third-party system for secondary development, use APIs to access the RTS service. |
   |                                   |                                                                                                                                                                                                               |
   |                                   | For details, see the *Resource Template Service API Reference*.                                                                                                                                               |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Basic Concepts
--------------

-  Templates

   An RTS template is a user-readable, easy-to-write file that describes how to deploy a set of resources and install the required software. Templates specify the resources to use, the attributes to set, and the parameters required for automatic deployment of a specific application. Template files can be in the YAML or JSON format.

-  Resources

   Resources are objects that are orchestrated by Heat. Currently, multiple cloud services are supported, such as Elastic Cloud Server (ECS), Elastic Volume Service (EVS), Elastic Load Balance (ELB), Cloud Eye, Relational Database Service (RDS), Scalable File Service (SFS), and Virtual Private Cloud (VPC).

-  Stacks

   A stack is a collection of resources, which may include multiple ECSs, networks, and EVS disks. You can use a template to create a stack that includes a set of resources to accommodate the specified application framework or components included in the templates. A stack is actually a running instance of a template, namely, you can deploy, update, and delete a collection of resources by creating, updating, and deleting stacks.

-  Regions and AZs

   A region is a geographic area where resources used by your RTS are located.

   An availability zone (AZ) is the physical location where resources use independent power supplies and networks. AZs are isolated from each other. An AZ can provide an economical, low-latency network connection for other AZs in the same region. A region can have multiple AZs. AZs are physically isolated from each other and communicate with each other over an internal network.

Product Functions
-----------------

-  Stack management: A stack is a cloud application based on a template. Stack management allows you to create, update, and delete stacks and manage resources, events, and templates in the stack.
-  Resource orchestration: You only need to create a resource configuration template in the JSON or YAML format. RTS analyzes resource dependencies based on your template and orchestrates resources on clouds in the sequence of resources, for example, if A depends on B and B depends on C, RTS will create C first, then B, and finally create A.
