:original_name: rts_03_0026.html

.. _rts_03_0026:

Updating a Stack
================

Function
--------

This API is used to update a stack.

URI
---

PUT /v1/{project_id}/stacks/{stack_name}/{stack_id}

For details about the parameters, see :ref:`Table 1 <rts_03_0026__table1759528275>`.

.. _rts_03_0026__table1759528275:

.. table:: **Table 1** Parameter description

   ========== ====== ========= =========================
   Parameter  Type   Mandatory Description
   ========== ====== ========= =========================
   project_id String Yes       Specifies the project ID.
   stack_name String Yes       Specifies the stack name.
   stack_id   String Yes       Specifies the stack UUID.
   ========== ====== ========= =========================

Request Parameter
-----------------

+------------------+------+---------+-----------+-------------------------------------------------------------------------------------+
| Parameter        | In   | Type    | Mandatory | Description                                                                         |
+==================+======+=========+===========+=====================================================================================+
| template         | body | Json    | Yes       | Specifies the template. The template content must use the YAML syntax.              |
+------------------+------+---------+-----------+-------------------------------------------------------------------------------------+
| template_url     | body | String  | No        | Specifies the template URL. You cannot select a template using the URL temporarily. |
+------------------+------+---------+-----------+-------------------------------------------------------------------------------------+
| environment      | body | Json    | No        | Specifies information about the environment for creating a stack.                   |
+------------------+------+---------+-----------+-------------------------------------------------------------------------------------+
| files            | body | Json    | No        | Specifies the files referenced in the environment.                                  |
+------------------+------+---------+-----------+-------------------------------------------------------------------------------------+
| parameters       | body | Json    | No        | Specifies parameter information of the stack.                                       |
+------------------+------+---------+-----------+-------------------------------------------------------------------------------------+
| timeout_mins     | body | Int     | No        | Specifies the timeout duration.                                                     |
+------------------+------+---------+-----------+-------------------------------------------------------------------------------------+
| disable_rollback | body | Boolean | No        | Specifies whether to perform a rollback when a stack update fails.                  |
+------------------+------+---------+-----------+-------------------------------------------------------------------------------------+

Response Parameter
------------------

N/A

Request Example
---------------

.. code-block:: text

   PUT /v1/95d02433133a4c0a87ba6967474a2ad3/stacks/HeatStack/c89c4bb3-96cb-4a55-aafa-076a7939a306
   {
       "template": {
           "heat_template_version": "2013-05-23",
           "description": "Create a simple stack",
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
                       "user_data": "#!/bin/bash -xv\necho \"hello world\" > /root/hello-world.txt\n"
                   }
               }
           }
       },
       "parameters": {
           "flavor": "m1.small"
       }
   }

Response Example
----------------

None

Return Code
-----------

.. table:: **Table 2** Normal return code

   +-------------+----------+--------------------------------------------------------------------+
   | Return Code | Type     | Description                                                        |
   +=============+==========+====================================================================+
   | 202         | Accepted | The request has been accepted, but the processing is not complete. |
   +-------------+----------+--------------------------------------------------------------------+

.. table:: **Table 3** Error return code

   +-------------+-----------------------+----------------------------------------------------------------------+
   | Return Code | Type                  | Description                                                          |
   +=============+=======================+======================================================================+
   | 400         | Bad Request           | The server failed to process the request.                            |
   +-------------+-----------------------+----------------------------------------------------------------------+
   | 401         | Unauthorized          | Authorization failed.                                                |
   +-------------+-----------------------+----------------------------------------------------------------------+
   | 404         | Not found             | The requested resources are not found.                               |
   +-------------+-----------------------+----------------------------------------------------------------------+
   | 500         | Internal Server Error | Failed to complete the request because of an internal service error. |
   +-------------+-----------------------+----------------------------------------------------------------------+
