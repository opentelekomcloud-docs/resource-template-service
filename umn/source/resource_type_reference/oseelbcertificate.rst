:original_name: rts_02_0083.html

.. _rts_02_0083:

OSE::ELB::Certificate
=====================

A resource for certificate.

Required Properties
-------------------

+-----------------------------------+-----------------------------------+
| Name                              | Description                       |
+===================================+===================================+
| certificate                       | PEM-formatted certificate chain.  |
|                                   |                                   |
|                                   | String value expected.            |
|                                   |                                   |
|                                   | Updates cause replacement.        |
+-----------------------------------+-----------------------------------+
| private_key                       | PEM-formatted private_key chain.  |
|                                   |                                   |
|                                   | String value expected.            |
|                                   |                                   |
|                                   | Updates cause replacement.        |
+-----------------------------------+-----------------------------------+

Optional Properties
-------------------

+-----------------------------------+-------------------------------------+
| Name                              | Description                         |
+===================================+=====================================+
| description                       | The description of the certificate. |
|                                   |                                     |
|                                   | String value expected.              |
|                                   |                                     |
|                                   | Can be updated without replacement. |
+-----------------------------------+-------------------------------------+
| name                              | The name of the certificate.        |
|                                   |                                     |
|                                   | String value expected.              |
|                                   |                                     |
|                                   | Can be updated without replacement. |
+-----------------------------------+-------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OSE::ELB::Certificate
       properties:
         certificate: String
         description: String
         name: String
         private_key: String
