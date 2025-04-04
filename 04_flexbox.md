# Hello Flexbox

- Flexbox was the first intentional part of CSS to deal with layout. Flex is used to control distribution of space in a single axis.

- Flexbox versus Grid.

- Different tools for different jobs. Grid is used for arranging stuff in 2 dimensions.

- Flexbox is for 1 dimension.

- `display: flex` changes the layout mode of the children. All children get the flex layout mode, whatever they might be earlier.

# Direction and Alignment

- 2 different directions - **primary-axis** and **cross-axis**. Primary-axis is set by **flex-direction**.

- `justify-content` is used to manage space in primary-axis. The default value is `flex-start`. Other values are `flex-end`, and `center`. These 3 are common.

- `justify-content: space-between` spreads the elements, `space-around` & `space-evenly` accordingly.

- `space-between`, etc for cross-items does not make sense.

- `align-items` for the cross-axis. The default value is `stretch`. Other values are `baseline` and `normal`.

## baseline

- `align-items: baseline;` aligns item to the baseline.

- `align-self` gives you the option of aligning individual flex child instead of all flex children.

- if `line-height` is too big, the text is aligned at the centre.

# Growing and Shrinking

- There are 2 important sizes when dealing with flex - minimum content size, and the hypothetical size.

- The minimum content size is the smallest an item can get without its size overflowing.

- The other size is `hypothetical-size` which would be the size if no other constraint exists.

- So `width` and `height` are not guarantees in flex - they are the hypothetical size.

- `flex-basis` is shorthand for `width` or `height` agnostic to axis. Also `flex-basis` always win over `width` or `height`. However, if there is not enough space it shrinks.

- `flex-grow` instruct a flex-child to take all the available space. That wins over `flex-basis` as well. `flex-grow` is all about consuming free space - if there is not free space then nothing happens.

- same with `flex-shrink` - how should an element should reduce its hypothetical size when there is not enough space to have its hypothetical size.
