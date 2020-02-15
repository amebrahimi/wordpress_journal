---
title: Development Starting Kit for Wordpress
published: true
plugin_name: "your-unique-plugin-name.php"
layout: post
---

- For start developing plugin for wordpress it's better to turn on debugging in `wp-config.php`.

{% highlight php %}
define('WP_DEBUG', false);
{% endhighlight %}

- You have to create your plugins in the `wp-content/plugins/{{page.plugin_name}}`.

- Inside that folder you have to create a php file exactly the name of the folder. (`{{page.plugin_name}}`)

- It's better practice to decorate the head of your php file like so:

{% highlight php %}

```
/**
 * @package PrinceBestPlugin
 */
/**
 Plugin Name: Prince Best Plugin
 Plugin URI: https://prince.best.plugin (The uri to the plugin like github)
 Description: This is my first attempt on writing a custom plugin for this amazing series.
 Version: 1.0.0
 Author: Amir Mahmoud Ebrahimi
 Author URI: http://mrclover.tk
 License: MIT
 Text Domain: prince-best-plugin
 */

 /*
 And here the license requirements
 */
```

{% endhighlight %}

- For security reasons and best practices, you have to create an `index.php` and make it empty like this:

{% highlight php %}

<? php
// silence is golden
{% endhighlight %}

- For security reasons is best to add this line into the plugin entry file. (`{{page.plugin_name}}`)

{% highlight php %}
// This
if (!defined('ABSPATH')) {
    die;
}

// Or this
defined('ABSPATH') or die('Hey, you can\'t access this file, you silly human');

// Or this
if (!function_exists('add_action')) {
    echo 'Hey, you can\'t access this file, you silly human';
    exit;
}
        
{% endhighlight %}

- If you create a class and want to instantiate an object from it, it's better to check if the class exists. (The function returns a boolean)

{% highlight php %}
class_exists('NameOfTheClass');
{% endhighlight %}

- Wordpress automatically triggers these functions on certain conditions:

{% highlight php %}
// on activation
register_activation_hook(__FILE__, array($princeBestPlugin, 'activate')); // When plugin is getting active the best practice is to create a CPT and flush the rewrite

// deactivation
register_activation_hook(__FILE__, array($princeBestPlugin, 'activate')); // When plugin is getting active the best practice is to create a CPT and flush the rewrite
{% endhighlight %}
