# WordPress

## Introduction

* It uses PHP at the backend.
* It powers roughly 1/3rd of the web, tens of millions of sites.
* Based on PHP & MySQL.
* First released in 2003.
* WordPress is the most popular CMS.
  * Content management systems\(CMS\) are applications\(web apps\) used to manage digital content.
  * 50% of the webs are made by Content Management Systems.
  * Popular CMSs are listed below. They are all written in PHP.
    * WordPress
    * Drupal
    * Joomla

## Installation

### Launch WordPress in an Apache Server

1. Unzip the content inside the [WordPress](https://en-ca.wordpress.org/download/) package in the folder that will be hosted by the server.
2. Visit the website in a browser.
3. Select the database created for the website.
4. Enter the admin info.
5. Launch the Site.

### Launch WordPress using AWS EC2

1. When launching an EC2 instance, choose WordPress powered by BitNami as the Amazon Machine Image\(AMI\)
   * If the SSH connection to the server is not required, it can be processed without a key pair.
2. Put the public IP in the address bar in a browser to login the site.
   * Login username will be `user`,
   * password can be found in `Actions -> Instance Setting -> Get System Log for WordPress instance.` The password is surrounded by hash marks.
3. To remove the banner link to the Bitnami Info page, follow these steps:
   * Log in to your server console using SSH and execute the following command. `sudo /opt/bitnami/apps/wordpress/bnconfig --disable_banner 1`
   * If you’re using Apache, execute the command below: \(The type is indicated in the AMI info\) `sudo /opt/bitnami/ctlscript.sh restart`
   * If you’re using NGINX, execute the command below: `sudo /opt/bitnami/ctlscript.sh restart nginx`

## Website Management

* Example website access: `yourdomain.com`
* Dashboard Access:
  * `yourdomain.com/login`
  * `yourdomain.com/wp-admin`
  * `yourdomain.com/admin`
* View Site - in the top `navigation bar`, click `Create a Website -> View Site`
* Update WordPress - In the dashboard left panel, click on updates.
* Change password - In the dashboard left panel, clicking the user name, then change the password.
* Permalinks settings - The links format for your website pages. In the dashboard left panel, click settings -&gt; Permalinks.
* All of the settings are stored in the database table `wp-options`.

## Themes Management

* They are templates.
* It can be customized by users, created and sold for profit. [Click](https://codex.wordpress.org/Theme_Development) to see the docs about themes development.

### Install Themes

* Installing WordPress Themes can usually be done automatically from the backend.
  * In dashboard left panel, Appearance -&gt; Themes
  * under the navigation menu when viewing the website, click create a website -&gt; themes
  * all the Installed themes are displayed here. Some theme has its plugins for easier editing.
  * Click `Add New` to install new themes.
* Optionally, WordPress themes can also be installed by unzipping them into `/wp-content/themes` folder.
* WordPress themes then need to be activated to make them the currently used theme.
* Some themes are powered by the desgniated plug-ins like `Ocean Extra` for `OceanWP`.

### Theme Package Files

* `style.css`
  * Defines the CSS styles for the theme
  * It contains theme details in comments at the top of the page
  * These theme details must be present for the theme.
  * Each theme must have unique theme details.
* screenshot.png
  * This will represent the theme in the WordPress backend theme selection page
* `js`, `img`, `fonts` folders
  * These folders contain images, Javascript, fonts and other code used by the theme to render the page.
* `functions.php`
  * Acts like a plugin... it’s run by WordPress during initialization•
  * Can define helper functions used in your theme files.
  * Loads theme style sheets and scripts
  * Enables theme features such as sidebars, navigation menus, etc.
  * Set up the options menu to allow admin users the ability to change aspects of the theme.
* Template Files
  * [Click](https://codex.wordpress.org/Stepping_Into_Templates) to see more explanation about template files.
  * They are located in the root of each theme folder.
  * `index.php` mandatory is the main template file.
  * `page.php` is the template that displays all pages by default.
  * `header.php` is the template that displays all of the `<head>` section and everything up until.
  * `single.php` template for a single post.
  * etc.
* `template` Folder
  * It contains templates for page settings.
* `template-part` Folder
  * It contains sample components.

### Theme Editor

* It can be used to edit theme files directly from the console.
* Steps
  * Access `functions.php` Through WordPress Admin
  * Log in or sign in WordPress as administrator.
  * Select "Appearance &gt; Theme Editor" from the sidebar.
  * In the editor, select the theme which you want to edit from `Select theme to edit` drop-down menu.
  * Locate the file for edition.

### Customize Theme

* Click on the `Customize` button in the top navigation menu.
* It is used to editing homepage settings, menus, header, and footer of the website.
* Select the blue icon to change the related item in the left menu.
* Click publish on the top of the left panel to save changes.
* Click the exit button to view the website.
* Header includes menus
* Page links can be added to the menu.
* menu types
  * Top bar: A bar menu on the top of the page.
  * Main menu: A navigation menu beside the page title.
* Set Site Identity:
  * In the top navigation bar, click customize, select site identity.
  * Site Title is the Name of the website.
  * A tagline is the explanation of the website.
  * Site Icon is the icon for the site in the tab of the browser.\(should be at least 512X512px\)

### Special Setting

* Different Theme might have different settings in the customize menu.
* For the famous `OceanWP` theme, it has.
  * Footer template
    * It is added through the theme panel.
    * There are two footers in many templates, one is the desktop version and the other is the mobile version.
    * Footer template section is added to the pages as footer widget.
  * Add logo
    * An image or image with text on the top of every pages.
    * In Customize, select header -&gt; logo

### Child Themes

* Allow us to make tweaks to existing themes that won’t be overwritten when the parent theme is updated.
* Steps to create a child theme
  1. Create a child theme folder as in the `theme` folder.
     * The name of the child theme can be `parentThemeName-child`.
  2. Create a `style.css`
     * Must have a unique name.
     * Add `Template: parentThemeDirectoryName` in the file.
  3. Inherit parent theme in `functions.php`
     * Example Code:

       ```php
       <?php
       add_action( 'wp_enqueue_scripts', 'my_theme_enqueue_styles' );
       function my_theme_enqueue_styles() {
       $parent_style = 'parent-theme-name';
       wp_enqueue_style( $parent_style, get_template_directory_uri() . '/style.css' );
       wp_enqueue_style( 'child-style',
         get_stylesheet_directory_uri() . '/style.css',
         array( $parent_style ),
         wp_get_theme()->get('Version')
       );
       }
       ```
  4. Activate child theme
  5. Adding Template Files
     * Any file that is added to the child theme will overwrite the same file in the parent theme.

## Pages Management

* To manage pages, in dashboard left panel, click Pages
  * Delete - click trash to move the page to the trash can, then delete it permanently in the trash can.
  * Add New Page, in the top navigation menu, select New -&gt; Page -&gt; Type page title -&gt; Edit with `elementor`.
  * Optionally, add pages in the pages menu in the dashboard and type pages context in the white space like using Office Word. Clicking update after editing.
* templates can be added for the new page or drag and drop elements from the left panel for customization.
* Settings for the new page is shown at the bottom.
* The pages URL slug is set in the quick edit menu.
* Clicking the save button to save the design of this new page.

## Posts management

* To manage posts, In dashboard left panel, click Posts
  * Delete - click trash to move the post to the trash can, then delete it permanently in the trash can.
* For themes designed with post layouts, when a new post is added, the page is updated with the new post at the bottom.

## Plugins:

* Plugins extend the functionality of WordPress.
* It can be customized, created and sold for pro
* Plugins can have add-ons for more modification, most of the add-ons are paid.
* Plugins can provide more options for widgets.

### Install Plugins

* In the dashboard side menu click plugin -&gt; add new, then it can be searched and installed.
* Optionally, download the plugin from the internet, then drag and drop plugin files to upload.

### Delete Plugins

* Deactivate first, then delete the plugins.

### Popular Plugins

#### Elementor:

* It is a very popular page builder.
* It is a plugin.
* Located in the top navigation menu.
* It is used for editing website main content except for header and footer.
* After clicking the edit with the elementor button, all the page content can be selected and edited directly.
* For text, click on the text and starting to edit. html tags can be used inside its text editor.
* For button, clicking on the button and edit its appearance in the left panel.
* For image, clicking on the image, selecting the image in the left panel, then drag and drop the desired image file.
* The default setting for all elements are not zero.
* Any element can be duplicated and dragged around.
* When done editing, clicking save in the left menu to save the image.
* Adaptive Design:
  * Display device can be chose in the left bottom menu, then adaptive design can get started for different devices.
  * set minimum height for 100 vh to make sure the content cover the entire screen.
* For all elements in the advanced menu, padding and margin can be set for three screen sizes \(desktop, tablet and mobile devices\) separately.
* Navigator found in the bottom left menu is very easy for element selection.
* Clicking on the exit button in the left bottom corner, selecting View Page or Dashboard to quit.
* Templates
  * It provide templates in the library, template json files can be searched and downloaded online and imported to build customized pages.
  * Add template files - In the dashboard left side menu click Elementor -&gt; My Library -&gt; Add New
* Font will not be adjustable if the paragraph is copied with certain font settings from any word editing software.
* use iframe to open a window inside a window,`<iframe src="https://huegoxaga.github.io/notes/"> </iframe>`

#### Contact Form

* It can be added using plugins like Contact Form 7, wpforms or ninja form
* Contact Form can then be created and edited in the Contact section of the dashboard left panel.
* make sure the email address is set properly, so when reader submit the form the content can be sent to this email address. By default, some plugin uses the email address in the dashboard setting.
* copy the shortcode. in the elementor page editing interface, add a new shortcode element and paste the code in the shortcode element menu to add contact form to the page.
* shortcode can also be used in the text editing mode\(the method like using Office word\) for a new page.
* for some plugins, insert the form as an element.

#### Slider

* It is created using plugin like Smart Slider 3.
* It can be edited in the Smart Slider section of the dashboard left panel.
* It can be added as elementor’s element.

#### Polylang

* Add language options for the website in the plugins setting. Add - new menu and new pages for different language. Be aware of the new language options for pages management on the top WordPress navigation bar. And new positions for menus in different language.

#### Custom Sidebar

* Add custom sidebars to hold different widgets in different positions.

#### Export as static webpages

* Plugins like WP Static HTML Output or Simple Static or WP2Static can be used to convert the web pages into HTML files.

