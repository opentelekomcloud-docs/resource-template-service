:original_name: rts_faq_0004.html

.. _rts_faq_0004:

How to Obtain the flavor Value of Resource OSE::RDS::Instance?
==============================================================

Method 1: By Using the Console
------------------------------

#. Log in to the management console.

   Google Chrome is recommended.

#. Choose **Database** > **Relational Database Service**.

#. In the upper right corner of the displayed page, click **Create DB Instance**.

#. Press **F12** and click **Network**.

#. Refresh the page, find **createInfo?regionCode=eu-de** in the request list, and click **Preview**. Choose **constant** > **flavors** to obtain the flavor IDs and other information.


   .. figure:: /_static/images/en-us_image_0128465684.png
      :alt: **Figure 1** Obtaining flavor information

      **Figure 1** Obtaining flavor information

#. Select the flavor ID based on the selected database type, backup policy, and required memory and CPU.

   Determine the database type and HA policy based on field **code** of the flavor. For example, if field **code** of the flavor is **rds.mysql.m1.large.ha**, you can create MySQL primary/standby DB instances.

Method 2: By Calling the API
----------------------------

#. .. _rts_faq_0004__li7547856798:

   Call the IAM API to obtain the token.

   **curl -i -k -X POST** *https://auth.otc-tsi.de:31943/v3/auth/tokens* **-d '{"auth": {"identity": {"methods": ["password"],"password": {"user": {"name": "**\ ``*****``\ **","domain": {"name": "**\ ``****``\ **"},"password": "**\ ``****``\ **"}}},"scope": {"project": {"name": "**\ *eu-de*\ **"}}}}' -H "Content-Type: application/json"**

#. Save the token information.

   Save the token obtained in :ref:`1 <rts_faq_0004__li7547856798>` and import variables.

   The following is an example command:

   **export token=**\ ``MIIF5gY*******cNxyvq4=``

#. .. _rts_faq_0004__li164268420109:

   Invoke the RDS API for obtaining the database version.

   URI format: **GET /rds/{versionId}/{project_id}/datastores/{datastore_name}/versions**

   The following is an example command:

   **curl -i -X GET** *https://rds.eu-de.otc.t-systems.com/rds/v1/3160d79af34b45e78fad478a046d7615/datastores/PostgreSQL/versions* **-H 'Content-Type: application/json' -H 'Accept: application/json' -H 'User-Agent: python-heatclient' -k -H "X-Auth-Token: $token" -H 'X-Language: en-us'**

   .. note::

      In the URI, *datastore_name* indicates the type of the database to be created. Currently, the following database types are supported: MySQL, PostgreSQL, and SQLServer. These types are case sensitive.

#. Invoke the RDS API for obtaining specifications of all DB instances.

   URI format: GET /rds/{versionId}/{project_id}/flavors

   Example command: **curl -i -k -X GET "**\ *https://rds.eu-de.otc.t-systems.com*\ **/rds/v1/**\ *3160d79af34b45e78fad478a046d7615*\ **/flavors?dbId=**\ *c66772dd-bd7a-11e7-a4c9-00ffa8375c2a*\ **&region=**\ *eu-de*\ **" -H 'Content-Type: application/json' -H 'Accept: application/json' -H 'User-Agent: python-heatclient' -H "X-Auth-Token: $token" -H "X-Language: en-us"**

   .. note::

      **dbId** indicates the ID of the DB engine version ID obtained in :ref:`3 <rts_faq_0004__li164268420109>`.

#. Select the flavor ID based on the selected backup policy and required memory and CPU.

   Determine the database type and HA policy based on field **specCode** of the flavor. For example, if field **specCode** of the flavor is **rds.mysql.m1.large.ha**, you can create MySQL primary/standby DB instances.
