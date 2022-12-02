:original_name: rts_03_0040.html

.. _rts_03_0040:

Querying Events of a Stack Resource
===================================

Function
--------

This API is used to query events of a stack resource.

URI
---

GET /v1/{project_id}/stacks/{stack_name}/{stack_id}/resources/{resource_name}/events

For details about the parameters, see :ref:`Table 1 <rts_03_0040__table1759528275>`.

.. _rts_03_0040__table1759528275:

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

========= ==== =========== ===================================
Parameter In   Type        Description
========= ==== =========== ===================================
events    body List <dict> Specifies the events of a resource.
========= ==== =========== ===================================

**events** structure information

+------------------------+------+-------------+------------------------------------------+
| Parameter              | In   | Type        | Description                              |
+========================+======+=============+==========================================+
| resource_name          | body | String      | Specifies the resource name.             |
+------------------------+------+-------------+------------------------------------------+
| event_time             | body | String      | Specifies the time when an event occurs. |
+------------------------+------+-------------+------------------------------------------+
| links                  | body | List <dict> | Specifies the event URL list.            |
+------------------------+------+-------------+------------------------------------------+
| logical_resource_id    | body | String      | Specifies the logical resource ID.       |
+------------------------+------+-------------+------------------------------------------+
| resource_status_reason | body | String      | Specifies the resource operation reason. |
+------------------------+------+-------------+------------------------------------------+
| resource_status        | body | String      | Specifies the resource status.           |
+------------------------+------+-------------+------------------------------------------+
| physical_resource_id   | body | String      | Specifies the physical resource ID.      |
+------------------------+------+-------------+------------------------------------------+
| id                     | body | String      | Specifies the event ID.                  |
+------------------------+------+-------------+------------------------------------------+

Request Example
---------------

.. code-block:: text

   GET /v1/95d02433133a4c0a87ba6967474a2ad3/stacks/HeatStack/c89c4bb3-96cb-4a55-aafa-076a7939a306/resources/my_instance/events

Response Example
----------------

.. code-block::

   {
       "events": [
           {
               "resource_name": "my_instance",
               "event_time": "2014-01-26T17:21:35Z",
               "links": [
                   {
                       "href":  "http://x.x.x.x:8004/v1/95d02433133a4c0a87ba6967474a2ad3/stacks/HeatStack/c89c4bb3-96cb-4a55-aafa-076a7939a306/resources/my_instance/events/1304",
                       "rel": "self"
                   }
               ],
               "logical_resource_id": "instacne_port",
               "resource_status_reason": "state changed",
               "resource_status": "CREATE_IN_PROGRESS",
               "physical_resource_id": null,
               "id": "1302"
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

   =========== ============ =========================================
   Return Code Type         Description
   =========== ============ =========================================
   400         Bad Request  The server failed to process the request.
   401         Unauthorized Authorization failed.
   404         Not found    The requested resources are not found.
   =========== ============ =========================================
