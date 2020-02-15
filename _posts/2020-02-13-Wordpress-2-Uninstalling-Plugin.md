---
title: Uninstalling Wordpress Plugin
published: true
plugin_name: "your-unique-plugin-name.php"
layout: post
---

- This is the method like the previous methods but with a slight deference:

{% highlight php %}
// Uninstall
register_uninstall_hook($file, $callback); // delete CPT, delete all the plugin data from the DB.
// The \$callback cannot be a method in a class and must be a static method or a top level function.
{% endhighlight %}

- Instead you can create a file named `uninstall.php` in the root folder of your plugin next to your `{{page.plugin_name}}` file. The purpose of creating uninstall is to clear the data stored for the plugin in database.

- For uninstall security check:

{% highlight php %}
// the first line should be
if (!defined('WP_UNINSTALL_PLUGIN')){
die;
}
{% endhighlight %}

## Deleting data from the database

---
