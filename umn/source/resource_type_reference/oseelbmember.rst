:original_name: rts_02_0082.html

.. _rts_02_0082:

OSE::ELB::Member
================

A resource for member.

Required Properties
-------------------

+-----------------------------------+-------------------------------------------------+
| Name                              | Description                                     |
+===================================+=================================================+
| listener_id                       | The ID of listener associated.                  |
|                                   |                                                 |
|                                   | String value expected.                          |
|                                   |                                                 |
|                                   | Updates cause replacement.                      |
|                                   |                                                 |
|                                   | Value must be of type elb.ls                    |
+-----------------------------------+-------------------------------------------------+
| members                           | The servers to add as members.                  |
|                                   |                                                 |
|                                   | List value expected.                            |
|                                   |                                                 |
|                                   | Can be updated without replacement.             |
|                                   |                                                 |
|                                   | Value length: from 1 to 6, include 1 and 6.     |
|                                   |                                                 |
|                                   | List contents:                                  |
|                                   |                                                 |
|                                   | -  \*                                           |
|                                   |                                                 |
|                                   |    Map value expected.                          |
|                                   |                                                 |
|                                   |    Can be updated without replacement.          |
|                                   |                                                 |
|                                   |    Map properties:                              |
|                                   |                                                 |
|                                   |    -  address                                   |
|                                   |                                                 |
|                                   |       The private address of the server to add. |
|                                   |                                                 |
|                                   |       String value expected.                    |
|                                   |                                                 |
|                                   |       Can be updated without replacement.       |
|                                   |                                                 |
|                                   |    -  server_id                                 |
|                                   |                                                 |
|                                   |       ID of the server to add.                  |
|                                   |                                                 |
|                                   |       String value expected.                    |
|                                   |                                                 |
|                                   |       Can be updated without replacement.       |
|                                   |                                                 |
|                                   |       Value must be of type nova.server         |
+-----------------------------------+-------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OSE::ELB::Member
       properties:
         listener_id: String
         members: [{"address": String, "server_id": String}, {"address": String, "server_id": String}, …]
