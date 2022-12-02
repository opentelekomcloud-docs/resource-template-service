:original_name: rts_03_0030.html

.. _rts_03_0030:

Querying Details of a Stack Resource
====================================

Function
--------

This API is used to query details of a stack resource.

URI
---

GET /v1/{project_id}/stacks/{stack_name}/{stack_id}/resources/{resource_name}

For details about the parameters, see :ref:`Table 1 <rts_03_0030__table1759528275>`.

.. _rts_03_0030__table1759528275:

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

N/A

Response Parameter
------------------

========= ==== ==== ============================================
Parameter In   Type Description
========= ==== ==== ============================================
resource  body Dict Specifies resource information of the stack.
========= ==== ==== ============================================

**resource** structure information

+------------------------+-----------------+-----------------+-----------------------------------------------------+
| Parameter              | In              | Type            | Description                                         |
+========================+=================+=================+=====================================================+
| resource_name          | body            | String          | Specifies the resource name.                        |
+------------------------+-----------------+-----------------+-----------------------------------------------------+
| description            | body            | String          | Describes the resource.                             |
+------------------------+-----------------+-----------------+-----------------------------------------------------+
| links                  | body            | List <dict>     | Specifies the resource URL list.                    |
+------------------------+-----------------+-----------------+-----------------------------------------------------+
| logical_resource_id    | body            | String          | Specifies the logical resource ID.                  |
+------------------------+-----------------+-----------------+-----------------------------------------------------+
| creation_time          | body            | String          | Specifies the time of creating the stack resource.  |
|                        |                 |                 |                                                     |
|                        |                 |                 | Example: 2019-04-30T02:55:48.869333                 |
+------------------------+-----------------+-----------------+-----------------------------------------------------+
| physical_resource_id   | body            | String          | Specifies the physical resource ID.                 |
+------------------------+-----------------+-----------------+-----------------------------------------------------+
| attributes             | body            | Object          | Includes key-value pairs of the resource attribute. |
+------------------------+-----------------+-----------------+-----------------------------------------------------+
| resource_type          | body            | String          | Specifies the resource type.                        |
+------------------------+-----------------+-----------------+-----------------------------------------------------+
| resource_status        | body            | String          | Specifies the resource status.                      |
+------------------------+-----------------+-----------------+-----------------------------------------------------+
| resource_status_reason | body            | String          | Specifies the resource operation reason.            |
+------------------------+-----------------+-----------------+-----------------------------------------------------+
| updated_time           | body            | String          | Specifies the time when the resource was updated.   |
+------------------------+-----------------+-----------------+-----------------------------------------------------+
| required_by            | body            | List <str>      | Specifies the resource dependency.                  |
+------------------------+-----------------+-----------------+-----------------------------------------------------+

Request Example
---------------

.. code-block:: text

   GET /v1/6e0193034db54600b889f890768a72ea/stacks/stack-0vi3/63a16fbe-717b-417c-a3e5-08fc51544b49/resources/random-group

Response Example
----------------

.. code-block::

   {
       "resource": {
           "attributes": {
               "attributes": null,
               "refs": null
           },
           "creation_time": "2019-03-04T06:36:45.455761",
           "description": "",
           "links": [
               {
                   "href": "https://orchestration.localdomain.com:8004/v1/6e0193034db54600b889f890768a72ea/stacks/stack-0vi3/63a16fbe-717b-417c-a3e5-08fc51544b49/resources/random-group",
                   "rel": "self"
               },
               {
                   "href": "https://orchestration.localdomain.com:8004/v1/6e0193034db54600b889f890768a72ea/stacks/stack-0vi3/63a16fbe-717b-417c-a3e5-08fc51544b49",
                   "rel": "stack"
               },
               {
                   "href": "https://orchestration.localdomain.com:8004/v1/6e0193034db54600b889f890768a72ea/stacks/stack-0vi3-random-group-k7emexipm2k6/2b6d0d58-0a7b-45d7-978f-519d0b1395ce",
                   "rel": "nested"
               }
           ],
           "logical_resource_id": "random-group",
           "physical_resource_id": "2b6d0d58-0a7b-45d7-978f-519d0b1395ce",
           "required_by": [],
           "resource_name": "random-group",
           "resource_status": "CREATE_COMPLETE",
           "resource_status_reason": "state changed",
           "resource_type": "OS::Heat::ResourceGroup",
           "updated_time": "2019-03-04T06:36:45.455761"
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
