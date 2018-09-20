# Modules

模块可以让你通过不同的文件来分离或组织一个原型的不同部分。它们是 JavaScript 或 CoffeeScript 文件，你可以在代码中通过`require`来引用不同的部分。借助于模块化你可以很好地组织代码并专注于原型的一个部分。
>Modules allow you to separate and organize parts of your prototype across different files. They're JavaScript or CoffeeScript files, which you can include (require) within your prototype. They help you organize your code, and choose what parts to focus on.

你可以在你的原型的`/modules`文件夹中看到 Module 。Module 是基于 `JavaScript` 和 `Node.js` 标准的，每个模块中对外导出的接口都可以在你的原型中使用。你可以通过关键词 `require` 在你的原型代码中导入模块。
>You can find them in the /modules folder of your prototype. Modules are based on JavaScript and Node.js standards. Everything that you've prefixed with exports in your module will be available in your prototype. The require keyword imports your module.

如果你想给老的项目添加模块，我们建议你使用最新版本的 Framer Studio 创建一个新项目并把你的文件复制过来。
>If you want to add modules to an older project, we advice to create a new project in the latest Framer Studio, and copy over your files.

### 开始

* 1. 使用 Framer Studio 创建一个新项目
* 2. 进入 `/modules` 文件夹，你会看到里面有个 `myModule.coffee` 文件，使用文本编辑器打开它
* 3. 在你的项目文件（`app.coffee`）中添加以下代码以引入该模块:


	# To include myModule.coffee in our prototype 
	module = require "myModule"

确定保存了模块文件，刷新原型就能看到变化了。在 Module 中可以做很多事情，比如说你可以在 Module 中创建图层、或者使用函数创建一个交互效果。
>Make sure to save your file and refresh your prototype to see changes. Modules can contain anything. For example, you can create Layers within your modules, or define specific interactions within functions.

	# Store variables 
	exports.myVar = "myVariable"
	 
	# Create functions 
	exports.myFunction = ->
	    print "I'm running!"
	 
	# Create Arrays 
	exports.myArray = [1, 2, 3]
	 
	# Create Layers 
	exports.mylayerA = new Layer
	    backgroundColor: "#fff"

在上面的例子中，我们使用模块创建了一个图层并将其引入原型中。想要运行它，你需要在原型代码中添加以下代码：
>In the example above, a new layer is automatically created and included within our prototype. To also run the function, you can write:

	# To include myModule.coffee 
	module = require "myModule"
	 
	# Run the function, printing "I'm running!" 
	module.myFunction()

<a id="example-interactions"></a>
## Example: Interactions

让我们一起创建一个简单的拖拽交互 Module。在 `myModule.coffee` 文件中，写入一下函数，它接受一个传入的图层，并使其变成可以拖拽的，并在拖拽结束后让图层返回原位置。
>Let's create a simple draggable interaction within a module. In our myModule.coffee file, we include the following function. It takes a layer, makes it draggable, and snaps it back to its original position on DragEnd.

	# A draggable function without our module 
	exports.makeDraggable = (layer) ->
	    layer.draggable.enabled = true
	 
	    # Store current x and y position 
	    startX = layer.x
	    startY = layer.y
	 
	    # Animate back on DragEnd 
	    layer.on Events.DragEnd, ->
	        this.animate
	            properties:
	                x: startX
	                y: startY
	            curve: "spring(300,20,0)"

现在，在我们的原型代码中就可以引入该模块并使用 `makeDraggable` 函数给图层添加拖拽效果了。
>Now, within our prototype, we can call the makeDraggable function from our module to include the dragging interaction.

	# Include module 
	module = require "myModule"
	 
	# Set background 
	bg = new BackgroundLayer
	    backgroundColor: "#28AFFA"
	 
	# Create a new layer 
	layerA = new Layer
	    backgroundColor: "#fff"
	    borderRadius: 4

	layerA.center()
	 
	# Add the dragging interaction to layerA 
	module.makeDraggable(layerA)

<a id="example-npm"></a>
## Example: NPM

Framer Studio 模块也可以支持 [NPM](https://www.npmjs.com/) ——一个包含很多 `JavaScript` 插件的包管理器。让我们来试着引入 `Backbone` 库，在此之前请确认你已经安装了 `NPM` 。
>Framer Studio modules work with NPM, a package manager where thousands of JavaScript packages are published. Let's import the Backbone library. Make sure you already have NPM installed.

	# In your terminal 
	cd ~/my-project.framer
	npm install moment

在 `/modules` 文件夹中创建一个新的文件 `npm.coffee`。请注意，如果你给它起的名字是那个插件的名字，比如 `backbone.coffee` ，会引起循环导入的问题。 
>Create a new module in /modules, and name it npm.coffee. Beware that if you name the file the same as the NPM module (like backbone.coffee), you could run into a recursive import problem.

	# File: modules/npm.coffee 
	exports.moment = require "moment"

刷新之后，你就可以在项目代码中导入它了。
>After a refresh, you can import underscore into your project.

	# Import the moment module from your npm index 
	moment = require("npm").moment
	 
	# Or use this nice shortcut, which is the exact same 
	{moment} = require "npm"

现在你就可以在项目中使用它了。
>And now you can use it in your project:

	dayStarted = new Layer
	    html: moment().startOf("day").fromNow()
