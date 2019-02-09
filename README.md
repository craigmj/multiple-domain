# Multiple Domain

Multiple Domain allows you having more than one domain in a single WordPress installation. This plugin doesn't support
more than one theme or advanced customizations for each domain. It's only intended to enable constant navigation under
many domains. For a more complex setup, there is
[WordPress Multisite (MU)](https://codex.wordpress.org/Create_A_Network).

When there is more than one domain set in your host, all links and resources will point to the default domain. This is
the default WordPress behavior. With Multiple Domain installed and properly configured, it'll update all link on the
fly. This way, the user navigation will be end-to-end under the same domain.

You can also set an optional base URL. If you want only a set of URL's available under a given domain, you can use this
restriction.

Additionally, a language can be set for each domain. The language will be used to add `<link>` tags with `hreflang`
attribute to document head. This is for SEO purposes.

Check the plugin page at WordPress.org: https://wordpress.org/plugins/multiple-domain/

## Installation

Follow the steps below to install the plugin:

1. Upload the plugin files to the `/wp-content/plugins/multiple-domain` directory, or install the plugin through the
    WordPress plugins screen directly.
2. Activate the plugin through the 'Plugins' screen in WordPress.
3. Use the Settings -> General screen to configure your additional domains.

## Frequently Asked Questions

**Does this plugin set extra domains within my host?**

No. You have to set additional domains, DNS, and everything else to use this plugin.

**Can I have a different theme/content/plugins for each domain?**

Nope. If you want a complex set up like this, you may be interested in WordPress Multisite. It's delivered with every
WordPress installation since 3.0, you can find more info here: https://codex.wordpress.org/Create_A_Network.

**There is a way to add domain based logic to my themes?**

Absolutely. You can use the `MULTPLE_DOMAIN_DOMAIN` and `MULTPLE_DOMAIN_ORIGINAL_DOMAIN` constants to get the current
and original domains. Just notice that since the value of the first one is checked against plugin settings, it may not
reflect the actual domain in `HTTP_HOST` element from `$_SERVER` or user's browser. They also may include the host port
when it's different than 80 (default HTTP port) or 443 (default HTTPS port).

**Can I create a custom access restriction logic for each domain?**

Yes. You can use the `multiple_domain_redirect` action to do that. Please check
https://github.com/straube/multiple-domain/issues/2 for an example on how to do that.

**Can I get the language associated with the current domain?**

Yes. You can use the `MULTPLE_DOMAIN_DOMAIN_LANG` constant to get the language associated with the current domain. Keep
in mind the value in this constant doesn't necessarily reflect the actual user language or locale. This is just the
language set in the plugin config. Also notice the language may be `null`.

**Can I show the current domain in the content of posts or pages?**

Yes. There is a shortcode available for that. Just add `[multiple_domain]` to the post/page and it'll be replaced by
the current domain when viewing the content. You can write things like "Welcome to [multiple_domain]!", which would be
rendered as "Welcome to mydomain.com!".

## Changelog

### 0.9.0

* Fixed bug in backward compatibility logic.
* Added a class to `<body>` tag containing the domain name (e.g. `multipled-domain-name-tld`) to allow front-end customizations.

### 0.8.7

* Loading Multiple Domain before other plugins to fix issue with paths.
* Fix #38: Missing locales on language list (this issue was reopened and now it's fixed)
* Refactored `initAttributes` method.

### 0.8.6

* Fix #39: Rolling back changes introduced in 0.8.4 and 0.8.5 regarding to avoid URL changes in the WP admin.

### 0.8.5

* Fixed an issue introduced in 0.8.4 that breaks the admin URLs.
* Fix #38: Missing locales on language list
* Add `[multiple_domain]` shortcode to show the current language.

### 0.8.4

* Fix: #36 Wrong host in URLs returned by the JSON API
* Using singleton pattern for main plugin class.
* Avoiding URL changes in the admin panel.

### 0.8.3

* Fix: #34 hreflang tag error

### 0.8.2

* Fix: #32 Image URLs not being re-written properly via Tor.

### 0.8.1

* Fix: #23 Undefined index when using wp-cli.

### 0.8.0

* Moved `MultipleDomain` class to its own file.
* Fix: #14 Remove `filter_input` from plugin.
* Attempt to fix #22.
* Added `MULTPLE_DOMAIN_DOMAIN_LANG` constant for theme/plugin customization. Fixes #20.
* Fix: #21 No 'Access-Control-Allow-Origin' header is present on the requested resource.

### 0.7.1

* Make the plugin compatible with PHP 5.4 again.

### 0.7

* Code review/refactoring.
* Added activation hook to fix empty settings bug.

### 0.6

* Fix: #11 Redirect to original domain if SSL/https.

### 0.5

* Added http/https for alternate link.

### 0.4

* Fixed resolving host name to boolean.
* Added Reflang links to head for SEO purpose.
e.g.
```html
<link rel="alternate" hreflang="x-default" href="https://example.com/">
<link rel="alternate" hreflang="de-DE" href="https://de.example.com/">
```

### 0.3

* Fixed bug when removing the port from current domain.
* Added `MULTPLE_DOMAIN_ORIGINAL_DOMAIN` constant to hold the original WP home domain.
* Allowing developers to create custom URL restriction logic through `multiple_domain_redirect` action.
* Improved settings interface.

### 0.2

* Improved port verification.
* Added `MULTPLE_DOMAIN_DOMAIN` constant for theme/plugin customization.
* And, last but not least, code refactoring.

### 0.1

This is the first release. It supports setting domains and an optional base URL for each one.

## Meta

Contributors: GustavoStraube, cyberaleks, jffaria  
Tags: multiple, domains, redirect  
Requires at least: 4.0  
Tested up to: 5.0.3  
Stable tag: trunk  
License: GPLv2 or later  
License URI: http://www.gnu.org/licenses/gpl-2.0.html  

## Contributing

Feel free to open a pull request to address any of the issues reported by the plugin users. In case you have questions
on how to fix or the best approach, start a discussion on the appropriate thread.

If you want to add a new feature, please open an issue explaining the feature and how it would help the users before
start writing your code.

Separate each new feature or improvement into a separate branch in your forked repository.

### Guidelines

To make sure every contribution follows the same code style, please follow these rules:

* Write PSR-2 compliant code
* Use UNIX line returns
* Remove trailing white space
* Use 4 spaces instead of tabs

Also notice that even if Wordpress has its own code styling guidelines, this plugin doesn't follow it in favor of a
global standard (PSR-2).

### Donations

If you find this plugin helpful, you can support the work involved buying me a coffee, beer or a Playstation 4 game.
You can send donations over PayPal to gustavo.straube@gmail.com.
