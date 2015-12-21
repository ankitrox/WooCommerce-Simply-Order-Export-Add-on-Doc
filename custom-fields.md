# WooCommerce Simply Order Export Add-on Documentation

### How to add custom field to export report?

Minimum requirement is having WooCommerce Simply Order Export add-on version **1.9** installed. Following is the procedure by which you can add
custom fields to the export.

**1.** Go to **Woocommerce > Settings > Order Export > Advanced Settings > Custom Fields**

**2.** Select the intended custom field key from dropdown list. Please note that dropdown auto-complete list only contains
names of the keys which are present in postmeta table, so if you want to export any field which is not present in postmeta 
table and not associated with order information, please enter the key manually (Key is mandatory).

**3.** Once you entered key, enter the name for the field. This name would appear as the column name in exported csv file.

**4.** As mentioned in point number 2, there may be some fields which you want to export, but may not be present in postmeta table of
wordpress. The fields which are present in postmeta table will get exported and added to the csv automatically behind the scene, but
those fields which are not present in postmeta table would require some custom code in order to add them to the csv file.

**5.** If the field is other than postmeta, you should check **not in meta** checkbox for that field.

**6.** Once all the information is inputted, click on the "Save" button at the bottom of the settings page.

**7.** Please take a reference of this image:
![custom fields]
(http://sharethingz.com/wp-content/uploads/2015/12/custom-field-section.png)

### Adding field other than postmeta value

**1.** Suppose the field key you have added is *_my_custom_field* in custom field section described above.

**2.** Add following code to the theme's functions.php file

```
function wsoe_add_custom_field_to_export( &$csv_values, $order_details, $key, $fields, $item_id, $current_item ) {
	
	switch ( $key ) {
		
		case '_my_custom_field':
			
			/**
			 * Your code will go here.
			 * code will differ according to the requirement.
			 */
			
			$value_to_add = 1; // This will be the intended value to export
			array_push( $csv_values, $value_to_add );
		break;
		
		default:
		break;

	}
}
add_action('wsoe_addon_add_to_csv', 'wsoe_add_custom_field_to_export', 10, 6 );
```

This should add and export the field in csv.