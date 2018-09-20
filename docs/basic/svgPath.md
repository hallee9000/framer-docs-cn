# SVGPath
使用 `SVGPath` 来调节设计模式下画的 SVG 路径的 `fill` 、`strokeStart` 、`strokeEnd` 等属性，并给它添加动画。
>Use SVGPath to modify and animate SVG paths targeted from Design. Set fill, strokeStart, strokeEnd and more.

在代码模式中不能创建 SVGPath ，我们一般使用 SVGLayer 并通过获取它的 `elements` 属性来获取 SVGPath 。
>An SVGPath should not be created in code. The only way to get an SVGPath is through the elements property of SVGLayer

	svg = new SVGLayer
	    svg: "<svg><path id='shape' name='Rectangle' d='M0 0 H 150 V 75 H 0 L 0 0' />"
	    fill: "#0AF"
	 
	path = svg.elements.shape

图层可以沿着一个 SVG 路径运动，下面的例子演示了一个图层沿着一个 SVG 路径的位置和角度运动。
>Layers can also be animated along a path, in combination with the point and rotation property, for example.

	layer = new Layer
	    size: 100
	 
	layer.midPoint = path.start
	layer.animate
	    point: path
	    rotation: path
	 
	# Shorthand for doing all of the above steps 
	layer.animate
	    path: path

<a id="length"></a>
## path.length &lt;number&gt;
路径长度。（只读）
>The length of the path. (Read-only)

	print path.length
	# Output: 450 

<a id="width"></a>
# path.width  &lt;number&gt;
路径宽度。（只读）
>The width of the path. (Read-only)

	print path.width
	# Output: 150 

<a id="height"></a>
# path.height  &lt;number&gt;
路径高度。（只读）
The height of the path. (Read-only)

	print path.height
	# Output: 75 

<a id="start"></a>
# path.start(relativeToLayer)
返回路径的起始位置坐标和角度。如果你传入了一个图层作为参数，那么返回的坐标就是以这个图层为参考系，否则的话以其父图层作为参考系。
>Returns the location and rotation of the start of the path. Pass a layer as final argument to get the coordinates for that layer. If no layer is passed, the coordinates will be for the current context.

	print path.start()
	# {x:0, y:0, rotation:90} 
	 
	# Shorthand to set the location of a layer to the start of the path 
	layer.point = path.start

<a id="end"></a>
# path.end(relativeToLayer)
返回路径的结束位置坐标和角度。如果你传入了一个图层作为参数，那么返回的坐标就是以这个图层为参考系，否则的话以其父图层作为参考系。
>Returns the location and rotation of the end of the path. Pass a layer as final argument to get the coordinates in that layer. If no layer is passed, the coordinates will be for the current context.

	print path.end()
	# {x:0, y:0, rotation:0} 
	 
	# Shorthand to set the location of a layer to the end of the path 
	layer.point = path.end

<a id="pointAtFraction"></a>
# path.pointAtFraction(fraction)
获取路径对应比例（ 0 到 1 ）长度处的坐标，该坐标是相对于这个路径的。
>Get the location of a point along a fraction (value from 0 to 1) of the path, relative to the position of the path.

	point = path.pointAtFraction(0.5)
	print point.x, point.y
	# Output: 150, 75 

<a id="rotationAtFraction"></a>
# path.rotationAtFraction(fraction, delta)
路径线条对应比例（ 0 到 1 ）处的角度，另一个可选参数是计算角度的偏差。
>Get the angle of the line at a fraction (value from 0 to 1) of the path. The optional second argument is the offset used to calculate the angle.

	print path.rotationAtFraction(0.5)
	# Output: -90 

<a id="fill"></a>
# path.fill &lt;string&gt;
设置路径填充色。
>Sets the fill color of the path.

	path.fill = "#FFF"

<a id="stroke"></a>
# path.stroke &lt;string&gt;
设置路径的描边颜色。
>Sets the stroke color of the path.

	path.stroke = "#0AF"

<a id="strokeWidth"></a>
# path.strokeWidth  &lt;number&gt;
设置路径的描边宽度。
>Sets the stroke width of the path.

	path.strokeWidth = 10

<a id="strokeStart"></a>
# path.strokeStart  &lt;number&gt;
设置路径的描边起始点。
>Set the start position of where to draw the stroke on the path.

	# Only stroke the last half of the path 
	path.strokeStart = path.length / 2

<a id="strokeEnd"></a>
# path.strokeEnd  &lt;number&gt;
设置路径的描边结束点。
>Set the end position of where to stop drawing the stroke on the path.

	# Only stroke the first half of the path 
	path.strokeEnd = path.length / 2

<a id="strokeLength"></a>
# path.strokeLength  &lt;number&gt;
设置路径的描边长度。
>Set the length of the stroke of the path.

	path.strokeLength = 200

<a id="strokeFraction"></a>
# path.strokeFraction  &lt;number&gt;
设置路径的描边长度比例，是 `strokeLength` 的一种简写。
>Set the stroke length to a fraction of the total length of the path. Shorthand for strokeLength.

	# Set the stroke length to half of the total length 
	# Same as path.strokeLength = path.length / 2 
	path.strokeFraction = 0.5

<a id="strokeLinecap"></a>
# path.strokeLinecap &lt;string&gt;
设置描边的两端样式。
>Set the line-cap of the stroke.

你可以选择 `butt` 、`round` 、`square` 中的一个。
>You can choose between butt, round and square.

	# Multiple types of line caps 
	shape.strokeLinecap = "butt"
	shape.strokeLinecap = "round"
	shape.strokeLinecap = "square"

<a id="strokeLinejoin"></a>
# path.strokeLinejoin &lt;string&gt;
设置描边的拐角样式。
>Set the line-join of the stroke.

你可以选择 `miter` 、`round` 、`bevel` 中的一个。
>You can choose between miter, round and bevel.

	# Multiple types of line joins 
	shape.strokeLinejoin = "miter"
	shape.strokeLinejoin = "round"
	shape.strokeLinejoin = "bevel"

<a id="strokeMiterlimit"></a>
# path.strokeMiterlimit  &lt;number&gt;
设置斜切限制，只在 `strokeLinejoin` 是 `miter` 时起作用。
>Set the miter limit of the stroke. Only works when strokeLinejoin is set to miter.

	star.strokeMiterlimit = 1

<a id="strokeOpacity"></a>
# path.strokeOpacity  &lt;number&gt;
设置描边不透明度，它的值是从 0 到 1 ，0 表示不可见，1 表示完全可见。
>Sets the stroke opacity. Opacity is defined with a number between 0 and 1, where 0 is invisible and 1 fully opaque.

	path.opacity = 0.5

<a id="strokeDasharray"></a>
# path.strokeDasharray &lt;array&gt;
给描边设置更加精细的虚线图案，可以看[MDN 的示例](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/stroke-dasharray)了解更多细节。
>Sets the stroke to have a certain pattern. See MDN’s examples for more details.

	path.strokeDasharray = [5, 5, 10, 10]

<a id="strokeDashoffset"></a>
# path.strokeDashoffset  &lt;number&gt;
设置虚线间隔宽度，当你想做虚线动画时很有用。
>The offset of the dash-pattern set by strokeDasharray. Useful for animating a dashed pattern.

	path.stroke = "#000"
	path.strokeDasharray = [10, 10]
	path.animate
	    strokeDashoffset: path.length

