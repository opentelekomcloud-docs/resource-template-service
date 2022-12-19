:original_name: rts_02_0072.html

.. _rts_02_0072:

OS::Nova::KeyPair
=================

A resource for creating Nova key pairs.

A keypair is an SSH key that can be injected into a server on launch.

**Note** that if a new key is generated setting *save_private_key* to *True* results in the system saving the private key which can then be retrieved via the *private_key* attribute of this resource.

Setting the *public_key* property means that the *private_key* attribute of this resource will always return an empty string regardless of the *save_private_key* setting since there will be no private key data to save.

.. note::

   The Server template does not support key pair update. If the key pair is updated, Servers will be rebuilt.

Required Properties
-------------------

+-----------------------------------+--------------------------------------------------------------+
| Name                              | Description                                                  |
+===================================+==============================================================+
| name                              | The name of the key pair.                                    |
|                                   |                                                              |
|                                   | String value expected.                                       |
|                                   |                                                              |
|                                   | Updates cause replacement.                                   |
|                                   |                                                              |
|                                   | The length must be in the range 1 to 255, include 1 and 255. |
+-----------------------------------+--------------------------------------------------------------+

Optional Properties
-------------------

+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                          |
+===================================+======================================================================================================================================================+
| public_key                        | The optional public key. This allows users to supply the public key from a pre-existing key pair. If not supplied, a new key pair will be generated. |
|                                   |                                                                                                                                                      |
|                                   | String value expected.                                                                                                                               |
|                                   |                                                                                                                                                      |
|                                   | Updates cause replacement.                                                                                                                           |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+
| save_private_key                  | True if the system should remember a generated private key; False otherwise.                                                                         |
|                                   |                                                                                                                                                      |
|                                   | Boolean value expected.                                                                                                                              |
|                                   |                                                                                                                                                      |
|                                   | Updates cause replacement.                                                                                                                           |
|                                   |                                                                                                                                                      |
|                                   | Defaults to "False".                                                                                                                                 |
+-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------+

Attributes
----------

=========== =====================================
Name        Description
=========== =====================================
private_key The private key if it has been saved.
public_key  The public key.
=========== =====================================

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Nova::KeyPair
       properties:
         name: String
         public_key: String
         save_private_key: Boolean
