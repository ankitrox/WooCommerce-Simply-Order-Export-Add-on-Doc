# WooCommerce Simply Order Export Add-on Documentation

### How to add custom field to export report?

Minimum requirement is having WooCommerce Simply Order Export add-on version **1.9** installed. Following is the procedure by which you can add
custom fields to the export.

1. Go to **Woocommerce > Settings > Order Export > Advanced Settings > Custom Fields**

2. Select the intended custom field key from dropdown list. Please note that dropdown auto-complete list only contains
names of the keys which are present in postmeta table, so if you want to export any field which is not present in postmeta 
table and not associated with order information, please enter the key manually (Key is mandatory).

3. Once you entered key, enter the name for the field. This name would appear as the column name in exported csv file.

4. As mentioned in point number 2, there may be some fields which you want to export, but may not be present in postmeta table of
wordpress. The fields which are present in postmeta table will get exported and added to the csv automatically behind the scene, but
those fields which are not present in postmeta table would require some custom code in order to add them to the csv file.