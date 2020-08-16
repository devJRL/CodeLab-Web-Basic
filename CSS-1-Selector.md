# CSS Selector

E { property: value; }

```css
div {
  width: 300px; /* 요소가로너비: 너비값; */
  height: 150px; /* 요소세로너비: 너비값; */

  margin: 20px 50px; /* 요소외부여백: 상하 좌우 (단축속성); */
  padding: 35px 25px; /* 요소내부여백: 상하 좌우 (단축속성); */

  background: red; /* 요소배경: 색상값 혹은 이미지; */

  color: white; /* 글자색: 색상값; */
  font-size: 16px; /* 글자크기: 크기값(16px 기본값) */
  font-weight: bold: /* 글자가중치: 가중치값 */
}
```

## Basic Selector

- Universial Selector

  ```css
  * {
    color: red;
  }
  ```

- Type(tag) Selector

  ```css
  div {
    color: red;
  }
  ```

- `class` attirbute Selector

  ```css
  .class-name {
    color: red;
  }
  ```

- `id` attirbute Selector : `must be unique!`
  ```css
  #id {
    color: red;
  }
  ```

## Combine Selector

- `EF`: Comninator Selector

  ```css
  div.class-name {
    color: red;
  }
  ```

- `P > C`: Child Selector

  ```css
  ul > li.class-name {
    color: red;
  }
  ```

- `P C`: Descendant Selector

  ```css
  ul .class-name {
    color: red;
  }
  ```

- `E + F`: Adjacent Sibling Cominator

  ```css
  /* class-name'next */
  .class-name + li {
    color: red;
  }
  ```

- E ~ F: Genera; Sibling Cominator

  ```css
  /* all of class-name's next */
  .class-name ~ li {
    color: red;
  }
  ```

---

## Pseudo-Classes Selector (`:`)

### Along `mouse pointer`

- `E:hover`: When mouse pointer is `over` on element

  ```css
  div {
    width: 100px;
    height: 100px;
    background: blue;
    transition: 0.5s;
  }

  div:hover {
    width: 200px;
    background: green;
  }
  ```

- `E:active`: When mouse porinter has `click` on element

  ```css
  button {
    width: 50px;
    height: 30px;
    background: blue;
  }

  button:active {
    background: green;
  }
  ```

- `E:focus`: When input element is focused.

  ```css
  input {
    width: 100px;
    outline: none;
    border: 1px solid lightgray;
    padding: 5px 10px;
  }

  input:focus {
    border-color: red;
    width: 200px;
  }
  ```

### Along `element`

- `E:first-child`: Select first of element

  ```css
  .fruits li:first-child {
    color: red;
  }
  ```

  ```html
  <ul class="fruits">
    <li>Apple<!-- selected! --></li>
    <li>Orange</li>
    <li>Banana</li>
    <li>Melon</li>
  </ul>
  ```

- `E:last-child`: Select last of element

  ```css
  .fruits li:last-child {
    color: red;
  }
  ```

  ```html
  <ul class="fruits">
    <li>Apple</li>
    <li>Orange</li>
    <li>Banana</li>
    <li>Melon<!-- selected! --></li>
  </ul>
  ```

- `E:nth-child(n)`: Select `n`th of element

  ```css
  .fruits li:nth-chlid(2) {
    color: red;
  }
  ```

  ```html
  <ul class="fruits">
    <li>Apple</li>
    <li>Orange<!-- selected! --></li>
    <li>Banana</li>
    <li>Melon</li>
  </ul>
  ```

  - `2n`

    > ```css
    > .fruits li:nth-chlid(2n) {
    >   color: red;
    > }
    > ```
    >
    > ```html
    > <ul class="fruits">
    >   <li>Apple</li>
    >   <li>Orange<!-- selected! --></li>
    >   <li>Banana</li>
    >   <li>Melon<!-- selected! --></li>
    > </ul>
    > ```

  - `n+3`

    > Please ignore that comment. `<!-- prettier-ignore -->`
    >
    > ```css
    > .fruits li:nth-chlid(n+3) { <!-- prettier-ignore -->
    >   color: red;
    > }
    > ```
    >
    > ```html
    > <ul class="fruits">
    >   <li>Apple</li>
    >   <li>Orange</li>
    >   <li>Banana<!-- selected! --></li>
    >   <li>Melon<!-- selected! --></li>
    > </ul>
    > ```

  - `Caution!` This sentence has not selected nothing.

    > ```css
    > .fruits p:nth-chlid(1) {
    >   color: red;
    > }
    > ```
    >
    > ```html
    > <ul class="fruits">
    >   <div>Apple<!-- non-selected! : not p tag --></div>
    >   <p>Orange</p>
    >   <p>Banana</p>
    >   <span>Melon</span>
    > </ul>
    > ```

- `E:nth-of-type(n)`: Select `n`th of element that is same type of `E`

  ```css
  .fruits p:nth-of-type(1) {
    color: red;
  }
  ```

  ```html
  <div class="fruits">
    <div>Apple</div>
    <p>Orange<!-- selected --></p>
    <p>Banana</p>
    <span>Melon</span>
  </div>
  ```

  - `Caution!`

    > ```css
    > .fruits .yammy:nth-of-type(1) {
    >   color: red;
    > }
    > ```
    >
    > ```html
    > <ul class="fruits">
    >   <li>Apple<!-- non-selected! : .yammy class, not type --></li>
    >   <li class="yammy">Orange</li>
    >   <li>Banana</li>
    >   <li class="yammy">Melon</li>
    > </ul>
    > ```

- `E:not(F)`: Negative select in `E` except `F`

  ```css
  .fruits :not(.new) {
    color: red;
  }
  ```

  ```html
  <div class="fruits">
    <div class="new">Apple</div>
    <p>Orange<!-- selected --></p>
    <p class="new">Banana</p>
    <span>Melon<!-- selected --></span>
  </div>
  ```

---

## Pseudo-Element Selector (`::`)

- `E::before`: Insert content with styling before `E`'s inner content.

  ```css
  ul {
    font-size: 30px;
  }

  ul li::before {
    content: "num"; /* Must need! */
    color: red;
    margin-right: 20px;
  }
  ```

  ```html
  <ul>
    <li>1<!-- num1 --></li>
    <li>2<!-- num2 --></li>
    <li>3<!-- num3 --></li>
    <li>4<!-- num4 --></li>
    <li>5<!-- num5 --></li>
  </ul>
  ```

- `E::after`: Insert content with styling after `E`'s inner content.

  ```css
  ul {
    font-size: 30px;
  }

  ul li::after {
    content: ".0"; /* Must need! */
    color: red;
    margin-right: 20px;
  }
  ```

  ```html
  <ul>
    <li>1<!-- 1.0 --></li>
    <li>2<!-- 2.0 --></li>
    <li>3<!-- 3.0 --></li>
    <li>4<!-- 4.0 --></li>
    <li>5<!-- 5.0 --></li>
  </ul>
  ```

---

## Attribute Selector (`[attr]`)

- `[attr]`: Select type has `attr` attribute.

  ```css
  [disabled] {
    color: red;
    opacity: 0.25; /* 25% */
  }
  ```

  ```html
  <input type="text" value="username" />
  <input type="password" value="password" />
  <input type="text" value="readonly text" disabled />
  ```

- `[attr=val]`: Select type has `attr` attribute and it's value is `val`.

  ```css
  [type="password"] {
    color: red;
    opacity: 0.25; /* 25% */
  }
  ```

  ```html
  <input type="text" value="username" />
  <input type="password" value="password" />
  <input type="text" value="readonly text" disabled />
  ```

- `[attr^=val]`: Select type has `attr` attribute and it's value is `start with 'val'`.

  ```css
  [class^="btn-"] {
    font-weight: bold;
    border-radius: 10px;
  }
  ```

  ```html
  <button>Normal-1</button>
  <button class="btn-success">Success<!-- selected --></button>
  <button>Normal-2</button>
  <button class="btn-danger">Danger<!-- selected --></button>
  <button>Normal-3</button>
  ```

- `[attr$=val]`: Select type has `attr` attribute and it's value is `end with 'val'`.

  ```css
  [class$="success"] {
    color: green;
    font-weight: bold;
  }
  [class$="danger"] {
    color: red;
    font-weight: bold;
  }
  ```

  ```html
  <button>Normal-1</button>
  <button class="btn-success">Success<!-- selected --></button>
  <button>Normal-2</button>
  <button class="btn-danger">Danger<!-- selected --></button>
  <button>Normal-3</button>
  ```

---

## Inheritance

Certain css-properties can be inheritanted to each decendant elements.

- font
  - font-size
  - font-weight
  - font-style
  - line-height
  - font-family
- color
- text-align
- text-indent
- text-decotation
- letter-spacing
- opacity
- etc..

---

## Score ranking for rendering in browser

- `!important` : max pt
- `Style Attribute`(inline on html) : 1000 pt
- `ID Selector(#)`: 100 pt
- `Class Selector(.)`: 10 pt (\*\* `:not` : 0pt )
- `Type Selector` : 1 pt
- `Universial Selector` : 0 pt
- `Inherit` : 0 pt
