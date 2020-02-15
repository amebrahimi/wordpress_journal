---
title: Wordpress tips and tricks
published: true
plugin_name: "your-unique-plugin-name.php"
layout: post
---

- echo something after the header was set, will trigger an **error**.

- To perform an action on initialization:

{% highlight php %}
add_action('init', 'the_function_name');
{% endhighlight %}

- Refresh all the wordpress stuff and tell we created something new:

{% highlight php %}
flush_rewrite_rules();
{% endhighlight %}

- To register a new post type:

{% highlight php %}
register_post_type('book', ['public' => true, 'label' => 'Books']);
{% endhighlight %}

- Enqueue the css files for loading:

{% highlight php %}
wp_enqueue_style('myplyginstyle', plugins_url('/assets/mystyle.css', __FILE__));
{% endhighlight %}

- Enqueue javascript files for loading:

{% highlight php %}
wp_enqueue_script('myplyginscript', plugins_url('/assets/myscript.css', __FILE__));
{% endhighlight %}

- Add scripts to admin area:

{% highlight php %}
add_action('admin_enqueue_scripts', array($this, 'enqueue'));
{% endhighlight %}

- To add scripts in the actual page:

{% highlight php %}
add_action('wp_enqueue_scripts', array($this, 'enqueue'));
{% endhighlight %}
