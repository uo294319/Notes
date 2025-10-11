
---
# Webpage Styling

[Back to index](../README.md)

---
## CSS Syntax

```css
/* GENERAL */
selector {
	propertie:value;
	...
}

/* EXAMPLE */
h1 {
	color:red;
}
```
---
## How to use CSS
### Inline
```html
<h1 style="color:red">Heading</h1>
```
### Embedded/Internal
```html
<head>
	<style>
		h1 {color:red}
	</style>
<head>

<body>
	<h1>Heading</h1>
</body>
```
### External
```html
<head>
	<link rel="stylesheet" type="text/css" href="styles.css"/>
<head>
```
### Imports
```css
@import url(styles.css)
```
---
## CSS Selector

### Basic
```css
/* All h1 will have this style */
/* Used to apply a style to all elements of a tag */

h1 {
	text-align: center;
	font-size: 300%;
}
```
### Using IDs
```css
/* Each element can have ONE id */
/* Used to apply a style to a specific element */
/* Example: <h1 id="header1">...</h1> */

#header1 {
	text-align: center;
	font-size: 200%;
}

/* Applied only to h1 that are header1 */
h1#header1 {
	text-align: center;
	font-size: 300%;
}
```
### Using Classes
```css
/* Each element can have one or several classes */
/* Used to apply a style to related elements */
/* Example: <h1 class="centered big">...</h1> */

.centered {
	text-align: center;
}
.big {
	font-size: 200%;
}

/* Applied only to h1 that are big */
h1.big {
	font-size: 300%;
}
```
---
## Combinators
```css
/* Descendant Selector */
/* All p inside the div */
div   p {background-color: yellow;}

/* Child Selector */
/* Only p directly inside the div */
div > p {background-color: yellow;}

/* General Sibling Selector */
/* All p behind the div */
div ~ p {background-color: yellow;}

/* Adjacent Sibling Selector */
/* Only p directly behind the div */
div + p {background-color: yellow;}
```
---
