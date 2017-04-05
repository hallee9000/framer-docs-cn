# Modules

模块可以让你通过不同的文件来分离或组织一个原型的不同部分。它们是JavaScript或CoffeeScript文件，你可以在代码中通过`require`来引用不同的部分。借助于模块化你可以很好地组织代码并专注于原型的一个部分。
>Modules allow you to separate and organize parts of your prototype across different files. They're JavaScript or CoffeeScript files, which you can include (require) within your prototype. They help you organize your code, and choose what parts to focus on.

You can find them in the /modules folder of your prototype. Modules are based on JavaScript and Node.js standards. Everything that you've prefixed with exports in your module will be available in your prototype. The require keyword imports your module.

If you want to add modules to an older project, we advice to create a new project in the latest Framer Studio, and copy over your files.

Get Started

Create a new project in Framer Studio
Navigate to the /modules folder and open the myModule.coffee file in a text-editor.
To include the module within your project, add the following:
# To include myModule.coffee in our prototype 
module = require "myModule"

Make sure to save your file and refresh your prototype to see changes. Modules can contain anything. For example, you can create Layers within your modules, or define specific interactions within functions.

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

In the example above, a new layer is automatically created and included within our prototype. To also run the function, you can write:

# To include myModule.coffee 
module = require "myModule"
 
# Run the function, printing "I'm running!" 
module.myFunction()

Example: Interactions

Let's create a simple draggable interaction within a module. In our myModule.coffee file, we include the following function. It takes a layer, makes it draggable, and snaps it back to its original position on DragEnd.

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

Now, within our prototype, we can call the makeDraggable function from our module to include the dragging interaction.

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

Example: NPM

Framer Studio modules work with NPM, a package manager where thousands of JavaScript packages are published. Let's import the Backbone library. Make sure you already have NPM installed.

# In your terminal 
cd ~/my-framer-project
npm install backbone

Create a new module in /modules, and name it npm.coffee. Beware that if you name the file the same as the NPM module (like backbone.coffee), you could run into a recursive import problem.

# File: modules/npm.coffee 
exports.backbone = require "backbone"

After a refresh, you can import underscore into your project.

# Import the backbone module from your npm index 
backbone = require("npm").backbone
 
# Or use this nice shortcut, which is the exact same 
{backbone } = require "npm"

