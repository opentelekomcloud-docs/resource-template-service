:original_name: rts_02_0074.html

.. _rts_02_0074:

OS::Nova::ServerGroup
=====================

A resource for managing a Nova server group.

Server groups allow you to make sure instances are on the same hypervisor host or on a different one.

Optional Properties
-------------------

+-----------------------------------+----------------------------------------------------------------+
| Name                              | Description                                                    |
+===================================+================================================================+
| name                              | Server Group name.                                             |
|                                   |                                                                |
|                                   | String value expected.                                         |
|                                   |                                                                |
|                                   | Updates cause replacement.                                     |
+-----------------------------------+----------------------------------------------------------------+
| policies                          | A list of string policies to apply. Defaults to anti-affinity. |
|                                   |                                                                |
|                                   | List value expected.                                           |
|                                   |                                                                |
|                                   | Updates cause replacement.                                     |
|                                   |                                                                |
|                                   | Defaults to "['anti-affinity']".                               |
|                                   |                                                                |
|                                   | Allowed values: anti-affinity, affinity                        |
+-----------------------------------+----------------------------------------------------------------+

Attributes
----------

==== ====================================
Name Description
==== ====================================
show Detailed information about resource.
==== ====================================

HOT Syntax
----------

.. code-block::

   heat_template_version: 2015-04-30
   ...
   resources:
     ...
     the_resource:
       type: OS::Nova::ServerGroup
       properties:
         name: String
         policies: [String, String, ...]
