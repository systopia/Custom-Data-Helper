# Custom-Data-Helper

Helper class for CiviCRM Extensions

This class can be copied into any CiviCRM extension to facilitate creating, updating and deleting custom data. It is therefore a close realtive to [CiviCoop's config items](https://github.com/CiviCooP/org.civicoop.configitems).

Disclaimer: This is still under development. Current functionality:

 * CustomGroup/CustomField data
 * OptionGroup/OptionValue data
 
 ## Instructions
 
  1. Copy the ``CustomData.php`` file into ``CRM/Utils`` of you extension
  2. Create a ``resources`` folder and create a resource JSON file. Take a look at the examples in this extension
  3. Add the following lines to your ``civicrm_enable`` hook:
  ```
  require_once 'CRM/Utils/CustomData.php';
  $customData = new CRM_Utils_CustomData('my.extension.domain');
  $customData->syncOptionGroup(__DIR__ . '/resources/my_option_group.json');
  $customData->syncCustomGroup(__DIR__ . '/resources/my_custom_group.json');
  ```

 ## JSON Format
 
 The data in the JSON resource files reflects the data as used by the API. Fields starting with an underscore ('_') have a special meaning and are not passed on to the API:
 
  * ``_lookup``: this takes an array of field names that are used to identify the entity in the system. Based on this lookup it will be decided whether the given entity is updated, or a new one is to be created.
  * ``_translate``: this takes an array of field names where the values are passed through ``ts()`` translation before being passed on the the API. The domain is passed on as well. Caution: due to the inexplicit syntax the ts parser won't pick up those strings and they have to be added to the POT file manually.
  