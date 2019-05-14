For more examples visit [compiler annotation](https://developers.google.com/closure/compiler/docs/js-for-compiler)

## Usage

### Function types
```js
/**
 * @param {type} a
 * @return {type}
 */
function foo(a) {
	return a;
}
```

### Type casting
```js
let b = /** @type {type} */ (a);
```

```js
foo(/** @type {type} */ (a));
```

### Object types

```js
/**
 * @type {type}
 */
Foo.prototype.a;
```
### Any type

```js
/**
 * @type {*} Whatever
 */
Foo.prototype.a;
```

### Multiple types
```js
/**
 * @type {string|number|undefined} String or number or undefined
 */
Foo.prototype.b;
```

### Nullable types
```
/**
 * @type {?string} String or null
 */
Foo.prototype.c;
```

### Required and optional arguments
```js
/**
 * @param {!string} a Required parameter
 * @param {string=} opt_b Optional parameter
 */
Foo.prototype.bar = function(a, opt_b) {

}
```

## Primitive types
```js
/** @type {number} */
/** @type {string} */
/** @type {boolean} */
/** @type {undefined} */
/** @type {null} */
```

## Const
```js
/**
 * @const
 * @type {number}
 */
Foo.A = 1;

/**
 * @const
 * @type {string}
 */
Foo.B = 'text';
```

## Array
```js
/**
 * @param {Array}
 */

/**
 * @param {Array.<*>} Array of unknown/whatever items
 * @param {Array.<string>} Items in array are strings
 * @param {Array.<Object>} Items in array are Objects
 */

/**
 * @param {Array.<Array.<string>>} Items in array are Arrays of strings
 */
```

## Object
```js
/**
 * @param {Object}
 */

/**
 * @param {Object.<number, string>} Object with number keys and string values
 */
```

## Function
```js
/**
 * @param {Function}
 */

/**
 * @param {function(): boolean} Param is a function which return boolean
 * @param {function(number): boolean} Function with number as parameter and return boolean
 */
```

## Html
```js
/** @type {Element} */
/** @type {Document} */
/** @type {DocumentFragment} */
/** @type {Node} */
/** @type {NodeList} */
/** @type {Window} */

/** @type {HTMLAnchorElement} */
/** @type {HTMLDocument} */
/** @type {HTMLElement} */
/** @type {HTMLFormElement} */
/** @type {HTMLImageElement} */
```

## Typedef
```js
/**
 * @typedef {{
 *      id: number,
 *      direction: string
 *  }}
 */
Foo.NAVIGATE_INFO;

/**
 * @type {Foo.NAVIGATE_INFO}
 */
Foo.prototype.info;
```

```js
/**
 * Function returning "typedef". Property "style" can be string or null.
 *
 * @return {{link: string, href: string, style: (string|null)}}
 */
Foo.prototype.getLink = function() {
	// ...
	return {
		link: 'Link',
		href: 'http://...',
		style: null
	};
}
```

## Enum
```js
/**
 * @enum {string}
 */
Foo.Api = {
	GET: '/get',
	PUT: '/put'
}

/**
 * @enum {number}
 */
Foo.Direction= {
	UP: 1,
	DOWN: 2
}
```

## VarArgs
```js
/**
 * @param {...string} var_args
 */
Foo.prototype.insertAll = function(var_args) {
	// arguments, arguments.length
};
```

## OOP
```js
/**
 * @interface
 */
Foo = function() {};

/**
 * @param {number} a
 */
Foo.prototype.bar = function(a) {};
```

```js
/**
 * @constructor
 * @implements {Foo}
 */
app.Some = () {

};

/**
 * @param {number} a
 */
app.Some.prototype.bar = function(a) {

};

```

```js
/**
 * @constructor
 * @extends {app.Some}
 */
app.Other = () {
	goog.base(this);
};
```

