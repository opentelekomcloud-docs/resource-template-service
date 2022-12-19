:original_name: rts_03_0031.html

.. _rts_03_0031:

Querying Metadata of a Stack Resource
=====================================

Function
--------

This API is used to query metadata of a stack resource.

URI
---

GET /v1/{project_id}/stacks/{stack_name}/{stack_id}/resources/{resource_name}/metadata

For details about the parameters, see :ref:`Table 1 <rts_03_0031__table1759528275>`.

.. _rts_03_0031__table1759528275:

.. table:: **Table 1** Parameter description

   +---------------+--------+-----------+--------------------------------------------------+
   | Parameter     | Type   | Mandatory | Description                                      |
   +===============+========+===========+==================================================+
   | project_id    | String | Yes       | Specifies the project ID.                        |
   +---------------+--------+-----------+--------------------------------------------------+
   | stack_name    | String | Yes       | Specifies the stack name.                        |
   +---------------+--------+-----------+--------------------------------------------------+
   | stack_id      | String | Yes       | Specifies the stack UUID.                        |
   +---------------+--------+-----------+--------------------------------------------------+
   | resource_name | String | Yes       | Specifies the name of the resource in the stack. |
   +---------------+--------+-----------+--------------------------------------------------+

Request Parameter
-----------------

N/A

Response Parameter
------------------

========= ==== ==== ================================
Parameter In   Type Description
========= ==== ==== ================================
metadata  body Dict Specifies the resource metadata.
========= ==== ==== ================================

Request Example
---------------

.. code-block:: text

   GET /v1/95d02433133a4c0a87ba6967474a2ad3/stacks/HeatStack/c89c4bb3-96cb-4a55-aafa-076a7939a306/resources/my_instance/metadata

Response Example
----------------

.. code-block::

   {
       "metadata": {
           "Name": "SmokeServer"
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

   =========== ============ =========================================
   Return Code Type         Description
   =========== ============ =========================================
   400         Bad Request  The server failed to process the request.
   401         Unauthorized Authorization failed.
   404         Not found    The requested resources are not found.
   =========== ============ =========================================
