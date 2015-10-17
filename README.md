## Pyramid.js

Pyramid.js is a Javascript library that leverages the awesome D3.js library to build pyramids.

![image](sample-pyramid.svg)

## Installation

Copy the pyramid.js file into your app directory. To keep things organized, I'd suggest copying the file into a `js/lib` directory and linking from there. Just make sure it is loaded into the browser _after_ D3.js and _before_ any code that relies upon the Pyramid.js functionality.

```{html}
<head>
	<title>Your Awesome App</title>
	<link rel="stylesheet" href="css/styles.css" />
	<script type="text/javascript" src="js/lib/d3.js"></script>

	<!-- Add Pyramid.js here! -->
	<script type="text/javascript" src="js/lib/pyramid.js"></script>

	<script type="text/javascript" src="js/app.js"></script>
</head>
```

## Using Pyramid.js

Using Pyramid.js is a 2-step process:

1. Create a pyramid object
2. Render it.

Here's how to do it

### Creating a pyramid

When creating a Pyramid, 3 elements are required: `data`, `parentContainer`, and `className`.

1. `data` is an array of strings / labels to be displayed in the pyramid - one for each layer
2. `parentContainer` is the `id` (as opposed to the class) of the containing element
3. `className` is the name of class you want for the pyramid SVG

```{javascript}
// set up Pyramid creation
var data = ["Item 1", "Item 2", "Item 3"];
var parent = "#visualization";
var className = "pyramid-2";

// create a pyramid
var pyramid = new Pyramid(data, parent, className);
```

### Rendering a pyramid

Simple.

```{javascript}
pyramid.render();
```

### Other Awesome Features

Pyramid.js ships with some additional features. Here's an overview:

#### Auto-fitting

By default, pyramids created with Pyramid.js will auto-fit themselves into their parent's container. You can decide whether to use auto-fitting by specifying it in the constructor.

```{javascript}
var pyramid = new Pyramid(["A", "B", "C"], "parentId", "className", true);
```

You can also set the autofitting behavior by passing `true` into `pyramid.autoFit()` before rendering your pyramid.

```{javascript}
pyramid.autoFit(true);
```

#### Color Scales

To specify a color scale, pass it in via the constructor:

```{javascript}
var pyramid = new Pyramid(["A", "B", "C"], "parentId", "className", true, d3.scale.category10());
```

You can also set the color scale explicitly using `pyramid.setColorScale()`.

```{javascript}
var color = d3.scale.category10();
pyramid.setColorScale(color);
```

**Note**: Only D3 color scales are supported at this time.

#### Changing the Size

If you choose to disable autofitting, you can manually change the size of the pyramid using `pyramid.setRelativeWidth()`. Try experimenting with a few values. `0.75` tends to work very well.

```{javascript}
pyramid.autoFit(false);
pyramid.setRelativeWidth(0.75);
```

#### Change margins

You can play with the margins. This comes in handy if you want to show a legend or a related scale. You can adjust the default margins by passing a `margins` object to `pyramid.setMargins()`. Here's an example:

```{javascript}
var newMargins = {
	top: 50,
	bottom: 60,
	left: 20
};

pyramid.setMargins(newMargins);
```
Margin values for the `top`, `bottom`, `left`, and `right` attributes are supported.

### Sample App

The sample application illustrates the library in action. Go ahead and check out the [Sample Application](sample).




Thanks!