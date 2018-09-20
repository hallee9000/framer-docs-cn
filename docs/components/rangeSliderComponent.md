# RangeSliderComponent

范围组件可以使用两个把手来调节一个范围。你可以用它来定义或编辑一个数字范围，比如价格筛选。它由四个图层组成，滑槽（也即组件本身）、填充区、最大值把手和最小值把手。
>The RangeSliderComponent creates a range slider with two knobs. You can use it to define and edit a numeric range, like a price filter. It consists of four layers: the slider itself, the fill, the minKnob and the maxKnob.

    # Create a range slider 
    range = new RangeSliderComponent
        x: Align.center
        y: Align.center

范围组件的填充区（选中的范围）默认是深色的，滑槽是浅灰色的背景，整个滑槽的两侧是圆角。填充区的圆角和滑槽 `slider` 是相关联的，所以只用给它们之一设置圆角。
>By default, the slider has a dark fill color, a light-gray backgroundColor and rounded corners with borderRadius. The radius of the fill automatically matches with that of the slider, so you only need to set it once.

    # Customize the appearance 
    range.backgroundColor = "#ddd"
    range.borderRadius = 4

<a id="min"></a>
## rangeSlider.min &lt;number&gt;

范围组件的最小范围，默认值是 0 。
>The mininum range of the slider. Set to 0 by default.

    # Create a range slider 
    range = new RangeSliderComponent
        x: Align.center
        y: Align.center
        min: 0
        max: 10

<a id="max"></a>
## rangeSlider.max &lt;number&gt;

范围组件的最大范围，默认值是 1 。
>The maximum range of the slider. Set to 1 by default.

    # Create a range slider 
    range = new RangeSliderComponent
        x: Align.center
        y: Align.center
        min: 0
        max: 10

<a id="minValue"></a>
## rangeSlider.minValue &lt;number&gt;

范围组件的最小值，默认是 0 。
>The minimum value of the slider. Set to 0 by default.

    # Create a range slider 
    range = new RangeSliderComponent
        x: Align.center
        y: Align.center
        minValue: 0

你可以单独监听最小值的变化。
>You can exclusively listen to minimum value changes.

    range.onMinValueChange ->
        print range.minValue

你也可以同时使用 `Value` 改变事件监听范围变化。
>You can also listen to any value changes using the Value Change event.

    range.onValueChange ->
        print range.minValue, range.maxValue

<a id="maxValue"></a>
## rangeSlider.maxValue &lt;number&gt;

范围组件的最大值，默认是0.5 。
>The maximum value of the slider. Set to 0.5 by default.

    # Create a range slider 
    range = new RangeSliderComponent
        x: Align.center
        y: Align.center
        maxValue: 0.5

你可以单独监听最大值的变化。
>You can exclusively listen to maximum value changes.

    range.onMaxValueChange ->
        print range.maxValue

你也可以同时使用 `Value` 改变事件监听范围变化。
>You can also listen to any value changes using the Value Change event.

    range.onValueChange ->
        print range.minValue, range.maxValue

<a id="knobSize"></a>
## rangeSlider.knobSize &lt;number&gt;

两个把手的尺寸。它的值是两个把手的宽和高，默认是 30 。
>The size of both knobs. This automatically sets the width and height of the minKnob and the maxKnob. The default value is 30.

    # Create a range slider 
    range = new RangeSliderComponent
        x: Align.center
        y: Align.center
     
    # Change the size of the knobs 
    range.knobSize = 40

<a id="fill"></a>
## rangeSlider.fill &lt;layer&gt;

范围组件的填充区，它的宽和高是跟着整个范围组件自动变化的。它的默认背景色是 `#333` 。
>The fill of the slider. The width and height are automatically updated, based on the size of the slider. By default, its backgroundColor is set to #333.

    # Create a range slider 
    range = new RangeSliderComponent
        x: Align.center
        y: Align.center
     
    # Set the fill color to blue 
    range.fill.backgroundColor = "#00AAFF"

<a id="minKnob"></a>
## rangeSlider.minKnob &lt;layer&gt;

调节最小值的把手。
>The knob that influences the minimum value of the slider.

    # Create a range slider 
    range = new RangeSliderComponent
        x: Align.center
        y: Align.center

它是一个可拖动的图层，带着动量模拟。
>The minKnob is a draggable layer, with momentum enabled.

    # 禁止动量模拟
    range.minKnob.draggable.momentum = false

<a id="maxKnob"></a>
## rangeSlider.maxKnob <layer>

调节最大值的把手。
>The knob that influences the maximum value of the slider.

    # Create a range slider 
    range = new RangeSliderComponent
        x: Align.center
        y: Align.center

它是一个可拖动的图层，带着动量模拟。
>The maxKnob is a draggable layer, with momentum enabled.

    # 禁止动量模拟
    range.maxKnob.draggable.momentum = false

<a id="animateToMinValue"></a>
## rangeSlider.animateToMinValue(minValue, animationOptions)

自动以动画形式调节到指定的最小值。
>Automatically animate to a specific minimum value.

### 参数

* **minValue** — 一个数字，指定的最小值。
* **animationOptions** — 一个动画选项对象，包含动画曲线、时间、延迟和重复属性。（可选）


    # Create a range slider 
    range = new RangeSliderComponent
        x: Align.center
        y: Align.center
     
    # Animate to 1 
    range.animateToMinValue(0.3)
     
    # Animate with a custom curve 
    range.animateToMinValue(0.3, { curve: Spring })

<a id="animateToMaxValue"></a>
## rangeSlider.animateToMaxValue(maxValue, animationOptions)

自动以动画形式运动到指定最大值。
>Automatically animate to a specific maximum value.

### 参数

* **maxValue** — 一个数字，指定的最大值。
* **animationOptions** — 一个动画选项对象，包含动画曲线、时间、延迟和重复属性。（可选）


    # Create a range slider 
    range = new RangeSliderComponent
        x: Align.center
        y: Align.center
     
    # Animate to 1 
    range.animateToMaxValue(1)
     
    # Animate with a custom curve 
    range.animateToMaxValue(1, { curve: Spring })

