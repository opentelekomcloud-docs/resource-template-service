:original_name: rts_03_0057.html

.. _rts_03_0057:

Querying Details of a Software Deployment
=========================================

Function
--------

This API is used to query details of a software deployment.

URI
---

GET /v1/{project_id}/software_deployments/{deployment_id}

For details about the parameters, see :ref:`Table 1 <rts_03_0057__table1759528275>`.

.. _rts_03_0057__table1759528275:

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

+---------------------+------+-------------+--------------------------------------------+
| Parameter           | In   | Type        | Description                                |
+=====================+======+=============+============================================+
| software_deployment | body | List <dict> | Specifies the software deployment objects. |
+---------------------+------+-------------+--------------------------------------------+

**software_deployment** structure information

+-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------+
| Parameter       | In              | Type            | Description                                                                                                               |
+=================+=================+=================+===========================================================================================================================+
| action          | body            | String          | Specifies the stack action that triggers the software deployment.                                                         |
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
| status_reason   | body            | String          | Specifies the cause of the software deployment status.                                                                    |
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

   GET /v1/95d02433133a4c0a87ba6967474a2ad3/software_deployments/3d5ec2a8-7004-43b6-a7f6-542bdbe9d434

Response Example
----------------

.. code-block::

   {
       "software_deployment": {
           "action": "CREATE",
           "config_id": "619d6e53-e14b-497f-8852-9c2671b07d79",
           "creation_time": "2018-05-15T08:48:23.500895",
           "id": "bb51252e-3e80-4be9-8c06-c52a88e87ec8",
           "input_values": {},
           "output_values": null,
           "server_id": "ca839c6d-c038-46b6-b0b8-8ce78e715639",
           "status": "IN_PROGRESS",
           "status_reason": "Deploy data available"
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
