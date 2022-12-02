:original_name: rts_03_0044.html

.. _rts_03_0044:

Validating a Template
=====================

Function
--------

This API is used to check whether the template syntax meets requirements.

URI
---

POST /v1/{project_id}/validate

For details about the parameters, see :ref:`Table 1 <rts_03_0044__table1759528275>`.

.. _rts_03_0044__table1759528275:

.. table:: **Table 1** Parameter description

   ========== ====== ========= =========================
   Parameter  Type   Mandatory Description
   ========== ====== ========= =========================
   project_id String Yes       Specifies the project ID.
   ========== ====== ========= =========================

Request Parameter
-----------------

+-------------+------+------+-----------+---------------------------------------------------------------------+
| Parameter   | In   | Type | Mandatory | Description                                                         |
+=============+======+======+===========+=====================================================================+
| environment | body | Json | No        | Specifies information about the environment for creating a stack.   |
+-------------+------+------+-----------+---------------------------------------------------------------------+
| files       | body | Json | No        | Specifies the files referenced in the environment.                  |
+-------------+------+------+-----------+---------------------------------------------------------------------+
| template    | body | Json | No        | Specifies the stack template on which operations will be performed. |
+-------------+------+------+-----------+---------------------------------------------------------------------+

Response Parameter
------------------

=========== ==== ====== ==================================
Parameter   In   Type   Description
=========== ==== ====== ==================================
description body String Describes the template.
parameters  body Dict   Specifies the template parameters.
=========== ==== ====== ==================================

Request Example
---------------

.. code-block:: text

   POST /v1/95d02433133a4c0a87ba6967474a2ad3/validate
   {
       "template": "heat_template_version: 2014-10-16\ndescription: Create a serious of random string\nparameters:\n  length:\n    type: number\n    default: 4\nresources:\n  random:\n    type: OS::Heat::RandomString\n    properties:\n      length: { get_param: length }",
       "environment": {},
       "files": {}
   }

Response Example
----------------

.. code-block::

   {
       "Description": "Create a serious of random string",
       "Parameters": {
           "length": {
               "Default": 4,
               "NoEcho": "false",
               "Type": "Number",
               "Description": "",
               "Label": "length"
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
   | 500         | Internal Server Error | Failed to complete the request because of an internal service error. |
   +-------------+-----------------------+----------------------------------------------------------------------+
