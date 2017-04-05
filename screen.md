Screen

The Screen object contains the size of the current device screen. The size changes when switching to a different device. You can also change the background color and the perspective of the device screen.

Screen.backgroundColor <string>

Sets the background color of the device screen.

# Change the device screen background color 
Screen.backgroundColor = "#28affa"

Screen.width <number>

The width of the current device screen in pixels. (Read-only)

print Screen.width
# Output: 640 

Screen.height <number>

The height of the current device screen in pixels. (Read-only)

print Screen.height
# Output: 1080 

Screen.size <object>

The width and height of the current device screen in pixels. (Read-only)

print Screen.size
# Output: { width:640, height: 1080 } 

Screen.frame <object>

The x, y, width and height of the current device screen in pixels. (Read-only)

print Screen.frame
# Output: { x:0, y:0, width:640, height: 1080 } 

Screen.perspective <number>

The perspective of the current device screen. Set to 1200 by default.

# Rotate layer in 3D 
layerA = new Layer
    rotationX = 30
 
# Adjust perspective 
Screen.perspective = 1000

Screen.perspectiveOriginX <number>

Sets the x origin for 3D transformations. The origin is defined as a number, where 0 is the left edge of the screen and 1 the right edge. The default value is 0.5, the center of the screen.

# Rotate layer in 3D 
layerA = new Layer
    rotationX = 30
 
# Set horizontal perspective origin 
Screen.perspectiveOriginX = 1

Screen.perspectiveOriginY <number>

Sets the y origin for 3D transformations. The origin is defined as a number, where 0 is the top edge of the screen and 1 the bottom edge. The default value is 0.5, the center of the screen.

# Rotate layer in 3D 
layerA = new Layer
    rotationX = 30
 
# Set vertical perspective origin 
Screen.perspectiveOriginY = 1

Screen.convertPointToCanvas(point)

Converts a point from the Screen to the Canvas.

point =
    x: 20
    y: 40
 
pointInCanvas = Screen.convertPointToCanvas(point)

Screen.convertPointToLayer(point, layer)

Converts a point from the Screen to a layer.

point =
    x: 20
    y: 40
 
layer = new Layer
 
pointInLayer = Screen.convertPointToLayer(point, layer)

