## goog.net.XhrIo
+ https://developers.google.com/closure/library/docs/xhrio

```
               [goog.net.EventType.READY_STATE_CHANGE]
                                 |
                   [goog.net.EventType.COMPLETE]
                   /                          \
    [goog.net.EventType.SUCCESS]        [goog.net.EventType.ERROR]
                   \                          /
                    [goog.net.EventType.READY]
```
### Simple GET
```js
goog.net.XhrIo.send('/about', function(e) {
	let xhr = /** @type {goog.net.XhrIo} */ (e.target);
	let response = xhr.getResponse();
	//let jsonResponse = xhr.getResponseJson();
});
```

### POST with query data
```js
let queryData = new goog.Uri.QueryData();
queryData.set('param1', 'value1');
queryData.set('param2', 'value2');

let responseHandler = function(e) {
	let xhr = /** @type {goog.net.XhrIo} */ (e.target);
	// ...
};

let xhr = new goog.net.XhrIo();

goog.events.listen(
	xhr,
	goog.net.EventType.SUCCESS,
	responseHandler
);

xhr.send('/about', 'POST', queryData.toString());
```

## goog.net.XhrManager
```
                     [goog.net.EventType.READY]
                                 |
                   [goog.net.EventType.COMPLETE]
                   /                          \
    [goog.net.EventType.SUCCESS]        [goog.net.EventType.ERROR]
```

```js
let xhrManager = new goog.net.XhrManager(/** opt_maxRetries */ 0);

goog.events.listen(
	xhrManager,
	goog.net.EventType.SUCCESS,
	function(e) {
		let xhr = /** @type {goog.net.XhrIo} */ (e.target);
		// ...
	}
);

let requestId = 'my-id';
// xhrManager.abort(requestId, true);
xhrManager.send(requestId, '/about');
```

## goog.net.IframeIo
Very usefully for sending FORM 'behind' the scene (especially file upload).

```
                   [goog.net.EventType.COMPLETE]
                   /                          \
    [goog.net.EventType.SUCCESS]        [goog.net.EventType.ERROR]
                   \                          /
                    [goog.net.EventType.READY]
```

```js
let iFrameIo = new goog.net.IframeIo();
let form = /** @type {HTMLFormElement} */ (goog.dom.getElement('form'));

goog.events.listen(
	iFrameIo,
	goog.net.EventType.SUCCESS,
	function(e) {
		let iFrameIo = /** @type {goog.net.IframeIo} */ (e.target);
		// iFrameIo.getResponseHtml()
		// iFrameIo.getResponseJson() -> response Content-type: text/plain
		// ...
	}
);

iFrameIo.sendFromForm(form);
```

## goog.net.ImageLoader
```
    [goog.events.EventType.LOAD]     [goog.events.EventType.ERROR]
                 \                           /
                 [goog.net.EventType.COMPLETE]
```

```js
let imageLoader = new goog.net.ImageLoader();

goog.events.listen(
	imageLoader,
	goog.events.EventType.LOAD,
	function(e) {
		let image = /** @type {HTMLImageElement} */ (e.target);
		// ...
	}
);

let imageId = 'image-id';
let imageUrl = 'http://.../....jpg';
imageLoader.addImage(imageId, imageUrl);
imageLoader.start();
```

## Cookies

### goog.net.cookies.isEnabled
```js
let cookiesEnabled = goog.net.cookies.isEnabled();
// true if cookies are enabled
// false if cookies are disabled
```

### goog.net.cookies.containsKey
```js
/**
 * Returns whether there is a cookie with the given name.
 * @param {string} key The name of the cookie to test for.
 * @return {boolean} Whether there is a cookie by that name.
 */
goog.net.cookies.containsKey = function(key) {}
```

### goog.net.cookies.get
```js
/**
 * Returns the value for the first cookie with the given name.
 * @param {string} name  The name of the cookie to get.
 * @param {string=} opt_default  If not found this is returned instead.
 * @return {string|undefined}
 */
goog.net.cookies.get = function(name, opt_default) {}
```

### goog.net.cookies.remove
```js
/**
 * Removes and expires a cookie.
 * @param {string} name  The cookie name.
 * @param {string=} opt_path  (the default is '/')
 * @param {string=} opt_domain  (default is null)
 * @return {boolean} Whether the cookie existed before it was removed.
 */
goog.net.cookies.remove = function(name, opt_path, opt_domain) {}
```

### goog.net.cookies.set
```js
/**
 * @param {string} name
 * @param {string} value
 * @param {number=} opt_maxAge in seconds (from now), -1 session cookie
 * @param {?string=} opt_path
 * @param {?string=} opt_domain
 * @param {boolean=} opt_secure
 */
goog.net.cookies.set = function(
	name, value, opt_maxAge, opt_path, opt_domain, opt_secure) {}
```

## Uri
### goog.uri.utils.getFragment
```js
let fragment = goog.uri.utils.getFragment('http://www.closurecheatsheet.com/about#xtb-generator');
// xtb-generator
```

### goog.uri.utils.getPath
```js
let path = goog.uri.utils.getPath('http://www.closurecheatsheet.com/about#xtb-generator');
// /about
```
