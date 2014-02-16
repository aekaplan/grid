##Grid

A simple guide to responsive design.<br>
www.adamkaplan.me/grid

####Why bother with responsive?
We want our websites to be useable on all devices by responding to the user’s behavior, screen size and screen orientation.

####A Fragmented World
As of 2013, there are thousands of different devices and screen sizes that browse the internet, so it's impossible to design layouts to target them all. Instead, we must take a more fluid approach to design.

####Mobile First
The term “mobile first” gets thrown around a lot lately. What it really means is to start with mobile styles and layer on styles optimized for larger screens only as needed. In other words, your mobile styles become the default and you no longer have to override them later. It’s much simpler!

##Min-width Media Queries
Introduce layout-specific rules only when you need them. Use `min-width` to layer complexity on your layout as the viewport widens. It’s easier to have all the media queries nearby, rather than at the end of the stylesheet or in a separate document.

```
/* Small screens (default) */
html { font-size; 100%; }

/* Medium screens (640px) */
@media (min-width: 40rem) {
  html { font-size: 112%; }
}

/* Large screens (1024px) */
@media (min-width: 64rem) {
  html { font-size: 120%; }
}
```

##Steps

####1. Not All Browsers are Created Equal
Browsers will render your CSS differently. To avoid this, it’s a good idea to use a modern alternative to a reset like [Normalize.css](http://necolas.github.io/normalize.css/), which will render elements more consistently cross-browser. Remember to include it as-is before your stylesheet.

```
<link rel="stylesheet" href="/css/normalize.css" type="text/css">
<link rel="stylesheet" href="/css/grid.css" type="text/css">
```

####2. Add the Viewport Meta Tag
Place in the `<head>` of your HTML. This enables use of media queries for cross-device layouts.
```
<meta name="viewport" content="width=device-width, initial-scale=1">
```

####3. Use box-sizing: border-box
Place at the top of your CSS file. The `*` will target all elements on the page.
```
*, *:before, *:after {
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}
```

####4. Create a Container
A container holds all elements and controls the page's maximum width. Using a container will make designing for responsive easier!
```
.container {
  margin: 0 auto;
  max-width: 48rem;
  width: 90%;
}
```

```
<div class="container">
  <!--Your Content-->
</div>
```

####5. Create a Column
With mobile first, columns are `block` level (takes up the full width available) by default. No additional styles needed!

```
<div class="container">
  <div class="column">
    <!--Your Content-->
  </div>
  <div class="column">
    <!--Your Content-->
  </div>
  <div class="column">
    <!--Your Content-->
  </div>
</div>
```

####6. Create Column Sizes
On larger screens, columns gain `float: left` in order to stack content horizontally. Columns now use padding for gutters, so we no longer need to worry about removing margins.

```
<div class="container">
  <div class="row">
    <div class="column half">
      <!--Your Content-->
    </div>
    <div class="column half">
      <!--Your Content-->
    </div>
  </div>
</div>
```

```
@media (min-width: 40rem) {
  .column {
    float: left;
    padding-left: 1rem;
    padding-right: 1rem;
  }

  .column.full { width: 100%; }
  .column.two-thirds { width: 66.7%; }
  .column.half { width: 50%; }
  .column.third { width: 33.3%; }
  .column.fourth { width: 24.95%; }
  .column.flow-opposite { float: right; }
}
```

####7. Create Rows
Columns are wrapped in rows to prevent other elements from stacking next to them, otherwise know as clearing issues. Rows are cleared using the popular `clearfix`, which was created by [Nicolas Gallagher](http://nicolasgallagher.com/micro-clearfix-hack/).

```
<div class="container">
  <div class="row clearfix">
    <div class="column half">
      <!--Your Content-->
    </div>
    <div class="column half">
      <!--Your Content-->
    </div>
  </div>

  <div class="row clearfix">
    <div class="column half">
      <!--Your Content-->
    </div>
    <div class="column half">
      <!--Your Content-->
    </div>
  </div>
</div>
```

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

#### Flow Opposite
Add the class `.flow-opposite` to columns where you want content to display first on mobile but appear on the right on larger screens.

```
<div class="container">
  <div class="row clearfix">
    <div class="column half flow-opposite">
      <!--Your Content-->
    </div>
    <div class="column half">
      <!--Your Content-->
    </div>
  </div>
</div>
```

```
@media (min-width: 40rem) {
  .column.flow-opposite { float: right; }
}
```

####Further Reading
* [A Book Apart: Mobile First](http://www.abookapart.com/products/mobile-first)
* [A Book Apart: Responsive Web Design](http://www.abookapart.com/products/responsive-web-design)
* [Beginner’s Guide to Responsive Web Design](http://blog.teamtreehouse.com/beginners-guide-to-responsive-web-design)
* [Box-sizing: Border-box FTW](http://www.paulirish.com/2012/box-sizing-border-box-ftw/)
* [Don't Forget the Viewport Meta Tag](http://dev.tutsplus.com/articles/quick-tip-dont-forget-the-viewport-meta-tag--webdesign-5972)
* [The Many Faces of ‘Mobile First’](http://bradfrostweb.com/blog/mobile/the-many-faces-of-mobile-first/)
* [Understanding the Humble Clearfix](http://fuseinteractive.ca/blog/understanding-humble-clearfix)

####References
* [Android Fragmentation Visualized](http://opensignal.com/reports/fragmentation-2013/)
* [Animate.css](http://daneden.github.io/animate.css/)
* [Box Model](http://developer.mozilla.org/en-US/docs/Web/CSS/box_model)
* [Chrome Developer Tools](http://developers.google.com/chrome-developer-tools/)
* [Code samples by GitHub Gist](https://gist.github.com/aekaplan)
* [Internet Explorer Box Model](http://en.wikipedia.org/wiki/Internet_Explorer_box_model_bug)
* [Progressive Enhancement](http://coding.smashingmagazine.com/2009/04/22/progressive-enhancement-what-it-is-and-how-to-use-it/)
