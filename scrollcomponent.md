ScrollComponent

A ScrollComponent is used to scroll content. It implements momentum and spring physics, allows for customization, and emits different events.

The ScrollComponent is built with two layers. The ScrollComponent itself is a layer that masks its content. It has a content layer that has draggable enabled and constraints configured. It automatically manages the size of the content layer based on the total size of the sub layers of the content layer.

# Create a new ScrollComponent 
scroll = new ScrollComponent
    width: 100
    height: 100
 
# Include a Layer 
layerA = new Layer
    parent: scroll.content

You can also wrap an existing layer within a ScrollComponent, using ScrollComponent.wrap(). The ScrollComponent will insert itself in-between the content and its super layer. This is useful when you've imported designs from Sketch or Photoshop and want to make a layer scrollable. You can learn more about wrapping in the learn section.

layerA = new Layer
    width: 300
    height: 300
 
scroll = ScrollComponent.wrap(layerA)

scroll.content <layer>

The layer to add content to. To add content, create a new Layer and set its parent to the scroll.content layer. When the content doesn't fit the ScrollComponent it will be clipped.

scroll = new ScrollComponent
    width: 100
    height: 100
 
layerA = new Layer
    parent: scroll.content
    image: "images/bg.png"
    width: 100
    height: 200

scroll.contentInset <object>

Inset for the content. This will give your content extra padding between the constraints and the actual content layers.

scroll = new ScrollComponent
    width: 100
    height: 100
 
layerA = new Layer
    parent: scroll.content
    image: "images/bg.png"
    width: 100
    height: 200
 
scroll.contentInset =
    top: 20
    right: 0
    bottom: 20
    left: 0

scroll.speedX <number>

Horizontal scrolling speed, number between 0 and 1. Default value is 1.

scroll = new ScrollComponent
 
layerA = new Layer
    parent: scroll.content 
 
scroll.speedX = 0.5

scroll.speedY <number>

Vertical scrolling speed, number between 0 and 1. Default value is 1.

scroll = new ScrollComponent
 
layerA = new Layer
    parent: scroll.content 
 
scroll.speedY = 0.5

scroll.scroll <boolean>

Enable or disable scrolling. Enabled by default. If you set this to false, it will set both scrollVertical and scrollHorizontal to false.

scroll = new ScrollComponent
 
layerA = new Layer
    parent: scroll.content
 
scroll.scroll = false

scroll.scrollHorizontal <boolean>

Enable or disable horizontal scrolling.

scroll = new ScrollComponent
 
layerA = new Layer
    parent: scroll.content
 
scroll.scrollHorizontal = false

scroll.scrollVertical <boolean>

Enable or disable vertical scrolling.

scroll = new ScrollComponent
 
layerA = new Layer
    parent: scroll.content
 
scroll.scrollVertical = false

scroll.scrollX <number>

Horizontal scroll location.

scroll = new ScrollComponent
 
layerA = new Layer
    parent: scroll.content
 
scroll.scrollX = 250

scroll.scrollY <number>

Vertical scroll location.

scroll = new ScrollComponent
 
layerA = new Layer
    parent: scroll.content 
 
scroll.scrollY = 250

scroll.scrollPoint <object>

Define the scroll location with x and y properties.

scroll = new ScrollComponent
 
layerA = new Layer
    parent: scroll.content
 
scroll.scrollPoint =
    x: 0
    y: 50

scroll.scrollFrame <object>

Visible scroll frame.

scroll = new ScrollComponent
 
layerA = new Layer
    parent: scroll.content
 
scroll.scrollFrame =
    x: 0
    y: 250
    width: 250
    height: 250

scroll.velocity <number>

Current scroll speed and direction in pixels per second at this current time.

scroll = new ScrollComponent
 
# On scroll, print the velocity 
scroll.on Events.Scroll, ->
    print scroll.velocity

scroll.direction <string>

Current scrolling direction. Returns "up", "down", "left", or "right". The scrolling direction is the inverse of the direction of the drag action: when dragging downwards, you're effectively scrolling upwards. (Read-only)

scroll = new ScrollComponent
 
# On scroll, print the direction 
scroll.on Events.Scroll, ->
    print scroll.direction

scroll.directionLock <boolean>

Snap to horizontal/vertical direction after a certain threshold.

scroll = new ScrollComponent
 
# Allow dragging only in one direction at a time 
scroll.directionLock = true

scroll.directionLockThreshold <object>

The thresholds for lock directions. The x and y values represent the distance you can drag in a certain direction before it starts locking.

scroll = new ScrollComponent
 
# Snap horizontally after dragging 50px 
# Snap vertically instantly 
scroll.directionLock = true
 
scroll.directionLockThreshold =
    x: 50
    y: 0

scroll.angle <number>

Current scrolling angle (in degrees). The scrolling angle is the inverse of the direction of the drag action: when dragging downwards, you're effectively scrolling upwards. (Read-only)

scroll = new ScrollComponent
 
# On scroll, print the angle 
scroll.on Events.Scroll, ->
    print scroll.angle

scroll.isDragging <boolean>

Whether the layer is currently being dragged (returns false when animating). (Read-only)

scroll = new ScrollComponent
 
# Check if the layer is being dragged 
scroll.onMove ->
    print scroll.isDragging

scroll.isMoving <boolean>

Whether the content is currently moving, either by dragging or by a momentum/bounce animation. (Read-only)

scroll = new ScrollComponent
 
# Check if the layer is moving 
scroll.onMove ->
    print scroll.isMoving

scroll.closestContentLayer(originX, originY)

Get the layer closest to the ScrollComponent, depending on the defined origin. The origin is defined as numbers between 0 and 1, where (0,0) is the top-left corner, (0.5, 0.5) the center, and (1,1) the bottom-right corner.

The default values are (0,0). This means that it calculates the distance from the top-left of the ScrollComponent to the top-left of the content layers.

scroll = new ScrollComponent
 
# Create content layers 
layerA = new Layer
    parent: scroll.content
    name: "layerA"
    x: 0
    y: 0
 
layerB = new Layer
    parent: scroll.content
    name: "layerB"
    x: 50
    y: 50
 
# Get the Layer of which the center point is closest 
# to the center point of the ScrollComponent 
print scroll.closestContentLayer(0.5, 0.5)

scroll.closestContentLayerForScrollPoint(originX, originY)

Get the content layer closest to a specific point.

scroll = new ScrollComponent
 
# Create content layers 
layerA = new Layer
    parent: scroll.content
    name: "layerA"
    x: 0
    y: 0
 
layerB = new Layer
    parent: scroll.content
    name: "layerB"
    x: 50
    y: 50
 
# Get the layer of which the top-left 
# corner is closest to x: 50, y: 25 
print scroll.closestContentLayerForScrollPoint(
    x: 50
    y: 25
)
 
# Returns layerB 

You can adjust the origin values to define how the distance is calculated. The default values are (0,0). This means that it calculates the distance from the top-left of the ScrollComponent to the top-left of the content layers.

scroll = new ScrollComponent
 
# Create content layers 
layerA = new Layer
    parent: scroll.content
    name: "layerA"
    x: 0
    y: 0
 
 
layerB = new Layer
    parent: scroll.content
    name: "layerB"
    x: 50
    y: 50
 
# With the origins set to the center, 
# layerA becomes the closest 
print scroll.closestContentLayerForScrollPoint({ x: 50, y: 25 }, 0.5, 0.5)
 
# Returns layerA 

scroll.scrollToPoint(point, animate, animationOptions)

Scroll to a specific point, optionally animating.

Arguments

point — An object with x and y properties.
animate — A boolean, set to true by default. (Optional)
animationOptions — An object with curve, time, delay and repeat properties. (Optional)
scroll = new ScrollComponent
 
# Scroll content to x: 200, y: 100 
scroll.scrollToPoint(
    x: 200, y: 100
    true
    curve: "ease"
)
 
# Scroll very slowly 
scroll.scrollToPoint(
    x: 200, y: 100
    true
    curve: "ease", time: 10
)

scroll.scrollToLayer(layer, originX, originY, animate, animationOptions)

Scroll to a specific layer. You can only scroll to layers that are children of the scroll.content layer.

Arguments

layer — A layer object.
originX — A number between 0 and 1. (Optional)
originY — A number between 0 and 1. (Optional)
animate — A boolean, set to true by default. (Optional)
animationOptions — An object with curve, time, delay and repeat properties. (Optional)
# Create ScrollComponent 
scroll = new ScrollComponent
    width: 500
    height: 500
 
# Define Background 
layerA = new Layer
    x: 500
    y: 1000
    image: "bg.png"
    parent: scroll.content
 
# Scroll to this layer 
scrollerA = new Layer
    parent: scroll.content
 
scroll.scrollToLayer(scrollerA)

The originX and originY arguments define the point within the layer that will be scrolled to. The default values are 0,0 - which is the top-left corner.

scroll.scrollToLayer(
    layerA
    0.5, 0
    true
    time: 2
)

scroll.scrollToClosestLayer(originX, originY)

Scroll to the closest content layer, using the given origin. The default values are (0,0) which is the top-left corner, (0.5, 0.5) the center, and (1,1) the bottom-right corner.

Arguments

originX — A number between 0 and 1.
originY — A number between 0 and 1.
scroll = new ScrollComponent
 
layerA = new Layer
    parent: scroll.content
    x: 75
    y: 75
 
# Scroll to the center of layerA 
scroll.scrollToClosestLayer(0.5, 0.5)

scroll.mouseWheelEnabled <boolean>

Enable or disable scrolling with mousewheel. Disabled by default. When set to true, layers can be scrolled both by dragging and with the mouse.

scroll = new ScrollComponent
    width: 100
    height: 100
 
# Allow scrolling with mouse 
scroll.mouseWheelEnabled = true
 
layerA = new Layer
    parent: scroll.content
    image: "images/bg.png"
    width: 100
    height: 200

scroll.wrap(layer)

Wraps a layer within a new ScrollComponent. This is useful to create scrollable layers out of imported layers.

# Import files from Sketch 
sketch = Framer.Importer.load "imported/Scrollable"
 
# Wrap the "content" layer group 
scroll = ScrollComponent.wrap(sketch.content)

Now, scroll is the variable name of the ScrollComponent. This also automatically wraps your layer within a ScrollContent layer, which you can select to adjust certain properties like momentum, overdrag or bounce.

# Import files from Sketch 
sketch = Framer.Importer.load "imported/Scrollable"
 
# Wrap the "content" layer group 
scroll = ScrollComponent.wrap(sketch.content)
 
# Change scroll properties 
scroll.scrollHorizontal = false
scroll.speedY = 0.5
 
# Change scroll.content properties 
scroll.content.draggable.momentum = true
scroll.content.draggable.overdrag = false
scroll.content.draggable.bounce = false

scroll.updateContent()

Re-calculates and updates the size of the content and the dragging constraints. It also accounts for the contentInset.

If you're looking to change the size of your content layers, you can call it to update the size of your ScrollComponent accordingly.

scroll = new ScrollComponent
 
# Update the contents of the ScrollComponent 
scroll.updateContent()

scroll.copy()

Copies a ScrollComponent, including its content and properties.

scroll = new ScrollComponent
 
layerA = new Layer
    parent: scroll.content
 
# Copy the ScrollComponent 
scrollB = scroll.copy()

scroll.propagateEvents <boolean>

Set the propagateEvents property of the draggable content layer. Set to true by default. This is useful when working with nested ScrollComponents or PageComponents.

Let's say you'd like to have a draggable layer within the scroll.content layer. By default, moving the layer will also move the scroll.content. This is because both layers will listen to the dragging events.

To prevent any draggable children from passing events to its parent, set propagateEvents to false. This applies to all nested draggable layers.

scroll = new ScrollComponent
    width: Screen.width,
    height: Screen.height
 
scroll.content.backgroundColor = "#28affa"
 
layerA = new Layer
    parent: scroll.content,
    backgroundColor: "#fff"
 
layerA.draggable.enabled = true
 
# Setting propagateEvents to false allows you to drag layerA 
# without also scrolling within the ScrollComponent 
layerA.draggable.propagateEvents = false

