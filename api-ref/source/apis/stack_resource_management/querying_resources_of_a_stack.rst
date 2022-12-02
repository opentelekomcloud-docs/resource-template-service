:original_name: rts_03_0029.html

.. _rts_03_0029:

Querying Resources of a Stack
=============================

Function
--------

This API is used to query resources of a stack.

URI
---

GET /v1/{project_id}/stacks/{stack_name}/{stack_id}/resources

.. note::

   This API supports redirection. During the calling, you can specify only **stack_name** or **stack_id**.

For details about the parameters, see :ref:`Table 1 <rts_03_0029__table1759528275>`.

.. _rts_03_0029__table1759528275:

.. table:: **Table 1** Parameter description

   ========== ====== ========= =========================
   Parameter  Type   Mandatory Description
   ========== ====== ========= =========================
   project_id String Yes       Specifies the project ID.
   stack_name String Yes       Specifies the stack name.
   stack_id   String Yes       Specifies the stack UUID.
   ========== ====== ========= =========================

Request Parameter
-----------------

N/A

Response Parameter
------------------

========= ==== =========== ============================================
Parameter In   Type        Description
========= ==== =========== ============================================
resources body List <dict> Specifies resource information of the stack.
========= ==== =========== ============================================

**resources** structure information

+------------------------+------+-------------+---------------------------------------------------+
| Parameter              | In   | Type        | Description                                       |
+========================+======+=============+===================================================+
| resource_name          | body | String      | Specifies the resource name.                      |
+------------------------+------+-------------+---------------------------------------------------+
| links                  | body | List <dict> | Specifies the resource URL list.                  |
+------------------------+------+-------------+---------------------------------------------------+
| logical_resource_id    | body | String      | Specifies the logical resource ID.                |
+------------------------+------+-------------+---------------------------------------------------+
| physical_resource_id   | body | String      | Specifies the physical resource ID.               |
+------------------------+------+-------------+---------------------------------------------------+
| resource_type          | body | String      | Specifies the resource type.                      |
+------------------------+------+-------------+---------------------------------------------------+
| resource_status        | body | String      | Specifies the resource status.                    |
+------------------------+------+-------------+---------------------------------------------------+
| resource_status_reason | body | String      | Specifies the resource operation reason.          |
+------------------------+------+-------------+---------------------------------------------------+
| updated_time           | body | String      | Specifies the time when the resource was updated. |
+------------------------+------+-------------+---------------------------------------------------+
| creation_time          | body | String      | Specifies the time when the resource was created. |
+------------------------+------+-------------+---------------------------------------------------+
| required_by            | body | List <str>  | Specifies the resource dependency.                |
+------------------------+------+-------------+---------------------------------------------------+

Request Example
---------------

.. code-block:: text

   GET /v1/95d02433133a4c0a87ba6967474a2ad3/stacks/HeatStack/c89c4bb3-96cb-4a55-aafa-076a7939a306/resources

Response Example
----------------

.. code-block::

   {
       "resources": [
           {
               "resource_name": "instacne_port",
               "links": [
                   {
                       "href":  "http://x.x.x.x:8004/v1/95d02433133a4c0a87ba6967474a2ad3/stacks/HeatStack/c89c4bb3-96cb-4a55-aafa-076a7939a306/resources/instacne_port",
                       "rel": "self"
                    },
                   {
                       "href":  "http://x.x.x.x:8004/v1/95d02433133a4c0a87ba6967474a2ad3/stacks/HeatStack/c89c4bb3-96cb-4a55-aafa-076a7939a306",
                       "rel": "stack"
                    }
               ],
               "logical_resource_id": "instacne_port",
               "resource_status_reason": "state changed",
               "updated_time": "2014-01-27T16:28:03Z",
               "required_by": ["my_instance"],
               "resource_status": "RESUME_COMPLETE",
               "physical_resource_id": "202307c7-d10e-4bcf-af85-6253f5d6b022",
               "resource_type": "OS::Neutron::Port"
           },
           {
               "resource_name": "my_instance",
               "links": [
                   {
                       "href":  "http://x.x.x.x:8004/v1/95d02433133a4c0a87ba6967474a2ad3/stacks/HeatStack/c89c4bb3-96cb-4a55-aafa-076a7939a306/resources/my_instance",
                       "rel": "self"
                    },
                   {
                       "href":  "http://x.x.x.x:8004/v1/95d02433133a4c0a87ba6967474a2ad3/stacks/HeatStack/c89c4bb3-96cb-4a55-aafa-076a7939a306",
                       "rel": "stack"
                    }
               ],
               "logical_resource_id": "my_instance",
               "resource_status_reason": "state changed",
               "updated_time": "2014-01-27T16:28:06Z",
               "required_by": [],
               "resource_status": "RESUME_COMPLETE",
               "physical_resource_id": "e722ad16-ff09-4622-aa5c-0466ae4ef8d8",
               "resource_type": "OS::Nova::Server"
           }
       ]
   }

Return Code
-----------

.. table:: **Table 2** Normal return code

   +-------------+-------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Return Code | Type  | Description                                                                                                                                          |
   +=============+=======+======================================================================================================================================================+
   | 200         | OK    | Request was successful.                                                                                                                              |
   +-------------+-------+------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 302         | Found | The response is about redirection. The response header usually contains a location value that allows you to track the real location of the resource. |
   +-------------+-------+------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Error return code

   =========== ============ =========================================
   Return Code Type         Description
   =========== ============ =========================================
   400         Bad Request  The server failed to process the request.
   401         Unauthorized Authorization failed.
   404         Not found    The requested resources are not found.
   =========== ============ =========================================
