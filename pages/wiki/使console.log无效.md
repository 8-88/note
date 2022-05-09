<pre>
tmpDebug = console.log
this.debug = () ->
	tmpDebug.apply console, arguments
emptyFunction = ->

for method of console
	if Object.prototype.toString.call method is '[object Function]'
		console[method] = emptyFunction
</pre>