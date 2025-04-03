# Built in Declaration and Inheritence

- While styling, we dont start with a blank canvas, HTML tags include a few minimal styles which are unique to each browser.

- Certain CSS properties inherit. Most of the properties that inherit are typography related ie `color`, `font-size`, `text-shadow`, etc.

- Inheritence in CSS is similar to JS prototypical inheritence.

- Caveat: Even though the property `color` inherit, in case `a` the default browser provided color takes precedence. We can force inherit a property by `color: inherit`

# Cascade

- When multiple rules target the same element, the browser uses a process called the **cascade** to figure out which role is applied.

- How does the CSS algorithm determine which rule is applicable? It depends on the specificity of the rules.

- We can think that CSS merges together all different rules.

- Specificity rules can be hairy and in a well designed HTML / CSS, specificity rules should never come into the picture.

# Directions

- English language have 2 directions. The page consists of vertically oriented blocks (paragraphs) and each block made of horizontally oriented words.

- CSS builds its sense of direction based on the system - block direction (vertical), and inline direction (horizontal)

- Block direction is like lego blocks, one stand on top of another. Inline direction is like people standing **in-line**, they stand side by side, not one on top of another.

- `margin-block-start`, `margin-block-end`, `margin-inline-start` and `margin-inline-end` are similar to `margin-top`, `margin-bottom`, `margin-left` and `margin-right`.

# The Box Model

- The 4 aspects that make up the box model are: `content`, `padding`, `border` and `margin`.

- **box-sizing** is a CSS property which controls how `width` and `height` of an element are calculated. The default value is `box-sizing: content-box`

- With `content-box`, the explicitly set `width` and `height` applies only to the `content` - `padding` and `border` gets added to `content` to determine the total `padding` and `border`.

- With `box-sizing: border-box`, the padding and border are automatically included so that content+padding+border equals the explicitly set `width` and `height`.

## Padding

- Padding is an element's inner space.

- All units for padding can be used like `px`, `em` and `rem`. The best practise is to use `px` for padding.

## Border

- Border is not just for spacing. Border width, style, color are styles specific to a border. These can be combined into a shorthand.

- `border-radius` should be called `corner-radius`.

- `outline` is not part of the box model, does not affect layout (or take up space), can not be styled per side. `outline` is more like box shadow.

- `buton { outline: none; }` should never be applied. This breaks the keyboard based navigation.

## Margin

- Margin increases the space around elements, giving it breathing room.

- Margin can be negative as well. A negative margin can:

1. Pull the element outside its container
2. Pull the siblings closer (strange!!)

- We can think that margin is about changing the gap between elements.

3. Margin can affect positioning of all elements.

- `margin: auto` instructs the margin to take maximum available space. When both `margin-left` and `margin-right` are set to auto, they take max available place in left and right.

1. The above trick only works for horizontal margin.
2. Only works for elements with explicit width. Block elements will naturally grow to fill the available horizontal space, so we need to give explicit width.

- If we give negative margin on both left and right, then we stretch out the element. For img: `width: 100%` takes the full width of the container, no explicit `width` property makes them take their natural space. `img` are replaced element and they should be wrapped for their layout to be managed.

# The Flow Layout

- Every HTML element has its layout calculated by a layout algorithm. These are known as **layout modes**, there are 7 distinct ones.

- **Flow Layout** is the default mode. A plain HTML, with no CSS, uses flow layout exclusively.

- In flow layout, every element has a `display` property of `inline`, `block` or `inline-block`. The default value depends on the tag.

- In flow layout, flow elements stack in the flow direction, while inline elements stack in the inline direction.

**Inline Elements dont make a fuss**

- We can't change height of inline element, while we can shift things in inline direction ie `margin-left` or `margin-right`.

- Exceptions are replaced elements which embed a foreign element.

- The browser treats inline elements as if they are typography, so it adds a bit of extra space. 2 way around it `display: block;`, and `line-height: 0;` on the wrapping `div` to be zero (this works for image only as they have no text.)

- Between 2 `inline` elements, browser adds some whitespace. Remember, the browser treats them as typography - so browser cant tell the difference between space between words and newline to indent our HTML.

**Block elements dont share**

- Block elements greedily explands to take all the horizontal space.

- `width: fit-content;` contraints the block elements to take only the available size.

**Inline elements can line wrap**

- An inline elements can produce non box shapes.

- Horizontal spacing in inline elements is weird because that's applied only at tips.

**The deal with inline blocks**

- Essentially allows to drop a block element into an inline context. ie these elements internally act as block but externally as inline.

- With inline blocks properties like `width` make sense because, unlike for `inline` elements where they do not.

- Remeber that inline block elements DO NOT line wrap.

## Width Algorithm

- Block elements expanding to take all the horizontal space is differernt from setting `width: 100%`.

- Their default width is `auto` - which expands to consume all available space. By default, block elements are context aware.

- In contrast, `width: 100%` mean that the elements content area equals the parent elements content space.

- The above is called _extrinsic_ control of size. In contrast, if we set `width: min-content`, then thats _intrinsic_ control.

- `width: min-content` squishes the element to smalles size without overflowing contenxt by forcing line breaks.

- `width: max-content` takes an opposite strategy - it never adds any inline breaks, and disregard any contraint set by parent.

- `width: fit-content` behaves like `max-content` if the element fits within the container, otherwise line wraps.

- We also have `min-width` and `max-width`.

- `max-width: max-content` means make this element as wide as possible inside without wrapping, but no bigger than the content. It does not force the element to grow.

### Figure and captions

- `figure` is the semantic container for any self container media element. `figcaption` is the caption for content inside a `figure`.

- `figure` is block element. `width: min-content` is used to set the width of `figure` element equal to the image element within.

## Height Algorithms

- The default behaviour for `height` of block elements is opposite to `width` ie the element tries to take as less space as possible. This is similar to `min-content` than `auto`.

- We generally want to avoid setting fixed height otherwise the content might overflow.

- What if we a wrapper element for our entire app to take 100% of the vertical space, even if there is not enough content ?

- `min-height: 100%` does not work. Why ? For determining height, an element tends to look at its children, for width an element looks at its parent. (Another way to think is that parent element will shrink wrap around its children)

- To fix this we need to put `height: 100%` on `html`. Then we put `min-height: 100%` on the wrapper. That ways minimum height is equal to viewport height.

# Margin Collapse

- Think about margin as personal space. Sometimes the margin collapse, sometime not. This can lead to suprising behaviour.

- If we put 2 `p` on top of each other with `20px` margin, total margin is not `40px`.

## Rules of margin collapse

1. Only vertical margins collapse (more accurate to say that only block direction margins collapse)
2. Margins only collapse in flow layout.
3. Elements need to be adjacent in the DOM for their margins to collapse. Even a `<br />` element would prevent margin collapse.
4. The bigger margin wins.
5. Nesting DOES NOT prevent collapsing. Why ? Margin is meant to increase the distance between siblings, not between parent and container.
6. If there is a padding or margin, then margins can't collapse.
7. Margins must be touching for them to collapse.
8. More than 2 margins can collapse.

## Using Margin Effectively

- Try avoid margin at the component boundary.
