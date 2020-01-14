Design Concepts

Check fonts on google.com/fonts

Copyright free Image on pixabay.com

To make logos using logomakr.com

More templates on tyler.com

png format can contain transparent images.

Installation
Launch WordPress using AWS EC2
When creating EC2 instance, choose WordPress powered by BitNami as the Amazon Machine Image(AMI)
If the instances terminal access is not required, it can be processed without a key pair.
Use the public IP/login to go to the Dashboard.
Login username will be user, password can be found in Actions -> Instance Setting -> Get System Log for WordPress instance. The password is surrounded by hash marks.
———————————————————-
To remove the banner link to the Bitnami Info page, follow these steps:

Log in to into your server console using SSH and execute the following command.

sudo /opt/bitnami/apps/wordpress/bnconfig --disable_banner 1

If you’re using Apache, execute the command below: (The type is indicated in the AMI info)

sudo /opt/bitnami/ctlscript.sh restart

If you’re using NGINX, execute the command below:

sudo /opt/bitnami/ctlscript.sh restart nginx

Website Design


Website management

Example website access:
yourdomain.com

Dashboard Access:
yourdomain.com/login
or
yourdomain.com/wp-admin
or
yourdomain.com/admin

view site
in the top navigation bar, click Create a Website -> View Site

update wordpress
In dashboard left panel, click on updates.

Change password:
In dashboard left panel, clicking the user name, then change the password.

Permalinks settings:
The links format for your website pages.
In the dashboard left panel, click settings -> Permalinks.

Themes management
In dashboard left panel, Appearance -> Themes,
or
under the navigation menu when viewing the website, click create a website -> themes

all the Installed themes are displayed here. Some theme has its own plugins for easier editing.

Install - installation first, then activation


Pages management
In dashboard left panel, click Pages
Delete - click trash to move the page to trash can, then delete it permanently in the trash can.

Posts management
In dashboard left panel, click Posts
Delete - click trash to move the post to trash can, then delete it permanently in the trash can.

Plugins:

Install - in the dashboard side menu click plugin -> add new, then it can be searched and installed.
or
download the plugin from the internet, then drag and drop plugin files to upload.

Delete - deactivate first, then delete the plugins.

Plugins can have add-ons for more modification, most of the add-ons are paid.
Plugins can provide more options for widgets.


Add template files
In the dashboard left side menu click Elementor -> My Library -> Add New





Content Design

Customize:
Located in the top navigation menu.
It is used to editing homepage setting, menus, header, and footer of the website.
select the blue icon to change the related item in the left menu.
Click public on the top of the left panel to save changes.
Click the exit button to view the website.

Header includes menus
Pages can be added to the menu.

menu types
Top bar:       A bar menu on the top of the page.
Main menu: A navigation menu beside the page title.

Set Site Title:
In the top navigation bar, click customize, select site identity.
Site Title is the Name of the website.
Tagline is the explanation of the website.
Site Icon is the icon for the site in the tab of the browser.(should be at least 512X512px)


footer template
It is added through theme panel.
There are two footers in many templates, one is the desktop version and the other is the mobile version.
footer template section is added to the pages as footer widget.

Add logo
An image or image with text on the top of every pages.
In Customize, select header -> logo


New Pages:
in the top navigation menu, select New -> Page -> Type page title -> Edit with elementor
or
add pages in the pages menu in the dashboard and type pages context in the white space like using Office Word. Clicking update after editing.
templates can be added for the new page or drag and drop elements from the left panel for customization.
Settings for the new page is shown at the bottom.

The pages URL slug is set in the quick edit menu.

Clicking save button to save the design of this new page.


Add Posts
For themes designed with post layouts, when new post is added, the page are updates with new post in the bottom.

Theme editor
Access functions.php Through WordPress Admin
Log in or sign in WordPress as administrator.
Select "Appearance > Theme Editor" from the sidebar.
In the editor, select the theme which you want to edit from "Select theme to edit" drop-down menu.
Locate the file for edition.

functions.php It contains all the functions definitions of specific wordpress theme.




















Plugins for different functions:

Export as static webpages
Plugins like WP Static HTML Output or Simple Static or WP2Static can be used to convert the web pages into HTML files.

Elementor:
It is a very popular page builder.
It is a plugin.
Located in the top navigation menu.
It is used for editing website main content except header and footer.
After clicking the edit with elementor button, all the page content can be selected and edited directly.
For text, clicking on the text and starting to edit. html tags can be used inside its text editor.
For button, clicking on the button and edit its appearance in the left panel.
For image, clicking on the image, selecting the image in the left panel, then drag and drop the desired image file.

The default setting for all elements are not zero.

Any element can be duplicated and dragged around.

When done editing, clicking save in the left menu to save the image.

Adaptive Design:
Display device can be chose in the left bottom menu, then adaptive design can get started for different devices.
set minimum height for 100 vh to make sure the content cover the entire screen.

For all elements in the advanced menu, padding and margin can be set for three screen sizes (desktop, tablet and mobile devices) separately.

Navigator found in the bottom left menu is very easy for element selection.

Clicking on the exit button in the left bottom corner, selecting View Page or Dashboard to quit.


Templates
It provide templates in the library, template json files can be searched and downloaded online and imported to build customized pages.

Font will not be adjustable if the paragraph is copied with certain font settings from any word editing software.


Contact Form
It can be added using plugins like Contact Form 7, wpforms or ninja form
Contact Form can then be created and edited in the Contact section of the dashboard left panel.
make sure the email address is set properly, so when reader submit the form the content can be sent to this email address. By default, some plugin uses the email address in the dashboard setting.
copy the shortcode. in the elementor page editing interface, add a new shortcode element and paste the code in the shortcode element menu to add contact form to the page.
shortcode can also be used in the text editing mode(the method like using Office word) for a new page.
for some plugins, insert the form as an element.


Slider
It is created using plugin like Smart Slider 3.
It can be edited in the Smart Slider section of the dashboard left panel.
It can be added as elementor’s element.


Polylang
Add language options for the website in the plugins setting. Add new menu and new pages for different language. Be aware of the new language options for pages management on the top WordPress navigation bar. And new positions for menus in different language.

Custom Sidebar
Add custom sidebars to hold different widgets in different position.
