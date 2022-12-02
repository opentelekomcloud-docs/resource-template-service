:original_name: rts_03_0021.html

.. _rts_03_0021:

Creating a Stack
================

Function
--------

This API is used to create a stack. Heat verifies a request body and parses the template. After that, Heat invokes the API of the target component based on resource dependencies to create a resource.

URI
---

POST /v1/{project_id}/stacks

For details about the parameters, see :ref:`Table 1 <rts_03_0021__table1759528275>`.

.. _rts_03_0021__table1759528275:

.. table:: **Table 1** Parameter description

   ========== ====== ========= =========================
   Parameter  Type   Mandatory Description
   ========== ====== ========= =========================
   project_id String Yes       Specifies the project ID.
   ========== ====== ========= =========================

Request Parameter
-----------------

+------------------+-------------+-------------+-------------+----------------------------------------------------------------------------------------------------------------------------+
| Parameter        | In          | Type        | Mandatory   | Description                                                                                                                |
+==================+=============+=============+=============+============================================================================================================================+
| stack_name       | body        | String      | Yes         | Specifies the stack name.                                                                                                  |
|                  |             |             |             |                                                                                                                            |
|                  |             |             |             | -  The value can contain only uppercase letters, lowercase letters, digits, hyphens (-), periods (.), and underscores (_). |
|                  |             |             |             | -  The value must start with an uppercase letter or a lowercase letter.                                                    |
|                  |             |             |             | -  The value can contain 1 to 255 characters.                                                                              |
+------------------+-------------+-------------+-------------+----------------------------------------------------------------------------------------------------------------------------+
| template         | body        | Json        | Yes         | Specifies the template. The template uses the YAML syntax for content orchestration.                                       |
+------------------+-------------+-------------+-------------+----------------------------------------------------------------------------------------------------------------------------+
| template_url     | body        | String      | No          | Specifies the template URL. You cannot select a template using the URL temporarily.                                        |
+------------------+-------------+-------------+-------------+----------------------------------------------------------------------------------------------------------------------------+
| environment      | body        | Json        | No          | Specifies the environment information for creating a stack.                                                                |
+------------------+-------------+-------------+-------------+----------------------------------------------------------------------------------------------------------------------------+
| files            | body        | Json        | No          | Specifies the files referenced in the environment.                                                                         |
+------------------+-------------+-------------+-------------+----------------------------------------------------------------------------------------------------------------------------+
| parameters       | body        | Json        | No          | Specifies parameter information of the stack.                                                                              |
+------------------+-------------+-------------+-------------+----------------------------------------------------------------------------------------------------------------------------+
| timeout_mins     | body        | Int         | No          | Specifies the timeout duration.                                                                                            |
+------------------+-------------+-------------+-------------+----------------------------------------------------------------------------------------------------------------------------+
| disable_rollback | body        | Boolean     | No          | Specifies whether to perform a rollback when stack creation fails.                                                         |
+------------------+-------------+-------------+-------------+----------------------------------------------------------------------------------------------------------------------------+

**environment** structure information

+---------------------+------+------+-----------+----------------------------------------------------+
| Parameter           | In   | Type | Mandatory | Description                                        |
+=====================+======+======+===========+====================================================+
| parameters          | body | Json | No        | Specifies the parameters and their values.         |
+---------------------+------+------+-----------+----------------------------------------------------+
| parameters_defaults | body | Json | No        | Specifies the parameters and their default values. |
+---------------------+------+------+-----------+----------------------------------------------------+
| resource_registry   | body | Json | No        | Specifies the custom resource information.         |
+---------------------+------+------+-----------+----------------------------------------------------+

Response Parameter
------------------

========= ==== ==== ===========================
Parameter In   Type Description
========= ==== ==== ===========================
stack     body Dict Specifies the stack object.
========= ==== ==== ===========================

**stack** structure information

========= ==== =========== =============================
Parameter In   Type        Description
========= ==== =========== =============================
id        body String      Specifies the stack UUID.
links     body List <dict> Specifies the stack URL list.
========= ==== =========== =============================

Request Example
---------------

.. code-block:: text

   POST /v1/95d02433133a4c0a87ba6967474a2ad3/stacks
   {
       "files": {},
       "disable_rollback": true,
       "parameters": {
           "flavor": "m1.heat"
       },
       "environment": {
           "parameters": {
               "flavor": "m1.heat"
           },
           "parameter_defaults": {
               "flavor": "m1.heat"
           },
           "resource_registry": {
               "OS::Networking::FloatingIP": "OS::Nova::FloatingIP"
           }
       },
       "stack_name": "teststack",
       "template": {
           "heat_template_version": "2013-05-23",
           "description": "Simple template to test heat commands",
           "parameters": {
               "flavor": {
                   "default": "m1.tiny",
                   "type": "string"
               }
           },
           "resources": {
               "hello_world": {
                   "type": "OS::Nova::Server",
                   "properties": {
                       "key_name": "heat_key",
                       "flavor": {
                           "get_param": "flavor"
                       },
                       "image": "40be8d1a-3eb9-40de-8abd-43237517384f",
                       "user_data": "#!/bin/bash -xv\necho \"hello world\" &gt; /root/hello-world.txt\n"
                   }
               }
           }
       },
       "timeout_mins": 60
   }

Response Example
----------------

.. code-block::

   {
       "stack": {
           "id": "c89c4bb3-96cb-4a55-aafa-076a7939a306",
           "links": [
               {
                   "href":  "http://x.x.x.x:8004/v1/95d02433133a4c0a87ba6967474a2ad3/stacks/HeatStack/c89c4bb3-96cb-4a55-aafa-076a7939a306",
                   "rel": "self"
               }
           ]
       }
   }

Return Code
-----------

.. table:: **Table 2** Normal return code

   =========== ======= ===================================================
   Return Code Type    Description
   =========== ======= ===================================================
   201         Created The resource has been created and is ready for use.
   =========== ======= ===================================================

.. table:: **Table 3** Error return code

   +-------------+--------------+-------------------------------------------------------+
   | Return Code | Type         | Description                                           |
   +=============+==============+=======================================================+
   | 400         | Bad Request  | The server failed to process the request.             |
   +-------------+--------------+-------------------------------------------------------+
   | 401         | Unauthorized | Authorization failed.                                 |
   +-------------+--------------+-------------------------------------------------------+
   | 409         | Conflict     | The request could not be processed due to a conflict. |
   +-------------+--------------+-------------------------------------------------------+
