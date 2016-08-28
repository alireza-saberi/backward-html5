# Making browsers backward compatible HTML5

All browsers have a master list of HTML elements which they support. Elements which are not in that list are treated as **unknown-elements**.

For unknown elements two things must be figured out:

1. Styling
2. Overall look in DOM

In the first part,  it's simple : 
*Don’t give any special styling to unknown elements. Just let them inherit whatever CSS properties are in effect wherever they appear on the page, and let the page author specify all styling with CSS. And that works, mostly, but there’s one little gotcha you need to be aware of.*

**Note:** All browsers render unknown elements inline, i.e. as if they had a display:inline CSS rule.
So to support HTML5 elements for the older browser, you should style them as block level elements.
