:original_name: rts_02_0010.html

.. _rts_02_0010:

Template Version
================

The **heat_template_version** field indicates the template version. Each HOT template includes the **heat_template_version** field that specifies the template version. Different HOT template versions support different internal functions. RTS supports the following HOT template versions:

-  heat_template_version 2013-05-23:

   The **heat_template_version 2013-05-23** template supports the following internal functions:

   **get_attr**, **get_file**, **get_param**, **get_resource**, **list_join**, **resource_facade**, **str_replace**, **Fn::Base64**, **Fn::GetAZs**, **Fn::Join**, **Fn::MemberListToMap**, **Fn::Replace**, **Fn::ResourceFacade**, **Fn::Select**, **Fn::Split**, and **Ref**

-  heat_template_version 2014-10-16:

   The **heat_template_version 2014-10-16** template supports the following internal functions:

   **get_attr**, **get_file**, **get_param**, **get_resource**, **list_join**, **resource_facade**, **str_replace**, and **Fn::Select**

-  heat_template_version 2015-04-30:

   The **heat_template_version 2015-04-30** template supports the following internal functions:

   **get_attr**, **get_file**, **get_param**, **get_resource**, **list_join**, **repeat**, **digest**, **resource_facade**, **str_replace**, and **Fn::Select**

-  heat_template_version 2015-10-15:

   The **heat_template_version 2015-10-15** template supports the following internal functions:

   **get_attr**, **get_file**, **get_param**, **get_resource**, **list_join**, **repeat**, **digest**, **resource_facade**, **str_replace**, and **str_split**

-  heat_template_version 2016-04-08:

   The **heat_template_version 2016-04-08** template supports the following internal functions:

   **digest**, **get_attr**, **get_file**, **get_param**, **get_resource**, **list_join**, **map_merge**, **repeat**, **resource_facade**, **str_replace**, and **str_split**
