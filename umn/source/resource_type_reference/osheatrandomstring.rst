:original_name: rts_02_0051.html

.. _rts_02_0051:

OS::Heat::RandomString
======================

A resource which generates a random string.

This is useful for configuring passwords and secrets on services. Random string can be generated from specified character sequences, which means that all characters will be randomly chosen from specified sequences, or with some classes, e.g. letterdigits, which means that all character will be randomly chosen from union of ascii letters and digits. Output string will be randomly generated string with specified length (or with length of 32, if length property doesnt specified).

Optional Properties
-------------------

+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name                              | Description                                                                                                                                                                   |
+===================================+===============================================================================================================================================================================+
| character_classes                 | A list of character class and their constraints to generate the random string from.                                                                                           |
|                                   |                                                                                                                                                                               |
|                                   | List value expected.                                                                                                                                                          |
|                                   |                                                                                                                                                                               |
|                                   | Updates cause replacement.                                                                                                                                                    |
|                                   |                                                                                                                                                                               |
|                                   | Defaults to "[{class: lettersdigits, min: 1}]".                                                                                                                               |
|                                   |                                                                                                                                                                               |
|                                   | List contents:                                                                                                                                                                |
|                                   |                                                                                                                                                                               |
|                                   | -  \*                                                                                                                                                                         |
|                                   |                                                                                                                                                                               |
|                                   |    Map value expected.                                                                                                                                                        |
|                                   |                                                                                                                                                                               |
|                                   |    Updates cause replacement.                                                                                                                                                 |
|                                   |                                                                                                                                                                               |
|                                   |    Map properties:                                                                                                                                                            |
|                                   |                                                                                                                                                                               |
|                                   |    -  class                                                                                                                                                                   |
|                                   |                                                                                                                                                                               |
|                                   |       A character class and its corresponding min constraint to generate the random string from.                                                                              |
|                                   |                                                                                                                                                                               |
|                                   |       String value expected.                                                                                                                                                  |
|                                   |                                                                                                                                                                               |
|                                   |       Updates cause replacement.                                                                                                                                              |
|                                   |                                                                                                                                                                               |
|                                   |       Defaults to "lettersdigits".                                                                                                                                            |
|                                   |                                                                                                                                                                               |
|                                   |       Allowed values: lettersdigits, letters, lowercase, uppercase, digits, hexdigits, octdigits                                                                              |
|                                   |                                                                                                                                                                               |
|                                   |    -  min                                                                                                                                                                     |
|                                   |                                                                                                                                                                               |
|                                   |       The minimum number of characters from this character class that will be in the generated string.                                                                        |
|                                   |                                                                                                                                                                               |
|                                   |       Integer value expected.                                                                                                                                                 |
|                                   |                                                                                                                                                                               |
|                                   |       Updates cause replacement.                                                                                                                                              |
|                                   |                                                                                                                                                                               |
|                                   |       Defaults to "1".                                                                                                                                                        |
|                                   |                                                                                                                                                                               |
|                                   |       The value must be in the range 1 to 512, include 1 and 512.                                                                                                             |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| character_sequences               | A list of character sequences and their constraints to generate the random string from.                                                                                       |
|                                   |                                                                                                                                                                               |
|                                   | List value expected.                                                                                                                                                          |
|                                   |                                                                                                                                                                               |
|                                   | Updates cause replacement.                                                                                                                                                    |
|                                   |                                                                                                                                                                               |
|                                   | List contents:                                                                                                                                                                |
|                                   |                                                                                                                                                                               |
|                                   | -  \*                                                                                                                                                                         |
|                                   |                                                                                                                                                                               |
|                                   |    Map value expected.                                                                                                                                                        |
|                                   |                                                                                                                                                                               |
|                                   |    Updates cause replacement.                                                                                                                                                 |
|                                   |                                                                                                                                                                               |
|                                   |    Map properties:                                                                                                                                                            |
|                                   |                                                                                                                                                                               |
|                                   |    -  min                                                                                                                                                                     |
|                                   |                                                                                                                                                                               |
|                                   |       The minimum number of characters from this sequence that will be in the generated string.                                                                               |
|                                   |                                                                                                                                                                               |
|                                   |       Integer value expected.                                                                                                                                                 |
|                                   |                                                                                                                                                                               |
|                                   |       Updates cause replacement.                                                                                                                                              |
|                                   |                                                                                                                                                                               |
|                                   |       Defaults to "1".                                                                                                                                                        |
|                                   |                                                                                                                                                                               |
|                                   |       The value must be in the range 1 to 512, include 1 and 512.                                                                                                             |
|                                   |                                                                                                                                                                               |
|                                   |    -  sequence                                                                                                                                                                |
|                                   |                                                                                                                                                                               |
|                                   |       A character sequence and its corresponding min constraint to generate the random string from.                                                                           |
|                                   |                                                                                                                                                                               |
|                                   |       String value expected.                                                                                                                                                  |
|                                   |                                                                                                                                                                               |
|                                   |       Updates cause replacement.                                                                                                                                              |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| length                            | Length of the string to generate.                                                                                                                                             |
|                                   |                                                                                                                                                                               |
|                                   | Integer value expected.                                                                                                                                                       |
|                                   |                                                                                                                                                                               |
|                                   | Updates cause replacement.                                                                                                                                                    |
|                                   |                                                                                                                                                                               |
|                                   | Defaults to "32".                                                                                                                                                             |
|                                   |                                                                                                                                                                               |
|                                   | The value must be in the range 1 to 512, include 1 and 512.                                                                                                                   |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| salt                              | Value which can be set or changed on stack update to trigger the resource for replacement with a new random string. The salt value itself is ignored by the random generator. |
|                                   |                                                                                                                                                                               |
|                                   | String value expected.                                                                                                                                                        |
|                                   |                                                                                                                                                                               |
|                                   | Updates cause replacement.                                                                                                                                                    |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| sequence                          | Sequence of characters to build the random string from.                                                                                                                       |
|                                   |                                                                                                                                                                               |
|                                   | String value expected.                                                                                                                                                        |
|                                   |                                                                                                                                                                               |
|                                   | Updates cause replacement.                                                                                                                                                    |
|                                   |                                                                                                                                                                               |
|                                   | Allowed values: lettersdigits, letters, lowercase, uppercase, digits, hexdigits, octdigits                                                                                    |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Attributes
----------

+-------+---------------------------------------------------------------------------------------------------------+
| Name  | Description                                                                                             |
+=======+=========================================================================================================+
| value | The random string generated by this resource. This value is also available by referencing the resource. |
+-------+---------------------------------------------------------------------------------------------------------+

HOT Syntax
----------

.. code-block::

   heat_template_version: 2014-10-16
   ...
   resources:
     ...
     the_resource:
       type: OS::Heat::RandomString
       properties:
         character_classes: [{"class": String, "min": Integer}, {"class": String, "min": Integer}, ...]
         character_sequences: [{"min": Integer, "sequence": String}, {"min": Integer, "sequence": String}, ...]
         length: Integer
         salt: String
         sequence: String
