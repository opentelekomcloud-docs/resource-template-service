:original_name: rts_02_0081.html

.. _rts_02_0081:

OSE::ELB::HealthCheck
=====================

A resource for ELB Health Check.

.. note::

   You must configure health checks for load balancers.

Required Properties
-------------------

+-----------------------------------+-----------------------------------+
| Name                              | Description                       |
+===================================+===================================+
| listener_id                       | The ID of listener associated.    |
|                                   |                                   |
|                                   | String value expected.            |
|                                   |                                   |
|                                   | Updates cause replacement.        |
|                                   |                                   |
|                                   | Value must be of type elb.ls      |
+-----------------------------------+-----------------------------------+

Optional Properties
-------------------

+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                        |
+===================================+====================================================================================================================================================================+
| healthcheck_connect_port          | The port of the health check.                                                                                                                                      |
|                                   |                                                                                                                                                                    |
|                                   | Integer value expected.                                                                                                                                            |
|                                   |                                                                                                                                                                    |
|                                   | Can be updated without replacement.                                                                                                                                |
|                                   |                                                                                                                                                                    |
|                                   | Allowed values: from 1 to 65535, include 1 and 65535.                                                                                                              |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| healthcheck_interval              | The interval between the health checks in seconds.                                                                                                                 |
|                                   |                                                                                                                                                                    |
|                                   | Integer value expected.                                                                                                                                            |
|                                   |                                                                                                                                                                    |
|                                   | Can be updated without replacement.                                                                                                                                |
|                                   |                                                                                                                                                                    |
|                                   | Allowed values: from 1 to 5, include 1 and 5.                                                                                                                      |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| healthcheck_protocol              | The protocol of the health check.                                                                                                                                  |
|                                   |                                                                                                                                                                    |
|                                   | String value expected.                                                                                                                                             |
|                                   |                                                                                                                                                                    |
|                                   | Can be updated without replacement.                                                                                                                                |
|                                   |                                                                                                                                                                    |
|                                   | Allowed values: HTTP, TCP                                                                                                                                          |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| healthcheck_timeout               | The timeout of the health check in seconds.                                                                                                                        |
|                                   |                                                                                                                                                                    |
|                                   | Integer value expected.                                                                                                                                            |
|                                   |                                                                                                                                                                    |
|                                   | Can be updated without replacement.                                                                                                                                |
|                                   |                                                                                                                                                                    |
|                                   | Allowed values: from 1 to 50, include 1 and 50.                                                                                                                    |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| healthcheck_uri                   | The HTTP path used in the HTTP request to check a member health.                                                                                                   |
|                                   |                                                                                                                                                                    |
|                                   | String value expected.                                                                                                                                             |
|                                   |                                                                                                                                                                    |
|                                   | Can be updated without replacement.                                                                                                                                |
|                                   |                                                                                                                                                                    |
|                                   | It is allowed to start with **/** characters. It is allowed to include **numbers**, **letters**, **-/.%?#&** characters, and the string length is **1** to **80**. |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| healthy_threshold                 | The number of the successful threshold before change the member status to healthy.                                                                                 |
|                                   |                                                                                                                                                                    |
|                                   | Integer value expected.                                                                                                                                            |
|                                   |                                                                                                                                                                    |
|                                   | Can be updated without replacement.                                                                                                                                |
|                                   |                                                                                                                                                                    |
|                                   | Allowed values: from 1 to 10, include 1 and 10. The default value is **3**.                                                                                        |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| unhealthy_threshold               | The number of the failure threshold before change the member status to unhealthy.                                                                                  |
|                                   |                                                                                                                                                                    |
|                                   | Integer value expected.                                                                                                                                            |
|                                   |                                                                                                                                                                    |
|                                   | Can be updated without replacement.                                                                                                                                |
|                                   |                                                                                                                                                                    |
|                                   | Allowed values: from 1 to 10, include 1 and 10.                                                                                                                    |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OSE::ELB::HealthCheck
       properties:
         healthcheck_connect_port: Integer
         healthcheck_interval: Integer
         healthcheck_protocol: String
         healthcheck_timeout: Integer
         healthcheck_uri: String
         healthy_threshold: Integer
         listener_id: String
         unhealthy_threshold: Integer
