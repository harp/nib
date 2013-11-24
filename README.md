# harp-nib

> Nib is a Stylus library, providing robust, cross-browser, CSS3 mixins.


## Dependencies

- [NodeJS](http://nodejs.org) – _Server-side JavaScript runtime_
- [Harp](http://harpjs.com) – _The static web server with built-in preprocessing_
  
## Install

To install Nib, run the following command from the root of your Harp project:

```bash
harp install nib
```

Your project will look something like this…

```
myproject/            <-- your project root (or public dir if in framework-mode)
  |- components/      <-- harp puts components here
  |   +- harp-nib/    <-- where this lib gets installed
  |       …
  |- main.styl              <-- where you reference Nib
  +- index.jade             <-- where you reference main.css
```

## Link

From within a `.less` file in your project you can then `@import` Nib:

```styl
@import "components/harp-nib/styl"
```

Or, a portion of Nib:

```styl
@import "components/harp-nib/gradients"
@import "components/harp-nib/overflow"
```

## Use

#### Gradients

Nib’s gradient support has been borrowed from [Axis](https://github.com/jenius/axis) so no additional dependencies are necessary and is is by far the largest feature Nib provides. Not only is the syntax extremely similar to what you would normally write, it’s more forgiving and expands to vendor equivalents.

```css
body {
  background: linear-gradient(top, white, black);
}
```
yields:

```css
body {
  background: -webkit-gradient(linear, left top, left bottom, color-stop(0, #fff), color-stop(1, #000));
  background: -webkit-linear-gradient(top, #fff 0%, #000 100%);
  background: -moz-linear-gradient(top, #fff 0%, #000 100%);
  background: linear-gradient(top, #fff 0%, #000 100%);
}
```

Any number of color stops may be provided:

```css
body {
  background: linear-gradient(bottom left, white, red, blue, black);
}
```

Units may be placed before, or after the color:

```css
body {
  background: linear-gradient(left, 80% red, #000);
  background: linear-gradient(top, #eee, 90% white, 10% black);
}
```

Creating a radial gradient is similar `linear-gradient` and also supports numerous color stops.

```styl
background: radial-gradient(white, red)
```

The most concusses option are a simple top-to-bottom two-colour gradient:

```styl
gradient(red, orange)
```

Or, pass in a base color, and the `simple-gradient` mixin will lighten and darken it by the specified strength and create a simple gradient with the base color being the middle/average. 

```styl
simple-gradient(purple, 10%)
```

#### Positional Mixins

The position mixins `absolute`, `fixed`, and `relative` provide a shorthand variant to what is otherwise three CSS properties. The syntax is as follows:

```
fixed|absolute|relative: top|bottom [n] left|right [n]
```

The following example will default to (0,0):

```css
#back-to-top {
  fixed: bottom right;
}
```

yielding:

```css
#back-to-top {
  position: fixed;
  bottom: 0;
  right: 0;
}
```

You may also specify the units:

```css
#back-to-top {
  fixed: bottom 10px right 5px;
}
```

yielding:

```css
#back-to-top {
  position: fixed;
  bottom: 10px;
  right: 5px;
}
```

#### Clearfix

The clearfix mixin currently takes no arguments, so it may be called as shown below:

```css
.clearfix {
  clearfix();
}
```

yielding:

```css
.clearfix {
  zoom: 1;
}
.clearfix:before,
.clearfix:after {
  content: "";
  display: table;
}
.clearfix:after {
  clear: both;
}
```

#### Border Radius

Nib’s border-radius supports both the regular syntax as well as augmenting it to make the value more expressive.

```css
button {
  border-radius: 1px 2px / 3px 4px;
}

button {
  border-radius: 5px;
}

button {
  border-radius: bottom 10px;
}
```

yielding:

```css
button {
  -webkit-border-radius: 1px 2px/3px 4px;
  -moz-border-radius: 1px 2px/3px 4px;
  border-radius: 1px 2px/3px 4px;
}
button {
  -webkit-border-radius: 5px;
  -moz-border-radius: 5px;
  border-radius: 5px;
}
button {
  -moz-border-radius-topleft: 10px;
  -webkit-border-top-left-radius: 10px;
  border-top-left-radius: 10px;
  -moz-border-radius-bottomright: 10px;
  -webkit-border-bottom-right-radius: 10px;
  border-bottom-right-radius: 10px;
}
```

#### Responsive

The image mixin allows you to define a background-image for both the normal image, and a doubled image for devices with a higher pixel ratio such as retina displays. This works by using a @media query to serve an "@2x" version of the file.

```css
#logo {
  image: '/images/branding/logo.main.png'
}

#logo {
  image: '/images/branding/logo.main.png' 50px 100px
}
```

yields:

```css
#logo {
  background-image: url("/images/branding/logo.main.png");
}
@media all and (-webkit-min-device-pixel-ratio: 1.5) {
  #logo {
    background-image: url("/images/branding/logo.main@2x.png");
    background-size: auto auto;
  }
}
#logo {
  background-image: url("/images/branding/logo.main.png");
}
@media all and (-webkit-min-device-pixel-ratio: 1.5) {
  #logo {
    background-image: url("/images/branding/logo.main@2x.png");
    background-size: 50px 100px;
  }
}
```

#### Ellipsis

The overflow property is augmented with a "ellipsis" value, expanding to what you see below.

```css
.description {
  overflow: ellipsis;
}
```

yielding:

```css
button {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
```

#### Reset

Nib comes bundled with Eric Meyer’s style reset support, you can choose to apply the global or any specifics that you wish. To view the definitions view reset.styl

- global-reset()
- nested-reset()
- reset-font()
- reset-box-model()
- reset-body()
- reset-table()
- reset-table-cell()
- reset-html5()

#### Miscellaneous properties

The following properties follow vendor expansion much like border-radius, however without augmentation, as well as some aliases such as whitespace instead of white-space.

- no-wrap == nowrap
- whitespace == white-space
- box-shadow
- user-select
- column-count
- column-gap
- column-rule
- column-rule-color
- column-rule-width
- column-rule-style
- column-width
- background-size
- transform
- border-image
- transition
- transition-property
- transition-duration
- transition-timing-function
- transition-delay
- backface-visibility
- opacity
- box-sizing
- box-orient
- box-flex
- box-flex-group
- box-align
- box-pack
- box-direction
- animation
- animation-name
- animation-duration
- animation-delay
- animation-direction
- animation-iteration-count
- animation-timing-function
- animation-play-state
- animation-fill-mode
- border-image
- hyphens
- appearance


## Resources

* [Harp documentation](http://harpjs.com/docs/)
* [Stylus documentation](http://learnboost.github.io/stylus/)
* [Nib documentation](http://visionmedia.github.com/nib/)
* [Axis’ gradient documentation](http://roots.cx/axis/#gradients)

## License

This component is [Nib](https://github.com/visionmedia/nib), which is MIT Licensed.
