:original_name: rts_03_0047.html

.. _rts_03_0047:

Querying Resource Types
=======================

Function
--------

This API is used to query resource types.

URI
---

GET /v1/{project_id}/resource_types

For details about the parameters, see :ref:`Table 1 <rts_03_0047__table1759528275>`.

.. _rts_03_0047__table1759528275:

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

============== ==== ========== =================================
Parameter      In   Type       Description
============== ==== ========== =================================
resource_types body List <str> Specifies the resource type list.
============== ==== ========== =================================

Request Example
---------------

.. code-block:: text

   GET /v1/95d02433133a4c0a87ba6967474a2ad3/resource_types

Response Example
----------------

.. code-block::

   {
       "resource_types": [
           "OS::Nova::Server",
           "OS::Neutron::Net",
           "OS::Neutron::Port",
           "OS::Cinder::VolumeAttachment",
           "OS::Neutron::RouterInterface",
           "OS::Neutron::Router"
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

   =========== ============ =========================================
   Return Code Type         Description
   =========== ============ =========================================
   400         Bad Request  The server failed to process the request.
   401         Unauthorized Authorization failed.
   =========== ============ =========================================
