# Screen

屏幕对象包含了当前所选设备的屏幕尺寸信息。当你切换设备时，它的尺寸信息也会跟着变化。你也可以改变屏幕的背景色和透视景深值。
>The Screen object contains the size of the current device screen. The size changes when switching to a different device. You can also change the background color and the perspective of the device screen.

<a id="backgroundColor"></a>
## Screen.backgroundColor &lt;string&gt;

设置屏幕的背景色。
>Sets the background color of the device screen.

	# Change the device screen background color 
	Screen.backgroundColor = "#28affa"


<a id="width"></a>
## Screen.width &lt;number&gt;

读取屏幕的宽度。（只读）
>The width of the current device screen in pixels. (Read-only)

	print Screen.width
	# Output: 640 

<a id="height"></a>
## Screen.height &lt;number&gt;

读取屏幕的高度。（只读）
>The height of the current device screen in pixels. (Read-only)

	print Screen.height
	# Output: 1080 

<a id="size"></a>
## Screen.size &lg;object&gt;

读取屏幕的宽度和高度信息。（只读）
>The width and height of the current device screen in pixels. (Read-only)

	print Screen.size
	# Output: { width:640, height: 1080 } 

<a id="frame"></a>
## Screen.frame &lg;object&gt;

读取屏幕的坐标和尺寸信息。（只读）
>The x, y, width and height of the current device screen in pixels. (Read-only)

	print Screen.frame
	# Output: { x:0, y:0, width:640, height: 1080 } 

<a id="perspective"></a>
## Screen.perspective &lt;number&gt;

屏幕的透视景深值，默认设置为 1200 。
>The perspective of the current device screen. Set to 1200 by default.

	# Rotate layer in 3D 
	layerA = new Layer
		rotationX: 30
	 
	# Adjust perspective 
	Screen.perspective = 1000

<a id="perspectiveOriginX"></a>
## Screen.perspectiveOriginX &lt;number&gt;
设置 3D 转换的 x 轴中心。他的只是一个数字，0 表示该中心处于屏幕左边缘，1 表示该中心处于屏幕右边缘。默认值是 0.5 ，即屏幕的水平中心。
>Sets the x origin for 3D transformations. The origin is defined as a number, where 0 is the left edge of the screen and 1 the right edge. The default value is 0.5, the center of the screen.

	# Rotate layer in 3D 
	layerA = new Layer
		rotationX: 30
	 
	# Set horizontal perspective origin 
	Screen.perspectiveOriginX = 1

<a id="perspectiveOriginY"></a>
## Screen.perspectiveOriginY &lt;number&gt;

设置 3D 转换的 y 轴中心。他的只是一个数字，0 表示该中心处于屏幕上边缘，1 表示该中心处于屏幕下边缘。默认值是 0.5 ，即屏幕的垂直中心。
>Sets the y origin for 3D transformations. The origin is defined as a number, where 0 is the top edge of the screen and 1 the bottom edge. The default value is 0.5, the center of the screen.

	# Rotate layer in 3D 
	layerA = new Layer
		rotationX: 30
	 
	# Set vertical perspective origin 
	Screen.perspectiveOriginY = 1

<a id="convertPointToCanvas"></a>
## Screen.convertPointToCanvas(point)

将屏幕上的一个点坐标转换成相对于画布的点坐标。
>Converts a point from the Screen to the Canvas.

	point =
		x: 20
		y: 40
	 
	pointInCanvas = Screen.convertPointToCanvas(point)

<a id="convertPointToLayer"></a>
## Screen.convertPointToLayer(point, layer)

将屏幕上的一个点坐标转换成相对于某个图层的点坐标。
>Converts a point from the Screen to a layer.

	point =
		x: 20
		y: 40
	 
	layer = new Layer
	 
	pointInLayer = Screen.convertPointToLayer(point, layer)

