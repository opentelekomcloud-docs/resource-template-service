:original_name: rts_03_0020.html

.. _rts_03_0020:

Querying the Stacks
===================

Function
--------

This API is used to query stacks of a specified tenant.

URI
---

GET /v1/{project_id}/stacks

For details about the parameters, see :ref:`Table 1 <rts_03_0020__table7797142512383>`.

.. _rts_03_0020__table7797142512383:

.. table:: **Table 1** Parameter description

   ========== ====== ========= =========================
   Parameter  Type   Mandatory Description
   ========== ====== ========= =========================
   project_id String Yes       Specifies the project ID.
   ========== ====== ========= =========================

Request Parameter
-----------------

+---------------------+-------------+-------------+-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter           | In          | Type        | Mandatory   | Description                                                                                                                                                                                                         |
+=====================+=============+=============+=============+=====================================================================================================================================================================================================================+
| status/stack_status | query       | String      | No          | Specifies the stack status.                                                                                                                                                                                         |
+---------------------+-------------+-------------+-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| name/stack_name     | query       | String      | No          | Specifies the stack name.                                                                                                                                                                                           |
|                     |             |             |             |                                                                                                                                                                                                                     |
|                     |             |             |             | -  The value can contain only uppercase letters, lowercase letters, digits, hyphens (-), periods (.), and underscores (_).                                                                                          |
|                     |             |             |             | -  The value must start with an uppercase letter or a lowercase letter.                                                                                                                                             |
|                     |             |             |             | -  The value can contain 1 to 255 characters.                                                                                                                                                                       |
+---------------------+-------------+-------------+-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| limit               | query       | Integer     | No          | Specifies the number of returned stacks. This parameter is used to control the stack display mode and quantity. It can be used independently or together with the **marker** parameter.                             |
|                     |             |             |             |                                                                                                                                                                                                                     |
|                     |             |             |             | For example, if the **limit** and **marker** parameters are not used, the queried stack list is as follows:                                                                                                         |
|                     |             |             |             |                                                                                                                                                                                                                     |
|                     |             |             |             | .. code-block::                                                                                                                                                                                                     |
|                     |             |             |             |                                                                                                                                                                                                                     |
|                     |             |             |             |    [stack1,stack2,stack3,stack4,stack5,stack6,stack7,stack8]                                                                                                                                                        |
|                     |             |             |             |                                                                                                                                                                                                                     |
|                     |             |             |             | If **limit** is set to **3**, only the first three data records in the stack list are returned.                                                                                                                     |
|                     |             |             |             |                                                                                                                                                                                                                     |
|                     |             |             |             | .. code-block::                                                                                                                                                                                                     |
|                     |             |             |             |                                                                                                                                                                                                                     |
|                     |             |             |             |    [stack1,stack2,stack3]                                                                                                                                                                                           |
|                     |             |             |             |                                                                                                                                                                                                                     |
|                     |             |             |             | If **limit** is set to **3** and **marker** is set to **stack3**, three stacks are displayed in sequence from the next data record of **stack3**.                                                                   |
|                     |             |             |             |                                                                                                                                                                                                                     |
|                     |             |             |             | .. code-block::                                                                                                                                                                                                     |
|                     |             |             |             |                                                                                                                                                                                                                     |
|                     |             |             |             |    [stack4,stack5,stack6]                                                                                                                                                                                           |
|                     |             |             |             |                                                                                                                                                                                                                     |
|                     |             |             |             | If **limit** is set to **3** and **marker** is set to **stack6**, but fewer than three data records are available after **stack6**, all the remaining data records are displayed.                                   |
|                     |             |             |             |                                                                                                                                                                                                                     |
|                     |             |             |             | .. code-block::                                                                                                                                                                                                     |
|                     |             |             |             |                                                                                                                                                                                                                     |
|                     |             |             |             |    [stack7,stack8]                                                                                                                                                                                                  |
+---------------------+-------------+-------------+-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| marker              | query       | String      | No          | Specifies the stack from which the next data record starts to be queried. This parameter is used to control the stack display mode and quantity. This parameter must be used together with the **limit** parameter. |
+---------------------+-------------+-------------+-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| sort_keys           | query       | String      | No          | Specifies the sorting keyword.                                                                                                                                                                                      |
|                     |             |             |             |                                                                                                                                                                                                                     |
|                     |             |             |             | stack_name, stack_status, creation_time, and updated_time                                                                                                                                                           |
+---------------------+-------------+-------------+-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| sort_dir            | query       | String      | No          | Specifies the sorting method.                                                                                                                                                                                       |
|                     |             |             |             |                                                                                                                                                                                                                     |
|                     |             |             |             | The value can be **asc** (in the ascending order) or **desc** (in the descending order).                                                                                                                            |
+---------------------+-------------+-------------+-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameter
------------------

========= ==== =========== =========================
Parameter In   Type        Description
========= ==== =========== =========================
stacks    body List <dict> Specifies the stack list.
========= ==== =========== =========================

**stacks** structure information

+-----------------------+------+-------------+---------------------------------------------------------------------------------+
| Parameter             | In   | Type        | Description                                                                     |
+=======================+======+=============+=================================================================================+
| id                    | body | String      | Specifies the stack UUID.                                                       |
+-----------------------+------+-------------+---------------------------------------------------------------------------------+
| stack_name            | body | String      | Specifies the stack name.                                                       |
+-----------------------+------+-------------+---------------------------------------------------------------------------------+
| stack_status          | body | String      | Specifies the stack status.                                                     |
+-----------------------+------+-------------+---------------------------------------------------------------------------------+
| stack_status_reason   | body | String      | Describes the stack operation.                                                  |
+-----------------------+------+-------------+---------------------------------------------------------------------------------+
| description           | body | String      | Describes the stack.                                                            |
+-----------------------+------+-------------+---------------------------------------------------------------------------------+
| links                 | body | List <dict> | Specifies the stack URL list.                                                   |
+-----------------------+------+-------------+---------------------------------------------------------------------------------+
| creation_time         | body | String      | Specifies the time when the stack was created.                                  |
+-----------------------+------+-------------+---------------------------------------------------------------------------------+
| updated_time          | body | String      | Specifies the time when the stack was updated.                                  |
+-----------------------+------+-------------+---------------------------------------------------------------------------------+
| parent                | body | String      | Specifies the UUID of the parent stack (for a nested stack).                    |
+-----------------------+------+-------------+---------------------------------------------------------------------------------+
| tags                  | body | String      | Specifies the stack tag.                                                        |
+-----------------------+------+-------------+---------------------------------------------------------------------------------+
| stack_user_project_id | body | String      | Specifies the project UUID of the stack user. This parameter may be left blank. |
+-----------------------+------+-------------+---------------------------------------------------------------------------------+

Request Example
---------------

.. code-block:: text

   GET /v1/95d02433133a4c0a87ba6967474a2ad3/stacks

Response Example
----------------

.. code-block::

   {
       "stacks": [
           {
               "description": "Hello world HOT template that just defines a single compute instance. Contains just base features to verify base HOT support.\n",
               "links": [
                   {
                        "href":  "http://x.x.x.x:8004/v1/95d02433133a4c0a87ba6967474a2ad3/stacks/HeatStack/c89c4bb3-96cb-4a55-aafa-076a7939a306",
                        "rel": "self"
                    }
                ],
               "stack_status_reason": "Stack create completed successfully",
               "stack_name": "HeatStack",
               "creation_time": "2018-01-26T17:21:35Z",
               "updated_time": "2018-01-26T17:21:41Z",
               "stack_status": "CREATE_COMPLETE",
               "id": "c89c4bb3-96cb-4a55-aafa-076a7939a306"
           }
       ]
   }

Return Code
-----------

.. table:: **Table 2** Normal return code

   =========== ==== =======================
   Return Code Type Description
   =========== ==== =======================
   200         OK   Request was successful.
   =========== ==== =======================

.. table:: **Table 3** Error return code

   +-------------+-----------------------+----------------------------------------------------------------------+
   | Return Code | Type                  | Description                                                          |
   +=============+=======================+======================================================================+
   | 400         | Bad Request           | The server failed to process the request.                            |
   +-------------+-----------------------+----------------------------------------------------------------------+
   | 401         | Unauthorized          | Authorization failed.                                                |
   +-------------+-----------------------+----------------------------------------------------------------------+
   | 500         | Internal Server Error | Failed to complete the request because of an internal service error. |
   +-------------+-----------------------+----------------------------------------------------------------------+
