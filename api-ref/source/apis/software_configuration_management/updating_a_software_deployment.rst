:original_name: rts_03_0058.html

.. _rts_03_0058:

Updating a Software Deployment
==============================

Function
--------

This API is used to update a software deployment.

URI
---

PUT /v1/{project_id}/software_deployments/{deployment_id}

For details about the parameters, see :ref:`Table 1 <rts_03_0058__table1759528275>`.

.. _rts_03_0058__table1759528275:

.. table:: **Table 1** Parameter description

   ============= ====== ========= =======================================
   Parameter     Type   Mandatory Description
   ============= ====== ========= =======================================
   project_id    String Yes       Specifies the project ID.
   deployment_id String Yes       Specifies the software deployment UUID.
   ============= ====== ========= =======================================

Request Parameter
-----------------

+---------------+------+--------+-----------+-------------------------------------------------------------------------------------------------------------------+
| Parameter     | In   | Type   | Mandatory | Description                                                                                                       |
+===============+======+========+===========+===================================================================================================================+
| action        | body | String | No        | Specifies the stack action that triggers this software deployment.                                                |
+---------------+------+--------+-----------+-------------------------------------------------------------------------------------------------------------------+
| config_id     | body | String | No        | Specifies the ID of the software configuration running on a server.                                               |
+---------------+------+--------+-----------+-------------------------------------------------------------------------------------------------------------------+
| input_values  | body | Object | No        | Specifies input data stored in the form of a key-value pair.                                                      |
+---------------+------+--------+-----------+-------------------------------------------------------------------------------------------------------------------+
| output_values | body | Object | No        | Specifies output data stored in the form of a key-value pair.                                                     |
+---------------+------+--------+-----------+-------------------------------------------------------------------------------------------------------------------+
| status        | body | String | No        | Specifies the status of software deployments. Valid values include **COMPLETE**, **IN_PROGRESS**, and **FAILED**. |
+---------------+------+--------+-----------+-------------------------------------------------------------------------------------------------------------------+
| status_reason | body | String | No        | Specifies the cause of the software deployment status.                                                            |
+---------------+------+--------+-----------+-------------------------------------------------------------------------------------------------------------------+

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
| updated_time    | body            | String          | Specifies the update time. The timestamp uses the ISO 8601 format:                                                |
|                 |                 |                 |                                                                                                                   |
|                 |                 |                 | .. code-block::                                                                                                   |
|                 |                 |                 |                                                                                                                   |
|                 |                 |                 |    CCYY-MM-DDThh:mm:ss±hh:mm                                                                                      |
+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------+

Request Example
---------------

.. code-block:: text

   PUT /v1/95d02433133a4c0a87ba6967474a2ad3/software_deployments/3d5ec2a8-7004-43b6-a7f6-542bdbe9d434
   {
       "status": "COMPLETE",
       "output_values": {
           "deploy_stdout": "Writing to /tmp/baaaaa\nWritten to /tmp/baaaaa\n",
           "deploy_stderr": "+ echo Writing to /tmp/baaaaa\n+ echo fooooo\n+ cat /tmp/baaaaa\n+ echo -n The file /tmp/baaaaa contains fooooo for server ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5 during CREATE\n+ echo Written to /tmp/baaaaa\n+ echo Output to stderr\nOutput to stderr\n",
           "deploy_status_code": 0,
           "result": "The file /tmp/baaaaa contains fooooo for server ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5 during CREATE"
       },
       "status_reason": "Outputs received"
   }

Response Example
----------------

.. code-block::

   {
       "software_deployment": {
           "status": "COMPLETE",
           "server_id": "ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5",
           "config_id": "3d5ec2a8-7004-43b6-a7f6-542bdbe9d434",
           "output_values": {
               "deploy_stdout": "Writing to /tmp/baaaaa\nWritten to /tmp/baaaaa\n",
               "deploy_stderr": "+ echo Writing to /tmp/baaaaa\n+ echo fooooo\n+ cat /tmp/baaaaa\n+ echo -n The file /tmp/baaaaa contains fooooo for server ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5 during CREATE\n+ echo Written to /tmp/baaaaa\n+ echo Output to stderr\nOutput to stderr\n",
               "deploy_status_code": 0,
               "result": "The file /tmp/baaaaa contains fooooo for server ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5 during CREATE"
           },
           "input_values": null,
           "action": "CREATE",
           "status_reason": "Outputs received",
           "id": "06e87bcc-33a2-4bce-aebd-533e698282d3",
           "creation_time": "2015-01-31T15:12:36Z",
           "updated_time": "2015-01-31T15:18:21Z"
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
