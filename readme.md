# LESS helpers & normalize option

This module provides useful less helper functions and a normalize function to quickly get started with new projects.

## Normalize

Can be used by calling `.normalize()` - must be done in the root (not within html or body).

If you want to render default html styling (`<li>`, `<ol>` etc.) you should wrap them into an element with the class `html-text`.

```html
<div class="html-text">
  <h1>Headline</h1>
  <p>This is html Text</p>
  <ul>
    <li>With List Styling</li>
  </ul>
  <p>And default margins & line-heights.</p>
</div>
```

## Helpers

### flex

```less
.flex(@direction: row, @align: flex-start, @justify: flex-start, @wrap: nowrap) {
```

Basic flex styling with parameters.

Example: `.flex(row, flex-end, space-between, wrap)`

### row

```less
.row(@align: flex-start, @justify: flex-start, @wrap: nowrap)
```

Same as the `flex` helper, but without the first parameter. Therefore, it's always row. 

Example `.row(center)`

### column

```less
.column(@align: flex-start, @justify: flex-start, @wrap: nowrap)
```

Same as the `flex` helper, but without the first parameter. Therefore, it's always column. 

Example `.column(flex-end, stretch)`

### max

```less
.max(@max-width)
```

Sets a max width to an element and also sets the width to 100%. Typically used for simple responsive elements (predefined width but shrinks for smaller screens).

Example: `.max(1024px)`

### size

```less
.size(@width, @height)
```

Set width and height.

### stretch
```less
.stretch(@position: absolute)
```

Used to stretch something to full size. By default absolute - can be set to `fixed` for example. Typically used for full screen overlays.

Example: `.stretch(fixed)`

### center
```less
.center()
```

Center an element vertically and horizontally using position absolute. Horizontal alignment is done via margin auto and vertical alignment is done via transform.

### shadow
```less
.shadow()
```

Default shadow style.

### animate
```less
.animate(@property: all)
```

Default animation style - can pass the property that shall be animated. Defaults to `all`

Example: `.animate(background)`

### background
```less
.background(@background)
```

Sets the given color as background and determines & sets the text color based on the best contrast.

Example: `.background(white)`

### mp
```less
.mp(@margin, @padding)
```

Sets margin and padding.

Example: `.mp(0 auto, 1rem)`

### pointer
```less
.pointer()
```

Ensures that the element and all children have a pointer cursor.

## Responsive Helpers

Some of the helpers have a responsive variant to define the styles. In the variables 5 screen sizes are defined

```less
@xl: ~"only screen and (min-width: 1921px)";
@l: ~"only screen and (max-width: 1920px)";
@m: ~"only screen and (max-width: 1199px)";
@s: ~"only screen and (max-width: 719px)";
@xs: ~"only screen and (max-width: 449px)";
```

These are used by the responsive helpers to define multiple variants of a helper for different screen sizes.

### r-flex

```less
.r-flex(
  @xs-direction, @xs-align, @xs-justify, @xs-wrap,
  @s-direciton, @s-align, @s-justify, @s-wrap,
  @m-direciton, @m-align, @m-justify, @m-wrap,
  @l-direciton, @l-align, @l-justify, @l-wrap,
  @xl-direciton, @xl-align, @xl-justify, @xl-wrap
)
```

#### Example

```less
.r-flex(
  row, flex-start, flex-start, wrap,
  row, flex-start, flex-start, wrap,
  row, flex-start, flex-start, nowrap,
  column, stretch, flex-start, nowrap,
  column, stretch, flex-start, nowrap
)
```

### r-mp

```less
.r-mp(
  @xs-margin, @xs-padding,
  @s-margin, @s-padding,
  @m-margin, @m-padding,
  @l-margin, @l-padding,
  @xl-margin, @xl-padding
)
```

#### Example

```less
.r-mp(
  0, 0.5rem,
  0 auto, 1rem,
  1rem, 2rem,
  2rem, 2rem,
  auto, 4rem
)
```

### r-max

```less
.r-max(
  @xs-max-width,
  @s-max-width,
  @m-max-width,
  @l-max-width,
  @xl-max-width
)
```

### r-size

```less
.r-size(
  @xs-width, @xs-height,
  @s-width, @s-height,
  @m-width, @m-height,
  @l-width, @l-height,
  @xl-width, @xl-height
)
```
