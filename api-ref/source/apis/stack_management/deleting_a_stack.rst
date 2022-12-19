:original_name: rts_03_0027.html

.. _rts_03_0027:

Deleting a Stack
================

Function
--------

This API is used to delete a stack.

URI
---

DELETE /v1/{project_id}/stacks/{stack_name}/{stack_id}

For details about the parameters, see :ref:`Table 1 <rts_03_0027__table1759528275>`.

.. _rts_03_0027__table1759528275:

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

This request does not return any content in the response body.

Request Example
---------------

.. code-block:: text

   DELETE /v1/9c53a566cb3443ab910cf0daebca90c4/stacks/HeatStack/34247a47-7bf9-4842-a899-421a3cca5779

Response Example
----------------

None

Return Code
-----------

.. table:: **Table 2** Normal return code

   +-------------+------------+---------------------------------------------------------------------+
   | Return Code | Type       | Description                                                         |
   +=============+============+=====================================================================+
   | 204         | No Content | The RTS service has fulfilled the request by deleting the resource. |
   +-------------+------------+---------------------------------------------------------------------+

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
