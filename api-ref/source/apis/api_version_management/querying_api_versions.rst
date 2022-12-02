:original_name: rts_03_0018.html

.. _rts_03_0018:

Querying API Versions
=====================

Function
--------

This API is used to query all available versions.

URI
---

GET /

Request Parameter
-----------------

N/A

Response Parameter
------------------

+-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+
| Parameter       | In              | Type            | Description                                                                                  |
+=================+=================+=================+==============================================================================================+
| versions        | body            | List <dict>     | Specifies the API version list.                                                              |
|                 |                 |                 |                                                                                              |
|                 |                 |                 | Each object in the list provides API version information, such as the ID, status, and links. |
+-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------+

**versions** structure information

+-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Parameter       | In              | Type            | Description                                                                                                                                                                     |
+=================+=================+=================+=================================================================================================================================================================================+
| id              | body            | String          | Specifies the API version.                                                                                                                                                      |
+-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| status          | body            | String          | Specifies the API version status. Available values are as follows:                                                                                                              |
|                 |                 |                 |                                                                                                                                                                                 |
|                 |                 |                 | -  **CURRENT**: preferred API version                                                                                                                                           |
|                 |                 |                 | -  **SUPPORTED**: an earlier API version, which is still in use                                                                                                                 |
|                 |                 |                 | -  **DEPRECATED**: an obsolete API version to be deleted                                                                                                                        |
+-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| links           | body            | List <dict>     | Specifies the API URL list.                                                                                                                                                     |
|                 |                 |                 |                                                                                                                                                                                 |
|                 |                 |                 | Each URL is a JSON object with one **href** keyword for identifying the URL and one **rel** keyword indicating the relationship between the API version and the involved stack. |
+-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Example
---------------

None

Response Example
----------------

.. code-block::

   {
       "versions": [
           {
               "status": "CURRENT",
               "id": "v1.0",
               "links": [
                   {
                       "href": "http://x.x.x.x:8774/v1/",
                       "rel": "self"
                   }
               ]
           }
       ]
   }

Return Code
-----------

The following code will be returned if the system is operating normally.

+-------------+------------------+----------------------------------------------------------+
| Return Code | Type             | Description                                              |
+=============+==================+==========================================================+
| 300         | Multiple choices | The requested resource has multiple available responses. |
+-------------+------------------+----------------------------------------------------------+
