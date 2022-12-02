:original_name: rts_03_0055.html

.. _rts_03_0055:

Creating One or More Software Deployments
=========================================

Function
--------

This API is used to create one or more software deployments.

URI
---

POST /v1/{project_id}/software_deployments

For details about the parameters, see :ref:`Table 1 <rts_03_0055__table1759528275>`.

.. _rts_03_0055__table1759528275:

.. table:: **Table 1** Parameter description

   ========== ====== ========= =========================
   Parameter  Type   Mandatory Description
   ========== ====== ========= =========================
   project_id String Yes       Specifies the project ID.
   ========== ====== ========= =========================

Request Parameter
-----------------

+-----------------------+------+--------+-----------+-------------------------------------------------------------------------------------------------------------------+
| Parameter             | In   | Type   | Mandatory | Description                                                                                                       |
+=======================+======+========+===========+===================================================================================================================+
| action                | body | String | No        | Specifies the stack action that triggers this software deployment.                                                |
+-----------------------+------+--------+-----------+-------------------------------------------------------------------------------------------------------------------+
| config_id             | body | String | Yes       | Specifies the ID of the software configuration running on a server.                                               |
+-----------------------+------+--------+-----------+-------------------------------------------------------------------------------------------------------------------+
| input_values          | body | Object | No        | Specifies input data stored in the form of a key-value pair.                                                      |
+-----------------------+------+--------+-----------+-------------------------------------------------------------------------------------------------------------------+
| server_id             | body | String | Yes       | Specifies the ID of the server deployed using the software configuration.                                         |
+-----------------------+------+--------+-----------+-------------------------------------------------------------------------------------------------------------------+
| stack_user_project_id | body | String | No        | Specifies the ID of the authenticated tenant who can perform operations on the deployment resources.              |
+-----------------------+------+--------+-----------+-------------------------------------------------------------------------------------------------------------------+
| status                | body | String | No        | Specifies the status of software deployments. Valid values include **COMPLETE**, **IN_PROGRESS**, and **FAILED**. |
+-----------------------+------+--------+-----------+-------------------------------------------------------------------------------------------------------------------+
| status_reason         | body | String | No        | Specifies the cause of the software deployment status.                                                            |
+-----------------------+------+--------+-----------+-------------------------------------------------------------------------------------------------------------------+

Response Parameter
------------------

+---------------------+------+------+----------------------------------------------------+
| Parameter           | In   | Type | Description                                        |
+=====================+======+======+====================================================+
| software_deployment | body | Dict | Specifies the software deployment resource object. |
+---------------------+------+------+----------------------------------------------------+

**software_deployment** structure information

+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+
| Parameter       | In              | Type            | Description                                                                                                       |
+=================+=================+=================+===================================================================================================================+
| action          | body            | String          | Specifies the stack action that triggers this software deployment.                                                |
+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+
| config_id       | body            | String          | Specifies the ID of the software configuration running on a server.                                               |
+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+
| creation_time   | body            | String          | Specifies the creation time. The timestamp uses the ISO 8601 format:                                              |
|                 |                 |                 |                                                                                                                   |
|                 |                 |                 | .. code-block::                                                                                                   |
|                 |                 |                 |                                                                                                                   |
|                 |                 |                 |    CCYY-MM-DDThh:mm:ss±hh:mm                                                                                      |
+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+
| id              | body            | String          | Specifies the software deployment UUID.                                                                           |
+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+
| input_values    | body            | Object          | Specifies input data stored in the form of a key-value pair.                                                      |
+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+
| output_values   | body            | Object          | Specifies output data stored in the form of a key-value pair.                                                     |
+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+
| server_id       | body            | String          | Specifies the server ID.                                                                                          |
+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+
| status          | body            | String          | Specifies the status of software deployments. Valid values include **COMPLETE**, **IN_PROGRESS**, and **FAILED**. |
+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+
| status_reason   | body            | String          | Specifies the cause of the software deployment status.                                                            |
+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+

Request Example
---------------

.. code-block:: text

   POST /v1/95d02433133a4c0a87ba6967474a2ad3/software_deployments
   {
       "status": "IN_PROGRESS",
       "server_id": "ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5",
       "config_id": "8da95794-2ad9-4979-8ae5-739ce314c5cd",
       "stack_user_project_id": "c024bfada67845ddb17d2b0c0be8cd79",
       "action": "CREATE",
       "status_reason": "Deploy data available"
   }

Response Example
----------------

.. code-block::

   {
       "software_deployment": {
           "status": "IN_PROGRESS",
           "server_id": "ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5",
           "config_id": "8da95794-2ad9-4979-8ae5-739ce314c5cd",
           "output_values": null,
           "input_values": null,
           "action": "CREATE",
           "status_reason": "Deploy data available",
           "id": "ef422fa5-719a-419e-a10c-72e3a367b0b8",
           "creation_time": "2015-01-31T15:12:36Z"
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
   | 500         | Internal Server Error | Failed to complete the request because of an internal service error. |
   +-------------+-----------------------+----------------------------------------------------------------------+
