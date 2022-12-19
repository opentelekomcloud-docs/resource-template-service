:original_name: rts_03_0052.html

.. _rts_03_0052:

Querying Software Configurations
================================

Function
--------

This API is used to query the software configurations.

URI
---

GET /v1/{project_id}/software_configs

For details about the parameters, see :ref:`Table 1 <rts_03_0052__table1759528275>`.

.. _rts_03_0052__table1759528275:

.. table:: **Table 1** Parameter description

   ========== ====== ========= =========================
   Parameter  Type   Mandatory Description
   ========== ====== ========= =========================
   project_id String Yes       Specifies the project ID.
   ========== ====== ========= =========================

Request Parameter
-----------------

+-----------+-------+--------+-----------+--------------------------------------------------------------------------------------------+
| Parameter | In    | Type   | Mandatory | Description                                                                                |
+===========+=======+========+===========+============================================================================================+
| limit     | query | String | No        | Specifies the number of returned software configurations.                                  |
+-----------+-------+--------+-----------+--------------------------------------------------------------------------------------------+
| marker    | query | String | No        | Specifies the software configuration from which the next data record starts to be queried. |
+-----------+-------+--------+-----------+--------------------------------------------------------------------------------------------+

Response Parameter
------------------

+------------------+------+-------------+-----------------------------------------------+
| Parameter        | In   | Type        | Description                                   |
+==================+======+=============+===============================================+
| software_configs | body | List <dict> | Specifies the software configuration objects. |
+------------------+------+-------------+-----------------------------------------------+

**software_configs** structure information

+-----------------+-----------------+-----------------+----------------------------------------------------------------------+
| Parameter       | In              | Type            | Description                                                          |
+=================+=================+=================+======================================================================+
| creation_time   | body            | String          | Specifies the creation time. The timestamp uses the ISO 8601 format: |
|                 |                 |                 |                                                                      |
|                 |                 |                 | .. code-block::                                                      |
|                 |                 |                 |                                                                      |
|                 |                 |                 |    CCYY-MM-DDThh:mm:ss±hh:mm                                         |
+-----------------+-----------------+-----------------+----------------------------------------------------------------------+
| group           | body            | String          | Specifies the name of the software configuration group.              |
+-----------------+-----------------+-----------------+----------------------------------------------------------------------+
| id              | body            | String          | Specifies the software configuration UUID.                           |
+-----------------+-----------------+-----------------+----------------------------------------------------------------------+
| name            | body            | String          | Specifies the name of the software configuration.                    |
+-----------------+-----------------+-----------------+----------------------------------------------------------------------+

Request Example
---------------

.. code-block:: text

   GET /v1/95d02433133a4c0a87ba6967474a2ad3/software_configs

Response Example
----------------

.. code-block::

   {
       "software_configs": [
           {
               "group": "script",
               "name": "a-config-we5zpvyu7b5o",
               "creation_time": "2015-01-31T15:12:36Z",
               "id": "ddee7aca-aa32-4335-8265-d436b20db4f1",
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
