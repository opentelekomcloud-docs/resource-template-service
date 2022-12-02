:original_name: rts_03_0049.html

.. _rts_03_0049:

Querying the Building Information
=================================

Function
--------

This API is used to query the building information.

URI
---

GET /v1/{project_id}/build_info

For details about the parameters, see :ref:`Table 1 <rts_03_0049__table1759528275>`.

.. _rts_03_0049__table1759528275:

.. table:: **Table 1** Parameter description

   ========== ====== ========= =========================
   Parameter  Type   Mandatory Description
   ========== ====== ========= =========================
   project_id String Yes       Specifies the project ID.
   ========== ====== ========= =========================

Request Parameter
-----------------

N/A

Response Parameter
------------------

========= ==== ==== =================================
Parameter In   Type Description
========= ==== ==== =================================
api       body Dict Specifies the API information.
engine    body Dict Specifies the engine information.
========= ==== ==== =================================

Request Example
---------------

.. code-block:: text

   GET /v1/95d02433133a4c0a87ba6967474a2ad3/build_info

Response Example
----------------

.. code-block::

   {
       "api": {
           "revision": "{api_build_revision}"
       },
       "engine": {
           "revision": "{engine_build_revision}"
       }
   }

**Return Code**
---------------

.. table:: **Table 2** Normal return code

   =========== ==== =======================
   Return Code Type Description
   =========== ==== =======================
   200         OK   Request was successful.
   =========== ==== =======================

.. table:: **Table 3** Error return code

   =========== ============ =====================
   Return Code Type         Description
   =========== ============ =====================
   401         Unauthorized Authorization failed.
   =========== ============ =====================
