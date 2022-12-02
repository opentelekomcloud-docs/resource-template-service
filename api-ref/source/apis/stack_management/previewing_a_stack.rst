:original_name: rts_03_0022.html

.. _rts_03_0022:

Previewing a Stack
==================

Function
--------

This API is used to preview a stack.

URI
---

POST /v1/{project_id}/stacks/preview

For details about the parameters, see :ref:`Table 1 <rts_03_0022__table1759528275>`.

.. _rts_03_0022__table1759528275:

.. table:: **Table 1** Parameter description

   ========== ====== ========= =========================
   Parameter  Type   Mandatory Description
   ========== ====== ========= =========================
   project_id String Yes       Specifies the project ID.
   ========== ====== ========= =========================

Request Parameter
-----------------

+------------------+-------------+-------------+-------------+----------------------------------------------------------------------------------------------------------------------------+
| Parameter        | In          | Type        | Mandatory   | Description                                                                                                                |
+==================+=============+=============+=============+============================================================================================================================+
| stack_name       | body        | String      | Yes         | Specifies the stack name.                                                                                                  |
|                  |             |             |             |                                                                                                                            |
|                  |             |             |             | -  The value can contain only uppercase letters, lowercase letters, digits, hyphens (-), periods (.), and underscores (_). |
|                  |             |             |             | -  The value must start with an uppercase letter or a lowercase letter.                                                    |
|                  |             |             |             | -  The value can contain 1 to 255 characters.                                                                              |
+------------------+-------------+-------------+-------------+----------------------------------------------------------------------------------------------------------------------------+
| template_url     | body        | String      | No          | Specifies the template URL. You cannot select a template using the URL temporarily.                                        |
+------------------+-------------+-------------+-------------+----------------------------------------------------------------------------------------------------------------------------+
| template         | body        | Dict        | Yes         | Specifies the template. The template content must use the YAML syntax.                                                     |
+------------------+-------------+-------------+-------------+----------------------------------------------------------------------------------------------------------------------------+
| files            | body        | Dict        | No          | Specifies the files referenced in the environment.                                                                         |
+------------------+-------------+-------------+-------------+----------------------------------------------------------------------------------------------------------------------------+
| disable_rollback | body        | Boolean     | No          | Specifies whether to perform a rollback when stack creation fails.                                                         |
+------------------+-------------+-------------+-------------+----------------------------------------------------------------------------------------------------------------------------+
| parameters       | body        | Dict        | No          | Specifies parameter information of the stack.                                                                              |
+------------------+-------------+-------------+-------------+----------------------------------------------------------------------------------------------------------------------------+

Response Parameter
------------------

========= ==== ==== ===========================
Parameter In   Type Description
========= ==== ==== ===========================
stack     body Dict Specifies the stack object.
========= ==== ==== ===========================

**stack** structure information

+----------------------+------+-------------+--------------------------------------------------------------------+
| Parameter            | In   | Type        | Description                                                        |
+======================+======+=============+====================================================================+
| parent               | body | String      | Specifies the UUID of the parent stack (for a nested stack).       |
+----------------------+------+-------------+--------------------------------------------------------------------+
| id                   | body | String      | Specifies the stack UUID.                                          |
+----------------------+------+-------------+--------------------------------------------------------------------+
| links                | body | List <dict> | Specifies the stack URL list.                                      |
+----------------------+------+-------------+--------------------------------------------------------------------+
| stack_name           | body | String      | Specifies the stack name.                                          |
+----------------------+------+-------------+--------------------------------------------------------------------+
| description          | body | String      | Describes the stack.                                               |
+----------------------+------+-------------+--------------------------------------------------------------------+
| template_description | body | String      | Describes the template defined by the stack.                       |
+----------------------+------+-------------+--------------------------------------------------------------------+
| timeout_mins         | body | Int         | Specifies the timeout duration.                                    |
+----------------------+------+-------------+--------------------------------------------------------------------+
| disable_rollback     | body | Boolean     | Specifies whether to perform a rollback when stack creation fails. |
+----------------------+------+-------------+--------------------------------------------------------------------+
| capabilities         | body | List        | Specifies the list of stack capacities.                            |
+----------------------+------+-------------+--------------------------------------------------------------------+
| creation_time        | body | Date Time   | Specifies the time when the stack was created.                     |
+----------------------+------+-------------+--------------------------------------------------------------------+
| notification_topics  | body | List        | Specifies the message notification list of the stack.              |
+----------------------+------+-------------+--------------------------------------------------------------------+
| updated_time         | body | Date Time   | Specifies the last time when the stack was updated.                |
+----------------------+------+-------------+--------------------------------------------------------------------+
| stack_owner          | body | Sting       | Specifies the name of the stack owner.                             |
+----------------------+------+-------------+--------------------------------------------------------------------+
| parameters           | body | Dict        | Specifies parameters defined by the stack.                         |
+----------------------+------+-------------+--------------------------------------------------------------------+
| resources            | body | List <dict> | Specifies the stack resource list.                                 |
+----------------------+------+-------------+--------------------------------------------------------------------+

Request Example
---------------

.. code-block:: text

   POST /v1/95d02433133a4c0a87ba6967474a2ad3/stacks/preview
   {
       "files": {},
       "disable_rollback": true,
       "parameters": {
           "flavor": "m1.heat"
       },
       "stack_name": "teststack",
       "template": {
           "heat_template_version": "2013-05-23",
           "description": "Simple template to test heat commands",
           "parameters": {
               "flavor": {
                   "default": "m1.tiny",
                   "type": "string"
               }
           },
           "resources": {
               "hello_world": {
                   "type": "OS::Nova::Server",
                   "properties": {
                       "key_name": "heat_key",
                       "flavor": {
                           "get_param": "flavor"
                       },
                       "image": "40be8d1a-3eb9-40de-8abd-43237517384f",
                       "user_data": "#!/bin/bash -xv\necho \"hello world\" &gt; /root/hello-world.txt\n"
                   }
               }
           }
       },
       "timeout_mins": 60
   }

Response Example
----------------

.. code-block::

   {
       "stack": {
           "capabilities": [],
           "creation_time": "2015-01-31T15:12:36Z",
           "description": "HOT template for Nova Server resource.\n",
           "disable_rollback": true,
           "id": "None",
           "links": [
               {
                   "href": "http://x.x.x.x:8004/v1/6e18cc2bdbeb48a5basad2dc499f6804/stacks/test_stack/None",
                   "rel": "self"
               }
           ],
           "notification_topics": [],
           "parameters": {
               "OS::project_id": "6e18cc2bdbeb48a5basad2dc499f6804",
               "OS::stack_id": "None",
               "OS::stack_name": "teststack",
               "admin_user": "cloud-user",
               "flavor": "m1.small",
               "image": "F20-cfg",
               "key_name": "heat_key",
               "server_name": "MyServer"
           },
           "parent": null,
           "resources": [
               {
                   "attributes": {},
                   "description": "",
                   "metadata": {},
                   "physical_resource_id": "",
                   "properties": {
                       "description": "Ping and SSH",
                       "name": "the_sg",
                       "rules": [
                           {
                               "direction": "ingress",
                               "ethertype": "IPv4",
                               "port_range_max": null,
                               "port_range_min": null,
                               "protocol": "icmp",
                               "remote_group_id": null,
                               "remote_ip_prefix": null,
                               "remote_mode": "remote_ip_prefix"
                           },
                           {
                               "direction": "ingress",
                               "ethertype": "IPv4",
                               "port_range_max": 65535,
                               "port_range_min": 1,
                               "protocol": "tcp",
                               "remote_group_id": null,
                               "remote_ip_prefix": null,
                               "remote_mode": "remote_ip_prefix"
                           },
                           {
                               "direction": "ingress",
                               "ethertype": "IPv4",
                               "port_range_max": 65535,
                               "port_range_min": 1,
                               "protocol": "udp",
                               "remote_group_id": null,
                               "remote_ip_prefix": null,
                               "remote_mode": "remote_ip_prefix"
                           }
                       ]
                   },
                   "required_by": [
                       "server1"
                   ],
                   "resource_action": "INIT",
                   "resource_identity": {
                       "path": "/resources/the_sg_res",
                       "stack_id": "None",
                       "stack_name": "teststack",
                       "tenant": "6e18cc2bdbeb48a5b3cad2dc499f6804"
                   },
                   "resource_name": "the_sg_res",
                   "resource_status": "COMPLETE",
                   "resource_status_reason": "",
                   "resource_type": "OS::Neutron::SecurityGroup",
                   "stack_identity": {
                       "path": "",
                       "stack_id": "None",
                       "stack_name": "teststack",
                       "tenant": "6e18cc2bdbeb48a5b3cad2dc499f6804"
                   },
                   "stack_name": "teststack",
                   "updated_time": "2015-01-31T15:12:36Z"
               },
               {
                   "attributes": {
                       "accessIPv4": "",
                       "accessIPv6": "",
                       "addresses": "",
                       "console_urls": "",
                       "first_address": "",
                       "instance_name": "",
                       "name": "MyServer",
                       "networks": "",
                       "show": ""
                   },
                   "description": "",
                   "metadata": {},
                   "physical_resource_id": "",
                   "properties": {
                       "admin_pass": null,
                       "admin_user": "cloud-user",
                       "availability_zone": null,
                       "block_device_mapping": null,
                       "config_drive": null,
                       "diskConfig": null,
                       "flavor": "m1.small",
                       "flavor_update_policy": "RESIZE",
                       "image": "F20-cfg",
                       "image_update_policy": "REPLACE",
                       "key_name": "heat_key",
                       "metadata": {
                           "ha_stack": "None"
                       },
                       "name": "MyServer",
                       "networks": [
                           {
                               "fixed_ip": null,
                               "network": "private",
                               "port": null,
                               "uuid": null
                           }
                       ],
                       "personality": {},
                       "reservation_id": null,
                       "scheduler_hints": null,
                       "security_groups": [
                           "None"
                       ],
                       "software_config_transport": "POLL_SERVER_CFN",
                       "user_data": "",
                       "user_data_format": "HEAT_CFNTOOLS"
                   },
                   "required_by": [],
                   "resource_action": "INIT",
                   "resource_identity": {
                       "path": "/resources/hello_world",
                       "stack_id": "None",
                       "stack_name": "teststack",
                       "tenant": "6e18cc2bdbeb48a3433cad2dc499sdf32234"
                   },
                   "resource_name": "hello_world",
                   "resource_status": "COMPLETE",
                   "resource_status_reason": "",
                   "resource_type": "OS::Nova::Server",
                   "stack_identity": {
                       "path": "",
                       "stack_id": "None",
                       "stack_name": "teststack",
                       "tenant": "6e18cc2bdbeb48a3433cad2dc499sdf32234"
                   },
                   "stack_name": "teststack",
                   "updated_time": "2015-01-31T15:12:36Z"
               }
           ],
           "stack_name": "test_stack",
           "stack_owner": "admin",
           "template_description": "HOT template for Nova Server resource.\n",
           "timeout_mins": null,
           "updated_time": null
       }
   }

Return Code
-----------

.. table:: **Table 2** Normal return code

   =========== ======= ===================================================
   Return Code Type    Description
   =========== ======= ===================================================
   201         Created The resource has been created and is ready for use.
   =========== ======= ===================================================

.. table:: **Table 3** Error return code

   +-------------+-----------------------+----------------------------------------------------------------------+
   | Return Code | Type                  | Description                                                          |
   +=============+=======================+======================================================================+
   | 400         | Bad Request           | The server failed to process the request.                            |
   +-------------+-----------------------+----------------------------------------------------------------------+
   | 401         | Unauthorized          | Authorization failed.                                                |
   +-------------+-----------------------+----------------------------------------------------------------------+
   | 409         | Conflict              | The request could not be processed due to a conflict.                |
   +-------------+-----------------------+----------------------------------------------------------------------+
   | 500         | Internal Server Error | Failed to complete the request because of an internal service error. |
   +-------------+-----------------------+----------------------------------------------------------------------+
