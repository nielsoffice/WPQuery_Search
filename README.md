# WP_Query_Search
WP Query search filter using get native php function or post method from input field for advance search from post and custom post type.

```PHP
<?php 

$args = array(
    'post_type'     => 'post',
    'post_status'   => 'publish',
    'orderby'       => $_POST['orderby'], 
    'order'         => $_POST['order'],
    'search_prod_title' => $_POST['search'],
);

add_filter( 'posts_where', 'title_filter', 10, 2 );
$query = new WP_Query($args);
remove_filter( 'posts_where', 'title_filter', 10, 2 );

?>
```

```PHP
<?php

$args = array(
        'post_type'        => 'post',
        'search_title'     => $param,
        'posts_per_page'   => $page_size,
        'paged'            => $page,
        'post_status'      => 'publish',
        'orderby'          => 'title', 
        'order'            => 'ASC',
);
 
$wp_query = new WP_Query( $args );
if ( $wp_query->have_posts() ) : 
     while ( $wp_query->have_posts() ) : $wp_query->the_post();
            //Your Code to display post...
     endwhile;
endif;

?>
```

Reference: <br />
<a href="https://nielsoffice197227997.wordpress.com/2021/11/24/wordpress-the-loop-fetch-data-from-database-wp_query-php/"> WordPress The Loop Fetch Data From Database WP_Query/PHP </a> <br />
<a href="https://stackoverflow.com/questions/62350261/how-to-search-only-in-post-title-wp-query"> Andvance Filter Search WP_Query </a> <br />
<a href="https://qirolab.com/posts/example-of-wp-query-to-search-by-post-title-in-wordpress"> Example of WP_Query to search by post title in WordPress </a> <br />
