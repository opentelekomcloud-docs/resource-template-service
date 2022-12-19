:original_name: rts_03_0059.html

.. _rts_03_0059:

Deleting a Software Deployment
==============================

Function
--------

This API is used to delete a software deployment.

URI
---

DELETE /v1/{project_id}/software_deployments/{deployment_id}

For details about the parameters, see :ref:`Table 1 <rts_03_0059__table1759528275>`.

.. _rts_03_0059__table1759528275:

.. table:: **Table 1** Parameter description

   ============= ====== ========= =======================================
   Parameter     Type   Mandatory Description
   ============= ====== ========= =======================================
   project_id    String Yes       Specifies the project ID.
   deployment_id String Yes       Specifies the software deployment UUID.
   ============= ====== ========= =======================================

Request Parameter
-----------------

N/A

Response Parameter
------------------

This request does not return any content in the response body.

Request Example
---------------

.. code-block:: text

   DELETE /v1/95d02433133a4c0a87ba6967474a2ad3/software_deployments/80p72409093a9005bb7a6698c85a1b61

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
