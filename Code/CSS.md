div.class -> selects element with both
div .class -> selects element with class that has parent div
.class[attr="value"] -> selects equal
.class[attr*="value"] -> selects like values
a::after -> content after the a tag
li+li::before -> content before the second li when 2 are found together

display:
  block -> can be resized, occupies entire width
  inline-block -> can be resized doesn't occupy entire width
  inline -> can't be resized, wraps around content tightly
  flex -> makes children flex items, but is still block
  inline-flex -> makes children flex items, but is inline 
  grid -> block grid of resizable rows and cols
  inline-grid -> same but inline


flex stuff:
  justify-content -> sets horizontal layout of items inside the flex parent
  align-items -> sets vertical layout of items inside the flex parent
  align-content -> same but for rows in the flex parent
  flex-shrink(def:1) / flex-grow(def:0) -> sets flex items to shrink or grow when their
    container can't hold them properly anymore. A 2 will grow twice as fast as a 1, etc..
  flex:
    can set item properties quicker. flex: grow shrink basis. or: grow shrink. 
    or: grow basis
  flex-wrap -> determines the way the items inside will wrap when space is short
  flex-direction -> determines how items in the flex parent will be displayed. 
    row, column, etc..
  flex-flow:
    set container properties quicker. flex-flow: direction wrap


grid stuff:
  by default only 1 column
  grid-template-columns: sets number of cols and size of each
  grid-template-rows: same but with rows
  grid-template: shorthand as (grid-template: rows / columns)
  fractions for size in grids: 1fr 2fr (1/3 + 2/3)
  repeat(3, 100px): sets 3 rows or cols of 100px (100px 100px 100px)
  minmax(50px, 300px): minmax stuff
  gap: row col (or row&col), sets the gap between grid items, not with the border
  grid-row: start / end -> (5 / 7) takes rows 5 and 6 and ends at the start of 7
    this will also take the space of the gap between rows
  grid-column: same thing but with columns
    both can also use span as (start / span 2) -> 2 rows or cols starting in start
  grid-area: shorthand as (rowstart / columnstart / rowend / columnend)
    can also be used with template area, as grid-area: content
  grid-template-areas: "head head" "nav content" "foot foot" 
    3 rows with "", 2 cols inside each row
    the names can be later attributed to specific items with grid-area
  justify-items: justifies items within the columns
  justify-content: justifies the columns themselves within the grid
  align-items: justifies items within the rows
  align-content: justifies the rows themselves within the grid
  align-self & justify-self: same as justifying and aligning items
    but called by the items, not the container
  grid-auto-rows & grid-auto-columns: like template but for implicit
    new rows and columns added over the ones in template
  grid-auto-flow: sets if new items add to rows or columns, and can
    also fill in empty spots using the dense value
  


clear:
  The clear CSS property sets whether
   an element must be moved below (cleared) floating elements that precede it. 
   The clear property applies to floating and non-floating elements.
   left -> if touching on left clear
   etc..

position:
  static:
    The element is positioned according to the normal flow of the document. 
    The top, right, bottom, left, and z-index properties have no effect. This is the default value.
  relative:
    The element is positioned according to the normal flow of the document, and then offset relative to itself based on the values of top, right, bottom, and left. 
    The offset does not affect the position of any other elements; thus, the space given for the element in the page layout is the same as if position were static.
  absolute:
    The element is removed from the normal document flow, and no space is created for the element in the page layout. 
    It is positioned relative to its closest positioned ancestor, if any; otherwise, it is placed relative to the initial containing block. 
    Its final position is determined by the values of top, right, bottom, and left.
  fixed:
    The element is removed from the normal document flow, and no space is created for the element in the page layout. 
    Its final position is determined by the values of top, right, bottom, and left.
  sticky:
    The element is positioned according to the normal flow of the document, 
    and then offset relative to its nearest scrolling ancestor and containing block (nearest block-level ancestor), 
    including table-related elements, based on the values of top, right, bottom, and left. 
    The offset does not affect the position of any other elements.

box-sizing:
  content-box:
    Default CSS box-sizing behavior. 
    If you set an element's width to 100 pixels, then the element's content box will be 100 pixels wide, 
    and the width of any border or padding will be added to the final rendered width, making the element wider than 100px.
  border-box:
    Tells the browser to account for any border and padding in the values you specify for an element's width and height. 
    If you set an element's width to 100 pixels, that 100 pixels will include any border or padding you added, and the content box will shrink to absorb that extra width. 
    This typically makes it much easier to size elements. 
  Note: It is often useful to set box-sizing to border-box to lay out elements. 
  This makes dealing with the sizes of elements much easier, and generally eliminates a number of pitfalls you can stumble on while laying out your content. 
  On the other hand, when using position: relative or position: absolute, use of box-sizing: content-box allows the positioning values to be relative to the content, 
  and independent of changes to border and padding sizes, which is sometimes desirable.

text-transform: uppercase;
  all text becomes uppercase

text-align: aligns text to its parent element.

overflow: what to do with overflow on the selection (hidden, etc..)

example of scaling img:
  .container img {
    max-width: 100%;
    height: auto;
    display: block;
  }
  display block so it won't try to align with other elements
  and cause weird margins
  can switch which is auto depending on size of img and container

  for background-image:
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;

em: based on current font-size (if size is 16px, 2em is 32px, etc..)
rem: based on html (root) element, works the same as em

height and width as percentages are based on the parent element

<meta name="viewport" content="width=device-width, initial-scale=1">
  viewport is the container that the user is viewing on
  set width to the device width
  initial-scale is the zoom

@media only screen and (min-width: 480px), (orientation: landscape) {
  /* CSS ruleset */
}
  only screen (other selectors that are not screen are outdated)
  and: and
  or: ,

transition: defines types, duration and delays of transitions

:root -> pseudo-class matches root of the tree of the document, in html 
  it gets the html tag but with more specificity
  good for declaring variables

calc (math + * etc) can calculate different units too: 100px + 20vw + 20%

var(--variable) -> to use variables
  in css --variable: value;
  in html <div style="--variable: value;">

counter(): for making counters 

element:focus-within -> for not losing focus when the focus is on the children