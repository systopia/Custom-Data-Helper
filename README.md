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
  $customData = new CRM_Utils_CustomData('de.systopia.segmentation');
  $customData->syncOptionGroup(__DIR__ . '/resources/my_option_group.json');
  $customData->syncCustomGroup(__DIR__ . '/resources/my_custom_group.json');
  ```

 
