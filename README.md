Grid
===

A simple guide to responsive design. <br>
www.adamkaplan.me/grid


####Why bother with responsive?

We want our websites to be useable on all devices by responding to the user’s behavior, screen size and screen orientation.

####A Fragmented World

As of 2013, there are thousands of different devices and screen sizes that browse the internet, so it's impossible to design layouts to target them all. Instead, we must take a more fluid approach to design.

##Steps

####1. Add the Viewport Meta Tag
Place in the `<head>` of your HTML. This enables use of media queries for cross-device layouts.
```
<meta name="viewport" content="width=device-width, initial-scale=1">
```

####2. Use box-sizing: border-box
Place at the top of your CSS file. The `*` will target all elements on the page.
```
*, *:before, *:after {
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}
```

####3. Create a Container
A container holds all elements and controls the page's maximum width. Using a container will make designing for responsive easier!
```
.container {
  margin: 0 auto;
  max-width: 960px;
  width: 90%;
}
```

```
<div class="container"></div>
```

####4. Create a Column
A column is a class used for stacking content horizontally. The first margin is removed using the pseudo-class `first-child`.

```
.column {
  float: left;
  margin-left: 5%;
}
 
.column:first-child {
  margin-left: 0;
}
```

```
<div class="container">
  <div class="column"></div>
</div>
```

####5. Create Column Sizes
Add size classes to columns to create a reuseable grid system.

```
<div class="container">
  <div class="row">
    <div class="column full"></div>
  </div>
  
  <div class="row">
    <div class="column two-thirds"></div>
    <div class="column one-third"></div>
  </div>
  
  <div class="row">
    <div class="column half"></div>
    <div class="column half"></div>
  </div>
  
  <div class="row">
    <div class="column one-third"></div>
    <div class="column one-third"></div>
    <div class="column one-third"></div>
  </div>
  
  <div class="row">
    <div class="column one-fourth"></div>
    <div class="column one-fourth"></div>
    <div class="column one-fourth"></div>
    <div class="column one-fourth"></div>
  </div>
</div>
```

```
.column.full {
  width: 100%;
}
  
.column.two-thirds {
  width: 65%;
}
  
.column.half {
  width: 47.5%;
}
 
.column.one-third {
  width: 30%;
}
 
.column.one-fourth {
  width: 21.25%;
}
```
####6. Create Rows
Columns are wrapped in rows to prevent other elements from stacking next to them, otherwise know as clearing issues. Rows are cleared with either a `clearfix` or `overflow: hidden`. This clearfix was created by Nicolas Gallager.

```
.clearfix:before,
.clearfix:after {
  content: " ";
  display: table;
}
 
.clearfix:after {
  clear: both;
}
 
.clearfix {
  *zoom: 1;
}
```

```
.row {
  overflow: hidden;
}
```

```
<div class="container">
  <div class="row">
    <div class="column half"></div>
    <div class="column half"></div>
  </div>
  
  <div class="row">
    <div class="column one-third"></div>
    <div class="column one-third"></div>
    <div class="column one-third"></div>
  </div>
</div>
```
####7. Add a Mobile Breakpoint
If the browser's screen size is within a set range, a media query will replace the CSS the browser uses. This is the bread and butter of responsive web design.

```
@media screen and (max-width: 640px) {
  .column.full,
  .column.two-thirds,
  .column.half,
  .column.one-third,
  .column.one-fourth {
    margin: 0;
    width: 100%;
  }
}
```
