:original_name: rts_03_0054.html

.. _rts_03_0054:

Deleting a Software Configuration
=================================

Function
--------

This API is used to delete a software configuration.

URI
---

DELETE /v1/{project_id}/software_configs/{config_id}

For details about the parameters, see :ref:`Table 1 <rts_03_0054__table1759528275>`.

.. _rts_03_0054__table1759528275:

.. table:: **Table 1** Parameter description

   ========== ====== ========= ==========================================
   Parameter  Type   Mandatory Description
   ========== ====== ========= ==========================================
   project_id String Yes       Specifies the project ID.
   config_id  String Yes       Specifies the software configuration UUID.
   ========== ====== ========= ==========================================

Request Parameter
-----------------

N/A

Response Parameter
------------------

This request does not return any content in the response body.

Request Example
---------------

.. code-block:: text

   DELETE /v1/95d02433133a4c0a87ba6967474a2ad3/software_configs/40p72423093a900a8b7a669768421a6a

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

   =========== ============ =========================================
   Return Code Type         Description
   =========== ============ =========================================
   400         Bad Request  The server failed to process the request.
   401         Unauthorized Authorization failed.
   404         Not found    The requested resources are not found.
   =========== ============ =========================================
