:original_name: rts_01_0007.html

.. _rts_01_0007:

Heat Client
===========

Overview
--------

The Heat client is a subproject of OpenStack Client, functioning as a command line client targeted for Heat. You can use this client to access cloud services by running commands.

RTS supports Heat 1.5.1.

.. note::

   To use the Heat client, you need to install and configure OpenStack Client first. For details, see :ref:`Installing OpenStack Client <rts_01_0007__section9738343155012>` and :ref:`Configuration <rts_01_0007__section33343719617>`.

.. _rts_01_0007__section9738343155012:

Installing OpenStack Client
---------------------------

To install OpenStack Client, you need to install and run the python-openstackclient plug-in and ensure that the plug-in is running properly.

OpenStack Client can be used on all OSs as long as python-openstackclient is running properly. Operation methods vary depending on the OS you use. The 64-bit Ubuntu 16.04 OS is recommended. This section describes how to install and configure OpenStack Client by using the 64-bit Ubuntu 16.04 OS as an example.

To install OpenStack Client, perform the following operations as user **root**:

#. Run the following commands to update the OS:

   **apt-get update**

   **apt-get upgrade**

#. Install Python.

   Install Python and pip based on the type of the OS. Python 2.7 is supported.

   Ubuntu 16.04 includes Python 2.7. If Python is not installed, perform the following steps to install it:

   Run the following command to install Python:

   **apt-get install python**

   Run the following command to install Setuptools:

   **apt-get install python-setuptools**

   Run the following command to install pip:

   **apt-get install python-pip**

   If Ubuntu supports Setuptools and pip of earlier versions, you can install them offline.

   Run the following command to install Dev:

   **apt-get install python-dev**

#. Install python-openstackclient and its dependent components.

   The following python-openstackclient versions are supported by default:

   -  python-openstackclient: 3.2.1
   -  python-novaclient: 6.0.2
   -  python-glanceclient: 2.5.0
   -  python-keystoneclient: 3.5.1
   -  python-neutronclient: 6.0.1
   -  python-cinderclient: 1.9.0
   -  python-heatclient: 1.5.1
   -  python-designateclient: 2.3.0
   -  openstacksdk: 0.9.5
   -  cliff: 2.2.0
   -  os-client-config: 1.21.1
   -  osc-lib: 1.1.0

   Run the following command to install python-openstackclient using pip:

   **pip install python-openstackclient==3.2.1**

   After the installation is complete, run the following command to verify the installation:

   **openstack -h**

   Check whether help information is displayed. The installation is successful if help information is displayed.

   Other components can be installed in sequence using the same command.

.. _rts_01_0007__section33343719617:

Configuration
-------------

You can configure OpenStack Client either as user **root** or as a common user.

#. Switch to the directory where OpenStack Client is installed and create an environment variable file, for example, **novarc**.

#. Use a text editor to edit the environment variable file and enter the username, password, region, IAM IP address, and port number.

   The following is an example:

   .. code-block::

      export OS_USERNAME="user_name"
      export OS_USER_DOMAIN_NAME=user_domain_name
      export OS_PASSWORD=*******
      export TENANT_ID=********

      # Only change these for a different region
      export OS_TENANT_NAME=az1
      export OS_PROJECT_NAME=az1
      export OS_AUTH_URL=https://iam.az1.domainname.com:443/v3

      # No changes needed beyond this point
      export NOVA_ENDPOINT_TYPE=publicURL
      export OS_ENDPOINT_TYPE=publicURL
      export CINDER_ENDPOINT_TYPE=publicURL
      export OS_VOLUME_API_VERSION=2
      export OS_IDENTITY_API_VERSION=3
      export OS_IMAGE_API_VERSION=2

   Environment variables to be configured include the username, password, IAM URL, and port number. :ref:`Table 1 <rts_01_0007__table1638643151819>` describes the required environment variables.

   .. _rts_01_0007__table1638643151819:

   .. table:: **Table 1** Environment variables

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                             |
      +===================================+=========================================================================================================================================================+
      | OS_USERNAME                       | Specifies the username for logging in to the management console.                                                                                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | OS_USER_DOMAIN_NAME               | Specifies the enterprise account for logging in to the management console.                                                                              |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | OS_PASSWORD                       | Specifies the password for logging in to the management console.                                                                                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | TENANT_ID                         | Specifies the project ID provided in the project list on the **My Credentials** page.                                                                   |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | OS_TENANT_NAME                    | Specifies the project name provided in the project list on the **My Credentials** page.                                                                 |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | OS_PROJECT_NAME                   | The value is the same as the **OS_TENANT_NAME** value.                                                                                                  |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | OS_AUTH_URL                       | The parameter value is in the format of **https://**\ *IAM URL*:*Port number*/*API version*, for example, **https://iam.**\ *example*\ **.com:443/v3**. |
      |                                   |                                                                                                                                                         |
      |                                   | -  *IAM URL*: Obtain the value from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.                               |
      |                                   | -  **Port number**: 443                                                                                                                                 |
      |                                   | -  **API version**: v3                                                                                                                                  |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Run the following command to set environment variables:

   **source novarc**

The Heat client becomes available after OpenStackClient is installed and configured. For more information, see :ref:`Creating Resources Using a Template (Using the Heat Client) <rts_02_0002>`.
