# CSS Foundation

## Selector 
Selector is a pointer which is binded with some HTML element one/more, on which css rule apply

## CSS Rule
CSS rule is pair of property and value sperated by `:`

Example -- 
```css
h1 {font-family: sans-serif;}
```

In above example `font-family` is property, rest you are smart enough to guess


## Universal Selector 
Select all element on web page

Example -- 

```css
* {
	font-family: sans-serif;
}
```

## Type Selector or Element Selector
Will select all element of given type 

Example --

```css
h1 {
	font-family: sans-serif;
}

```

## Class Selector
Class selectors will select all elements with the given class

```html
<h1 class="class1"> Hello class 1 </h1>
<h1> Hello normal</h1>
```

Example --
```css
.class1 {
	color: red;
}
```

Above example will only select `<h1>` tag with class name `class1`

## ID Selector
Select an element with the given ID

```html
<h1 id="id1"> Hello id1 </h1>
<h1>Hello normal</h1>
```

Example --
```css
#id1 {
	color: red;
}
```

Above example will only make effect on `<h1>` tag havind id as `id1`


## Grouping Selector
What if we have two groups of elements that share some of their style declarations?

```css
.read {
  color: white;
  background-color: black;
  /* several unique declarations */
}

.unread {
  color: white;
  background-color: black;
  /* several unique declarations */
}
```

Both our .read and .unread selectors share the color: white; and background-color: black; declarations, but otherwise have several of their own unique declarations. To cut down on the repetition, we can group these two selectors together as a comma-separated list:

```css
.read,
.unread {
  color: white;
  background-color: black;
}

.read {
  /* several unique declarations */
}

.unread {
  /* several unique declarations */
}
```

## Chaining Selectors
Example -- 
```css
/* Chaining selector with class and class*/
.box.container{
	background-color: yellowgreen;
}
/* Chaining selector with class and id*/
.box#id1 {
	background-color: gray;
}
```

For more context -- refer `chaining-selector.html`



# Descendant Combinator

## Descendant Combinator
Represented in CSS by a single space between selectors. A descendant combinator will only cause elements that match the last selector to be selected if they also have an ancestor (parent, grandparent, etc) that matches the previous selector.

Example --
```html
<!-- index.html -->

<div class="ancestor"> <!-- A -->
  <div class="contents"> <!-- B  selected from css rule--> 
    <div class="contents"> <!-- C selected from css rule --> 
    </div>
  </div>
</div>

<div class="contents"></div> <!-- D -->
```

```css
/* styles.css */

.ancestor .contents {
  /* some declarations */
}
```

In the above example, the first two elements with the contents class (B and C) would be selected, but that last element (D) won’t be. Was your guess correct?

There’s really no limit to how many combinators you can add to a rule, so .one .two .three .four would be totally valid. This would just select an element that has a class of four if it has an ancestor with a class of three, and if that ancestor has its own ancestor with a class of two, and so on. You generally want to avoid trying to select elements that need this level of nesting, though, as it can get pretty confusing and long, and it can cause issues when it comes to specificity.

# Some basics css property
|||
|-|-|
|Property|Description|
|color|sets an element’s text color|
|background-color|sets, well, the background color of an element|
|font-family|can be a single value or a comma-separated list of values that determine what font an element uses|
|font-size|set the size of the font|
|font-weight| affects the boldness of text|
|text-align|will align text horizontally(x-axis) within an element|
 
# Image Height and Width
By default, an <img> element’s height and width values will be the same as the actual image file’s height and width

> Note -- If you wanted to adjust the size of the image without causing it to lose its proportions, you would use a value of “auto” for the height property and adjust the width value:

```css
img {
  height: auto;
  width: 500px;
}
```

It’s best to include both of these properties for <img> elements, even <strong>if you don’t plan on adjusting the values from the image file’s original ones. When these values aren’t included, if an image takes longer to load than the rest of the page contents, the image won’t take up any space on the page at first, but will suddenly cause a drastic shift of the other page contents once it does load in</strong>

Explicitly stating a height and width prevents this from happening, as space will be “reserved” on the page and will just appear as a blank space until the image loads.



# Specificity
CSS declaration that is more specific will take precedence over less specific ones.

|||
|-|-|
| Type | Rank|
|ID selectors| 1|
|Class selectors| 2|
|Type selectors| 3|


<strong>Note -  a larger amount of a single selector will beat a smaller amount of that same selector.</strong>


# Property Inheritance

Inheritance refers to certain CSS properties that, when applied to an element, are inherited by that element’s descendants, even if we don’t explicitly write a rule for those descendants. Typography based properties (color, font-size, font-family, etc.) are usually inherited, while most other properties aren’t.

The exception to this is when directly targeting an element, as this always beats inheritance:
```html
<!-- index.html -->

<div id="parent">
  <div class="child"></div>
</div>
```

```css
/* styles.css */

#parent {
  color: red;
}

.child {
  color: blue;
}
```

Despite the parent element having a higher specificity with an ID, the child element would have the color: blue style applied since that declaration directly targets it, while color: red from the parent is only inherited.

 ## Rule Order

The final factor, the end of the line, the tie-breaker of the tie-breaker. Let’s say that after every other factor has been taken into account, there are still multiple conflicting rules targeting an element. How does the cascade determine which rule to apply?

Really simply, actually. Whichever rule was the last defined is the winner

```css
/* styles.css */

.alert {
  color: red;
}

.warning {
  color: yellow;
}
```

For an element that has both the alert and warning classes, the cascade would run through every other factor, including inheritance (none here) and specificity (neither rule is more specific than the other). Since the .warning rule was the last one defined, and no other factor was able to determine which rule to apply, it’s the one that gets applied to the element.

