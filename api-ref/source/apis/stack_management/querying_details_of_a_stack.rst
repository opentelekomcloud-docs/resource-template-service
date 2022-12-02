:original_name: rts_03_0025.html

.. _rts_03_0025:

Querying Details of a Stack
===========================

Function
--------

This API is used to query details of a stack.

URI
---

GET /v1/{project_id}/stacks/{stack_name}/{stack_id}

.. note::

   This API supports redirection. During the calling, you can specify only **stack_name** or **stack_id**.

For details about the parameters, see :ref:`Table 1 <rts_03_0025__table1759528275>`.

.. _rts_03_0025__table1759528275:

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

N/A

Response Parameter
------------------

========= ==== ==== ===========================
Parameter In   Type Description
========= ==== ==== ===========================
stack     body Dict Specifies the stack object.
========= ==== ==== ===========================

**stack** structure information

+-----------------------+------+-------------+------------------------------------------------------------------------+
| Parameter             | In   | Type        | Description                                                            |
+=======================+======+=============+========================================================================+
| disable_rollback      | body | Boolean     | Specifies whether to perform a rollback when stack creation fails.     |
+-----------------------+------+-------------+------------------------------------------------------------------------+
| description           | body | String      | Describes the stack.                                                   |
+-----------------------+------+-------------+------------------------------------------------------------------------+
| parent                | body | String      | Specifies the ID of the parent stack if the stack is the nesting type. |
+-----------------------+------+-------------+------------------------------------------------------------------------+
| tags                  | body | Array       | Specifies whether to perform a rollback when stack creation fails.     |
+-----------------------+------+-------------+------------------------------------------------------------------------+
| parameters            | body | Dict        | Specifies parameter information of the stack.                          |
+-----------------------+------+-------------+------------------------------------------------------------------------+
| stack_status_reason   | body | String      | Describes the stack operation.                                         |
+-----------------------+------+-------------+------------------------------------------------------------------------+
| stack_name            | body | String      | Specifies the stack name.                                              |
+-----------------------+------+-------------+------------------------------------------------------------------------+
| stack_user_project_id | body | String      | This is a reserved parameter.                                          |
+-----------------------+------+-------------+------------------------------------------------------------------------+
| outputs               | body | List        | Specifies the output stack list.                                       |
+-----------------------+------+-------------+------------------------------------------------------------------------+
| creation_time         | body | String      | Specifies the time when the stack was created.                         |
+-----------------------+------+-------------+------------------------------------------------------------------------+
| links                 | body | List <dict> | Specifies the stack URL list.                                          |
+-----------------------+------+-------------+------------------------------------------------------------------------+
| capabilities          | body | List        | Specifies the list of stack capacities.                                |
+-----------------------+------+-------------+------------------------------------------------------------------------+
| notification_topics   | body | List        | Specifies the message notification list of the stack.                  |
+-----------------------+------+-------------+------------------------------------------------------------------------+
| timeout_mins          | body | Integer     | Specifies the timeout duration.                                        |
+-----------------------+------+-------------+------------------------------------------------------------------------+
| stack_status          | body | String      | Specifies the stack status.                                            |
+-----------------------+------+-------------+------------------------------------------------------------------------+
| stack_owner           | body | String      | This is a reserved parameter.                                          |
+-----------------------+------+-------------+------------------------------------------------------------------------+
| updated_time          | body | String      | Specifies the time when the stack was updated.                         |
+-----------------------+------+-------------+------------------------------------------------------------------------+
| id                    | body | String      | Specifies the stack UUID.                                              |
+-----------------------+------+-------------+------------------------------------------------------------------------+
| template_description  | body | String      | Describes the template.                                                |
+-----------------------+------+-------------+------------------------------------------------------------------------+

Request Example
---------------

.. code-block:: text

   GET /v1/95d02433133a4c0a87ba6967474a2ad3/stacks/HeatStack/c89c4bb3-96cb-4a55-aafa-076a7939a306

Response Example
----------------

.. code-block::

   {
       "stack": {
           "disable_rollback": true,
           "description": "Hello world HOT template that just defines a single compute instance. Contains just base features to verify base HOT support.\n",
           "parent": null,
           "tags": null,
           "parameters": {
               "Network": "3f8713b7-8aea-4b0f-a70b-98d4e1d6251f",
               "OS::stack_name": "HeatStack",
               "ImageId": "68e22196-a4aa-4946-85c3-75f4957e667a",
               "OS::stack_id": "c89c4bb3-96cb-4a55-aafa-076a7939a306",
               "KeyName": "heat-key",
               "OS::project_id": "95d02433133a4c0a87ba6967474a2ad3",
               "InstanceType": "m1.tiny"
           },
           "stack_user_project_id": "95d02433133a4c0a87ba6967474a2ad3",
           "stack_status_reason": "Stack create completed successfully",
           "stack_name": "HeatStack",
           "outputs": [],
           "creation_time": "2014-01-26T17:21:35Z",
           "links": [
               {
                   "href":  "http://x.x.x.x:8004/v1/95d02433133a4c0a87ba6967474a2ad3/stacks/HeatStack/c89c4bb3-96cb-4a55-aafa-076a7939a306",
                   "rel": "self"
                }
           ],
           "capabilities": [],
           "notification_topics": [],
           "timeout_mins": 60,
           "stack_status": "CREATE_COMPLETE",
           "stack_owner": null,
           "updated_time": "2014-01-26T17:21:41Z",
           "id": "c89c4bb3-96cb-4a55-aafa-076a7939a306",
           "template_description": "Hello world HOT template that just defines a single compute instance. Contains just base features to verify base HOT support.\n"
       }
   }

Return Code
-----------

.. table:: **Table 2** Normal return code

   +-------------+-------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Return Code | Type  | Description                                                                                                                                          |
   +=============+=======+======================================================================================================================================================+
   | 200         | OK    | Request was successful.                                                                                                                              |
   +-------------+-------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 302         | Found | The response is about redirection. The response header usually contains a location value that allows you to track the real location of the resource. |
   +-------------+-------+------------------------------------------------------------------------------------------------------------------------------------------------------+

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
