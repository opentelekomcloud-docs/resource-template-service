:original_name: rts_03_0033.html

.. _rts_03_0033:

Marking a Resource as Unhealthy
===============================

Function
--------

This API is used to mark the status of a specified resource as unhealthy.

URI
---

PATCH /v1/{project_id}/stacks/{stack_name}/{stack_id}/resources/{resource_name_or_physical_id}

For details about the parameters, see :ref:`Table 1 <rts_03_0033__table1759528275>`.

.. _rts_03_0033__table1759528275:

.. table:: **Table 1** Parameter description

   +------------------------------+--------+-----------+------------------------------+
   | Parameter                    | Type   | Mandatory | Description                  |
   +==============================+========+===========+==============================+
   | project_id                   | String | Yes       | Specifies the project ID.    |
   +------------------------------+--------+-----------+------------------------------+
   | stack_name                   | String | Yes       | Specifies the stack name.    |
   +------------------------------+--------+-----------+------------------------------+
   | stack_id                     | String | Yes       | Specifies the stack UUID.    |
   +------------------------------+--------+-----------+------------------------------+
   | resource_name_or_physical_id | String | Yes       | Specifies the resource name. |
   +------------------------------+--------+-----------+------------------------------+

Request Parameter
-----------------

+------------------------+------+---------+-----------+------------------------------------------------------------------+
| Parameter              | In   | Type    | Mandatory | Description                                                      |
+========================+======+=========+===========+==================================================================+
| mark_unhealthy         | body | Boolean | Yes       | Specifies whether to mark the status of a resource as unhealthy. |
+------------------------+------+---------+-----------+------------------------------------------------------------------+
| resource_status_reason | body | String  | No        | Describes the cause causing the current resource status.         |
+------------------------+------+---------+-----------+------------------------------------------------------------------+

Response Parameter
------------------

This operation does not return the response body.

Request Example
---------------

.. code-block::

   PATCH /v1/95d02433133a4c0a87ba6967474a2ad3/stacks/HeatStack/65eb0ae7-36de-4104-aace-6bd040a2f95f/resources/my_instance
   {
       "mark_unhealthy": false,
       "resource_status_reason": "test reset"
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
