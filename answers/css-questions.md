# CSS Questions

#### What is reflow?What causes reflow?How could you reduce reflow?
The re-calculation of positions and dimensions of all elements, which leads to re-rendering part or all of the document. Changing a single element can affect all children, ancestors, and siblings.

Causes are: 
- Adding, removing or changing visible DOM elements
- Adding, removing or changing CSS styles
- CSS3 animations and transitions
- Using offsetWidth and offsetHeight
- User actions

We can reduce it by:
- Use Best-Practice Layout Techniques
- Minimize the Number of CSS Rules
- Minimize DOM depths
- Update Classes Low in the DOM Tree
- Remove Complex Animations From the Flow
- Modify Hidden Elements
- Update Elements in Batch
- Limit the Affected Elements
- Recognize that Smoothness Compromises Performance
- Analyze Repaint Issues with Browser Tools

https://www.sitepoint.com/10-ways-minimize-reflows-improve-performance/


#### What is Repaints?
A repaint occurs when changes are made to elements that affect visibility but not the layout. For example, opacity, background-color, visibility, and outline. Repaints are expensive because the browser must check the visibility of all other nodes in the DOM — one or more may have become visible beneath the changed element.


#### What is the difference between visibility:hidden and display:none?


display:none means that the tag in question will not appear on the page at all (although you can still interact with it through the dom). There will be no space allocated for it between the other tags.

visibility:hidden means that unlike display:none, the tag is not visible, but space is allocated for it on the page. The tag is rendered, it just isn't seen on the page.


#### How do you clear float?

clear: both

overflow: hidden

empty div after floated element


#### What is the difference between classes and ID's in CSS?

Id is unique and you can use only one with that name on your page. Class you can assign to different elements and have two and more elements with same class on your page; id is also more specific when you style elements because of it's priority. So if you use same styles (font-size, for example) to the same element with id (20px) and class (10px) the font-size of id will be used.

#### What's the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?

- Resetting: Remove all the native styles provided by browsers
- Normalizing: Make the browser styles consistent

#### Describe Floats and how they work.

There are `left`, `right` and `none` for `float`. Each value indicates how an
element should float. When `float` is set, each element will get out of its
normal flow and will be shifted to the specified direction, until it gets its
container or another floated element.

#### Describe z-index and how stacking context is formed.

`z-index` tells how elements should be stacked in a screen. Stacking context
can be formed in several situations, but most famously, by a root element and
positioned elements. In each stacking context, `z-index` will be calculated
separately for its children and will stack the children in ascending order.

#### Describe BFC(Block Formatting Context) and how it works.

BFC is a part of rendering a webpage. It's used to determine from which
positioning and clearing should be done. The context is created by several
ways, but the most famously, by a root element, float, positioned elements.

#### What are the various clearing techniques and which is appropriate for what context?

```css
clear:both;
```

```css
overflow: hidden;
height: auto;
```

#### Explain CSS sprites, and how you would implement them on a page or site.

CSS sprite is combining multiple images into a merged one image and use CSS to
render each of them properly for each element.

It's usually implemented using `background: url(...) x-axis y-axis;`, or
both `background-image` and `background-position`.

#### What are your favourite image replacement techniques and which do you use when?

Image replacement technique is to replace a normal text element with an image.
There are many methods such as H5BP and Scott Kellum, as suggested [here](https://css-tricks.com/the-image-replacement-museum/).

My favourite is H5BP, as it is the simplest and most intuitive one.

#### How would you approach fixing browser-specific styling issues?

Use a separate stylesheet that only loads when that specific browser is being used. Thankfully, the days of IE specific stylesheets are almost gone.

#### How do you serve your pages for feature-constrained browsers?

Polyfills or graceful degradation.


###### What techniques/processes do you use?

Nowadays, I tend to use webpack, wherein I use SASS as a preprocessor. I then run it through PostCSS using autoprefixer so I don't have to worry about vendor prefixes. I then use CSS modules to create component specific styles.

Otherwise, I tend to use BEM, but there are plenty of others. Atomic Design is also worth looking into.

- OOCSS
- SMACSS

#### What are the different ways to visually hide content (and make it available only for screen readers)?

```
visibility: hidden;
```

```
display:none;
```

#### Have you ever used a grid system, and if so, what do you prefer?

Yes, but not so many. I prefer Bootstrap.

#### Have you used or implemented media queries or mobile specific layouts/CSS?

Yes, Media query is a CSS technique introduced in CSS3. It uses the @media rule to include a block of CSS properties only if a certain condition is true.

```
@media only screen and (max-width: 600px) {
    body {
        background-color: lightblue;
    }
}
```
If the browser window is 600px or smaller, the background color will be lightblue:

#### Are you familiar with styling SVG?

SVG is an image format for vector graphics. It literally means Scalable Vector Graphics. Basically, what you work with in Adobe Illustrator. You can use SVG on the web pretty easily.

Advantages:

- Small file sizes that compress well
- Scales to any size without losing clarity (except very tiny)
- Looks great on retina displays
- Design control like interactivity and filters


#### How do you optimize your webpages for print?

```css
@media print {
  ...
}
```

#### What are some of the "gotchas" for writing efficient CSS?

Usually about CSS selectors.

- Avoid key selector for large numbers of elements
- Prefer class and ID selector to tag selector
- Avoid redundant selectors
- Care of batching

#### What are the advantages/disadvantages of using CSS preprocessors?

Advantages:

- Nested tags
- Mixins
- Importing other styles in
- Modularity


Disadvantages:

- Nested tags are hard to read after a certain point
- Have to use build tools to compile
- Easy to abuse (@extend in sass)



###### Describe what you like and dislike about the CSS preprocessors you have used.

Likes:

- Mostly the advantages mentioned above.
- Less is written in JavaScript, which plays well with Node.


Dislikes:

- I use Sass via node-sass, which is a binding for LibSass written in C++. I have to frequently recompile it when switching between node versions.
- In Less, variable names are prefixed with @, which can be confused with native CSS keywords like @media, @import and @font-face rule.

#### How would you implement a web design comp that uses non-standard fonts?

- `@font-face` to write my own `font-family`
- `@import` to import prepared web font(e.g. Google Webfonts)

#### Explain how a browser determines what elements match a CSS selector.

- Reads right-to-left
  - Check matching elements for the key(right-most) selector
  - Check if the elements are matching parents for the next selectors

#### Describe pseudo-elements and discuss what they are used for.

It's to style a part of an element, like `::first-letter` or `::before`.

They can be used to add a special symbol before a paragraph, change color of
first character of a line, etc.

#### Explain your understanding of the box model and how you would tell the browser in CSS to render your layout in different box models.

The CSS box model describes the rectangular boxes that are generated for elements in the document tree and laid out according to the visual formatting model. Each box has a content area (e.g. text, an image, etc.) and optional surrounding padding, border, and margin areas.

The CSS box model is responsible for calculating:

- How much space a block element takes up.
- Whether or not borders and/or margins overlap, or collapse.
- A box's dimensions.

The box model has the following rules:

- The dimensions of a block element are calculated by width, height, padding, borders, and margins.
- If no height is specified, a block element will be as high as the content it contains, plus padding (unless there are floats, for which see below).
- If no width is specified, a non-floated block element will expand to fit the width of its parent minus padding.
- The height of an element is calculated by the content's height.
- The width of an element is calculated by the content's width.
- By default, paddings and borders are not part of the width and height of an element.

#### What does ```* { box-sizing: border-box; }``` do? What are its advantages?

- By default, elements have box-sizing: content-box applied, and only the content size is being accounted for.
- box-sizing: border-box changes how the width and height of elements are being calculated, border and padding are also being included in the calculation.
- The height of an element is now calculated by the content's height + vertical padding + vertical border width.
- The width of an element is now calculated by the content's width + horizontal padding + horizontal border width.
- Taking into account paddings and borders as part of our box model resonates better with how designers actually imagine content in grids.

#### List as many values for the display property that you can remember.

- display: none;
- display: inline;
- display: block;
- display: inline-block;

#### What's the difference between inline and inline-block?

https://github.com/yangshun/front-end-interview-handbook/blob/master/questions/css-questions.md#whats-the-difference-between-inline-and-inline-block

#### What's the difference between a relative, fixed, absolute and statically positioned element?

A positioned element is an element whose computed position property is either relative, absolute, fixed or sticky.

- static - The default position; the element will flow into the page as it normally would. The top, right, bottom, left and z-index properties do not apply.
- relative - The element's position is adjusted relative to itself, without changing layout (and thus leaving a gap for the element where it would have been had it not been positioned).
- absolute - The element is removed from the flow of the page and positioned at a specified position relative to its closest positioned ancestor if any, or otherwise relative to the initial containing block. Absolutely positioned boxes can have margins, and they do not collapse with any other margins. These elements do not affect the position of other elements.
- fixed - The element is removed from the flow of the page and positioned at a specified position relative to the viewport and doesn't move when scrolled.
- sticky - Sticky positioning is a hybrid of relative and fixed positioning. The element is treated as relative positioned until it crosses a specified threshold, at which point it is treated as fixed positioned.

#### The 'C' in CSS stands for Cascading.  How is priority determined in assigning styles (a few examples)?  How can you use this system to your advantage?

CSS priority is determined by [specificity and inheritance](https://www.smashingmagazine.com/2010/04/css-specificity-and-inheritance/).

- Specificity: ID > class, psuedo-class > element, psudo-element
- Inheritence: specified value → computed value → used value → actual value

#### What existing CSS frameworks have you used locally, or in production? How would you change/improve them?

- Bootstrap - Slow release cycle. Bootstrap 4 has been in alpha for almost 2 years. Add a spinner button component, as it is widely used.
- Semantic UI - Source code structure makes theme customization extremely hard to understand. Its unconventional theming system is a pain to customize. Hardcoded config path within the vendor library. Not well-designed for overriding variables unlike in Bootstrap.
- Bulma - A lot of non-semantic and superfluous classes and markup required. Not backward compatible. Upgrading versions breaks the app in subtle manners.


#### Have you played around with the new CSS Flexbox or Grid specs?

Yes. Flexbox is mainly meant for 1-dimensional layouts while Grid is meant for 2-dimensional layouts.

Flexbox solves many common problems in CSS, such as vertical centering of elements within a container, sticky footer, etc. Bootstrap and Bulma are based on Flexbox, and it is probably the recommended way to create layouts these days. Have tried Flexbox before but ran into some browser incompatibility issues (Safari) in using flex-grow, and I had to rewrite my code using inline-blocks and math to calculate the widths in percentages, it wasn't a nice experience.

Grid is by far the most intuitive approach for creating grid-based layouts (it better be!) but browser support is not wide at the moment.

- http://flexboxfroggy.com
- https://scotch.io/tutorials/a-visual-guide-to-css3-flexbox-properties

#### How is responsive design different from adaptive design?

- Responsive: There is one basic layout, and it changes responsively to
  screen changes
- Adaptive: For each possible screen size, there is a distinct layout.

#### Have you ever worked with retina graphics? If so, when and what techniques did you use?

```css
@media (-webkit-min-device-pixel-ratio: 1.25), (min-resolution: 120dpi) {
  ...
}
```

#### Is there any reason you'd want to use `translate()` instead of *absolute positioning*, or vice-versa? And why?

translate() is a value of CSS transform. Changing transform or opacity does not trigger browser reflow or repaint but does trigger compositions; whereas changing the absolute positioning triggers reflow. transform causes the browser to create a GPU layer for the element but changing absolute positioning properties uses the CPU. Hence translate() is more efficient and will result in shorter paint times for smoother animations.

When using translate(), the element still occupies its original space (sort of like position: relative), unlike in changing the absolute positioning.
