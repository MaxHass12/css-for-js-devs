- A **CSS Declaraion** is a single rule (ie a key-value pair) that tells the browser how to style a specific property of an element. The "entire object" is called **rule**.

# Media Queries

- The **media query** is like a JS conditional.

```css
@media (condition) {
  <css rule>;
}
```

- Aside: An **iframe** is an embedded document within an HTML document.

- In media queries `min-width` means **apply styles when the viewport is at least this wide**, `max-width` when **viewport is at most this wide**.

- Media queries are only run on viewport features, not on any other css properties like `(font-size: 32px)`, although they look the same.

# Selectors

## pseudo classes

- pseudo-class apply styling based on the state of the component. `:hover` is similar to `onMouseEnter` and `onMouseLeave`, but with built in state management.

- `:focus` targets an element **when it is focused** ie when user selects it with keyboard, mouse or via JS. A button usually gains focus after being tabbed or clicked.

- `:checked` only applies to checkboxes and radio buttons that are filled in.

## pseudo elements

- pseudo elements targets elements that we have not explicitly created.

- For eg: we can apply styling to `input::placeholder`.

- 2 of the most common pseudo-elements are `::before` and `::after`. These 2 go inside the element (like a `span`). These should be used with empty content string, purely for decorative purpose.

## combinators

- combinator refers to the **character** that combines multiple selectors. For eg in `nav a`, the space character combines `nav` and `a` to create a **descendent selector**. The space character is called the **descendent combinator**

- A **descendent selector** will apply to all descendents, no matter how deeply nested they are.

- `>` aka **child combinator** is used to target immediate descendants.

## color formats

- `hsl()` allows you to define colors by their `hsl(hue, separation, lightness)

## Units

The most popular exception for anything type related is the pixel. They correspond with more or less what you see, the big exception is typography.

- `em` is a relative unit, relative to the font size of the current element.

- `rem` is relative to the root element size ie that of the `html` element.

- IMPORTANT: We should not set a `px` font size on the `html` tag. This will override a user's default size. If we want to change the baseline units, the best way is using `ems`

- `%` is used with `width` and `height`, as a way to consume a portion of the available space.

- Rule of thumbs for typography:

1. `rem` for typography because of accessibility benefits.
2. pixels for box model properties like `padding`, `margin`, and `border`
3. for `width` / `height` it depends if you want a fixed size or percentage
4. for colors prefer `hsl`

## Typography

- There are handful of websafe fonts - those that come pre installed on all major OS like Arial, Times New Roman and Tahoma

- we can create bold text with `font-weight` property. There is also a number system mapping to it. The default value for `font-weight` is `400`, `bold` keyword maps to `700`.

- We should leave `text-decoration: underline` for hyperlinks.

- We should reserver `text-align` for aligning text. `text-align` property sets the horizontal alighnment of the inline content.

- `text-transform: uppercase`, `text-transform: capitalize` is used to transform the text.

- `letter-spacing` is used to tweak the horizontal gaps between the characters.

- `line-height` sets the vertical space between lines of text. The minimum recommended value is `1.5`.
