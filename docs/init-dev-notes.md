# Make Drupal Email

TL;DR You can't

## Notes from colleague

* Use Litmus for help, they have a great [community](https://litmus.com/community ) a lot of [snippets](https://litmus.com/community/snippets) and free [templates too](https://litmus.com/community/templates).
* If anything needs to be “responsive” look up the Fluid Hybrid coding approach
* Quick tips:
  * Standard email template width is 600px and no more than 650px (Outlook doesn’t read %)
  * Code keeping in mind the most popular email clients, Apple, Gmail, Outlook and Yahoo. Outlook is the hardest and requires conditional code for certain elements (i.e. bulletproof buttons, web fonts, width, etc.) This may be helpful for [starters:](https://www.emailonacid.com/images/blog_images/downloads/2014/wp_outlook.pdf)
  * Use wrapper and container tables.
  * Some email clients read CSS, but not all. Inline styling is best.
  * Use the standard range of “Client Specific Styles” to target certain rendering issues (check out Litmus templates)
  * Hyperlinks default to underlined blue in many clients if styling is not added to the hyperlink itself
* Campaign Monitor and Email on Acid are also useful resources.

-----------

## Issues with template

* Some clients, e.g. will find dates and addresses and convert themt o hyperlinks, e.g. to add them to the calendar. If there is no styling it defaults to hyperlink-blue
* Outlook can't read the `<style>` so everything NEEDS to be inline styles as much as possible
* the `<style>` in the body needs to be moved to the `<head>`
* Biggest email clients - apple (iphone, mac), gmail, outlook, and yahoo
* webfonts - outlook can't do the webfonts, and if nothing is explicitly applied to outlook, then it defaults to times new roman
  * Add conditional fallback for outlook that relies on the fallback fonts.
  * font awesome icons aren't going to be reliable, see pain abuot web font
* Are not able to dynamically load external css sheets
* Most emails contain a standard set of css rules.
  * [example](https://gist.github.com/aczietlow/f8276268af76f445ea9a1fec1e2c4f00)
* We should have `<meta http-equiv="X-UA-Compatible" content="IE=edge" />`, (What does it do?)
* Responsiveness
  * Need wrapper tables - (Can't believe I just typed that)
  * Email clients don't really do % based widths, the standard is 600px, 650px being the widest
  * [good resource](https://litmus.com/blog/understanding-responsive-and-hybrid-email-design)
  * Responsiveness in outlook is going to be hard
    * not all outlook clients are the same
      * 2011 can do %, but 2013 can not
      * Also differs from OS e.g. mac and windows
* To many table, causing spacing issues in outlook.
  * outlook adds a lot of space around tables
    * padding or margin? or not something that we can control?
* can't use all header tags. Not all clients respect smaller header tags. Use font weights where possible
  * not 100% on this one, research further.
* Styles for elements need to be applied directly to those elements, not wrapping parent tags.
  * e.g. `<p class="read-more align-left"><a href="index.html">+ Read More</a></p>`
  * should be `<a href="index.html" class="read-more align-left">+ Read More</a>`
  * or `<a href="index.html" style="text-decoration: none; color: #347928; text-align:left;">+ Read More</a>`
* Img should all have alt and title tags.
  * helps with Spam
  * and ereaders
  * Falls under the "don't be shitty" design principle

## Issue with Drupal theming

* Drupal theme functions don't allow for the `<style>` attribute for sec reasons.
* All images and links need to use full paths, no relative path

## Mailchimp needs to put the sub/unsub links at the bottom

* Does MC add the sub/unsub links if we dump a full html email?
* Figure out how to add a newsletter subscribe form to Drupal from MC

--------

## Things to look into further:

* Whiskey... lots of whiskey
* Litmus will take css styles, within a sytle tag, and add them inline.
  * That may be an option rather than making Drupal do it