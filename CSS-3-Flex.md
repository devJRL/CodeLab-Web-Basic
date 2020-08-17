# CSS Flex (Flexible Box)

## Intro

### Compare 'float' and 'flex'

#### Using `float` display

```html
<!-- in HTML -->
<div class="container clearfix">
  <div class="item">1st</div>
  <div class="item">2nd</div>
  <div class="item">3rd</div>
</div>
```

```css
/* in CSS */
.clearfix::after {
  content: ""; /* blank block */
  display: block;
  clear: both; /* remove float property */
}
.container {
  border: 2px solid red;
}
.container .item {
  width: 100px;
  height: 100px;
  border: 2px solid;
  border-radius: 10px;
  float: left;
}
```

#### Using 'flex' display - `recommand!`

```html
<!-- in HTML -->
<div class="container">
  <div class="item">1st</div>
  <div class="item">2nd</div>
  <div class="item">3rd</div>
</div>
```

```css
/* in CSS */
.container {
  display: flex; /* so simple way! */
  border: 2px solid red;
}
.container .item {
  width: 100px;
  height: 100px;
  border: 2px solid;
  border-radius: 10px;
}
```

### CSS Flexible Box Concept

- `Container`: It is affectted 'flex' property. It's child elements convert 'item'

  > **display**  
  > **flex-flow**: flex-direction, flex-wrap  
  > **justify-content**  
  > **align-content**  
  > **align-items**

- `items`: The child of 'container' has 'flex' property.
  > **order**  
  > **flex**: flex-grow, flex-shrink, flex-basis  
  > **align-self**

### Key idea!

- `flex`: stack vertical like 'block'

- `inline-flex`: stack horizontail liek 'inline'

---

## Container Properties!

1. **`flex-direction`**: set **main-axis** of items

   - `row`: (default) Set axis along with horizontal direction (Left -> Right)
   - `row-reverse`: reverse of row (Right -> Left)
   - `column`: Set axis along with vertical direction (Top -> Bottom)
   - `column-reverse`: reverse of column (Bottom -> Top)

   **`Reference`**

   > The **cross-axis** is created by **main-axis**. This is relative concept.
   > Each axis have 'start' and 'end' line.
   > The things to watch out for is that
   > `'reverse' properties doesn't reverse 'start' and 'end' line.`.
   > This fact is not change.

2. **`flex-wrap`**: set `wrapping items` in one or multi line

   - `nowrap`: (default) fit the items in one line along with container witdh.
   - `wrap`: along the items's width, lay out each item in multi line.
   - `wrap-reverse`: lay out like 'wrap' property, but start with bottom.

3. **`justify-content`**: set how to justify items along 'main-axis'.

   - `flex-start`: (default) Attach to the start line and list in order (right-hand blank)
   - `flex-end`: Attach to the end line and list in order (left-hand blank)
   - `center`: Central alignment (left and right spaces)
   - `space-between`: Uniform division of space remaining after left and right stitched
   - `space-around`: Arrange the spaces evenly on the left and right sides of the item.

4. **`align-content`**: set how to justify items along 'cross-axis'. (affect on `flex-wrap: wrap;`)

   - `stretch`: (default) fit in 'cross-axis;
   - `flex-start`: Attach to the start line and list in order (right-hand blank)
   - `flex-end`: Attach to the end line and list in order (left-hand blank)
   - `center`: Central alignment (left and right spaces)
   - `space-between`: Uniform division of space remaining after left and right stitched
   - `space-around`: Arrange the spaces evenly on the left and right sides of the item.

5. **`align-items`**: set how to justify items along 'cross-axis'. (affect on each line)
   - `stretch`: (default) fit in 'cross-axis;
   - `flex-start`: Attach to the start line and list in order (right-hand blank)
   - `flex-end`: Attach to the end line and list in order (left-hand blank)
   - `center`: Central alignment (left and right spaces)
   - `baseline`: Align to Character line

---

## Items Properties!

1. **`order`**: (default: 0) set item's order in container. The larger the order, the more negative you can specify.

2. **`flex-grow`**: (default: 0) set ratio of width increase to total

3. **`flex-shrink`**: (default: 1) set ratio of width decrease to total

4. **`flex-basis`**: (default: auto) set default width ratio to all  
   -> `Set flex-basis to zero if you want to increase the flex-grow only.`

5. **`flex`**: set(default) flex-grow[`0`] flex-shrink[`1`] flex-basis[`0`(not auto!)]

6. **`align-self`**: (default: auto)
