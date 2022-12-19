:original_name: rts_02_0020.html

.. _rts_02_0020:

Template Package Structure
==========================

You need to prepare a .zip package. For the package structure, see :ref:`Figure 1 <rts_02_0020__fig56857421>`.

.. _rts_02_0020__fig56857421:

.. figure:: /_static/images/en-us_image_0076468668.png
   :alt: **Figure 1** Package structure

   **Figure 1** Package structure

#. **Resources** Directory

   This directory is used to store the files referenced by template files in the root directory. You can save the template files, configuration files, and script files used by the template in this directory. Templates of a nested stack must be placed in this directory. Do not change the name and structure of the directory.


   .. figure:: /_static/images/en-us_image_0106214513.png
      :alt: **Figure 2** Structure of **Resources** directory

      **Figure 2** Structure of **Resources** directory

#. File **logo.png**

   The default file name **logo** is recommended, and there are no restrictions on the logo file name. However, if the file name is different from the default **logo.png** file, you need to ensure that the logo file name in the package is consistent with the **Logo** value in file **manifest.yaml**.

   .. note::

      File **logo.png** is not supported and will be supported in later versions.

#. File **manifest.yaml**

   File **manifest. yaml** describes basic information of the package. The default file format is recommended. The following is an example file:

   .. code-block::

      Format: Heat.HOT/1.0
      Type: Application
      FullName: Reserved
      Name: Auto Scaling Group
      Description: "Heat template to deploy a stack."
      Author: RTS
      Tags:
        - hot-based
      Logo: logo.png

   .. note::

      The file name is fixed and cannot be user-defined.

#. **random.yaml** and **template.yaml**

   **random.yaml** and **template.yaml** are two example templates. You can define your own template based on these example templates. **random.yaml** is a template file that can be used to create random strings. This file can be used to create two random strings. **template.yaml** is a nested template file, which contains a nested template (**random1.yaml**). The sub-template is in the **Resources/HotFiles** directory.

   The following is an example **manifest.yaml** file:

   .. code-block::

      heat_template_version: 2014-10-16
      description: Create a serious of random string

      parameters:
        length:
          type: number
          default: 4

      resources:
        random1:
          type: OS::Heat::RandomString
          properties:
            length: {get_param: length}
        random2:
          type: OS::Heat::RandomString
          properties:
            length: {get_param: length}

   The following is an example **template.yaml** file:

   .. code-block::

      heat_template_version: 2014-10-16
      description: Create a serious of random string

      parameters:
        length:
          type: number
          default: 4

      resources:
        random1:
          type: OS::Heat::RandomString
          properties:
            length: {get_param: length}
        random2:
          type: OS::Heat::RandomString
          properties:
            length: {get_param: length}
        random3:
          type: random1.yaml

.. note::

   #. A valid package name contains a maximum of 32 characters, including letters, digits, hyphens (-), and underscores (_). The name must start with a letter and end with .zip.
   #. The structure of directory **Resources/HotFiles** is fixed and cannot be changed.
   #. When you use a .zip package, all template files in the root directory are displayed on the console, and you can select any template to create a stack.
   #. If necessary, you can add a file named **environment.yaml** to the root directory configured on the console.
   #. The logo file and the **manifest.yaml** file are mandatory and must be stored in the root directory.
   #. If file **get_file:** *abc*\ **.txt** is used in the template, this file must be placed in directory **Resources/HotFiles**.
   #. Other restrictions are as follows:

      -  The maximum size of a template file is 100 KB.
      -  The maximum size of a .zip package cannot exceed 80 KB.
      -  The maximum nesting depth is restricted to seven.
      -  The maximum number of files is 50.
