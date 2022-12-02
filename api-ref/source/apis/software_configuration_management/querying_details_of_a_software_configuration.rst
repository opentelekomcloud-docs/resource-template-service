:original_name: rts_03_0053.html

.. _rts_03_0053:

Querying Details of a Software Configuration
============================================

Function
--------

This API is used to query details of a software configuration.

URI
---

GET /v1/{project_id}/software_configs/{config_id}

For details about the parameters, see :ref:`Table 1 <rts_03_0053__table1759528275>`.

.. _rts_03_0053__table1759528275:

.. table:: **Table 1** Parameter description

   ========== ====== ========= ==========================================
   Parameter  Type   Mandatory Description
   ========== ====== ========= ==========================================
   project_id String Yes       Specifies the project ID.
   config_id  String Yes       Specifies the software configuration UUID.
   ========== ====== ========= ==========================================

Request Parameter
-----------------

N/A

Response Parameter
------------------

=============== ==== ==== ==========================================
Parameter       In   Type Description
=============== ==== ==== ==========================================
software_config body Dict Specifies the software configuration list.
=============== ==== ==== ==========================================

**software_config** structure information

+---------------+------+-------------+---------------------------------------------------------+
| Parameter     | In   | Type        | Description                                             |
+===============+======+=============+=========================================================+
| inputs        | body | List <dict> | Specifies the software configuration input.             |
+---------------+------+-------------+---------------------------------------------------------+
| name          | body | String      | Specifies the name of the software configuration.       |
+---------------+------+-------------+---------------------------------------------------------+
| outputs       | body | List <dict> | Specifies the software configuration output.            |
+---------------+------+-------------+---------------------------------------------------------+
| creation_time | body | Date Time   | Specifies the time when a configuration is created.     |
+---------------+------+-------------+---------------------------------------------------------+
| group         | body | String      | Specifies the name of the software configuration group. |
+---------------+------+-------------+---------------------------------------------------------+
| config        | body | String      | Specifies the software configuration code.              |
+---------------+------+-------------+---------------------------------------------------------+
| options       | body | String      | Specifies configuration options.                        |
+---------------+------+-------------+---------------------------------------------------------+
| id            | body | String      | Specifies the software configuration UUID.              |
+---------------+------+-------------+---------------------------------------------------------+

Request Example
---------------

.. code-block:: text

   GET /v1/95d02433133a4c0a87ba6967474a2ad3/software_configs/40p72423093a900a8b7a669768421a6a

Response Example
----------------

.. code-block::

   {
       "software_config": {
           "inputs": [
               {
                   "default": null,
                   "type": "String",
                   "name": "foo",
                   "description": null
               },
               {
                   "default": null,
                   "type": "String",
                   "name": "bar",
                   "description": null
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
           "creation_time": "2015-01-31T15:12:36Z",
           "id": "ddee7aca-aa32-4335-8265-d436b20db4f1",
           "config": "#!/bin/sh -x\necho \"Writing to /tmp/$bar\"\necho $foo > /tmp/$bar\necho -n \"The file /tmp/$bar contains `cat /tmp/$bar` for server $deploy_server_id during $deploy_action\" > $heat_outputs_path.result\necho \"Written to /tmp/$bar\"\necho \"Output to stderr\" 1>&2",
           "options": null
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
