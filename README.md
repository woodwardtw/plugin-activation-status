# Plugin Activation Status #
**Contributors:** cgrymala

**Donate link:** http://giving.umw.edu/

**Tags:** plugins, multisite, multi-network, active, network-active, status

**Requires at least:** 3.8

**Tested up to:** 4.9.5

**Stable tag:** 1.0.2.1

**License:** GPLv2 or later

**License URI:** http://www.gnu.org/licenses/gpl-2.0.html


Scans a multisite or multi-network installation to identify all plugins that are active or not.

## Description ##

Plugin Activation Status makes it easier for owners of multisite and multi-network WordPress installations to perform plugin audits on their installations. The plugin generates a list of plugins that are not currently active on any sites or networks. It generates a separate list of plugins that are active somewhere within the installation, and provides details about where and how those plugins are activated.

This plugin first retrieves a full list of all of the plugins that are network-activated throughout your installation. Then, it loops through all of the sites in your installation, retrieving a list of all of the active plugins on each site. Next, it runs a diff between the full list of installed plugins and the list of all active plugins.

Once it retrieves all of that information, it outputs two separate lists.

The first list is the list of Inactive Plugins; all plugins that are installed, but not activated anywhere within WordPress will be listed there. The second list shows all of the Active Plugins; all plugins that are installed and activated somewhere within WordPress are shown there.

Within the Active Plugins list, each plugin also has a list of all of the places the plugin is active (at the top, a list of all of the places it's network-active; at the bottom, all of the places it's normally-activated).

When the plugin generates the lists of plugins, it stores those lists as site options in the database, so the lists can be retrieved for reference without using any additional server resources. If you would like to remove those cached lists and generate new lists, you simply have to click the Continue button on the admin page.

## Installation ##

### Standard Installation ###

1. Upload `plugin-activation-status` folder to the `/wp-content/plugins/` directory
1. Network-activate the plugin through the 'Plugins' menu in WordPress

### MU-Plugins Installation ###

1. Upload the `plugin-activation-status` folder to the `/wp-content/mu-plugins/` directory (if that directory does not exist, you can create it)
1. Move `plugin-activation-status.php` out of `/wp-content/mu-plugins/plugin-activation-status/` and directly into `/wp-content/mu-plugins/`

## Frequently Asked Questions ##

### Why don't I see the new Plugins -> Active Plugins menu item? ###

That menu item will only appear in the Network Admin area for the primary (root/main) network. If you are running a multi-network installation and you activated the plugin on a network other than the first, you won't see that menu item.

### Will this work on a non-multisite installation? ###

No. If you need to see the activation status of plugins in a standard WP install, you can simply go to Plugins -> Installed Plugins in your admin area. This plugin is specifically developed for multisite and multi-network installs of WordPress, where it's much more difficult to get a clear, accurate picture of which plugins are active and where they're active.

### Why do I see file paths at the bottom of the list of Active Plugins? ###

When a plugin is installed and activated, WordPress uses that file path as the indicator that the plugin has been activated, and stores that information in the database. If a plugin file is removed or renamed after it's been activated on a site, WordPress doesn't know that it has to remove that old path from the list of active plugins until you visit the Plugins page on each site where it was active.

To make a long story short (too late!), those are plugins that are still considered "active" by WordPress, but no longer exist in your `/wp-content/plugins/` directory.

## Screenshots ##

### 1. [An example of the introductory information presented on the plugin's admin page](screenshot-1.jpg) ###

### 2. [Part of the "Inactive Plugins" list presented by this plugin](screenshot-2.jpg) ###

### 3. [Part of the "Active Plugins" list presented by this plugin](screenshot-3.jpg) ###

## Changelog ##

### 2.0 ###
* Implements new layout of plugin lists
* Adds deactivated plugins to list of Recently Active plugins in appropriate admin pages
* Implements "Bulk Actions" for items in the plugins list; allowing you to:
  * Delete multiple inactive plugins at once
  * Network-deactivate multiple plugins on all networks at once
  * Blog-deactivate multiple plugins on all blogs at once

### 1.1.2 ###
* Test compatibility with latest version of WordPress and update readme to reflect compatibility

### 1.1.1 ###
* Implement better method to test for main network

### 1.1 ###
* Reorganize files within plugin folder
* Re-formulate status table to use native WP_List_Table layout

### 1.0.2.1 ###
* Adds i18n and l10n features

### 1.0.2 ###
* Tested compatibility with WordPress 4.9.x
* Fixes undefined constant warning as pointed out by [@chenryahts](https://wordpress.org/support/topic/use-of-undefined-constant-missing-character/)
* Fixes undefined index warning as pointed out by [@cliffpaulick](https://wordpress.org/support/topic/wp_debug-php-notice-undefined-index-site_id/)
* Begins adding compatibility with core implementation of multi-network (uses the [`is_main_network()` function](https://developer.wordpress.org/reference/functions/is_main_network/))

### 1.0 ###
* Tested compatibility with WordPress 4.0
* Added link allowing you to delete inactive plugins

### 0.3 ###
* Added new buttons allowing you to deactivate plugins on all sites/networks from within the list
* Tested with WP 3.8.2 to ensure everything still works

### 0.2 ###
* Moved styles to their own style sheet
* Changed name of plugin to "Plugin Activation Status"
* Split plugin into separate files

### 0.1 ###
* First beta release of "UMW Plugin Locator"

## Upgrade Notice ##

### 2.0 ###
Completely new layout; some new functionality

### 1.1 ###
The file structure of this plugin has changed; if you are upgrading manually (especially if this is a mu-plugin), be sure to delete old files & upload all-new versions

### 1.0.2.1 ###
Adds i18n and l10n features

### 1.0 ###
This version adds the ability to deactivate any active plugins and delete any inactive plugins.

### 0.2 ###
The file structure for this plugin, along with the file name of the main plugin file, have changed. You should *delete* the old copy of this plugin before installing this new version.
