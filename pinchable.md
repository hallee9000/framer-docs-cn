Pinchable

Pinchable layers can be scaled and rotated with two fingers. By default, both of these properties are enabled. You can also define custom scale ranges, by defining minimum and maximum values. To pinch layers within Framer Studio, hold the alt key while moving your cursor.

layer.pinchable.enabled <boolean>

Enable pinching for the layer.

layerA = new Layer
layerA.pinchable.enabled = true

layer.pinchable.threshold <number>

The minimal distance between two pointers before the gesture is recognized. Set to 0 by default.

layerA = new Layer
layerA.pinchable.enabled = true
 
# Set the minimal distance to 10 
layerA.pinchable.threshold = 10

layer.pinchable.centerOrigin <boolean>

Sets the transform origin of your pinchable layer to the center point between your fingers. Set to true by default.

layerA = new Layer
layerA.pinchable.enabled = true
 
# Always scale from the center of the layer   
layerA.pinchable.centerOrigin = false

layer.pinchable.scale <boolean>

Enable or disable scaling on pinch. Set to true by default.

layerA = new Layer
layerA.pinchable.enabled = true
 
# Disable scale on pinch 
layerA.pinchable.scale = false

layer.pinchable.scaleIncrements <number>

Scale the pinchable layer incrementally.

layerA = new Layer
layerA.pinchable.enabled = true
 
# Scale in increments of 0.5 (0.5, 1, 1.5, 2) 
layerA.pinchable.scaleIncrements = 0.5

layer.pinchable.minScale <number>

Set the minimal scale value of the pinchable layer.

layerA = new Layer
layerA.pinchable.enabled = true
 
# Set the minimal scale to 0.5 
layerA.pinchable.minScale = 0.5

layer.pinchable.maxScale <number>

Set the maximal scale value of the pinchable layer.

layerA = new Layer
layerA.pinchable.enabled = true
 
# Set the maximal scale to 2 
layerA.pinchable.maxScale = 2

layer.pinchable.scaleFactor <number>

Set the scaling factor of the pinchable layer. Set to 1 by default.

layerA = new Layer
layerA.pinchable.enabled = true
 
# Increase scaling speed by 2 
layerA.pinchable.scaleFactor = 2

layer.pinchable.rotate <boolean>

Enable or disable rotation on pinch. Set to true by default.

layerA = new Layer
layerA.pinchable.enabled = true
 
# Disable scale on pinch 
layerA.pinchable.rotate = false

layer.pinchable.rotateIncrements <number>

Rotate the pinchable layer incrementally.

layerA = new Layer
layerA.pinchable.enabled = true
 
# Scale in increments of 15 degrees 
layerA.pinchable.rotateIncrements = 15

layer.pinchable.rotateFactor <number>

Set the rotation factor of the pinchable layer. Set to 1 by default.

layerA = new Layer
layerA.pinchable.enabled = true
 
# Increase the rotation speed by 2 
layerA.pinchable.rotateFactor = 2

