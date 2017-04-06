# TextLayer

A TextLayer allows you to work with type in Framer. Define text within a string, and use its unique properties to style it. Almost all property names match the CSS text styles. You can change the typeface, change the style, adjust the line height, add padding, shadows and much more.

## text.text <string>

The text content. By default, the color is set to #888.

    # Create a TextLayer 
    title = new TextLayer
        text: "Title"

## text.fontSize <number>

The size of the text. By default, it's set to 40.

# Set fontSize to 64px 
title = new TextLayer
    fontSize: 64

text.fontFamily <string>

The current typeface of the text. By default, it's set to use the system typeface of the device you're currently previewing on.

Apple Device: SF UI.
Google Device: Roboto.
Microsoft Device: Segoe UI.
# Create a TextLayer 
title = new TextLayer
    fontFamily: "-apple-system"

text.fontWeight <number>

The weight of the text. By default, it's set to 400.

# Create a TextLayer 
title = new TextLayer
    fontWeight: 400

text.fontStyle <string>

The style of the text.

# Set font style to italic 
title = new TextLayer
    fontStyle: "italic"

You can choose between italic, bold and oblique.

# Set font style to bold 
title = new TextLayer
    fontStyle: "bold"

text.font <string>

A shorthand to define all font styles using a single line. These properties can be set (in order): "fontStyle fontWeight fontSize/lineHeight fontFamily".

# Set font styles in one line 
title = new TextLayer
    font: "300 64px/1 -apple-system, Helvetica Neue"

Note that the fontSize and fontFamily properties are required.

# Set font size and font family 
title = new TextLayer
    font: "64px -apple-system"

text.padding <object>

The padding of the text. By default, it's set to 0.

# Set padding 
title = new TextLayer
    padding: 40

You can also define padding of each side individually.

# Set padding of each side 
title = new TextLayer
    padding:
        top: 40
        left: 20
        bottom: 40
        right: 20

Left and right padding can be defined by using the horizontal shorthand. Top and bottom padding can also be defined using the vertical shorthand.

# Set horizontal and vertical padding 
title = new TextLayer
    padding:
        horizontal: 40
        vertical: 80

text.lineHeight <number>

The line height of the text. By default, it's set to 1.25. This means that if you've set the fontSize to 40, the line-height will effectively be 50px.

# Set line-height 
title = new TextLayer
    lineHeight: 1.5

text.letterSpacing <number>

The letter spacing of the text in pixels. Set to 0 by default.

# Set letter spacing 
title = new TextLayer
    letterSpacing: 2

text.wordSpacing <number>

The letter spacing of the words in pixels. Set to 0 by default.

# Set word spacing 
title = new TextLayer
    wordSpacing: 10

text.textAlign <string>

The alignment of the text.

# Center-align the text 
title = new TextLayer
    textAlign: "center"

You can choose between left, right and center.

# Multiple ways to align text 
title.textAlign = "left"
title.textAlign = "right"
title.textAlign = "center"

Alternatively, you can also use the Align class.

# Center-align the text 
title = new TextLayer
    textAlign: Align.center

text.textTransform <string>

The capitalization of the text.

# Uppercase all characters 
title = new TextLayer
    textTransform: "uppercase"

You can choose between uppercase, lowercase and capitalize.

# Multiple ways to capitalize text 
title.textTransform = "uppercase"
title.textTransform = "lowercase"
title.textTransform = "capitalize"

text.textDecoration <string>

The decoration of the text.

# Add an underline to the text 
title = new TextLayer
    textDecoration: "underline"

You can choose between underline, overline and line-through.

# Add an overline to the text 
title = new TextLayer
    textDecoration: "overline"

text.textIndent <number>

The indentation of the first paragraph of text in pixels.

# Indent the text by 20 pixels 
title = new TextLayer
    textIndent: 20

text.textOverflow <string>

Add an ellipsis to overflowing text content.

# Single line clipping 
paragraph = new TextLayer
    textOverflow: "ellipsis"
    text:
        """
        Lorem ipsum dolor sit amet, consectetur adipiscing elit,
        sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
        """

If you set the height, you’ll be able to add an ellipsis to multiple lines.

# Multi line clipping 
paragraph = new TextLayer
    textOverflow: "ellipsis"
    height: 100
    text:
        """
        Lorem ipsum dolor sit amet, consectetur adipiscing elit,
        sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
        """

text.direction <string>

The direction of the text. The direction of the text. Set to left-to-right by default.

# Set the text direction 
title = new TextLayer
    direction: "right-to-left"

You can choose between right-to-left (rtl) and left-to-right (ltr).

# Set the text direction 
title = new TextLayer
    direction: "rtl"

text.truncate <boolean>

A shorthand of setting textOverflow to "ellipsis".

# Single line clipping 
paragraph = new TextLayer
    truncate: true
    text:
        """
        Lorem ipsum dolor sit amet, consectetur adipiscing elit,
        sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
        """

If you set the height, you’ll be able to add an ellipsis to multiple lines.

# Multi line clipping 
paragraph = new TextLayer
    truncate: true
    height: 100
    text:
        """
        Lorem ipsum dolor sit amet, consectetur adipiscing elit,
        sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
        """

text.shadowX <number>

Defines the shadow direction on the x-axis. A positive value will produce a shadow from the right edge of a layer, whereas a negative value will produce a shadow from the left edge.

# Set horizontal text shadow 
title = new TextLayer
    shadowX: 10

text.shadowY <number>

Defines the shadow direction on the y-axis. A positive value will produce a shadow from the bottom edge of a layer, whereas a negative value will produce a shadow from the top edge.

# Set vertical text shadow 
title = new TextLayer
    shadowY: 10

text.shadowBlur <number>

Adds a gaussian blur to the shadowX or shadowY property. shadowBlur is defined with a number. The default value is 0.

# Set text shadow 
title = new TextLayer
    shadowY: 1
    shadowBlur: 4

text.shadowColor <string>

Sets the color of a layers shadow. The color is expressed as a string in the CSS color format.

# Set text shadow and color 
title = new TextLayer
    shadowY: 10
    shadowColor: "rgba(0,0,0,0.2)"

