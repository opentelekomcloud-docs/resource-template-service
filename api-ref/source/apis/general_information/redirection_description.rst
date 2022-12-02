:original_name: rts_03_0016.html

.. _rts_03_0016:

Redirection Description
=======================

Redirect
--------

In the Heat API, the stack ID consists of **stack_name** and **stack_id**. When the system calls APIs to access resources such as stacks, templates, events, and actions, if only **stack_name** is specified, Heat queries the **stack_id** value and returns a redirect response pointing to the correct URL. The following provides a request example:

.. code-block:: text

   GET /v1/95d02433133a4c0a87ba6967474a2ad3/stacks/HeatStack

After redirection, the actual request is as follows:

.. code-block::

   Location: http://x.x.x.x:8004/v1/95d02433133a4c0a87ba6967474a2ad3/stacks/HeatStack/c89c4bb3-96cb-4a55-aafa-076a7939a306

Redirect APIs
-------------

The APIs used in the following topics support redirection. When calling the following APIs to access stacks or templates, you can specify only **stack_name** or **stack_id**.

-  :ref:`Querying Details of a Stack <rts_03_0025>`
-  :ref:`Querying Resources of a Stack <rts_03_0029>`
-  :ref:`Querying Events of a Stack <rts_03_0038>`
-  :ref:`Querying a Stack Template <rts_03_0043>`
