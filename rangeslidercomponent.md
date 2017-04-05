# RangeSliderComponent

The RangeSliderComponent creates a range slider with two knobs. You can use it to define and edit a numeric range, like a price filter. It consists of four layers: the slider itself, the fill, the minKnob and the maxKnob.

    # Create a range slider 
    range = new RangeSliderComponent
        x: Align.center
        y: Align.center

By default, the slider has a dark fill color, a light-gray backgroundColor and rounded corners with borderRadius. The radius of the fill automatically matches with that of the slider, so you only need to set it once.

# Customize the appearance 
range.backgroundColor = "#ddd"
range.borderRadius = 4

rangeSlider.min <number>

The mininum range of the slider. Set to 0 by default.

# Create a range slider 
range = new RangeSliderComponent
    x: Align.center
    y: Align.center
    min: 0
    max: 10

rangeSlider.max <number>

The maximum range of the slider. Set to 1 by default.

# Create a range slider 
range = new RangeSliderComponent
    x: Align.center
    y: Align.center
    min: 0
    max: 10

rangeSlider.minValue <number>

The minimum value of the slider. Set to 0 by default.

# Create a range slider 
range = new RangeSliderComponent
    x: Align.center
    y: Align.center
    minValue: 0

You can exclusively listen to minimum value changes.

range.onMinValueChange ->
    print range.minValue

You can also listen to any value changes using the Value Change event.

range.onValueChange ->
    print range.minValue, range.maxValue

rangeSlider.maxValue <number>

The maximum value of the slider. Set to 0.5 by default.

# Create a range slider 
range = new RangeSliderComponent
    x: Align.center
    y: Align.center
    maxValue: 0.5

You can exclusively listen to maximum value changes.

range.onMaxValueChange ->
    print range.maxValue

You can also listen to any value changes using the Value Change event.

range.onValueChange ->
    print range.minValue, range.maxValue

rangeSlider.knobSize <number>

The size of both knobs. This automatically sets the width and height of the minKnob and the maxKnob. The default value is 30.

# Create a range slider 
range = new RangeSliderComponent
    x: Align.center
    y: Align.center
 
# Change the size of the knobs 
range.knobSize = 40

rangeSlider.fill <layer>

The fill of the slider. The width and height are automatically updated, based on the size of the slider. By default, its backgroundColor is set to #333.

# Create a range slider 
range = new RangeSliderComponent
    x: Align.center
    y: Align.center
 
# Set the fill color to blue 
range.fill.backgroundColor = "#00AAFF"

rangeSlider.minKnob <layer>

The knob that influences the minimum value of the slider.

# Create a range slider 
range = new RangeSliderComponent
    x: Align.center
    y: Align.center

The minKnob is a draggable layer, with momentum enabled.

# Disable momentum 
range.minKnob.draggable.momentum = false

rangeSlider.maxKnob <layer>

The knob that influences the maximum value of the slider.

# Create a range slider 
range = new RangeSliderComponent
    x: Align.center
    y: Align.center

The maxKnob is a draggable layer, with momentum enabled.

# Disable momentum 
range.maxKnob.draggable.momentum = false

rangeSlider.animateToMinValue(minValue, animationOptions)

Automatically animate to a specific minimum value.

Arguments

minValue — A number, representing the minimum value.
animationOptions — An object with curve, time, delay and repeat properties. (Optional)
# Create a range slider 
range = new RangeSliderComponent
    x: Align.center
    y: Align.center
 
# Animate to 1 
range.animateToMinValue(0.3)
 
# Animate with a custom curve 
range.animateToMinValue(0.3, { curve: Spring })

rangeSlider.animateToMaxValue(maxValue, animationOptions)

Automatically animate to a specific maximum value.

Arguments

maxValue — A number, representing the maximum value.
animationOptions — An object with curve, time, delay and repeat properties. (Optional)
# Create a range slider 
range = new RangeSliderComponent
    x: Align.center
    y: Align.center
 
# Animate to 1 
range.animateToMaxValue(1)
 
# Animate with a custom curve 
range.animateToMaxValue(1, { curve: Spring })

