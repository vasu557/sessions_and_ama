# HTML & CSS AMA Questions and Answers

## 1. How to center a div in a container using flex?

A div can be centered using Flexbox with `justify-content: center` and `align-items: center`.

```css
.container{
  display:flex;
  justify-content:center;
  align-items:center;
}
```
We can also center a div using positions and margin(horizontal centering), but Flexbox is more effective and commonly used for responsive layouts.
---

## 2. What is the use of iframe?

The `iframe` tag is used to embed another webpage, video, map, or external content inside a webpage.

---

## 3. Difference between absolute and relative

`relative` positions an element based on its normal position, while `absolute` positions an element relative to its nearest positioned parent.

---

## 4. How to make an element rounded corner?

Rounded corners can be created using the `border-radius` property.

```css
div{
  border-radius:10px;
}
```

---

## 5. What is Box Model?

The CSS box model consists of:

* Content
* Padding
* Border
* Margin

Every HTML element is treated like a rectangular box.

---

## 6. Why do we use reset.css?

`reset.css` is used to remove default browser styles like margin, padding, and spacing so that all browsers behave consistently.

---

## 7. Difference between inline, internal and external CSS

### Inline CSS

CSS written directly inside the HTML element using the `style` attribute.

### Internal CSS

CSS written inside the `<style>` tag in the same HTML file.

### External CSS

CSS written in a separate `.css` file and linked using the `<link>` tag.

---

## 8. Does inline CSS override external CSS and why?

Yes, inline CSS overrides external CSS because inline CSS has higher specificity.

---

## 9. Difference between out of the flow and in the flow

### In the Flow

Elements follow the normal document layout.

### Out of the Flow

Elements like `absolute` and `fixed` are removed from normal layout flow.

---

## 10. What is flex-wrap?

`flex-wrap` controls whether flex items should stay in one line or move to the next line.

```css
.container{
  flex-wrap:wrap;
}
```

---

## 11. What is CSS specificity?

CSS specificity decides which CSS rule is applied when multiple rules target the same element.

Priority order:

```text
Inline > ID > Class > Element
```

---

## 12. Difference between display: none and display: block

`display: none` hides the element completely and removes its space, while `display: block` shows the element as a block-level element.

---

## 13. Difference between Grid and Flexbox

### Flexbox

Used mainly for one-dimensional layouts (row or column).

### Grid

Used mainly for two-dimensional layouts (rows and columns together).

---

## 14. What does display: contents do?

`display: contents` removes the element’s own box but keeps its child elements visible.

---

## 15. What happens if we don’t write doctype at the top of HTML?

Without `<!DOCTYPE html>`, the browser may enter quirks mode and the webpage may not behave consistently across browsers.
