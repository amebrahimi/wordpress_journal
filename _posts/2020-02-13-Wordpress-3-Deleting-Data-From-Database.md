---
title: Deleting Data From DataBase
published: true
plugin_name: "your-unique-plugin-name.php"
layout: post
---

- This is one way to delete data from database; using variables:

{% highlight php %}
//get all the posts from database
$books = get_posts(array('post_type' => 'book', 'numberposts' => -1));
//                        the unique slug ^ ,  get all the posts  ^

foreach ($books as $book) {
    wp_delete_post( $book->ID, true);
    // Just delete it           ^
}
{% endhighlight %}

- Another way for deleting all the posts using directly the database commands:

{% highlight php %}
global $wpdb;
$wpdb->query( "DELETE FROM wp_posts WHERE post_type = 'book' " );

// delete all the wp_postmeta that don't match this id
$wpdb->query("DELETE FROM wp_postmeta WHERE post_id NOT IN (SELECT id FROM wp_posts)");

$wpdb->query("DELETE FROM wp_term_relationships WHERE post_id NOT IN (SELECT id FROM wp_posts)");
{% endhighlight %}