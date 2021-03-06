# googclass-to-es6class

Transform a google closure class defined using goog.defineClass into an es6 class

For example:

```javascript
const Parent = goog.require('some.ns.Parent');

const FooBar = goog.defineClass(Parent, {
  /**
   * Creates a new instance of...
   * @param {Object} name
   */
  constructor: function(name) {
    this.name = name;
  }
});

exports = FooBar;
```

Will be transformed into:

```javascript
const Parent = goog.require('some.ns.Parent');

class FooBar extends Parent {
  /**
   * Creates a new instance of...
   * @param {Object} name
   */
  constructor(name) {
    super(name);

    this.name = name;
  }
}

exports = FooBar;
```

## How to use it

### Install from npm

```shell
npm i goog-class-to-es6 -g
```

### Transform a file

Provide the name of the file. The transformed class will be written to stdout:

```shell
goog-class-to-es6 some_goog_define_class.js
```

Do inline replacement. The file will be overwritten.

```shell
goog-class-to-es6 -i some_goog_define_class.js
```

Write to another file

```shell
goog-class-to-es6 some_goog_define_class.js output_file_es6.js
```

## Testing

```shell
# 1. Clone this repo
# 2. Install
npm i
# 3. Test
npm test
```

## Changelog

* 1.4.0 Add empty line at the end of file if original file has it.
* 1.5.0 Skip files without goog.defineClass.
