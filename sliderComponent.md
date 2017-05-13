SliderComponent

The SliderComponent creates a fully customisable slider for you. With it, you can adjust any numeric value or layer property. It consists of three layers: the slider itself, the fill and the knob.

# Create a SliderComponent  
slider = new SliderComponent
slider.center()

By default, the slider has a dark fill color, a light-gray backgroundColor and rounded corners with borderRadius. The radius of the fill automatically matches with that of the slider, so you only need to set it once.

# Customize the appearance 
slider.backgroundColor = "#ddd"
slider.borderRadius = 4

slider.knob <layer>

The knob of the slider. By default, it's made circular using borderRadius and has a little bit of a drop shadow applied to it.

# Create a SliderComponent  
slider = new SliderComponent
slider.center()
 
# Customize the appearance 
slider.knob.shadowY = 2
slider.knob.shadowBlur = 4
slider.knob.borderRadius = 6

The knob is a draggable layer, with momentum enabled.

# Disable momentum 
slider.knob.draggable.momentum = false

slider.knobSize <number>

The size of the knob. This automatically sets the width and height of the knob. The default value is 30.

# Create a SliderComponent  
slider = new SliderComponent
slider.center()
 
# Change the size of the knob 
slider.knobSize = 40

slider.fill <layer>

The fill of the slider. The width and height are automatically updated, based on the size of the slider. By default, its backgroundColor is set to #333.

# Create a SliderComponent  
slider = new SliderComponent
slider.center()
 
# Set the fill color to blue 
slider.fill.backgroundColor = "#28affa"

slider.min <number>

The mininum value of the slider. Set to 0 by default.

# Create a SliderComponent  
slider = new SliderComponent
slider.center()
 
# Set the minimum value 
slider.min = -1

slider.max <number>

The maximum value of the slider. Set to 1 by default.

# Create a SliderComponent  
slider = new SliderComponent
slider.center()
 
# Set the maximum value 
slider.max = 2

slider.value <number>

The value of the slider. Set to 0.5 by default.

# Create a SliderComponent  
slider = new SliderComponent
slider.center()
 
# Print the current value 
print slider.value

You can listen to any value changes with the "change:value" event. This is useful for retreiving the value or mapping it to another layer property, like changing the opacity of a layer with the slider.

slider.on "change:value", ->
    print this.value

slider.pointForValue(value)

Takes a value and returns the corresponding point (x) within the slider. With a slider ranging from 0 to 1, the pointForValue(0.5) will be the center of the slider. With a width of 200, this will return 100.

# Create a SliderComponent 
slider = new SliderComponent
    width: 200
 
slider.center()
 
# Print the point for a value of 0.5 
print slider.pointForValue(0.5)
# Returns 100 

slider.valueForPoint(value)

Takes a point and returns the corresponding value of the slider. With a width of 200, the valueForPoint(100) will be the center of the slider. With a slider ranging from 0 to 1, this will return 0.5.

# Create a SliderComponent 
slider = new SliderComponent
    width: 200
 
slider.center()
 
# Print the value for the point 100 
print slider.valueForPoint(100)
# Returns 0.5 

slider.animateToValue(value, animationOptions)

Automatically animate to a specific value.

Arguments

value — A number, ranging from the min to the max value.
animationOptions — An object with curve, time, delay and repeat properties. (Optional)
# Create a SliderComponent 
slider = new SliderComponent
slider.center()
 
# Animate to 1 
slider.animateToValue(1)
 
# Animate with a custom curve 
slider.animateToValue(1, { curve: "spring(400,40,0)"})

