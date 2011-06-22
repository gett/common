# Common
A small utility module for both node.js and the browser.  
It is available through npm:

	    npm install common

Or as minified js file for the browser:

		<script src='common.min.js'></script>

This module among other things contains a fork of [step](https://github.com/creationix/step) that also provides error handling

``` js
	common.step([
		function(next) { // next is the last argument, except in the last handler
			fs.readFile(__filename, 'utf-8', next);
		},
		function(file) {
			console.log(file);
		}
	], function(err) {
		// any error received in a callback will be forwarded here
	});
```

It also contains a shortcut to the `EventEmitter` prototype and a compatible implementation of this for the browser.

``` js
	var MyEmitter = common.emitter(function() {
		this.foo = 42;
	});
	
	var me = new MyEmitter();
	
	me.emit('foo', me.foo); // emits 'foo',42
```

Besides the two major parts explained above it implements some of the utilities mentioned in The Good Parts like `memoizer` and `curry` and some other useful functional stuff.  
For more information view `index.js`