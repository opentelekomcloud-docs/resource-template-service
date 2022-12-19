:original_name: rts_03_0036.html

.. _rts_03_0036:

Checking a Stack
================

Function
--------

This API is used to check whether a stack is in the expected status.

URI
---

POST /v1/{project_id}/stacks/{stack_name}/{stack_id}/actions

For details about the parameters, see :ref:`Table 1 <rts_03_0036__table1759528275>`.

.. _rts_03_0036__table1759528275:

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

========= ==== ====== ========= =======================
Parameter In   Type   Mandatory Description
========= ==== ====== ========= =======================
check     body Object Yes       Checks stack resources.
========= ==== ====== ========= =======================

Response Parameter
------------------

This operation does not return the response body.

Request Example
---------------

.. code-block:: text

   POST /v1/95d02433133a4c0a87ba6967474a2ad3/stacks/HeatStack/c89c4bb3-96cb-4a55-aafa-076a7939a306/actions
   {
       "check": null
   }

Response Example
----------------

None

Return Code
-----------

.. table:: **Table 2** Normal return code

   =========== ==== =======================
   Return Code Type Description
   =========== ==== =======================
   200         OK   Request was successful.
   =========== ==== =======================

.. table:: **Table 3** Error return code

   =========== ============ =========================================
   Return Code Type         Description
   =========== ============ =========================================
   400         Bad Request  The server failed to process the request.
   401         Unauthorized Authorization failed.
   404         Not found    The requested resources are not found.
   =========== ============ =========================================
