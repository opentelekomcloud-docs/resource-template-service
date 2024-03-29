:original_name: rts_03_0060.html

.. _rts_03_0060:

Viewing Metadata Configured on a Server
=======================================

Function
--------

This API is used to view the metadata configured on a server.

URI
---

GET /v1/{project_id}/software_deployments/metadata/{server_id}

For details about the parameters, see :ref:`Table 1 <rts_03_0060__table1759528275>`.

.. _rts_03_0060__table1759528275:

.. table:: **Table 1** Parameter description

   ========== ====== ========= ===============================
   Parameter  Type   Mandatory Description
   ========== ====== ========= ===============================
   project_id String Yes       Specifies the project ID.
   server_id  String Yes       Specifies the target server ID.
   ========== ====== ========= ===============================

Request Parameter
-----------------

N/A

Response Parameter
------------------

========= ==== =========== ===========================================
Parameter In   Type        Description
========= ==== =========== ===========================================
metadata  body List <dict> Specifies the software deployment metadata.
========= ==== =========== ===========================================

**metadata** structure information

+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
| Parameter       | In              | Type            | Description                                                                               |
+=================+=================+=================+===========================================================================================+
| config          | body            | String          | Specifies the configuration script or list.                                               |
+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
| creation_time   | body            | String          | Specifies the creation time. The timestamp uses the ISO 8601 format:                      |
|                 |                 |                 |                                                                                           |
|                 |                 |                 | .. code-block::                                                                           |
|                 |                 |                 |                                                                                           |
|                 |                 |                 |    CCYY-MM-DDThh:mm:ss±hh:mm                                                              |
+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
| group           | body            | String          | Specifies the name of the software configuration group.                                   |
+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
| id              | body            | String          | Specifies the software configuration UUID.                                                |
+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
| inputs          | body            | List <dict>     | Specifies the software configuration input.                                               |
+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
| name            | body            | String          | Specifies the name of the software configuration.                                         |
+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
| options         | body            | String          | Contains mapping for the options of the software management tool that this resource uses. |
+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
| outputs         | body            | List <dict>     | Specifies the software configuration output.                                              |
+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+
| updated_time    | body            | String          | Specifies the update time. The timestamp uses the ISO 8601 format:                        |
|                 |                 |                 |                                                                                           |
|                 |                 |                 | .. code-block::                                                                           |
|                 |                 |                 |                                                                                           |
|                 |                 |                 |    CCYY-MM-DDThh:mm:ss±hh:mm                                                              |
+-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------+

Request Example
---------------

.. code-block:: text

   GET /v1/95d02433133a4c0a87ba6967474a2ad3/software_deployments/metadata/6a5eca38-6a04-4b26-6af5-543cdbd3d5e4

Response Example
----------------

.. code-block::

   {
       "metadata": [
           {
               "inputs": [
                   {
                       "default": null,
                       "type": "String",
                       "name": "foo",
                       "value": "fooooo",
                       "description": null
                   },
                   {
                       "default": null,
                       "type": "String",
                       "name": "bar",
                       "value": "baaaaa",
                       "description": null
                   },
                   {
                       "type": "String",
                       "name": "deploy_server_id",
                       "value": "ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5",
                       "description": "ID of the server being deployed to"
                   },
                   {
                       "type": "String",
                       "name": "deploy_action",
                       "value": "CREATE",
                       "description": "Name of the current action being deployed"
                   },
                   {
                       "type": "String",
                       "name": "deploy_stack_id",
                       "value": "a/9bd57090-8954-48ab-bab9-adf9e1ac70fc",
                       "description": "ID of the stack this deployment belongs to"
                   },
                   {
                       "type": "String",
                       "name": "deploy_resource_name",
                       "value": "deployment",
                       "description": "Name of this deployment resource in the stack"
                    },
                   {
                       "type": "String",
                       "name": "deploy_signal_id",
                       "value": "http://x.x.x.x:8000/v1/signal/arn%3Aopenstack%3Aheat%3A%3Ae2a84fbdaeb047ae8da4b503f3b69f1f%3Astacks%2Fa%2F9bd57090-8954-48ab-bab9-adf9e1ac70fc%2Fresources%2Fdeployment?Timestamp=2014-03-19T20%3A30%3A59Z&SignatureMethod=HmacSHA256&AWSAccessKeyId=ca3571413e4a49998d580215517b3685&SignatureVersion=2&Signature=w6Iu%2BNbg86mqwSOUf1GLuKPO7KaD82PiGpL4ig9Q1l4%3D",
                       "description": "ID of signal to use for signalling output values"
                   }
               ],
               "group": "script",
               "name": "a-config-we5zpvyu7b5o",
               "outputs": [
                   {
                       "type": "String",
                       "name": "result",
                       "error_output": false,
                       "description": null
                   }
               ],
               "options": null,
               "creation_time": "2015-01-31T15:12:36Z",
               "updated_time": "2015-01-31T15:18:21Z",
               "config": "#!/bin/sh -x\necho \"Writing to /tmp/$bar\"\necho $foo > /tmp/$bar\necho -n \"The file /tmp/$bar contains `cat /tmp/$bar` for server $deploy_server_id during $deploy_action\" > $heat_outputs_path.result\necho \"Written to /tmp/$bar\"\necho \"Output to stderr\" 1>&2",
               "id": "3d5ec2a8-7004-43b6-a7f6-542bdbe9d434"
           },
           {
               "inputs": [
                   {
                       "default": null,
                       "type": "String",
                       "name": "foo",
                       "value": "fu",
                       "description": null
                   },
                   {
                       "default": null,
                       "type": "String",
                       "name": "bar",
                       "value": "barmy",
                       "description": null
                   },
                   {
                       "type": "String",
                       "name": "deploy_server_id",
                       "value": "ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5",
                       "description": "ID of the server being deployed to"
                   },
                   {
                       "type": "String",
                       "name": "deploy_action",
                       "value": "CREATE",
                       "description": "Name of the current action being deployed"
                   },
                   {
                       "type": "String",
                       "name": "deploy_stack_id",
                       "value": "a/9bd57090-8954-48ab-bab9-adf9e1ac70fc",
                       "description": "ID of the stack this deployment belongs to"
                   },
                   {
                       "type": "String",
                       "name": "deploy_resource_name",
                       "value": "other_deployment",
                       "description": "Name of this deployment resource in the stack"
                   },
                   {
                       "type": "String",
                       "name": "deploy_signal_id",
                       "value": "http://x.x.x.x:8000/v1/signal/arn%3Aopenstack%3Aheat%3A%3Ae2a84fbdaeb047ae8da4b503f3b69f1f%3Astacks%2Fa%2F9bd57090-8954-48ab-bab9-adf9e1ac70fc%2Fresources%2Fother_deployment?Timestamp=2014-03-19T20%3A30%3A59Z&SignatureMethod=HmacSHA256&AWSAccessKeyId=7b761482f8254946bcd3d5ccb36fe939&SignatureVersion=2&Signature=giMfv%2BhrAw6y%2FCMKQIQz2IhO5PkAj5%2BfP5YsL6rul3o%3D",
                       "description": "ID of signal to use for signalling output values"
                   }
               ],
               "group": "script",
               "name": "a-config-we5zpvyu7b5o",
               "outputs": [
                   {
                       "type": "String",
                       "name": "result",
                       "error_output": false,
                       "description": null
                   }
               ],
               "options": null,
               "creation_time": "2015-01-31T16:14:13Z",
               "updated_time": "2015-01-31T16:18:19Z",
               "config": "#!/bin/sh -x\necho \"Writing to /tmp/$bar\"\necho $foo > /tmp/$bar\necho -n \"The file /tmp/$bar contains `cat /tmp/$bar` for server $deploy_server_id during $deploy_action\" > $heat_outputs_path.result\necho \"Written to /tmp/$bar\"\necho \"Output to stderr\" 1>&2",
               "id": "8da95794-2ad9-4979-8ae5-739ce314c5cd"
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
