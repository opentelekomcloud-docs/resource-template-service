:original_name: rts_02_0080.html

.. _rts_02_0080:

OSE::ELB::Listener
==================

A resource for ELB Listener.

Required Properties
-------------------

+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                                                            |
+===================================+========================================================================================================================================================================================================+
| name                              | The name of the listener.                                                                                                                                                                              |
|                                   |                                                                                                                                                                                                        |
|                                   | String value expected.                                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                        |
|                                   | Can be updated without replacement.                                                                                                                                                                    |
|                                   |                                                                                                                                                                                                        |
|                                   | It is allowed to start with **numbers**, **letters**, \_, and **-** characters. It is allowed to include **numbers**, **letters**, \_, and **-** characters, and the string length is **1** to **64**. |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| loadbalancer_id                   | The ID of load balancer associated.                                                                                                                                                                    |
|                                   |                                                                                                                                                                                                        |
|                                   | String value expected.                                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                        |
|                                   | Updates cause replacement.                                                                                                                                                                             |
|                                   |                                                                                                                                                                                                        |
|                                   | Value must be of type elb.lb                                                                                                                                                                           |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| protocol                          | The protocol of the listener.                                                                                                                                                                          |
|                                   |                                                                                                                                                                                                        |
|                                   | String value expected.                                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                        |
|                                   | Updates cause replacement.                                                                                                                                                                             |
|                                   |                                                                                                                                                                                                        |
|                                   | Allowed values: HTTP, HTTPS, TCP                                                                                                                                                                       |
|                                   |                                                                                                                                                                                                        |
|                                   | .. note::                                                                                                                                                                                              |
|                                   |                                                                                                                                                                                                        |
|                                   |    Do not update this attribute. Otherwise, the listener update will fail.                                                                                                                             |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| backend_protocol                  | The backend protocol of the listener.                                                                                                                                                                  |
|                                   |                                                                                                                                                                                                        |
|                                   | String value expected.                                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                        |
|                                   | Updates cause replacement.                                                                                                                                                                             |
|                                   |                                                                                                                                                                                                        |
|                                   | Allowed values: HTTP, TCP                                                                                                                                                                              |
|                                   |                                                                                                                                                                                                        |
|                                   | .. note::                                                                                                                                                                                              |
|                                   |                                                                                                                                                                                                        |
|                                   |    Do not update this attribute. Otherwise, the listener update will fail.                                                                                                                             |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| port                              | The port of the listener.                                                                                                                                                                              |
|                                   |                                                                                                                                                                                                        |
|                                   | Integer value expected.                                                                                                                                                                                |
|                                   |                                                                                                                                                                                                        |
|                                   | Can be updated without replacement.                                                                                                                                                                    |
|                                   |                                                                                                                                                                                                        |
|                                   | Allowed values: from 1 to 65535, include 1 and 65535                                                                                                                                                   |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| backend_port                      | The backend port of the listener.                                                                                                                                                                      |
|                                   |                                                                                                                                                                                                        |
|                                   | Integer value expected.                                                                                                                                                                                |
|                                   |                                                                                                                                                                                                        |
|                                   | Can be updated without replacement.                                                                                                                                                                    |
|                                   |                                                                                                                                                                                                        |
|                                   | Allowed values: from 1 to 65535, include 1 and 65535                                                                                                                                                   |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| lb_algorithm                      | The algorithm used to distribute load.                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                        |
|                                   | String value expected.                                                                                                                                                                                 |
|                                   |                                                                                                                                                                                                        |
|                                   | Can be updated without replacement.                                                                                                                                                                    |
|                                   |                                                                                                                                                                                                        |
|                                   | Allowed values: roundrobin, leastconn, source                                                                                                                                                          |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Optional Properties
-------------------

+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                          |
+===================================+======================================================================================================================================+
| certificate_id                    | The ID of certificate.                                                                                                               |
|                                   |                                                                                                                                      |
|                                   | String value expected.                                                                                                               |
|                                   |                                                                                                                                      |
|                                   | Updates cause replacement.                                                                                                           |
|                                   |                                                                                                                                      |
|                                   | .. note::                                                                                                                            |
|                                   |                                                                                                                                      |
|                                   |    Do not update this attribute. Otherwise, the listener update will fail.                                                           |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
| cookie_timeout                    | The timeout of cookie in minute.                                                                                                     |
|                                   |                                                                                                                                      |
|                                   | Integer value expected.                                                                                                              |
|                                   |                                                                                                                                      |
|                                   | Updates cause replacement.                                                                                                           |
|                                   |                                                                                                                                      |
|                                   | Allowed values: from 1 to 1440, include 1 and 1440                                                                                   |
|                                   |                                                                                                                                      |
|                                   | .. note::                                                                                                                            |
|                                   |                                                                                                                                      |
|                                   |    Do not update this attribute. Otherwise, the listener update will fail.                                                           |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
| description                       | The description of the listener.                                                                                                     |
|                                   |                                                                                                                                      |
|                                   | String value expected.                                                                                                               |
|                                   |                                                                                                                                      |
|                                   | Can be updated without replacement.                                                                                                  |
|                                   |                                                                                                                                      |
|                                   | It is not allowed to start with the **<>** character. The **<>** character is not allowed and the string length is **1** to **128**. |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
| session_sticky                    | Whether to keep the session.                                                                                                         |
|                                   |                                                                                                                                      |
|                                   | Boolean value expected.                                                                                                              |
|                                   |                                                                                                                                      |
|                                   | Updates cause replacement.                                                                                                           |
|                                   |                                                                                                                                      |
|                                   | .. note::                                                                                                                            |
|                                   |                                                                                                                                      |
|                                   |    Do not update this attribute. Otherwise, the listener update will fail.                                                           |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
| sticky_session_type               | The way of handing cookie.                                                                                                           |
|                                   |                                                                                                                                      |
|                                   | String value expected.                                                                                                               |
|                                   |                                                                                                                                      |
|                                   | Updates cause replacement.                                                                                                           |
|                                   |                                                                                                                                      |
|                                   | Allowed values: insert                                                                                                               |
|                                   |                                                                                                                                      |
|                                   | .. note::                                                                                                                            |
|                                   |                                                                                                                                      |
|                                   |    Do not update this attribute. Otherwise, the listener update will fail.                                                           |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
| tcp_timeout                       | The timeout of TCP session in minute.                                                                                                |
|                                   |                                                                                                                                      |
|                                   | Integer value expected.                                                                                                              |
|                                   |                                                                                                                                      |
|                                   | Updates cause replacement.                                                                                                           |
|                                   |                                                                                                                                      |
|                                   | Allowed values: from 1 to 5, include 1 and 5. The default value is **5**.                                                            |
|                                   |                                                                                                                                      |
|                                   | .. note::                                                                                                                            |
|                                   |                                                                                                                                      |
|                                   |    Do not update this attribute. Otherwise, the listener update will fail.                                                           |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+

Attributes
----------

============= ====================================================
Name          Description
============= ====================================================
member_number The number of the members listened by this listener.
status        The status of the listener.
============= ====================================================

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OSE::ELB::Listener
       properties:
         backend_port: Integer
         backend_protocol: Integer
         certificate_id: String
         cookie_timeout: Integer
         description: String
         lb_algorithm: String
         loadbalancer_id: String
         name: String
         port: Integer
         protocol: String
         session_sticky: Boolean
         sticky_session_type
         tcp_timeout: Integer
