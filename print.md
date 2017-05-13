# Print

打印功能可以帮助你查看运行时的变量。它和控制台输出有点像，唯一的不同是使用 `print` 可以直接在屏幕上查看输出的变量。需要注意的是，在 `javascript` 中使用时要使用 `print()` ，但是在 `CoffeeScript` 中直接写 `print` 就可以啦。

>Printing allows you to inspect variables on runtime. It works similarly to console.log, only when using print, the output is shown directly within your prototype. Note that you need to use print() in Javascript (but not in CoffeeScript). We will omit these in the rest of the docs.

	print "Hello"
	# Output: "Hello" 

你可以查看任意类型的值，输出多个也是可以的。

>You can inspect any type of value, and even multiple at the same time.

	layerA = new Layer
	    x: 10
	    y: 20
	 
	# A single property value 
	print layerA.x
	# Output: 10 
	 
	# Multiple values 
	print layerA.x, print layerA.y
	# Output: 10, 20 

