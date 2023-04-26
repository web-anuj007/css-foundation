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
continue




