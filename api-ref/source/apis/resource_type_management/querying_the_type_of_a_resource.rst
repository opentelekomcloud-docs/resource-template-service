:original_name: rts_03_0046.html

.. _rts_03_0046:

Querying the Type of a Resource
===============================

Function
--------

This API is used to query the type of a resource.

URI
---

GET /v1/{project_id}/resource_types/{type_name}

For details about the parameters, see :ref:`Table 1 <rts_03_0046__table1759528275>`.

.. _rts_03_0046__table1759528275:

.. table:: **Table 1** Parameter description

   ========== ====== ========= =================================
   Parameter  Type   Mandatory Description
   ========== ====== ========= =================================
   project_id String Yes       Specifies the project ID.
   type_name  String Yes       Specifies the resource type name.
   ========== ====== ========= =================================

Request Parameter
-----------------

N/A

Response Parameter
------------------

+----------------+------+--------+------------------------------------------------------------------------+
| Parameter      | In   | Type   | Description                                                            |
+================+======+========+========================================================================+
| attributes     | body | Dict   | Specifies the resource feature dictionary.                             |
+----------------+------+--------+------------------------------------------------------------------------+
| properties     | body | Dict   | Specifies the resource attributes, including the description and type. |
+----------------+------+--------+------------------------------------------------------------------------+
| resource_type  | body | String | Specifies the resource type.                                           |
+----------------+------+--------+------------------------------------------------------------------------+
| support_status | body | Dict   | Specifies the current status.                                          |
+----------------+------+--------+------------------------------------------------------------------------+

Request Example
---------------

.. code-block:: text

   GET /v1/95d02433133a4c0a87ba6967474a2ad3/resource_types/OS%3A%3AHeat%3A%3ARandomString

Response Example
----------------

.. code-block::

   {
       "attributes": {
           "an_attribute": {
               "description": "A runtime value of the resource."
           }
       },
       "properties": {
           "a_property": {
               "constraints": [
                   {
                       "description": "Must be between 1 and 255 characters",
                       "length": {
                           "max": 255,
                           "min": 1
                       }
                   }
               ],
               "description": "A resource description.",
               "required": true,
               "type": "string",
               "update_allowed": false
           }
       },
       "resource_type": "OS::Heat::AResourceName",
       "support_status": {
           "message": "A status message",
           "status": "SUPPORTED",
           "version": "2014.1"
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
