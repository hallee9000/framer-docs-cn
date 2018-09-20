# SVGGroup
The SVGGroup allows you to modify SVG groups targeted form Design. Set fill, stroke, strokeWidth.

An SVGGroup should not be created in code. The only way to get an SVGGroup is through the elements property of SVGLayer

	svg = new SVGLayer
	    svg: """
	    <svg>
	      <g id='group' name='Container'>
	        <path id='shape' name='Rectangle' d='M0 0 H 150 V 75 H 0 L 0 0' />
	      </g>
	    </svg>
	    """

	group = svg.elements.group

All properties set on an SVGGroup will be set on the containing paths. When using a property from a group, it will return the value of the underlying SVGPath properties, or null if the underlying SVGPaths have different values for that property.

<a id="fill"></a>
## group.fill &lt;string&gt;
Sets the fill color of all the paths contained in the group.

	group.fill = "#FFF"

<a id="stroke"></a>
## group.stroke &lt;string&gt;
Sets the stroke color of all the paths contained in the group.

	group.stroke = "#0AF"

<a id="strokeWidth"></a>
## group.strokeWidth &lt;number&gt;
Sets the stroke width of all the paths contained in the group.

	group.strokeWidth = 10

