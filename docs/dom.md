## DOM

### goog.dom.append
```js
/*
 * Appends a node with text or other nodes.
 * @param {!Node} parent The node to append nodes to.
 * @param {...goog.dom.Appendable} var_args The things to append to the node.
 */
goog.dom.append = function(parent, var_args) {}
```

```js
let container = goog.dom.getElement('container'); // get <div id="container>
let child = goog.dom.createDom('div'); // create empty <div>
goog.dom.append(container, child); // append <div> into <div id="container">
```

```html
<!-- before -->
<div id="container"></div>

<!-- after -->
<div id="container">
	<div></div>
</div>
```

### goog.dom.createDom
```js
/**
 * @param {string} tagName Tag to create.
 * @param {(Object|Array.<string>|string)=} opt_attributes
 * @param {...(Object|string|Array|NodeList)} var_args Further DOM nodes or strings for text nodes
 * @return {!Element} Reference to a DOM node.
 */
goog.dom.createDom = function(tagName, opt_attributes, var_args) {
```

```js
let div = goog.dom.createDom('div', undefined, 'Div text content');
// <div>Div text content</div>
```

```js
let a = goog.dom.createDom('a', {'href': '#href'}, 'Link');
let li = goog.dom.createDom('li', {'class': 'menu-item'}, a);

// <li class="menu-item"><a href="#href">Link</a></li>
```

### goog.dom.getDocument
```js
/**
 * Gets the document object being used by the dom library.
 * @return {!Document} Document object.
 */
goog.dom.getDocument = function() {}
```

goog.dom.getElement
```js
/**
 * Get Element by ID
 * @param {string|Element} element Element ID or a DOM node.
 * @return {Element} The element with the given ID, or the node passed in.
 */
goog.dom.getElement = function(element) {};
```

```js
let container = goog.dom.getElement('container');
// <div id="container"></div>
```

### goog.dom.getElementsByTagNameAndClass
```js
/*
 * @param {?string=} opt_tag Element tag name.
 * @param {?string=} opt_class Optional class name.
 * @param {(Document|Element)=} opt_el Optional element to look in.
 * @return { {length: number} } Array-like list of elements
 */
goog.dom.getElementsByTagNameAndClass = function(opt_tag, opt_class, opt_el) {}
```

```html
<body>
	<div id="menu">
		<ul>
			<li class="menu">Menu item 1</li>
			<li class="menu">Menu item 2</li>
		</ul>
	</div>
	<div id="navigation">
		<ul>
			<li>Navigation item 1</li>
			<li>Navigation item 2</li>
		</ul>
	</div>
</body>
```

```js
let allLi = goog.dom.getElementsByTagNameAndClass('li');
// allLi.length 4
// allLi[0] <li>Menu item 1</li>
// ...
// allLi[3] <li>Navigation item 2</li>

let menuLi = goog.dom.getElementsByTagNameAndClass('li', 'menu');
// menuLi.length 2
// menuLi[0] <li class="menu">Menu item 1</li>
// menuLi[1] <li class="menu">Menu item 2</li>

let navigation = goog.dom.getElement('navigation');
let navigationLi = goog.dom.getElementsByTagNameAndClass('li', undefined, navigation);
// navigationLi.length 2
// navigationLi[0] <li>Navigation item 1</li>
// navigationLi[1] <li>Navigation item 2</li>
```


### goog.dom.getNextElementSibling
```js
/**
 * Returns the first next sibling that is an element.
 * @param {Node} node The node to get the next sibling element of.
 * @return {Element} The next sibling of node that is an element.
 */
goog.dom.getNextElementSibling = function(node) {}
```

```html
<ul>
	<li>Item 1</li>
	<li>Item 2</li>
</ul>
```

```js
let first = goog.dom.getElementsByTagNameAndClass('li', undefined)[0];
let next = goog.dom.getNextElementSibling(first);
// next <li>Item 2</li>
```

### goog.dom.getParentElement
```js
/**
 * Returns an element's parent, if it's an Element.
 * @param {Element} element The DOM element.
 * @return {Element} The parent, or null if not an Element.
 */
goog.dom.getParentElement = function(element) {}
```

```html
<ul>
	<li>Item 1</li>
	<li>Item 2</li>
</ul>
```

```js
let li = goog.dom.getElementsByTagNameAndClass('li', undefined)[0];
let ul = goog.dom.getParentElement(li);
// ul <ul></ul>
```

### goog.dom.getTextContent
```js
/*
 * @param {Node} node The node from which we are getting content.
 * @return {string} The text content.
 */
goog.dom.getTextContent = function(node) {}
```

```html
<div id="container">
	<span>Span</span>
	<a href="#href">Link</a>
	Text
</div>
```

```js
let container = goog.dom.getElement('container');
let text = goog.dom.getTextContent(container); // Span		Link		Text
```

### goog.dom.getViewportSize
```js
/**
 * @return {!goog.math.Size} The dimensions of the viewport (window)
 */
goog.dom.getViewportSize = function() {}
```

```js
let viewPort = goog.dom.getViewportSize();
// viewPort.width [px]
// viewPort.height [px]
```

### goog.dom.insertSibling...
```js
/**
 * @param {Node} newNode Node to insert.
 * @param {Node} refNode Reference node to insert after.
 */
goog.dom.insertSiblingBefore = function(newNode, refNode) {}
goog.dom.insertSiblingAfter = function(newNode, refNode) {}
```

```html
<ul>
	<li>Item 1</li>
	<li>Item 2</li>
</ul>
```

```js
let firstLi = goog.dom.getElementsByTagNameAndClass('li')[0];

let before = goog.dom.createDom('li', undefined, 'Item before');
let after = goog.dom.createDom('li', undefined, 'Item after');

goog.dom.insertSiblingBefore(before, firstLi);
goog.dom.insertSiblingAfter(after, firstLi);
```

```html
<ul>
	<li>Item before</li>
	<li>Item 1</li>
	<li>Item after</li>
	<li>Item 2</li>
</ul>
```

### goog.dom.removeNode
```js
/**
 * Removes a node from its parent.
 * @param {Node} node The node to remove.
 * @return {Node} The node removed if removed; else, null.
 */
goog.dom.removeNode = function(node) {}
```

### goog.dom.setProperties
```js
/**
 * Sets multiple properties on a node.
 * @param {Element} element DOM node to set properties on.
 * @param {Object} properties Hash of property:value pairs.
 */
goog.dom.setProperties = function(element, properties) {}
```

```js
let div = goog.dom.createDom('div');
goog.dom.setProperties(div, {
	'style': 'background-color: red',
	'class': 'div-class',
	'id': 'container'
});
```

```html
<div style="background-color: red;" class="div-class" id="container"></div>
```

## DataSet

```js
/**
 * Gets a custom data attribute from an element.
 * @param {Element} element DOM node to get the custom data attribute from.
 * @param {string} key Key for the custom data attribute.
 * @return {?string} The attribute value, if it exists.
 */
goog.dom.dataset.get = function(element, key) {}

/**
 * Checks whether custom data attribute exists on an element.
 * @param {Element} element DOM node to get the custom data attribute from.
 * @param {string} key Key for the custom data attribute.
 * @return {boolean} Whether the attibute exists.
 */
goog.dom.dataset.has = function(element, key) {}
```

```html
<div id="container" data-action="test"></div>
```

```js
let container = goog.dom.getElement('container');
let hasDataActionAttribute = goog.dom.dataset.has(container, 'action');
let dataActionAttribute = goog.dom.dataset.get(container, 'action');
// hasDataActionAttribute true
// dataActionAttribute test
```

## Forms
### goog.dom.forms.getFormDataMap
```js
/**
 * Returns form data as a map of name to value arrays.
 * @param {HTMLFormElement} form The form.
 * @return {!goog.structs.Map}
 */
goog.dom.forms.getFormDataMap = function(form) {}
```

```html
<form id="form">
	<input type="text" name="text" value="text" />
	<input type="radio" name="radio" value="1" checked/>
	<input type="checkbox" name="checkbox"  checked />
	<select name="select">
		<option value="1">1</option>
	</select>
</form>
```

```js
let form = /** @type {HTMLFormElement} */ (goog.dom.getElement('form'));
let data = goog.dom.forms.getFormDataMap(form);
// data.get('text')[0] text
// data.get('radio')[0] 1
// data.get('checkbox')[0] on
// data.get('select')[0] 1
```

### goog.dom.forms.setDisabled
```js
/**
 * Enables or disables either all elements in a form or a single form element.
 * @param {Element} el The element, either a form or an element within a form.
 * @param {boolean} disabled Whether the element should be disabled.
 */
goog.dom.forms.setDisabled = function(el, disabled) {}
```

```js
let form = /** @type {HTMLFormElement} */ (goog.dom.getElement('form'));
goog.dom.forms.setDisabled(form, true);
goog.dom.forms.setDisabled(form.elements['text'], true);
```

```html
<input type="text" name="text" value="text" disabled />
```

### goog.dom.forms.setValue
```js
/**
 * Sets the current value of any element with a type.
 * @param {Element} el The element.
 * @param {*=} opt_value (array for setting the value of select multiple elements)
 */
goog.dom.forms.setValue = function(el, opt_value) {}
```

```js
goog.dom.forms.setValue(form.elements['text'], 'new text');
```

## ClassList

### goog.dom.classlist.add, goog.dom.classlist.addAll
```js
/**
 * Adds a class to an element.  Does not add multiples of class names.  This
 * method may throw a DOM exception for an invalid or empty class name if
 * DOMTokenList is used.
 * @param {Element} element DOM node to add class to.
 * @param {string} className Class name to add.
 */
goog.dom.classlist.add = function(element, className) {}

/**
 * Convenience method to add a number of class names at once.
 * @param {Element} element The element to which to add classes.
 * @param {goog.array.ArrayLike.<string>} classesToAdd An array-like object
 * containing a collection of class names to add to the element.
 * This method may throw a DOM exception if classesToAdd contains invalid
 * or empty class names.
 */
goog.dom.classlist.addAll = function(element, classesToAdd) {}
```

```js
let container = goog.dom.getElement('container');
goog.dom.classlist.add(container, 'cls1');
```

### goog.dom.classlist.get
```js
/**
 * Gets an array-like object of class names on an element.
 * @param {Element} element DOM node to get the classes of.
 * @return {!goog.array.ArrayLike} Class names on {@code element}.
 */
goog.dom.classlist.get = function(element) {
```

```js
let container = goog.dom.getElement('container');
let classes = goog.dom.classlist.get(container);
// classes ['class1', 'class2']
```

### goog.dom.classlist.remove, goog.dom.classlist.removeAll
```js
/**
 * Removes a class from an element.  This method may throw a DOM exception
 * for an invalid or empty class name if DOMTokenList is used.
 * @param {Element} element DOM node to remove class from.
 * @param {string} className Class name to remove.
 */
goog.dom.classlist.remove = function(element, className) {}

/**
 * Removes a set of classes from an element.  Prefer this call to
 * repeatedly calling {@code goog.dom.classlist.remove} if you want to remove
 * a large set of class names at once.
 * @param {Element} element The element from which to remove classes.
 * @param {goog.array.ArrayLike.<string>} classesToRemove An array-like object
 * containing a collection of class names to remove from the element.
 * This method may throw a DOM exception if classesToRemove contains invalid
 * or empty class names.
 */
goog.dom.classlist.removeAll = function(element, classesToRemove) {}
```

```js
let container = goog.dom.getElement('container');
goog.dom.classlist.remove(container, 'cls1');
```

## Style

### goog.style.getSize
```js
/**
 * Gets the height and width of an element
 * @param {Element} element Element to get size of.
 * @return {!goog.math.Size} Object with width/height properties.
 */
goog.style.getSize = function(element) {}
```

```js
let container =  goog.dom.getElement('container');
let size = goog.style.getSize(container);
// size.width [px]
// size.height [px]
```

### goog.style.setElementShown
```js
/**
 * Shows or hides an element from the page
 * @param {Element} el Element to show or hide.
 * @param {*} isShown
 */
goog.style.setElementShown = function(el, isShown) {}
```

```js
let container =  goog.dom.getElement('container');
goog.style.setElementShown(container, false);
```

### goog.style.setHeight
```js
/**
 * Set the height of an element.
 * @param {Element} element Element to set the height of.
 * @param {string|number} height
 */
goog.style.setHeight = function(element, height) {
```

```js
let container =  goog.dom.getElement('container');
goog.style.setHeight(container, 100);
```

### goog.style.setOpacity
```js
/**
 * Sets the opacity of a node (x-browser).
 * @param {Element} el Elements whose opacity has to be set.
 * @param {number|string} alpha Between 0 and 1 or an empty string to clear the opacity
 */
goog.style.setOpacity = function(el, alpha) {}
```

```js
let container =  goog.dom.getElement('container');
goog.style.setOpacity(container, 0.5);
```

### goog.style.setStyle
```js
/**
 * Sets a style value on an element.
 * @param {Element} element The element to change.
 * @param {string|Object} style
 * @param {string|number|boolean=} opt_value
 */
goog.style.setStyle = function(element, style, opt_value) {}
```

```js
let container =  goog.dom.getElement('container');
goog.style.setStyle(container, {
	'background-color': 'red',
	'height': '100px'
});
```
