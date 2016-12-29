# Dev notes

An attempt at insight and lessons learned from a Drupal developer trying to do make Drupal spit out suitable html for email.

## What's that do?

Brief explanation of new concepts encountered while building an email template.

* What does this do? `<meta http-equiv="X-UA-Compatible" content="IE=edge">`
  * Edge mode tells IE to display content in the highest mode available.
  * The IE=Edge tag enables responsive behavior in Windows phones, which is VERY welcome for email developers. However, it will also break all of your images in Live Mail (God knows why, thanks Microsoft!). The solution is pretty simple though: just wrap your IE=Edge meta tag in a conditional comment to hide it from Live Mail, as I have it below.
  ```
  <!--[if !mso]><!-- -->
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
  <!--<![endif]-->
  ```
* Minimum of 2 nested table in layouts
  * 1 is the redundant `<body>` element. Some email clients strip some clients strip outer most element in body to render.
  * 1 is the "Email Container" - Sets width.

## Do's and Don'ts of email a web dev wouldn't know

Steadfast rules to live by when working on an email template

## Hard lessons learned

Pain points encountered

* Drupal theme functions doesn't allow for style attributes to be used.
  * style attributes are stripped at render time for security purposes.