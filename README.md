# Making browsers backward compatible HTML5

All browsers have a master list of HTML elements which they support. Elements which are not in that list are treated as **unknown-elements**.

For unknown elements two things must be figured out:

1. Styling
2. Overall look in DOM

In the first part,  it's simple : 
*Don’t give any special styling to unknown elements. Just let them inherit whatever CSS properties are in effect wherever they appear on the page, and let the page author specify all styling with CSS. And that works, mostly, but there’s one little gotcha you need to be aware of.*

**Note:** All browsers render unknown elements inline, i.e. as if they had a display:inline CSS rule.
So to support HTML5 elements for the older browser, you should style them as block level elements.

For more accurate setting up, you can use the following [reset sheet](http://html5doctor.com/html-5-reset-stylesheet/) from Richard Clark

In the second part, IE ( < 9) is most trouble making browsers. THe solution is creating the element once (per page) in JavaScript  to teach IE ( <9 ) to style the element it doesn’t recognize; like `document.createElement("article");` 

Remy Sharp has “minified” this script so-call `HTML5 SHIV` and hosted it on [Google Project Hosting](https://github.com/afarkas/html5shiv). If you like, you can even “hotlink” the script by pointing directly to the hosted version, like this:

```<head>
  <meta charset="utf-8" />
  <title>My Weblog</title>
  <!--[if lt IE 9]>
  <script src="http://html5shiv.googlecode.com/svn/trunk/html5.js"></script>
  <![endif]-->
</head>```
