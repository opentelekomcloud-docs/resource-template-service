:original_name: rts_02_0084.html

.. _rts_02_0084:

OS::Neutron::LBaaS::HealthMonitor
=================================

A resource to handle load balancer health monitors.

This resource creates and manages Neutron LBaaS v2 healthmonitors, which watches status of the load balanced servers.

Required Properties
-------------------

+-----------------------------------+--------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                  |
+===================================+==============================================================================================================+
| delay                             | The minimum time in milliseconds between regular connections of the member.                                  |
|                                   |                                                                                                              |
|                                   | Integer value expected.                                                                                      |
|                                   |                                                                                                              |
|                                   | Can be updated without replacement.                                                                          |
|                                   |                                                                                                              |
|                                   | The value must be in the range 0 to 2147483647, include 0 and 2147483647.                                    |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------+
| max_retries                       | Number of permissible connection failures before changing the member status to INACTIVE.                     |
|                                   |                                                                                                              |
|                                   | Integer value expected.                                                                                      |
|                                   |                                                                                                              |
|                                   | Can be updated without replacement.                                                                          |
|                                   |                                                                                                              |
|                                   | The value must be in the range 1 to 10, include 1 and 10.                                                    |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------+
| pool                              | ID or name of the load balancing pool.                                                                       |
|                                   |                                                                                                              |
|                                   | String value expected.                                                                                       |
|                                   |                                                                                                              |
|                                   | Updates cause replacement.                                                                                   |
|                                   |                                                                                                              |
|                                   | Value must be of type neutron.lbaas.pool                                                                     |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------+
| timeout                           | Maximum number of milliseconds for a monitor to wait for a connection to be established before it times out. |
|                                   |                                                                                                              |
|                                   | Integer value expected.                                                                                      |
|                                   |                                                                                                              |
|                                   | Can be updated without replacement.                                                                          |
|                                   |                                                                                                              |
|                                   | The value must be in the range 0 to 2147483647, include 0 and 2147483647.                                    |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------+
| type                              | One of predefined health monitor types.                                                                      |
|                                   |                                                                                                              |
|                                   | String value expected.                                                                                       |
|                                   |                                                                                                              |
|                                   | Updates cause replacement.                                                                                   |
|                                   |                                                                                                              |
|                                   | Allowed values: PING, TCP, HTTP                                                                              |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------+

Optional Properties
-------------------

+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                         |
+===================================+=====================================================================================================================================================+
| admin_state_up                    | The administrative state of the health monitor.                                                                                                     |
|                                   |                                                                                                                                                     |
|                                   | Boolean value expected.                                                                                                                             |
|                                   |                                                                                                                                                     |
|                                   | Updates are not supported.                                                                                                                          |
|                                   |                                                                                                                                                     |
|                                   | Allowed values: True                                                                                                                                |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
| expected_codes                    | The HTTP status codes expected in response from the member to declare it healthy.                                                                   |
|                                   |                                                                                                                                                     |
|                                   | Specify one of the following values:                                                                                                                |
|                                   |                                                                                                                                                     |
|                                   | -  a single value, such as 200.                                                                                                                     |
|                                   | -  a list, such as 200, 202.                                                                                                                        |
|                                   | -  a range, such as 200 to 204.                                                                                                                     |
|                                   |                                                                                                                                                     |
|                                   | String value expected.                                                                                                                              |
|                                   |                                                                                                                                                     |
|                                   | Can be updated without replacement.                                                                                                                 |
|                                   |                                                                                                                                                     |
|                                   | Defaults to "200".                                                                                                                                  |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
| http_method                       | The HTTP method used for requests by the monitor of type HTTP.                                                                                      |
|                                   |                                                                                                                                                     |
|                                   | String value expected.                                                                                                                              |
|                                   |                                                                                                                                                     |
|                                   | Can be updated without replacement.                                                                                                                 |
|                                   |                                                                                                                                                     |
|                                   | Defaults to "GET".                                                                                                                                  |
|                                   |                                                                                                                                                     |
|                                   | Allowed values: GET, HEAD, POST, PUT, DELETE, TRACE, OPTIONS, CONNECT, PATCH                                                                        |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
| tenant_id                         | ID of the tenant who owns the health monitor.                                                                                                       |
|                                   |                                                                                                                                                     |
|                                   | String value expected.                                                                                                                              |
|                                   |                                                                                                                                                     |
|                                   | Updates cause replacement.                                                                                                                          |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
| url_path                          | The HTTP path used in the HTTP request used by the monitor to test a member health. A valid value is a string that begins with a forward slash (/). |
|                                   |                                                                                                                                                     |
|                                   | String value expected.                                                                                                                              |
|                                   |                                                                                                                                                     |
|                                   | Can be updated without replacement.                                                                                                                 |
|                                   |                                                                                                                                                     |
|                                   | Defaults to "/".                                                                                                                                    |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

Attributes
----------

===== ==========================================
Name  Description
===== ==========================================
pools The list of Pools related to this monitor.
===== ==========================================

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Neutron::LBaaS::HealthMonitor
       properties:
         admin_state_up: Boolean
         delay: Integer
         expected_codes: String
         http_method: String
         max_retries: Integer
         pool: String
         tenant_id: String
         timeout: Integer
         type: String
         url_path: String
