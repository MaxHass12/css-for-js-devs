# Relative Positioning

- While Flow is the OG layout, its not the only one. Another one is **positioned layout**

- The defining feature of **positioned layout** is that the items can overlap. We opt into positioned layout by using `position` property which can be `relative`, `absolute`, `fixed` and `sticky`.

- `position: static` is the default positioning unless we change it. With this the element is placed in default document flow. Used to opt out of other positioning.

- `position: relative` is the most tricky. Slapping it into an element does 2 things:

1. Constrains certain children
2. Enables additional CSS properties `top`, `left`, `right`, `bottom`

- With `position: relative`, `top`, `left`, `right`, `bottom` are used to move _elements to their natural position_.

- Difference between changing `position` and `margin` is that `position` does not impact layout either internally resizing an element or externally pushing elements around.

- Relative Positioning can be applied to both _block_ and _inline_ elements. This gives us the power to move `inline` elements, which otherwise we did not have.

# Absolute Positioning

- So far elements are placed in the flow. What if we want to take element out of orderly flow, and stick it wherever we want.

- Unlike `relative` which are placed on their flow position, `absolute` elements are adjusted based on their containers.

- With `absolute`, we remove the element out of the flow.

- Absolute elements are like holograms, they do not really exist.

- With `position: absolute` layout, `display` property is irrelevant.

- Absolute elements want to be as small as possible. What if we have more content?

- It grows, until it can grow no more and then line wraps. The content can overflow, however the element itself will be as expected.

1. Absolute positioned elements are extremely compliant.
2. In general, line wraps.
3. Will try to be as small as possible.

## Absolute centering

- We can use Absolute Positioning to center an element. We just need to give 0 to all 4 directions and set `margin: auto`. In positioned layout, `margin: auto` works in all 4 directions.

# Containing Block

- In CSS, every HTML element has a **Containing Block**.

- In Flow Layout, elements are contained by their container. Flow layout uses containing blocks to figure out where on screen to place the element.

- How is absolute element's containing block calculated ?

- An Absolute element is NOT NECESSARILY contained by its parent. An Absolute element can only be contained by other elements with positioned layouts, either parent or closest `.relative` ancestor.

- If there is no ancestor with `position: relative`, then viewport becomes the containing block.

# Stacking Context

- In flow layout, elements do not stack up much. If we force them, then DOM order matters.

- Flow layout is not really meant with layering in mind, for that we want to use positioned layout.

- In general, Positioned Elements will always render on top of non positioned elements.

- If both siblings use positioned layout, the DOM order controls which element will be on top. Unlike in Flow Layout, the content does not float to the grant.

# z-index

- If we want the layered order to be different from DOM order, we can use the `z-index` to manually reorder them.

- `z-index` only works with positioned elements. It has no effect on element in Flow layout.

- Everytime we set `z-index` and `position: relative` we set a new stacking context (other ways as well). Each stacking context is isolated -- so `z-index` values only matter within that context, not across all elements globally.

## managinc z-index

To prevent the `z-index` wars we use `isolation: isolate`. It does only 1 thing - creates a stacking context.

## portals

- Portals are the standard way to show tooltips or modals.

# Fixed Positioning

- `position: fixed` is a more rebellious version of `position: absolute`. In that, it can only be constrained by the viewport.

- Their main advantage is that they are immune to scrolling.

- We can think of `fixed` as **super absolute**. An `absolute` element is constrained by the first ancestor which is relatively positioned, while `fixed` is constrained only by the viewport.

- All the tips and tricks for `absolute` (like centering, etc) works with `fixed` as well.

## The Transform Exception

- If any ancestor uses `transform` property, that becomes the containing block for the fixed element ie **transformed parents CAN NOT have fixed children**.

- `willChange: transform` has the same effect. (`willChange` is usually a performance optimization)

- This can be very hard to diagnose and fix, since it can be any ancestor in the tree.

- Remember that `iframe` is a separate HTML document embedded within an HTML document.

# overflow

- overflow happens when content does not fit into its parent's content box.

- Typically block elements have variable heights, but what if we constraint the height and the content does not fit it. Browser spills the content outside the box.

- Overflow has no affect on layout. It creates a big mess of overlapping text.

- To manage this, css gives us an `overflow` property. `overflow: hidden` hides the overflow, `overflow: scroll` creates a scrollbar.

- `overflow` is a shorthand for 2 properties : `overflow-x` and `overflow-y`. When we pass only 1 property to `overflow`, that automatically gets transferred to the 2 remaining properties.

- `overflow: auto` adds a scrollbar when it is required. `auto` is generally preferred than `scroll`. However, if we know before hand that element will need to scroll then `scroll` can provide a smoother experience.

**hidden**

- Might be necessary sometimes. Always add a comment when using this property.

- Sometimes we want to use `overflow-x` and `overflow-y` to clip the overflow in 1 axis, but not affect the other - this is not possible in CSS.

## horizontal overflow

- What if we want data to flow in horizontal direction? For eg: horizontally scrollable images

- Images are inline by default, they line wrap when they can't fit. In this case `overflow` property won't help. In this case, we set `white-space: nowrap`

## positioned layout

- In case of positioning `absolute`, elements can ignore the `overflow: hidden` propery of the parents when the parents itself are not relatively positioned. In that case, the parents are not containing their children.

- With relative positioning, `overflow: auto` treats `absolute` like just another element.

# Left overflow, sticky positioning, and hidden for later.
