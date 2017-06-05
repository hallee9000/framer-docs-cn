# TextLayer

`TextLayer`可以帮助你在 Framer 中更加方便地进行文字排版。你可以使用一个字符串来定义文字内容，并使用它的一些特有属性来渲染它的样式。几乎所有的文字图层属性都能在 CSS 中找到，你可以改变字体、改变样式、调整行高、添加内边距或阴影等等。
>A TextLayer allows you to work with type in Framer. Define text within a string, and use its unique properties to style it. Almost all property names match the CSS text styles. You can change the typeface, change the style, adjust the line height, add padding, shadows and much more.


<a id="textLayer.text"></a>
## text.text &lt;string&gt;

文本图层的文字内容，默认情况下它的颜色是 `#888`。
>The text content. By default, the color is set to #888.

    # 创建一个文字图层
    title = new TextLayer
        text: "Title"


<a id="textLayer.fontSize"></a>
## text.fontSize &lt;number&gt;

设置文本图层的字号，默认是 40 像素。
>The size of the text. By default, it's set to 40.

    # 设置字号为64px 
    title = new TextLayer
        fontSize: 64


<a id="textLayer.fontFamily"></a>
## text.fontFamily &lt;string&gt;

设置当前字体。默认情况下，它会使用你预览设备的系统字体。
>The current typeface of the text. By default, it's set to use the system typeface of the device you're currently previewing on.

* **Apple设备** : SF UI.
* **Google设备** : Roboto.
* **Microsoft设备** : Segoe UI.


    # 创建一个文字图层 
    title = new TextLayer
        fontFamily: "-apple-system"


<a id="textLayer.fontWeight"></a>
## text.fontWeight &lt;number&gt;

字体的粗细，默认是 400 。
>The weight of the text. By default, it's set to 400.

    # 创建一个文字图层 
    title = new TextLayer
        fontWeight: 400


<a id="textLayer.fontStyle"></a>
## text.fontStyle &lt;string&gt;

设置字体的风格。
>The style of the text.

    # 设置字体为斜体风格
    title = new TextLayer
        fontStyle: "italic"

你可以选择`italic`、`bold`和`oblique`。
>You can choose between italic, bold and oblique.

* **italic**  会显示一个斜体的字体样式。
* **bold** 会显示一个加粗的字体样式。
* **oblique** 会显示一个倾斜的字体样式。


    # 设置字体为加粗风格
    title = new TextLayer
        fontStyle: "bold"


<a id="textLayer.font"></a>
## text.font &lt;string&gt;

在一行内定义字体的所有属性。你可以站照这样的顺序写："fontStyle fontWeight fontSize/lineHeight fontFamily"。
>A shorthand to define all font styles using a single line. These properties can be set (in order): "fontStyle fontWeight fontSize/lineHeight fontFamily".

    # 在一行内设置字体样式属性
    title = new TextLayer
        font: "300 64px/1 -apple-system, Helvetica Neue"

需要注意的是`fontSize`和`fontFamily`是必须要写的。
>Note that the fontSize and fontFamily properties are required.

    # 设置字号和字体
    title = new TextLayer
        font: "64px -apple-system"


<a id="textLayer.padding"></a>
## text.padding &lt;object&gt;

文字图层内边距，默认是 0 。
>The padding of the text. By default, it's set to 0.

    # 设置内边距
    title = new TextLayer
        padding: 40

你也可以给每个方向独立设置不同的内边距。
>You can also define padding of each side individually.

    # 给每个方向设置内边距
    title = new TextLayer
        padding:
            top: 40
            left: 20
            bottom: 40
            right: 20

当然你也可以使用简写方式：用`horizontal`设置左右内边距，用`vertical`设置上下内边距。
>Left and right padding can be defined by using the horizontal shorthand. Top and bottom padding can also be defined using the vertical shorthand.

    # 设置左右和上下内边距
    title = new TextLayer
        padding:
            horizontal: 40
            vertical: 80


<a id="textLayer.lineHeight"></a>
## text.lineHeight &lt;number&gt;

文字图层的行高，默认情况下是 1.25 倍。也就是说，当你设置字号为 40px 时，行高就是 50px 。
>The line height of the text. By default, it's set to 1.25. This means that if you've set the fontSize to 40, the line-height will effectively be 50px.

    # 设置行高
    title = new TextLayer
        lineHeight: 1.5


<a id="textLayer.letterSpacing"></a>
## text.letterSpacing &lt;number&gt;

设置字间距，默认是 0 。
>The letter spacing of the text in pixels. Set to 0 by default.

    # 设置字间距
    title = new TextLayer
        letterSpacing: 2&gt;


<a id="textLayer.wordSpacing"></a>
## text.wordSpacing &lt;number&gt;

设置词间距，默认是 0 。
>The letter spacing of the words in pixels. Set to 0 by default.

    # 设置词间距
    title = new TextLayer
        wordSpacing: 10


<a id="textLayer.textAlign"></a>
## text.textAlign &lt;string&gt;

设置文字对齐方式。
>The alignment of the text.

    # 居中对齐文字 
    title = new TextLayer
        textAlign: "center"

你可以选择的对齐方式有`left`、`right`和`center`。
>You can choose between left, right and center.

    # 多种对齐方式
    title.textAlign = "left"
    title.textAlign = "right"
    title.textAlign = "center"

当然，你也可以使用`Align`对象。
>Alternatively, you can also use the Align class.

    # 居中对齐文字
    title = new TextLayer
        textAlign: Align.center


<a id="textLayer.textTransform"></a>
## text.textTransform &lt;string&gt;

设置字母大小写。
>The capitalization of the text.

    # 大写所有字母 
    title = new TextLayer
        textTransform: "uppercase"

你可以设置为`uppercase`、`lowercase`或`capitalize`。
>You can choose between uppercase, lowercase and capitalize.

    # 多种字母大小写形式
    title.textTransform = "uppercase"
    title.textTransform = "lowercase"
    title.textTransform = "capitalize"


<a id="textLayer.textDecoration"></a>
## text.textDecoration &lt;string&gt;

设置文字的修饰。
>The decoration of the text.

    # 给文字添加下划线
    title = new TextLayer
        textDecoration: "underline"

你可设置为`underline`、`overline`或`line-through`。
>You can choose between underline, overline and line-through.

    # 给文字添加上划线 
    title = new TextLayer
        textDecoration: "overline"


<a id="textLayer.textIndent"></a>
## text.textIndent &lt;number&gt;

设置首字缩进。
>The indentation of the first paragraph of text in pixels.

    # 首字缩进20像素
    title = new TextLayer
        textIndent: 20


<a id="textLayer.textOverflow"></a>
## text.textOverflow &lt;string&gt;

给溢出的文字添加省略号。
>Add an ellipsis to overflowing text content.

    # 单行截取
    paragraph = new TextLayer
        textOverflow: "ellipsis"
        text:
            """
            Lorem ipsum dolor sit amet, consectetur adipiscing elit,
            sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
            """

如果你设置了文字图层的高度，就可以给多行文字溢出的部分添加省略号。
>If you set the height, you’ll be able to add an ellipsis to multiple lines.

    # 多行截取
    paragraph = new TextLayer
        textOverflow: "ellipsis"
        height: 100
        text:
            """
            Lorem ipsum dolor sit amet, consectetur adipiscing elit,
            sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
            """


<a id="textLayer.direction"></a>
## text.direction &lt;string&gt;

文字方向，默认是从左向右。
>The direction of the text. The direction of the text. Set to left-to-right by default.

    # 设置文字方向
    title = new TextLayer
        direction: "right-to-left"

你可以设置为`right-to-left (rtl)`或`left-to-right (ltr)`。
>You can choose between right-to-left (rtl) and left-to-right (ltr).

    # 设置文字方向
    title = new TextLayer
        direction: "rtl"


<a id="textLayer.truncate"></a>
## text.truncate &lt;boolean&gt;

设置文字溢出显示省略号的简写。
>A shorthand of setting textOverflow to "ellipsis".

    # 单行截取
    paragraph = new TextLayer
        truncate: true
        text:
            """
            Lorem ipsum dolor sit amet, consectetur adipiscing elit,
            sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
            """

如果你设置了文字图层的高度，就可以给多行文字溢出的部分添加省略号。
>If you set the height, you’ll be able to add an ellipsis to multiple lines.

    #多行截取
    paragraph = new TextLayer
        truncate: true
        height: 100
        text:
            """
            Lorem ipsum dolor sit amet, consectetur adipiscing elit,
            sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
            """


<a id="textLayer.shadowX"></a>
## text.shadowX &lt;number&gt;

设置文字阴影在 x 轴方向的偏移，正值将会产生一个从右边缘伸出来的阴影，负值将会产生一个从左边缘伸出的阴影。
>Defines the shadow direction on the x-axis. A positive value will produce a shadow from the right edge of a layer, whereas a negative value will produce a shadow from the left edge.

    # 设置横向文字阴影。
    title = new TextLayer
        shadowX: 10


<a id="textLayer.shadowY"></a>
## text.shadowY &lt;number&gt;

设置文字阴影在 y 轴方向的偏移，正值将会产生一个从下边缘伸出来的阴影，负值将会产生一个从上边缘伸出的阴影。
>Defines the shadow direction on the y-axis. A positive value will produce a shadow from the bottom edge of a layer, whereas a negative value will produce a shadow from the top edge.

    # 设置纵向文字阴影
    title = new TextLayer
        shadowY: 10


<a id="textLayer.shadowBlur"></a>
## text.shadowBlur &lt;number&gt;

给文字阴影设置高斯模糊，它的只是一个数字，默认为 0 。
>Adds a gaussian blur to the shadowX or shadowY property. shadowBlur is defined with a number. The default value is 0.

    # 设置文字阴影 
    title = new TextLayer
        shadowY: 1
        shadowBlur: 4


<a id="textLayer.shadowColor"></a>
## text.shadowColor &lt;string&gt;

给文字阴影设置颜色，使用 CSS 颜色格式。
>Sets the color of a layers shadow. The color is expressed as a string in the CSS color format.

    # 设置文字阴影颜色
    title = new TextLayer
        shadowY: 10
        shadowColor: "rgba(0,0,0,0.2)"

