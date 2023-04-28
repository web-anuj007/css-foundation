# Box Model Foundation

Some basics --

|Property|Desciption|
|-|-|
|padding|increases the space between the border of a box and the content of the box.|
|margin|increases the space between the borders of a box and the borders of adjacent boxes.|
|border|adds space (even if it’s only a pixel or two) between the margin and the padding|

## Seleveral type of css box 

### Outer display type

**If a box has an outer display type of block, then:**
- The box will break onto a new line.
- The width and height properties are respected.
- Padding, margin and border will cause other elements to be pushed away from the box.
- If width is not specified, the box will extend in the inline direction to fill the space available in its container. In most cases, the box will become as wide as its container, filling up 100% of the space available.

Example -- <h1> & <p> element have default display type block

**If a box has an outer display type of inline, then:**

- The box will not break onto a new line.
- The width and height properties will not apply.
- Top and bottom padding, margins, and borders will apply but will not cause other inline boxes to move away from the box.
- Left and right padding, margins, and borders will apply and will cause other inline boxes to move away from the box.

Example -- <a>, <span>, <em> and <strong> use inline as their outer display type by default.

### Inner display type
Boxes also have an inner display type, which dictates how elements inside that box are laid out.

Block and inline layout is the default way things behave on the web. By default and without any other instruction, the elements inside a box are also laid out in normal flow and behave as block or inline boxes.

You can change the inner display type for example by setting display: flex;. The element will still use the outer display type block but this changes the inner display type to flex. Any direct children of this box will become flex items and behave according to the Flexbox specification.

When you move on to learn about CSS Layout in more detail, you will encounter flex, and various other inner values that your boxes can have, for example grid.


## What is CSS box model ?
The CSS box model as a whole applies to block boxes and defines how the different parts of a box — margin, border, padding, and content — work together to create a box that you can see on a page. Inline boxes use just some of the behavior defined in the box model.

> there is a `standard box` and an `alternate box model`. By default, browsers use the `standard box model`.

### Parts of a box
- Content box - The area where your content is displayed; size it using properties like `inline-size` and `block-size` or `width` and `height`.
- Padding box - The padding sits around the content as white space; size it using padding and related properties.
- Border box - The border box wraps the content and any padding; size it using `border` and `related properties`.
- Margin box - The margin is the outermost layer, wrapping the content, padding, and border as whitespace between this box and other elements; size it using margin and related properties.

### The standard CSS box model
In the standard box model, if you give a box an inline-size and a block-size (or width and a height) attributes, this defines the inline-size and block-size (width and height in horizontal languages) of the content box. Any padding and border is then added to those dimensions to get the total size taken up by the box (see image below).

Reference -- https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model#the_standard_css_box_model


### The alternative CSS box model
In the alternative box model, any width is the width of the visible box on the page. The content area width is that width minus the width for the padding and border (see image below). No need to add up the border and padding to get the real size of the box.

> To turn on the alternative model for an element, set box-sizing: border-box on it:

```css
.box {
  box-sizing: border-box;
}

```

>To use the alternative box model for all of your elements (which is a common choice among developers), set the box-sizing property on the <html> element and set all other elements to inherit that value:

```css
html {
  box-sizing: border-box;
}
*,
*::before,
*::after {
  box-sizing: inherit;
}
```


# Moargin Collapse

Margin collapsing

Depending on whether two elements whose margins touch have positive or negative margins, the results will be different:

- Two positive margins will combine to become one margin. Its size will be equal to the largest individual margin.
- Two negative margins will collapse and the smallest (furthest from zero) value will be used.
- If one margin is negative, its value will be subtracted from the total.

# Border 

**when using standard-box** - the size of the border is added to the width and height of the content box.
**when using alternative box** - the size of the border makes the content box smaller as it takes up some of that available width and height of the element box.
