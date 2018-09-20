# SliderComponent

`SliderComponent` 可以帮你创建一个完全可自定义化的滑块，最常见的是 APP 中的音量调节器。你可以将它和其他图层关联起来，调整其它图层的数值属性（尺寸、位置等）。它是由三个图层组成的：滑槽（就是滑块本身 `SliderComponent` ），填充区 `fill` 和调节把手 `knob` 。
>The SliderComponent creates a fully customisable slider for you. With it, you can adjust any numeric value or layer property. It consists of three layers: the slider itself, the fill and the knob.

	# Create a SliderComponent  
	slider = new SliderComponent
	slider.center()

滑块组件的滑槽默认是浅灰色的带圆角的矩形条，填充区——也即划过的区域——是深灰色的。填充区的圆角和滑槽`slider`是相互关联的，所以只用给它们之一设置圆角。
>By default, the slider has a dark fill color, a light-gray backgroundColor and rounded corners with borderRadius. The radius of the fill automatically matches with that of the slider, so you only need to set it once.

	# Customize the appearance 
	slider.backgroundColor = "#ddd"
	slider.borderRadius = 4

<a id="knob"></a>
## slider.knob &lt;layer&gt;

滑块组件的调节把手。默认情况下，它是一个带着浅浅投影的圆形图层。
>The knob of the slider. By default, it's made circular using borderRadius and has a little bit of a drop shadow applied to it.

	# Create a SliderComponent  
	slider = new SliderComponent
	slider.center()
	 
	# Customize the appearance 
	slider.knob.shadowY = 2
	slider.knob.shadowBlur = 4
	slider.knob.borderRadius = 6

调节把手是可以拖动的，并且带着动量模拟。
>The knob is a draggable layer, with momentum enabled.

	# Disable momentum 
	slider.knob.draggable.momentum = false

<a id="knobSize"></a>
## slider.knobSize &lt;number&gt;

调节把手的尺寸，它可以自动调节把手的宽和高，默认值是 30 。
>The size of the knob. This automatically sets the width and height of the knob. The default value is 30.

	# Create a SliderComponent  
	slider = new SliderComponent
	slider.center()
	 
	# Change the size of the knob 
	slider.knobSize = 40

<a id="fill"></a>
## slider.fill &lt;layer&gt;

滑块组件的填充区域。它的宽度和高度是跟随着整个滑块组件的尺寸变化的，它的默认背景色是 `#333` 。
>The fill of the slider. The width and height are automatically updated, based on the size of the slider. By default, its backgroundColor is set to #333.

	# Create a SliderComponent  
	slider = new SliderComponent
	slider.center()
	 
	# Set the fill color to blue 
	slider.fill.backgroundColor = "#28affa"

<a id="min"></a>
## slider.min &lt;number&gt;

滑块组件的最小值，默认是 0 。
>The mininum value of the slider. Set to 0 by default.

	# Create a SliderComponent  
	slider = new SliderComponent
	slider.center()
	 
	# Set the minimum value 
	slider.min = -1

<a id="max"></a>
## slider.max &lt;number&gt;

滑块组件的最大值，默认是 1 。
>The maximum value of the slider. Set to 1 by default.

	# Create a SliderComponent  
	slider = new SliderComponent
	slider.center()
	 
	# Set the maximum value 
	slider.max = 2

<a id="value"></a>
## slider.value &lt;number&gt;

滑块组件的初始值，默认是 0.5 。
>The value of the slider. Set to 0.5 by default.

	# Create a SliderComponent  
	slider = new SliderComponent
	slider.center()
	 
	# Print the current value 
	print slider.value

你可以通过 `change:value` 事件来监听任意改变的值，所以你可以通过这个事件来随时接收滑块组件的值，并将这个值映射到其它图层的属性上，比如通过滑块组件来调节一个图层的透明度。
>You can listen to any value changes with the "change:value" event. This is useful for retreiving the value or mapping it to another layer property, like changing the opacity of a layer with the slider.

	slider.on "change:value", ->
	    print this.value

<a id="pointForValue"></a>
## slider.pointForValue(value)

该方法可以将一个滑块组件当前的值转化为相对于整个组件的坐标（`x`）。比如有一个范围是 `0` 到 `1` 的滑块组件，`pointForValue(0.5)` 将会返回滑块组件的中间坐标，当它的宽度是 200 时，返回的值是 100 。
>Takes a value and returns the corresponding point (x) within the slider. With a slider ranging from 0 to 1, the pointForValue(0.5) will be the center of the slider. With a width of 200, this will return 100.

	# Create a SliderComponent 
	slider = new SliderComponent
	    width: 200
	
	slider.center()
 
	# Print the point for a value of 0.5 
	print slider.pointForValue(0.5)
	# Returns 100 

<a id="valueForPoint"></a>
## slider.valueForPoint(value)

该方法和上面那个方法相反，是通过一个 `x` 坐标值来计算滑块的值。比如有一个宽度是 200 的滑块，那么当它的指的范围设定为 `0` 到 `1` 时，将会返回 `0.5` 。
>Takes a point and returns the corresponding value of the slider. With a width of 200, the valueForPoint(100) will be the center of the slider. With a slider ranging from 0 to 1, this will return 0.5.

	# Create a SliderComponent 
	slider = new SliderComponent
	    width: 200
	 
	slider.center()
	 
	# Print the value for the point 100 
	print slider.valueForPoint(100)
	# Returns 0.5 

<a id="animateToValue"></a>
## slider.animateToValue(value, animationOptions)

自动动画过渡到一个特定值。
>Automatically animate to a specific value.

### 参数

* **value** — 一个处于滑块组件范围间的数字值。
* **animationOptions** — 一个包含了动画曲线、时间、延迟和重复等属性的动画选项（可选）。


	# Create a SliderComponent 
	slider = new SliderComponent
	slider.center()
	 
	# Animate to 1 
	slider.animateToValue(1)
	 
	# Animate with a custom curve 
	slider.animateToValue(1, { curve: "spring(400,40,0)"})

