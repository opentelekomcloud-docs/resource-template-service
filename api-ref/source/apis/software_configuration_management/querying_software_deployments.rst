:original_name: rts_03_0056.html

.. _rts_03_0056:

Querying Software Deployments
=============================

Function
--------

This API is used to query software deployments.

URI
---

GET /v1/{project_id}/software_deployments

For details about the parameters, see :ref:`Table 1 <rts_03_0056__table1759528275>`.

.. _rts_03_0056__table1759528275:

.. table:: **Table 1** Parameter description

   ========== ====== ========= =========================
   Parameter  Type   Mandatory Description
   ========== ====== ========= =========================
   project_id String Yes       Specifies the project ID.
   ========== ====== ========= =========================

Request Parameter
-----------------

========= ===== ====== ========= ===============================
Parameter In    Type   Mandatory Description
========= ===== ====== ========= ===============================
server_id query String No        Specifies the target server ID.
========= ===== ====== ========= ===============================

Response Parameter
------------------

+----------------------+------+-------------+----------------------------------------------------+
| Parameter            | In   | Type        | Description                                        |
+======================+======+=============+====================================================+
| software_deployments | body | List <dict> | Specifies the software deployment resource object. |
+----------------------+------+-------------+----------------------------------------------------+

**software_deployments** structure information

+-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
| Parameter       | In              | Type            | Description                                                                                                               |
+=================+=================+=================+===========================================================================================================================+
| action          | body            | String          | Specifies the stack action that triggers this software deployment resource.                                               |
+-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
| config_id       | body            | String          | Specifies the ID of the software configuration running on a server.                                                       |
+-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
| creation_time   | body            | String          | Specifies the creation time. The timestamp uses the ISO 8601 format:                                                      |
|                 |                 |                 |                                                                                                                           |
|                 |                 |                 | .. code-block::                                                                                                           |
|                 |                 |                 |                                                                                                                           |
|                 |                 |                 |    CCYY-MM-DDThh:mm:ss±hh:mm                                                                                              |
+-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
| id              | body            | String          | Specifies the software deployment UUID.                                                                                   |
+-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
| input_values    | body            | Object          | Specifies input data stored in the form of a key-value pair.                                                              |
+-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
| output_values   | body            | Object          | Specifies output data stored in the form of a key-value pair.                                                             |
+-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
| server_id       | body            | String          | Specifies the server ID.                                                                                                  |
+-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
| status          | body            | String          | Specifies the current status of software deployments. Valid values include **COMPLETE**, **IN_PROGRESS**, and **FAILED**. |
+-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
| status_reason   | body            | String          | Specifies the cause of the software deployment resource status.                                                           |
+-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
| updated_time    | body            | String          | Specifies the update time. The timestamp uses the ISO 8601 format:                                                        |
|                 |                 |                 |                                                                                                                           |
|                 |                 |                 | .. code-block::                                                                                                           |
|                 |                 |                 |                                                                                                                           |
|                 |                 |                 |    CCYY-MM-DDThh:mm:ss±hh:mm                                                                                              |
+-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+

Request Example
---------------

.. code-block:: text

   GET /v1/95d02433133a4c0a87ba6967474a2ad3/software_deployments

Response Example
----------------

.. code-block::

   {
       "software_deployments": [
           {
               "status": "COMPLETE",
               "server_id": "ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5",
               "config_id": "8da95794-2ad9-4979-8ae5-739ce314c5cd",
               "output_values": {
                   "deploy_stdout": "Writing to /tmp/barmy\nWritten to /tmp/barmy\n",
                   "deploy_stderr": "+ echo Writing to /tmp/barmy\n+ echo fu\n+ cat /tmp/barmy\n+ echo -n The file /tmp/barmy contains fu for server ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5 during CREATE\n+ echo Written to /tmp/barmy\n+ echo Output to stderr\nOutput to stderr\n",
                   "deploy_status_code": 0,
                   "result": "The file /tmp/barmy contains fu for server ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5 during CREATE"
               },
               "input_values": null,
               "action": "CREATE",
               "status_reason": "Outputs received",
               "id": "ef422fa5-719a-419e-a10c-72e3a367b0b8",
               "creation_time": "2015-01-31T15:12:36Z",
               "updated_time": "2015-01-31T15:18:21Z"
           }
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
