:original_name: rts_03_0043.html

.. _rts_03_0043:

Querying a Stack Template
=========================

Function
--------

This API is used to query a stack template.

URI
---

GET /v1/{project_id}/stacks/{stack_name}/{stack_id}/template

.. note::

   This API supports redirection. During the calling, you can specify only **stack_name** or **stack_id**.

For details about the parameters, see :ref:`Table 1 <rts_03_0043__table1759528275>`.

.. _rts_03_0043__table1759528275:

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

+-----------------------+------+--------+-------------------------------------------------------+
| Parameter             | In   | Type   | Description                                           |
+=======================+======+========+=======================================================+
| heat_template_version | body | String | Specifies the version of the HOT template.            |
+-----------------------+------+--------+-------------------------------------------------------+
| outputs               | body | Dict   | Includes key-value pairs of the output data.          |
+-----------------------+------+--------+-------------------------------------------------------+
| parameters            | body | Dict   | Specifies the key-value pairs of template parameters. |
+-----------------------+------+--------+-------------------------------------------------------+
| description           | body | String | Describes the stack template.                         |
+-----------------------+------+--------+-------------------------------------------------------+
| resources             | body | Dict   | Specifies the template resources.                     |
+-----------------------+------+--------+-------------------------------------------------------+

Request Example
---------------

.. code-block:: text

   GET /v1/95d02433133a4c0a87ba6967474a2ad3/stacks/HeatStack/c89c4bb3-96cb-4a55-aafa-076a7939a306/template

Response Example
----------------

.. code-block::

   {
       "description": "Hello world HOT template that just defines a single server. Contains just base features to verify base HOT support.\n",
       "heat_template_version": "2013-05-23",
       "outputs": {
           "foo": {
               "description": "Show foo parameter value",
               "value": {
                   "get_param": "foo"
               }
           }
       },
       "parameters": {
           "foo": {
               "default": "secret",
               "description": "Name of an existing key pair to use for the server",
               "hidden": true,
               "type": "string"
           }
       },
       "resources": {
           "random_key_name": {
               "properties": {
                   "length": 8
               },
               "type": "OS::Heat::RandomString"
           }
       }
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
   | 404         | Not found             | The requested resources are not found.                               |
   +-------------+-----------------------+----------------------------------------------------------------------+
   | 500         | Internal Server Error | Failed to complete the request because of an internal service error. |
   +-------------+-----------------------+----------------------------------------------------------------------+
