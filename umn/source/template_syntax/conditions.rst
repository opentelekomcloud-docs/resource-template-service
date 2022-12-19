:original_name: rts_02_0015.html

.. _rts_02_0015:

Conditions
==========

Conditions are specified in the **conditions** field. This field indicates the conditions that must be met during stack creation and update. You can define one or more conditions based on the parameters entered during stack creation and update.

Conditions can be associated with resources, resource attributes, and outputs. For example, you can create resources, set different attribute values, and provide stack outputs based on conditions.

Syntax
------

The syntax of conditions is as follows:

.. code-block::

   conditions:
     <condition name1>: {expression1}
     <condition name2>: {expression2}
     ...

**condition name**

Indicates the condition name, which is unique in the template.

**expression**

Indicates an expression that is expected to return **True** or **False**. Generally, conditional functions can be used as expressions, such as EQUALS, NOT, and AND.

The following provides an example:

.. code-block::

   parameters:
     env_type:
       default: test
       type: string
   conditions:
     create_prod_res: {equals : [{get_param: env_type}, "prod"]}
   resources:
     volume:
       type: OS::Cinder::Volume
       condition: create_prod_res
       properties:
         size: 1
   outputs:
     vol_size:
       value: {get_attr: [my_volume, size]}
       condition: create_prod_res

**volume** in **resources** and **vol_size** in **outputs** are both associated with the **create_prod_res** condition. It can be judged according to the definition of the **create_prod_res** condition that, **volume** is created and **vol_size** is output only when **env_type** is set to **prod**.
