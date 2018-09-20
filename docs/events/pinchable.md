# Pinchable

所谓可捏放图层，就是你可以用两指[缩放](#pinchable.scale)或[旋转](#pinchable.rotate)的图层。当开启可捏放后，这两个属性默认都是开启的。你可以通过[最大值](#pinchable.scaleMin)或[最小值](#pinchable.scaleMax)自定义缩放的范围。在 Framer Studio 中你可以按住 `Alt` 键同时使用鼠标拖动来模拟双指捏放。
>Pinchable layers can be scaled and rotated with two fingers. By default, both of these properties are enabled. You can also define custom scale ranges, by defining minimum and maximum values. To pinch layers within Framer Studio, hold the alt key while moving your cursor.

<a id="enabled"></a>
## layer.pinchable.enabled &lt;boolean&gt;

开启图层的可捏放属性。
>Enable pinching for the layer.

	layerA = new Layer
	layerA.pinchable.enabled = true

<a id="threshold"></a>
## layer.pinchable.threshold &lt;number&gt;

这是一个临界值，当量之间的距离大于这个值时才会被识别为捏放事件，默认是 0 。
>The minimal distance between two pointers before the gesture is recognized. Set to 0 by default.

	layerA = new Layer
	layerA.pinchable.enabled = true
	 
	# Set the minimal distance to 10 
	layerA.pinchable.threshold = 10

<a id="centerOrigin"></a>
## layer.pinchable.centerOrigin &lt;boolean&gt;

是否设置双指捏放时图层的变换中心处于你双指正中间的位置，默认为 `true` 。
>Sets the transform origin of your pinchable layer to the center point between your fingers. Set to true by default.

	layerA = new Layer
	layerA.pinchable.enabled = true
	 
	# Always scale from the center of the layer   
	layerA.pinchable.centerOrigin = false

<a id="scale"></a>
## layer.pinchable.scale &lt;boolean&gt;

是否开启双指捏放时图层跟着缩放，默认打开。
>Enable or disable scaling on pinch. Set to true by default.

	layerA = new Layer
	layerA.pinchable.enabled = true
	 
	# Disable scale on pinch 
	layerA.pinchable.scale = false

<a id="scaleIncrements"></a>
## layer.pinchable.scaleIncrements &lt;number&gt;

增量式地缩放，也就是缩放时图层的尺寸增长速度越来越大。
>Scale the pinchable layer incrementally.

	layerA = new Layer
	layerA.pinchable.enabled = true
	 
	# Scale in increments of 0.5 (0.5, 1, 1.5, 2) 
	layerA.pinchable.scaleIncrements = 0.5

<a id="minScale"></a>
## layer.pinchable.minScale &lt;number&gt;

设置图层缩小时的最小 `scale` 值。
>Set the minimal scale value of the pinchable layer.

	layerA = new Layer
	layerA.pinchable.enabled = true
	 
	# Set the minimal scale to 0.5 
	layerA.pinchable.minScale = 0.5

<a id="maxScale"></a>
## layer.pinchable.maxScale &lt;number&gt;

设置图层放大时的最大 `scale` 值。
>Set the maximal scale value of the pinchable layer.

	layerA = new Layer
	layerA.pinchable.enabled = true
	 
	# Set the maximal scale to 2 
	layerA.pinchable.maxScale = 2

<a id="scaleFactor"></a>
## layer.pinchable.scaleFactor &lt;number&gt;

设定缩放倍数，默认为 1 ，即和手指移动距离同步。
>Set the scaling factor of the pinchable layer. Set to 1 by default.

	layerA = new Layer
	layerA.pinchable.enabled = true
	 
	# Increase scaling speed by 2 
	layerA.pinchable.scaleFactor = 2

<a id="scaleFactor"></a>
## layer.pinchable.rotate &lt;boolean&gt;

是否开启双指旋转，默认开启。
>Enable or disable rotation on pinch. Set to true by default.

	layerA = new Layer
	layerA.pinchable.enabled = true
	 
	# Disable scale on pinch 
	layerA.pinchable.rotate = false

<a id="scaleFactor"></a>
## layer.pinchable.rotateIncrements &lt;number&gt;

增量式地旋转，也就是旋转时图层的旋转角度增长速度越来越大。
>Rotate the pinchable layer incrementally.

	layerA = new Layer
	layerA.pinchable.enabled = true
	 
	# Scale in increments of 15 degrees 
	layerA.pinchable.rotateIncrements = 15

<a id="scaleFactor"></a>
## layer.pinchable.rotateFactor &lt;number&gt;

设定旋转倍数，默认为 1 ，即和手指扭动角度同步。
>Set the rotation factor of the pinchable layer. Set to 1 by default.

	layerA = new Layer
	layerA.pinchable.enabled = true
	 
	# Increase the rotation speed by 2 
	layerA.pinchable.rotateFactor = 2

