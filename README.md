![travis badge](https://travis-ci.org/ihmeuw/ihme-ui.svg) [![codecov.io](https://codecov.io/github/ihmeuw/ihme-ui/coverage.svg?branch=master)](https://codecov.io/github/ihmeuw/ihme-ui?branch=master)

# [IHME-UI](https://github.com/ihmeuw/ihme-ui)

ihme-ui is a collection of JavaScript and React-based visualization tools and user interface elements developed by the [Institute of Health Metrics and Evaluation](http://healthdata.org). These elements are used in IHME's [visualizations of global health metrics](http://www.healthdata.org/results/data-visualizations). They are shared to support the community of global health researchers visualize and disseminate their work.

This document provides installation instructions, an overview of the elements, their APIs, and examples of their use.

* [Installation](#installation)
* [API Reference](#api)
  * [axis](#axis)
  * [axis-chart](#axis-chart)
  * [button](#button)
  * [choropleth-legend](#choropleth-legend)
  * [group](#group)
    * [options](#options)
  * [html-label](#html-label)
  * [reponse-container](#response-container)
  * [shape](#shape)
    * [area](#area)
    * [line](#line)
    * [multi-line](#multi-line)
    * [scatter-plot](#scatter-plot)
    * [symbol](#symbol)
  * [slider](#slider)
  * [spinner](#spinner)
  * [svg-text](#svg-text)
* [Code Quality](#code-quality)

###### WORK IN PROGRESS: Not stable until v1.0.0

Current version: 0.2.2

---

## Installation

Requirements:

* Node: ≥ v5.1.1

To install ihme-ui tools and all dependencies:

1. Navigate to the ihme-ui directory.
2. Run the following command from a command-line interpreter:
```sh
npm install ihme-ui
```

To install demo files:

1. Navigate to the ihme-ui directory.
2. Run the following command from a command-line intrepreter:
```sh
npm run demo
```

## API

### <a id="axis"></a>axis

Chart axes with customizable scales and ticks.

Property | Required | Type(s) | Description
        --- | :---: | :---: | ---
`position` | no | number | where to position ticks relative to axis line
`scale` | yes | object | appropriate scale for object
`style` | no | object | style object to apply to element
`ticks` | no | number | [number of axis ticks use](https://github.com/d3/d3-axis#axis_ticks)
`tickFormat` | no | object | [format of axis ticks ticks](https://github.com/d3/d3-axis#axis_tickFormat)
`tickPadding` | no | number | [padding of axis ticks](https://github.com/d3/d3-axis#axis_tickPadding) (default: 3px)
`tickSize` | no | number | [size of both inner and outer tick lines](https://github.com/d3/d3-axis#axis_tickSize) (default: 6)
`tickSizeInner` | no | number | [size of inner tick lines](https://github.com/d3/d3-axis#axis_tickSizeInner) (default: 6)
`tickSizeOuter` | no | number | [size of outer tick lines](https://github.com/d3/d3-axis#axis_tickSizeOuter) (default: 6)
`tickValues` | no | object | [user-specified tick values](https://github.com/d3/d3-axis#axis_tickValues) (default: automatic)
`translate` | no | object | push axis in x or y direction

### axis-chart

Chart with customizable width, height, scales, and margins.

Property | Required | Type(s) | Description
        --- | :---: | :---: | ---
`children` | no | object | React element or elements
`extraClasses` | no | string, object | extra class names to appended to the element
`height` | no | number | pixel height of line chart
`margins`| no | number | margins to subtract from width and height (default: top:20 right:20 bottom:30 left:50)
`width` | no | number | pixel width of line chart
`xDomain` | no | object | [min, max] for xScale (i.e., the domain of the data)
`xScaleType`| no | object | type of x scale
`yDomain` | no | object | [min, max] yScale (i.e., the range of the data)
`yScaleType` | no | object | type of y scale

### button

Button with customizable id, name, class name, icon, animation, and click handler.

Property | Required | Type(s) | Description
        --- | :---: | :---: | ---
`className` | no | string, object | array of classes to add to button
`clickHandler` | no | object | function to be executed on click
`disabled` | no | boolean | boolean value to set button as disabled
`icon` | no | string | path to image to render within button tag
`id` | no | string | id value for button
`name` | no | string | name of button
`showSpinner` | no | boolean | boolean value to display spinner
`text` | no | string | text to render within button tag
`theme` | no | string | color scheme of component (see button.css)

### choropleth-legend

Choropleth map legend with customizable color steps, color scale, data, appearance, and interaction handlers.

Property | Required | Type(s) | Description
        --- | :---: | :---: | ---
`colorSteps` | yes | object | array of color steps, e.g. ['#fff', '#ccc', '\#000', ...]
`colorScale` | yes | object | function that accepts data as a parameter and returns color
`data` | yes | object | array of datum objects
`domain` | yes | object | [min, max] for xScale; xScale positions <circles> and provides axis
`keyField` | yes | string | uniquely identifying property of datum, e.g., location_id
`margins` | no | object | margins to subtract from width and height
`onClick` | no | object | onClick function for DensityPlot circles
`onMouseOver` | no | object | onMouseOver function for DensityPlot circles
`onSliderMove` | no | object | callback function to attach to slider handles
`rangeExtent` | yes | object | array of [min, max] for slider in data space
`valueField` | yes | string | property of datum object that holds value
`unit` | no | string | unit of data; axis label
`width` | yes | number | width of element in pixels
`x1` | no | number | x-axis coord (as percentage) of the start of the gradient (e.g., 0)
`x2` | no | number | x-axis coord (as percentage) of the end of the gradient (e.g., 100)
`zoom` | no | number | float value used for implementing "zooming"; <br />any element that needs to become larger in "presentation mode" should respond to this scale factor. Guide: <br />zoom: 0 -> smallest possible<br />zoom: 0.5 -> half of normal size<br />zoom: 1 -> normal<br />zoom: 2 -> twice normal size

### group

Button set with `selectable` property and customizable class names and interaction handlers.

Property | Required | Type(s) | Description
        --- | :---: | :---: | ---
`children` | yes | object |  React element or elements
`className` | no | string, object |
`clickHandler` | no | object | clickHandler function with following signature: function({ value })
`disabledItems` | no | number, string, object |
`hoverHandler` | no | object |
`selectedItems` | no | number, string, object |
`theme` | no | string | color scheme of component (one of 'dark', 'light', 'common')

#### options

Options for the group element, wrapped by group.

Property | Required | Type(s) | Description
        --- | :---: | :---: - | ---
`className` | no | string, object |
`clickHandler` | no | object |
`disabled` | no | boolean | boolean value to apply disabled class styling
`hoverHandler` | no | object |
`icon` | no | string | path to image to render within label tag
`selected` | no | boolean | boolean value to apply selected class styling
`text` | no | string | text to render within label tag
`type` | no | string, number, object | react element to be wrapped by this option (default: Button)

### html-label

HTML element label with customizable class name, icon, text, appearance, and interaction handlers.

Property | Required | Type(s) | Description
        --- | :---: | :---: | ---
`children` | no | object |  React element or elements
`className` | no | string, object |
`clickHandler` | no | object | function with following signature: function({ value })
`hoverHandler` | no | object | function with following signature: function({ value })
`htmlFor` | no | string | ID of a labelable form-related element
`icon` | no |string | path to image to render within label tag
`text` | no | string | text to render within label tag
`theme` | no | string | color scheme of component; see html-label.css

### responsive-container

Responsive HTML container with customizable resize callback function and responsiveness to height and wait and

Property | Required | Type(s) | Description
        --- | :---: | :---: | ---
`children` | yes | object | React element or elements
`disableHeight` | no | boolean | boolean value to disable dynamic :height property
`disableWidth` | no | boolean | boolean value to disable dynamic :width property
`onResize` | no | object | Callback function to be invoked on resize ({height, width})

### shape

Selection of useful shapes and data displays, suitable for use within an ihme-ui chart.

#### area

Area element with customizable appearance, data, data accessors, and interaction handlers.

Property | Required | Type(s) | Description
        --- | :---: | :---: | ---
`clickHandler` | no | object | (default: noop)
`color` | no | string | (default: steelblue)
`data` | yes | object | array of objects, e.g. [ {}, {}, {} ]
`dataAccessors` | yes | object | (default: { x: 'x', y0: 'y0', y1: 'y1' })
`hoverHandler` | no | object | (default: noop)
`scales` | yes | object | [scales from d3Scale](https://github.com/d3/d3/wiki/Quantitative-Scales)
`strokeWidth` | no | string | (default: 2.5)

#### line

Line element with customizable appearance, data, data accessors, and interaction handlers.

Property | Required | Type(s) | Description
        --- | :---: | :---: | ---
`clickHandler` | no | object | (default: noop)
`data` | yes | object | array of objects e.g. [ {}, {}, {} ]
`dataAccessors` | yes | object | (default: { x: 'x', y: 'y' })
`fill` | no | string | (default: none)
`hoverHandler` | no | object | (default: noop)
`scales` |yes | object | [scales from d3Scale](https://github.com/d3/d3/wiki/Quantitative-Scales)
`stroke` | no | string | (default: steelblue)
`strokeWidth` | no | string | (default: 2.5)

#### multi-line

Multi-line element with customizable appearance, data, data accessors, and interaction handlers.

Property | Required | Type(s) | Description
        --- | :---: | :---: | ---
`clickHandler` | no | object |
`colorScale` | no | object | function that accepts keyfield, and returns stroke color for line
`data` | no | object | array of objects e.g. [ {location: 'USA',values: []}, {location: 'Canada', values: []}
`dataAccessors` | yes | object | key names containing x, y data<br />x -> accessor for xscale<br />y -> accessor for yscale (when there's one, e.g. <Line />)<br />y0 -> accessor for yscale (when there're two; e.g., lower bound)<br />y1 -> accessor for yscale (when there're two; e.g., upper bound)
`dataField` | no | string | key that holds values to be represented by individual lines
`hoverHandler` | no | object |
`keyField` | no | string | key that uniquely identifies dataset within array of datasets
`scales` | no | object | [scales from d3Scale](https://github.com/d3/d3/wiki/Quantitative-Scales)
`showLine` | no | boolean | whether or not to draw lines (e.g., mean estimate lines)
`showUncertainty` | no | boolean | whether or not to draw uncertainty areas for lines

#### scatter-plot

Scatterplot element with customizable appearance, data, data accessors, and interaction handlers.

Property | Required | Type(s) | Description
        --- | :---: | :---: | ---
`clickHandler` | no | object | partially applied function that takes in datum and returns function
`colorScale` | no | object | function that accepts keyfield, and returns stroke color for line
`data` | no | object | array of datasets (nested) or array of datum (flat; single dataset)<br />e.g., nested: [ {location: 'USA', values: []}, {location: 'Canada', values: []} ]<br />e.g., flat: [{loc: 1, mean: 3.0, sex: 2, year: 2013}, {loc: 1, mean: 3.0, sex: 2, year: 2013}]
`dataAccessors` | yes | object | key names containing x, y data
`dataField` | no | string | key name for values representing individual lines
`hoverHandler` | no | object | partially applied function that takes in datum and returns function
`isNested` | no | boolean | whether the data given to ScatterPlot is nested (i.e., contains multiple dastasets)
`keyField` | no | string | key name for topic of data
`scales` | yes | object | [scales from d3Scale](https://github.com/d3/d3/wiki/Quantitative-Scales)
`size` | no | number |
`symbolField` | no | string | key name for value of symbol
`symbolScale` | no | object | function to transform symbol value to a shape

#### symbol

Symbol element with customizable appearance, data, and interaction handlers.

Property | Required | Type(s) | Description
        --- | :---: | :---: | ---
`clickHandler` | no | object | partially applied fn that takes in datum and returns fn (default: noop)
`color` | no | string | (default:steelblue)
`data` | no | object | Datum for the click and hover handlers.
`hoverHandler` | no | object | partially applied fn that takes in datum and returns fn (default: noop)
`position` | no | object | (default: x: 0, y: 0)
`size` | no | number | area in square pixels (default: 64)
`strokeWidth` | no | number | (default: 1)
`type` | no | object | will match a [SYMBOL_TYPE](https://github.com/d3/d3/wiki/SVG-Shapes#symbol_type) (default: circle)

### slider

Single- or multi-input-value selector on a track with customizable appearance and interaction handlers.

Property | Required | Type(s) | Description
        --- | :---: | :---: | ---
`height` | no | number | the height of element (path, line, rect) that the slider will sit atop, in pixels (default: 15)
`marginTop` | no | number | top margin applied within svg document handle is placed within; used to calc origin offset (default: 0)
`marginLeft` | no | number | left margin applied within svg document handle is placed within; used to calc origin offset (default: 0)
`onSliderMove` | no | object | function called with updated extent (as percentage of slider width) (default: () => { return; })
`rangeExtent` | yes | object | [min, max] of domain (in data space) user has selected; used to position slider handles
`translateY` | no | number | y shift of entire slider, in pixels (default: 1)
`width` | yes | number | width of parent container, in pixels
`xScale` | yes | object | linear x scale
`zoom` | no | number |     float value used for implementing "zooming"; any element that needs to become larger in "presentation mode" should respond to this scale factor. Guide:<br />zoom: 0 -> smallest possible<br />zoom: 0.5 -> half of normal size<br />zoom: 1 -> normal<br />zoom: 2 -> twice normal size<br />(default: 1)

### spinner

Animated indicator (e.g., for loading) with customizable size.

Property | Required | Type(s) | Description
        --- | :---: | :---: | ---
`size` | no | string | one of: ['small', 'medium', 'large']

### svg-text

SVG element label with customizable anchor, position, and value.

Property | Required | Type(s) | Description
        --- | :---: | :---: | ---
`anchor` | yes | string | one of: ['start', 'middle', 'end']
`dx` | no | number |
`dy` | no | number |
`fill` | no | string | (default: black)
`value` | no | string, number |
`x` | yes | number |
`y` | no | number |

---

### Code Quality
- eslint enforces AirBnB rules: https://github.com/airbnb/javascript
