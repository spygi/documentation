## Basics
* [MDN full reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference).  
Some remarks:  
    * Child vs Descendant: children are direct descendants (like in graph theory). Children are selected with `>` while any descendant with ` `.
    * Selecting an element based on 2 (or more) classes, attr etc: `.hello.world { }` for a `<div class="hello world"/>`.
    * CSS3: ':hover' is a pseudo-class vs '::after' which is a pseudo-element. Pseudo-classes can be used for state (active, checked etc), to react to user actions (hover, focus etc), to access directly elements of lists (first-of.., nth-of etc.) or validate stuff (). Some useful pseudo-elements are first-letter, first-line and selection (can't find a good use case for after or before...)

## CSS Grid
For 2 dimensional designs, works well with Flex (they even share `align|justify-content|items`). 
* Notes: 
   * Explicit vs implicit grids: when you don't specify all properties the auto-placement algorithm kicks in. [For example](https://codepen.io/anon/pen/LzYVrw): 
       * no grid-template-rows is specified yet content and footer go in new rows.
       * even in the columns which are specified new columns need to be created for sidebar.
   The auto-placement algo is controlled via `grid-auto-flow`.
   * Naming of lines: start from 1 or you can specify (multiple) names with `[aname]`
* [CSS-tricks guide](https://css-tricks.com/snippets/css/complete-guide-grid/)
* [Grid garden game](http://cssgridgarden.com/): not a complete reference but OK for a start
* [Rachel Andrew's grid by example](https://gridbyexample.com/) and [cheatsheet for box alignment grid-flexbox](https://rachelandrew.co.uk/css/cheatsheets/box-alignment)

## Flexbox
* http://flexboxfroggy.com/
* https://css-tricks.com/snippets/css/a-guide-to-flexbox/
* https://codepen.io/justd/pen/yydezN/

## Transform
* Still mostly experimental (at the time of writing this)
* Applies on 'tranformable' elements which are block or inline block elements.
* For an annotated example check out [this](https://github.com/spygi/cv-app/commit/47c2276abcfc74ee9d6db3c77b40077ff58e8a94)

## Styleguide
* [Ordering properties](https://css-tricks.com/poll-results-how-do-you-order-your-css-properties/)
* [Css-tricks sass styleguide](https://css-tricks.com/sass-style-guide/)
* [Airbnb's styleguide](https://github.com/airbnb/css)
* Shorthand vs longhand: [explicit is better than implicit but also simple is better than complex](https://www.python.org/dev/peps/pep-0020/). The extra bytes argument against longhand is funny [and also wrong in some cases](https://www.impressivewebs.com/longhand-padding-margins/). As a rule of thumb, go with readability. If the settings are of different values (e.g. solid 1px red;) shorthand is easier to understand. Some good candidates for shorthand are [here](https://devrix.com/tutorial/css-shorthand-vs-longhand-properties/).  
    * NB: the shorthand order in box-related properties (e.g. `padding` and `margin`) is clockwise, while in grid-related ones (e.g. `grid-area`, `grid-template`) it's counter-clockwise.
