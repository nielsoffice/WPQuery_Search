# WP_Query_Search
WP Query search filter using get native php function or post method from input field for advance search from post and custom post type.

```PHP
<?php 

function title_filter($where, &$wp_query){
    global $wpdb;

    if($search_term = $wp_query->get( 'search_prod_title' )){
        /*using the esc_like() in here instead of other esc_sql()*/
        $search_term = $wpdb->esc_like($search_term);
        $search_term = ' \'%' . $search_term . '%\'';
        $where .= ' AND ' . $wpdb->posts . '.post_title LIKE '.$search_term;
    }

    return $where;
}

$args = array(
    'post_type' => 'post',
    's'         => $search_terms,
    'post_status' => 'publish',
    'orderby'     => 'title', 
    'order'       => 'ASC'        
);

$wp_query = new WP_Query($args);

?>
```

Reference: <br />
<a href="https://nielsoffice197227997.wordpress.com/2021/11/24/wordpress-the-loop-fetch-data-from-database-wp_query-php/"> WordPress The Loop Fetch Data From Database WP_Query/PHP </a> <br />
<a href="https://wordpress.stackexchange.com/questions/18703/wp-query-with-post-title-like-something"> By Ashan Jay </a> <br />
