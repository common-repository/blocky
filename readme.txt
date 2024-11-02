=== Blocky! - Additional Content Blocks ===
Contributors: cameronjonesweb,blockyplugins
Tags: admin, builder, cms, css, class, page, post, page builder, content, post meta, ajax, posts, pages, wordpress
Donate link: https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=WLV5HPHSPM2BG&lc=AU&item_name=Cameron%20Jones%20Web%20Development¤cy_code=AUD&bn=PP%2dDonationsBF%3abtn_donateCC_LG%2egif%3aNonHosted
Requires at least: 4.2
Tested up to: 4.4.2
Stable tag: 1.2.8
License: GPLv2
License URI: http://www.gnu.org/licenses/old-licenses/gpl-2.0.html

Blocky! is a revolutionary new way to manage your content and add additional sections to your page content with no theme editing required!

== Description ==
Have ever encountered the need to add new sections to your page content without needing to add divs to your content, editing your theme files or using a widget? Are you a WordPress novice and have no idea what that previous sentance means? Fear no longer - Blocky! is here. 

Blocky! allows you to add a new section to the content of your posts and pages without needing to know any web coding. Simply click on the "Add New Content Section" button and get typing. Blocky! brings in a new WYSIWYG editor, allowing you to add more content the same way you would with your main post content. Want to change the layout of your additional content sections? Simply add classes to your content section and use your stylesheet to do the rest. Would you rather not wrap your content in a `div`? Simply edit it in the settings page. Only want to use Blocky! on select post types? You can choose which post types to enable Blocky! from the settings page. Blocky! also grabs the current setting for the WYSIWYG editors, meaning that your Blocky! editors are consistent with the content editors even if you are using a plugin such as TinyMCE Advanced that extends the capabilities of the editor.

For more advanced uses, use the `get_additional_content( $postID );` to return Blocky!'s additional content as a multidimensional array with each section containing an array with both the class and the content. See "Other Notes" for more details.

If you like the plugin, please take the time to leave a review.

== Installation ==

= From your WordPress dashboard =

1. Click `Add New` from the plugins page in your WordPress site
2. Search for `Blocky! - Additional Content Sections`
3. Click on install

= Alternatively from wordpress.org =

1. Download the latest version of Blocky! - Additional Content Sections
2. Extract the files
3. Upload the entire `blocky` folder to the `/wp-content/plugins/` directory.

4. Activate the plugin through the 'Plugins' menu in WordPress.

== Frequently Asked Questions ==
= Why can't I use the plain text editor or media uploader? =
Unfortunately the way the WYSIWYG editor is activated for new sections it doesn't support the plain text editor or media uploader for new sections. However if you save your post any content sections that had been created will include both the media uploader and plain text editor.

= Why don't you just use a widget? =
I have found that users find it easier if all the content for a page or post is confined to the editor for that page or post, not split across multiple pages.

= Why aren't my Blocky! content sections saved in the revisions? =
Blocky! content sections are saved as post meta, which is different to post content. Only the title and content are saved in revisions. This is something I will look to explore in future versions.

= Can I get an unfiltered version of my post content? =
Yes. Blocky! adds a filter to the `the_content()` function, but you can use `echo get_the_content();` in your template to return your post content unfiltered. Blocky! also includes a `get_additional_content()` function, which returns the additional content sections as an array, so you can use your additional content sections in more advanced uses such as in a sidebar, with nested tags, use the class input as a data-attribute or to add additional filters to your additional content.

= I'm getting `stripos` and `preg_match_all` errors =
If you're using Jetpack's Embed Shortcodes module and Blocky 1.2.1 or below you will get these errors when saving a post. Please update to at least 1.2.2.

== Screenshots ==
1. The admin interface
2. Blocky! settings page
3. Blocky! in action

== Changelog ==
= 1.2.8 =
* Changes sanitization to only be dependent on posts instead of the post type
= 1.2.7 =
* Fixes data not being saved
= 1.2.6 =
* Fixes another undefined index bug
= 1.2.5 =
* Setting priority so additional content is grouped with the main post content
= 1.2.4 =
* Fixes `undefined index` bug
= 1.2.3 =
* Direct link to setting page from plugins page
* Setting Blocky! to be active on posts and pages by default when first installing
* Text fixes
* Additional conflict fixes
* Sanitizing class as well as content
= 1.2.2 =
* Fixing conflict with Jetpack's Shortcode Embeds module
= 1.2.0 =
* Changed settings page heading tag to come into line with WP 4.3 standards
* Updated to support translations
= 1.1.3 =
* Added filter to include Blocky! section content in Yoast SEO's Page Analysis
= 1.1.2 =
* Fixing `invalid argument for foreach` bug that would appear on seemingly random excerpts
= 1.1.1 =
* Applied `do_shortcode` filter to Blocky!'s content filter.
= 1.1.0 =
* Added `get_additional_content()` function to allow for more advanced uses of Blocky!
* Small readme fixes
= 1.0.2 =
* Fixing bug that would return errors if there were no content sections and `WP_DEBUG` is turned on.
= 1.0.1 =
* Fixing bug where meta box wouldn't close in certain situations
= 1.0 =
* Initial release

== Upgrade Notice ==

= 1.2.7 =

If you're using a version above 1.2.3 and less than 1.2.7 you need to update immediately.

= 1.2.3 =

This version further fixes some Jetpack conflicts. Please update immediately.

== Advanced Use Case ==
To use Blocky! without the content filter, use this template

Replace `<?php the_content();?>` with `<?php echo do_shortcode( get_the_content() );?>`

Where you want your additional content to display, add this code

`<?php $additional_content = get_additional_content();
for( $i = 0; $i < count($additional_content); $i++ ) {
	echo $additional_content[$i]['content'];
}?>`