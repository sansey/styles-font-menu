## Example output

![Example output](https://raw.github.com/stylesplugin/styles-font-dropdown/master/img/example-output.gif)

This menu can be displayed in your templates with this code: `do_action( 'styles_fonts_dropdown' );`

## Live Demo

To view a live demo of the menu in action, install and activate this WordPress plugin. Once activated, you can click the "How to use this plugin" link to view a working example.

![Example output](https://raw.github.com/stylesplugin/styles-font-dropdown/master/img/live-demo.png)

## Including in plugins and themes

Styles Font Dropdown has been packaged as a plugin only for testing purposes. In real world use, you should put it in your own theme or plugin, then include it with `include 'styles-font-dropdown/styles-font-dropdown.php';`

## Select Menu Values

**Standard Fonts**

For standard fonts, the option value is set to a font stack, such as `Arial, Helvetica, sans-serif`, suitable for output as the value of a CSS `font-family` declaration.

**Google Fonts**

For Google fonts, the option value is set to the URL fragment that can be passed as an `@import` request. For example, `Droid+Sans:regular,700`

This value should be inserted into an `@import url(//fonts.googleapis.com/css?family=$value);` declaration at the top of your CSS.

For example, final output for Droid Sans would be `@import url(//fonts.googleapis.com/css?family=Droid+Sans:regular,700);`

## Google Fonts API

**Automatic Updates**

If you [get a Google Fonts API key][1], you can enable auto-updates of the Google font list. By default, it caches and updates every 15 days.

The API key can be set in your local environment, or for all your users. If you enable it only for development, the values will update `wp-content/plugins/styles-font-dropdown/js/google-fonts-api-fallback.json` for users who do not have API access.

**Setting your API key**

Once you [get a Google Fonts API key][1], you can set it with `add_filter( 'styles_google_font_api', create_function('', "return 'YOUR_KEY_HERE';" ) );`

## Changing the cache interval

The default is 15 days. You can change the cache interval by setting this filter with a timeout (in seconds): `add_filter( 'styles_google_fonts_cache_interval', create_function('', 'return 60*60*24*15;' ) );`

## Changing the font order

Google Fonts are ordered by popularity by default. This seemed reasonable, since there are hundreds of fonts, and anything that doesn't appear at top would likely be found with the search field. If you would like change the default ordering, you can use the filter `add_filter( 'styles_google_font_sort', create_function( '', 'return "alpha";'));`

The possible sorting values are:

  * **alpha**: Sort the list alphabetically
  * **date**: Sort the list by date added (most recent font added or updated first)
  * **popularity**: Sort the list by popularity (most popular family first)
  * **style**: Sort the list by number of styles available (family with most styles first)
  * **trending**: Sort the list by families seeing growth in usage (family seeing the most growth first)

Note that you may need to flush your transients for the new sort order to appear immediately.

[Read more about the Google Fonts developer API](https://developers.google.com/fonts/docs/getting_started).

## About the drop-down menu

The dropdown menu uses [Chosen](http://harvesthq.github.io/chosen/) by Harvest.

   [1]: https://code.google.com/apis/console
  