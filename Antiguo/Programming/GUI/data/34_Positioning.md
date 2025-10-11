
---
# Box Positioning

[Back to index](../README.md)

---
## Box Model

- Each html element creates a box.
- Box are made from (inside out):
	- `content` is the actual contents of the element (usually text).
	- `padding` is the spacing between the content and border.
	- `border` is a line that encloses the content and padding
	- `margin` is the spacing between this element and another ones.
- Two ways of calculating
	- `box-sizing: content-box;`
		- `width` and `height` modify `contents`.
		- default behaviour.
	- `box-sizing: border-box;`
		- `width` and `height` modify `contents` + `padding` + `border`.

---
## Box position

```css
.something {
	position: /* value */;
	
	/* OPTIONAL */
	
	top: /* unit */;
	bottom: /* unit */;
	right: /* unit */;
	left: /* unit */;
}
```

- `absolute`
	- Is Independent from other elements.
	- Position is absolute to the document.
- `relative`
	- Is contain in another element.
	- Position is relative to the container element.
- `fixed`
	- Is Independent from other elements.
	- Position is fixed in the screen.
- `sticky`
	- Is contain in another element.
	- Position is stick to the screen on scrolling.

---
## Box display
```css
.container {
	display: /* value */;
}
```

- `block` displays element as a block (default).
- `inline` displays element as a inline element.
- `flex` displays element as a flex block element.
- `inline-flex` displays element as a inline flex element.
- `grid` displays element as a grid block element.
- `inline-grid` displays element as a inline grid element.