
---
# Markdown Cheat Sheet

[HOME](../README.md)

---
## Resources:

[The Markdown Guide](https://www.markdownguide.org/cheat-sheet/)

[Basic writing and formatting syntax - GitHub Docs](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

[GitHub Flavored Markdown Spec](https://github.github.com/gfm/)

---

## Heading
~~~
# H1
## H2
### H3
~~~

## Bold
~~~
**bold text**
~~~

## Italic
~~~
*italicized text*
~~~

## Blockquote
~~~
> blockquote
~~~

## Ordered List
~~~
1. First item
2. Second item
3. Third item
~~~

## Unordered List
~~~
- First item
- Second item
- Third item
~~~

## Code
~~~
`code`
~~~

## Horizontal Rule
```
---
```

## Link
```markdown
[Google](https://www.google.com)
```

## Image
```
![alternative text](image.png)
```

## Table
```markdown
| Syntax | Description |
| ----------- | ----------- |
| Header | Title |
| Paragraph | Text |
```

## Fenced Code Block

```markdown
~~~python
# Some python code
if __name__ = __main__:
	print("Hello World")
~~~
```

~~~markdown
```java
// Some java code
public class Main {
	public static void main(String[] args) {
		System.out.println("Hello World")
	}
}
```
~~~
## Strikethrough
```markdown
~~The world is flat.~~
```

## Task List
```markdown
- [x] Completed task
- [ ] Uncompleted task
```

## Comments
```markdown
<!-- COMMENT -->
```

---

## Some extra GitHub utilities
### Alerts

```markdown
> [!NOTE]
> Useful information that users should know, even when skimming content.

> [!TIP]
> Helpful advice for doing things better or more easily.

> [!IMPORTANT]
> Key information users need to know to achieve their goal.

> [!WARNING]
> Urgent info that needs immediate user attention to avoid problems.

> [!CAUTION]
> Advises about risks or negative outcomes of certain actions.
```

### Collapsed section

```html
<details open>
<summary>Title</summary>
Content
</details>
```

### Creating flow charts

~~~markdown
```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```
~~~

[Mermaid Docs](https://mermaid.js.org/syntax/examples.html)

### Mathematical expressions

[MathJax | Beautiful math in all browsers.](https://www.mathjax.org/)

Uses ``` $` ``` to start a inline mathematical expressions and ``` `$ ``` to end it.
```markdown
$` \sqrt{x}+(1+x)^2 `$
```

Uses `$$` to start and end a equation block.
```markdown
$$ \sqrt{x}+(1+x)^2 $$
```
