:original_name: rts_03_0032.html

.. _rts_03_0032:

Sending a Signal to a Stack Resource
====================================

Function
--------

This API is used to send a signal to a stack resource to change the resource orchestration.

URI
---

POST /v1/{project_id}/stacks/{stack_name}/{stack_id}/resources/{resource_name}/signal

For details about the parameters, see :ref:`Table 1 <rts_03_0032__table1759528275>`.

.. _rts_03_0032__table1759528275:

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

The requested content is determined by the stack resource to which the signal is to be sent. Some resources cannot receive signals.

.. note::

   This API is asynchronous. Status code **200** is returned if the request is successfully received.

Response Parameter
------------------

This operation does not return the response body.

Request Example
---------------

.. code-block:: text

   POST /v1/95d02433133a4c0a87ba6967474a2ad3/stacks/HeatStack/65eb0ae7-36de-4104-aace-6bd040a2f95f/resources/my_instance/signal

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
