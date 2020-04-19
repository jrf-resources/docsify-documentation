In this guide I will demonstrate how to add a button that duplicates the currently selected categories to a new post.

This button will appear in the admin bar only when editing a post.  This is what the button will look like:
![add-to-series.png](/wordpress/add-to-series.png)

index.php
```php
<?php
/**
 * Plugin Name: Add to Series
 * Plugin URI: 
 * Description: A button that appears in the admin bar to add new posts with the same categories
 * Version: 1.0
 * Author: Jesse Russell
 * Author URI: http://www.j-russell.com
 */
// Add to Series functionality
// declare the function that will create the add to series button
function jr_add_to_series($wp_admin_bar) {
    // if the post ID parameter exists, set the $post_id variable as well as the $post_type variable
    if ( isset( $_REQUEST['post'] ) ) {
        $post_id = $_REQUEST['post'];
        // use the builtin get_post function
        $thepost = get_post($post_id);
        // set the $post_type
        $post_type = $thepost->post_type;
    }
    $catlist = "";
    // if you want a certain post type to be ignored and to not show the button, use the following code:
    // if ( 'tutorial' == $post_type) {
    //     return;
    // }
    // if the post type is post.  Here you can set it to whatever post type you want, or add additional post types
    if ( 'post' == $post_type ) {
        // set the taxonomy name. useful for scenarios with odd taxonomy names.
        $taxonomy = 'category';
        // get the post's terms using this builtin function, passing in our custom taxonomy name
        $categories = get_the_terms($post_id,$taxonomy);
    }
    // loop through and set the category id variable. 
    foreach((array)$categories as $category) {
        $catid = $category->term_id;
        $catlist .= strval($category->term_id) . ',';
    }

    // create arguments list for Add to Series button
	$args = array(
		'id'    => 'add-to-series',
        'title' => 'Add to Series',
        // create url with query parameters, using information above
        'href'  => '/wp-admin/post-new.php?post_type=' . $post_type . '&taxonomy=' . $taxonomy . '&category_list=' . $catlist,
    );

    // add the button to the menu if it is has a post type
    if( $post_type ) {
        $wp_admin_bar->add_node($args);
    }
}
// add the above function
add_action('admin_bar_menu', 'jr_add_to_series', 100);
// declare the function that will add the Javascript to select the right category
function jr_select_categories() {
    // if there is a category ID and taxonomy
    if ( isset($_GET['category_list']) && isset($_GET['taxonomy']) ) {
        // set PHP variables to use in javascript
        $catList = strval($_GET['category_list']);
        $taxName = strval($_GET['taxonomy']);
        ?>
        <script type="text/javascript">
            jQuery(function() {
                // grab variables from PHP
                var catList = "<?php echo $catList; ?>";
                var taxName = "<?php echo $taxName; ?>"; 
                // create categories array by splitting on comma
                var categories = catList.split(',')
                for (i in categories) {
                    var category = categories[i];
                    // if there is no name, check the current category. Conditional used for trailing commas
                    if (category != "") {
                        // click that category
                        jQuery('#in-'+ taxName + '-' + category).click();
                    }
                }
            });
        </script>
        <?php
    }
}
// add the above function to the header of the post-new.php page.
add_action('admin_head-post-new.php', 'jr_select_categories');
```