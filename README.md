# CSS Shapes Editor

JavaScript library for interactive editing of CSS Shapes values like `polygon()`, `circle()` and `ellipse()` right in the browser.

## Demo

See the `demo/` folder for examples.

## Usage

Load `dist/CSSShapesEditor.js` into the page:

    <srcipt src="dist/CSSShapesEditor.js"></srcipt>

Setup the editor on an element to edit a CSS shape value:

    var element = document.querySelector('#element');
    var shape = window.getComputedStyle(element)['shape-outside'];
    var editor = CSSShapesEditor(element, shape);

An interactive editor for the shape will be drawn on top of the element.

Supported shape values:

 - `polygon()`
 - `circle()`
 - `ellipse()`

Create a new shape from scratch by passing a shape declaration with no coordinates.

    var editor = CSSShapesEditor(element, 'polygon()');

## Events

The `"ready"` event is dispatched after the editor was initialized

    editor.on('ready', function(){
      // editor is ready to work with
    })

The `"shapechange"` event is dispatched after the shape was changed in the editor

    editor.on('shapechange', function(){
      // update the CSS shape value on the element
      element.style['shape-outside'] = editor.getCSSValue();
    })

The `"removed"` event is dispatched after the editor has been turned off and removed by using `editor.remove()`.

    editor.on('removed', function(){
      // editor is gone; do other clean-up
    })

Turn off editor and remove if from the page. **Unsaved changes will be lost.**

    editor.remove()


## Contributing

### Requirements:

  - [node.js](http://nodejs.org/)
  - [Grunt](http://gruntjs.com/)

### Setup dev environment

Install dependencies:

    $ npm install

### Build

Edit source in the `src/` directory. Build with Grunt:

    $ grunt build

Build output goes into `dist/`. Do not edit source in `dist/`, it gets replaced automatically by the Grunt build process.

### Test

Add tests to `test/spec/`. Run tests with Testem:

    $ testem

Testem uses the configuration found in `testem.json`

## License

Apache 2.0 See [LICENSE.md](./LICENSE.md)
