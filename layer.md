# Layer

在Framer中图层是一个基本的容器，它可以包含图片、视频和文字。你可以使用固定数值把它放置在某个位置，也可以通过动态计算来放置它。图层包含很多可以决定其外观样式的属性，比如透明度、旋转角度和缩放比例等，你还可以通过嵌套来调整图层的层级。

创建图层使用`new`关键字，每个图层刚创建时都有一些默认属性：半透明黑色背景色，200×200的大小。

    layerA = new Layer

你可以在创建一个图层的时候定义它的一些属性：

    layerA = new Layer
        x: 100
        y: 100
        width: 250
        height: 250
        opacity: 0.5
        backgroundColor: "white"

也可以在后面覆盖它的某个属性：

    layerA = new Layer
        x: 100
        y: 100

    layerA.x = 200

<a id="layer.id"></a>
## layer.id &lt;number&gt;

id是一个图层的唯一身份标识，每一个图层的id都是不一样的。这个值是只读的，你改变不了它。

    layerA = new Layer
    print layerA.id
    # Output: 1

<a id="layer.name"></a>
## layer.name &lt;string&gt;

图层的名称，一般不会默认给图层命名。导入的图层将会继续使用你在Sketch或Photoshop中的命名。

    layerA = new Layer
    layerA.name = "Button"

    print layerA.name
    # Output: "Button"

<a id="layer.x"></a>
## layer.x &lt;number&gt;

x属性定义了图层水平方向相对于左上角的位置。

    layerA = new Layer
    layerA.x = 500

<a id="layer.y"></a>
## layer.y &lt;number&gt;

y属性定义了图层垂直方向相对于左上角的位置。

    layerA = new Layer
    layerA.y = 500

<a id="layer.z"></a>
## layer.z &lt;number&gt;

z属性定义了图层在空间里的位置，即我们常说的纵深。它的值越大，距离消失点就越远。

记住你需要开启它父图层的`perspective`，这样你才能看到效果。同时你还要注意`z`属性和`layer.index`是不一样的，`layer.index`是当两个图层具有相同的`z`属性时用来定义他们的前后顺序的。

    layerA = new Layer
    layerA.z = 500

<a id="layer.width"></a>
## layer.width &lt;number&gt;

图层的宽度像素值。

    layerA = new Layer
    layerA.width = 500

<a id="layer.height"></a>
## layer.height &lt;number&gt;

图层的高度像素值。

    layerA = new Layer
    layerA.height = 500

<a id="layer.minX"></a>
## layer.minX &lt;number&gt;

图层左边缘的横坐标，和`layer.x`相同。

    layerA = new Layer
        x: 100
        y: 100
        width: 100
        height: 100

    print layerA.minX
    # Output: 100

<a id="layer.midX"></a>
## layer.midX &lt;number&gt;

图层中心点横坐标。

    layerA = new Layer
        x: 100
        y: 100
        width: 100
        height: 100

    print layerA.midX
    # Output: 150

    layerA.midX = 500
    print layerA.x
    # Output: 450

<a id="layer.maxX"></a>
## layer.maxX &lt;number&gt;

图层右边缘横坐标。

    layerA = new Layer
        x: 100
        y: 100
        width: 100
        height: 100

    print layerA.maxX
    # Output: 200

    layerA.maxX = 500
    print layerA.x
    # Output: 400

<a id="layer.minY"></a>
## layer.minY &lt;number&gt;

图层上边缘纵坐标，和`layer.y`相同。

    layerA = new Layer
        x: 100
        y: 100
        width: 100
        height: 100

    print layerA.minY
    # Output: 100

<a id="layer.midY"></a>
## layer.midY &lt;number&gt;

图层中心点纵坐标。

    layerA = new Layer
        x: 100
        y: 100
        width: 100
        height: 100

    print layerA.midY
    # Output: 150

    layerA.midY = 500
    print layerA.y
    # Output: 450

<a id="layer.maxY"></a>
## layer.maxY &lt;number&gt;

图层下边缘纵坐标。

    layerA = new Layer
        x: 100
        y: 100
        width: 100
        height: 100

    print layerA.maxY
    # Output: 200

    layerA.maxY = 500
    print layerA.y
    # Output: 400

<a id="layer.point"></a>
## layer.point &lt;object&gt;

你可以通过该属性来获取或设定图层的坐标。

    layerA = new Layer

    print layerA.point
    # Output: { x: 0, y: 0 }

    layerA.point =
        x: 10
        y: 200

    print layerA.point
    # Output: { x: 10, y: 200 }

    print layerA.x
    # Output: 10

<a id="layer.size"></a>
## layer.size &lt;object&gt;

你可以通过该属性来获取或设定图层的长和宽。

    layerA = new Layer

    print layerA.size
    # Output: { width: 100, height: 100 }

    layerA.size =
        width: 10
        height: 10

    print layerA.size
    # Output: { width: 10, height: 10 }

    print layerA.width
    # Output: 10

<a id="layer.frame"></a>
## layer.frame &lt;object&gt;

你可以通过该属性来获取或设定图层的坐标和长宽。

    layerA = new Layer

    print layerA.frame
    # Output: { x: 100, y: 100, width: 100, height: 100 }

    layerA.frame =
        x: 10
        y: 200
        width: 10
        height: 10

    print layerA.frame
    # Output: { x: 10, y: 200, width: 10, height: 10 }

    print layerA.x
    # Output: 10

<a id="layer.props"></a>
## layer.props &lt;object&gt;

获取或者设定图层的所有属性。

    layerA = new Layer

    # Get current layer properties
    print layerA.props
    # Output: { x: 100, y: 100, ...}

    # Set properties
    layerA.props =
        rotation: 90
        opacity: 0.5

<a id="layer.center"></a>
## layer.center()

将图层在其父图层中水平垂直居中放置。如果它没有父图层，就相对与屏幕。

    layerA = new Layer
        width: 500
        height: 500

    layerB = new Layer
        parent: layerA
        width: 100
        height: 100

    layerB.center()

    print layerB.x, layerB.y
    # Output: 200, 200

<a id="layer.centerX"></a>
## layer.centerX(offset)

将图层相对于其父图层水平居中，如果没有父图层则相对与屏幕。参数`offset`代表从中间水平偏移的像素值，它是可选的。

### 参数

* **offset** — 一个代表偏移量的数字。


    layerA = new Layer
        width: 500
        height: 500

    layerB = new Layer
        parent: layerA
        width: 100
        height: 100

    layerB.centerX()
    print layerB.x, layerB.y
    # Output: 200, 0

    layerB.centerX(20)
    print layerB.x, layerB.y
    # Output: 220, 0

<a id="layer.centerY"></a>
## layer.centerY(offset)

将图层相对于其父图层垂直居中，如果没有父图层则相对与屏幕。参数`offset`代表从中间垂直偏移的像素值，它是可选的。

### 参数

* **offset** — 一个代表偏移量的数字。


    layerA = new Layer
        width: 500
        height: 500

    layerB = new Layer
        parent: layerA
        width: 100
        height: 100

    layerB.centerY()
    print layerB.x, layerB.y
    # Output: 0, 200

    layerB.centerY(20)
    print layerB.x, layerB.y
    # Output: 0, 220

<a id="layer.pixelAlign"></a>
## layer.pixelAlign()

将x和y的值四舍五入进行像素对齐，当[动态地将图层置于中心](#layer.center)时很有用。
>Round the x and y values of this layer to whole numbers. Allows you to snap layers on the pixel. This is useful when dynamically centering layers.


    layerA = new Layer
        x: 100.18293
        y: 10.12873

    layerA.pixelAlign()

    print layerA.x, layerA.y
    # Output: 100, 10

<a id="layer.screenFrame"></a>
## layer.screenFrame &lt;object&gt;

该方法可以帮助你获取或设置一个图层相对于屏幕的绝对位置信息，它会忽略层级之间的相对位置关系。
>Allows you to set or capture the absolute position of this layer on the screen, ignoring the inherited position from its parents.

    layerA = new Layer
        x: 100

    layerB = new Layer
        parent: layerA
        x: 100

    print layerB.screenFrame
    # Output: { x: 200, y: 0, width: 100, height: 100 }

    layerB.screenFrame =
        x: 400
        y: 0
        width: 100
        height: 100

    print layerB.x
    # Output: 300

<a id="layer.contentFrame"></a>
## layer.contentFrame()

计算一个图层包含其子图层的的位置尺寸信息。
>The calculated frame for the total size of all the children combined.

    layerA = new Layer
    layerB = new Layer
        parent: layerA
        x: 0
        width: 100

    layerC = new Layer
        parent: layerA
        x: 100
        width: 300

    print layerA.contentFrame()
    # Output: { x: 0, y: 0, width: 400, height: 100 }

<a id="layer.centerFrame"></a>
## layer.centerFrame()

将一个图层水平垂直居中于其父图层（若没有父图层就是屏幕）同时计算此时该图层的位置尺寸信息。
>The calculated frame, centered within its parent. If there is no parent, it will be centered relative to the screen.

    layerA = new Layer
        width: 500
        height: 500

    layerB = new Layer
        parent: layerA
        width: 100
        height: 100

    print layerB.centerFrame()
    # Output: { x: 200, y: 200, width: 100, height: 100 }

<a id="layer.backgroundColor"></a>
## layer.backgroundColor &lt;string&gt;

设置图层背景色，色值是一个[CSS颜色格式](https://developer.mozilla.org/en-US/docs/Web/CSS/color)，所有图层都默认为浅灰色背景。
>Sets the background color for this layer. The color is expressed as a string in the CSS color format. Layers have a light grey background color by default.

    layerA = new Layer

    layerA.backgroundColor = "red"
    layerA.backgroundColor = "#00ff00"
    layerA.backgroundColor = "rgba(134, 12, 64, 0.3)"
    layerA.backgroundColor = "transparent"

    # Remove the background color
    layerA.backgroundColor = ""

<a id="layer.color"></a>
## layer.color &lt;string&gt;

设置图层文字颜色，色值是一个[CSS颜色格式](https://developer.mozilla.org/en-US/docs/Web/CSS/color)，所有文字默认为白色。
>Sets the text color for this layer. The color is expressed as a string in the CSS color format. Layers have a white text color by default.

    layerA = new Layer

    layerA.color = "red"
    layerA.color = "#00ff00"
    layerA.color = "rgba(134, 12, 64, 0.3)"
    layerA.color = "transparent"

    # Remove the color
    layerA.color = ""

<a id="layer.image"></a>
## layer.image &lt;string&gt;

设置一个图层的背景图片，你可以写一个本地文件路径或者完整的图片链接。背景图片会自动适应、完全覆盖该图层，并且不会被随意拉伸。如果你想取消该背景图层可以设置其值为空字符串或者`null`。
>Sets the background-image url or path for this layer. You can set it as a local path or a full url. The image will always fit to cover the layer, and will never be stretched. You can remove an image by setting it to null or an empty string.

    # Local images
    layerA = new Layer
        image: "images/logo.png"

    # Hosted images
    layerA.image = "http://framerjs.com/logo.png"

设置图片背景之后原来的默认背景色就会被覆盖掉，但是再次设置一个背景色就会显示在图片后面（透明背景图片后面可以看见这个颜色）。
>Setting an image will remove the default background color of a layer. Set the background color to another color than the default to show it behind the image.

    # Show a color where the image is transparent
    layerA = new Layer
        image: "images/logo.png"
        backgroundColor: "blue"

你可以通过`Events.ImageLoaded`事件来检测图片是否加载完成并可以显示，如果加载出错（比如找不到图片）它将会抛出`Events.ImageLoadError`，你可以监听该事件来发现错误。
>You can be notified of when an image is loaded and ready to display with the Events.ImageLoaded event. If there is an error loading an image (like not found) it will throw an Events.ImageLoadError event.

    layerA = new Layer
        image: "images/logo.png"

    # Listen to the loading event
    layerA.on Events.ImageLoaded, ->
        print "The image loaded"

    layerA.on Events.ImageLoadError, ->
        print "The image couldn't be loaded"

<a id="layer.visible"></a>
## layer.visible &lt;boolean&gt;

设置图层是否可见。
>Sets whether the layer should be visible or not.

layerA = new Layer
layerA.visible = false

<a id="layer.opacity"></a>
## layer.opacity &lt;string&gt;

设置图层透明度。透明度的值是一个0到1之间的数字，0表示不可见而1表示完全不透明。
>Sets the opacity for this layer. Opacity is defined with a number between 0 and 1 where 0 is invisible and 1 fully opaque.

    layerA = new Layer
    layerA.opacity = 0.5

<a id="layer.clip"></a>
## layer.clip &lt;boolean&gt;

设置一个图层是否对其子图层进行裁切，如果裁切超出该图层范围部分不显示，默认是不裁切。
>Sets whether the layer should clip its children. Clipping is disabled by default.

    layerA = new Layer
        width: 100
        height: 100

    layerB = new Layer
        width: 200
        height: 200
        parent: layerA

    layerA.clip = true

<a id="layer.ignoreEvents"></a>
## layer.ignoreEvents &lt;boolean&gt;

启用或禁用一个图层的任意用户事件，当开启忽略事件时，图层将不会响应任何事件。默认情况下是`true`即不监听任何事件，当你给图层添加事件监听时Framer会自动把它的值设置为`false`即不忽略事件从而监听事件。
>Enable or disable any user events added to layers. When disabled, no user events on the layer will be emitted. The default value for this is true. Framer automatically disables it when you add an event listener.

    layerA = new Layer

    layerA.on Events.Click, ->
        print "Click!"

    # Now it won't respond to a click
    layerA.ignoreEvents = true

    # Now it will
    layerA.ignoreEvents = false

<a id="layer.originX"></a>
## layer.originX &lt;number&gt;

设置缩放、旋转和斜切的横向变换中心，它的值是一个数字，0表示以最左边为变换中心，1表示以最右边为变换中心，默认值是0.5，即图层的水平中心。
>Sets the x origin for scale, rotate and skew transformations. The origin is defined as a number, where 0 is the left edge of the layer and 1 the right edge. The default value is 0.5, the center of the layer.

    layerA = new Layer
    layerA.rotation = 45
    layerA.originX = 0
    layerA.originX = 1

<a id="layer.originY"></a>
## layer.originY &lt;number&gt;

设置缩放、旋转和斜切的纵向变换中心，它的值是一个数字，0表示以最顶部为变换中心，1表示以最底部为变换中心，默认值是0.5，即图层的垂直中心。
>Sets the y origin for scale, rotate and skew transformations. The origin is defined as a number, where 0 is the top edge of the layer and 1 the bottom edge. The default value is 0.5, the center of the layer.

    layerA = new Layer
    layerA.rotation = 45
    layerA.originY = 0
    layerA.originY = 1

<a id="layer.originZ"></a>
## layer.originZ &lt;number&gt;

设置3D变换z轴中心，它的值是一个像素值，正数表示图层在3D空间中更靠近你，负数表示远离你。
>Sets the z origin for 3D transformations. The origin is defined in pixels. Positive values bring 3D layers closer to you, and negative values further way.

    layerA = new Layer
        originZ: -45
        rotationY: 90

<a id="layer.perspective"></a>
## layer.perspective &lt;number&gt;

给子图层设置透视。对于一些类似于`rotationX`、`rotationY`的3D属性来说，不同的透视让它们在3D空间里有不同的纵深感。`perspective`的值是从1到无穷大，当它为1时透视感十分强烈；当它为0时就是一个和没设置透视时一样的效果。Framer默认没有开启透视。（想象一下一支铅笔一头对着自己的眼睛由远到近透视感越来越强的感觉）
>Sets the perspective for child layers. Perspective gives depth to 3d properties like rotationX, rotationY. The rotation is set from 1 to Infinity where 1 is a huge perspective. Setting perspective to 0 gives you an isometric effect. Perspective is disabled by default.

    layerA = new Layer

    # Set the perspective for all sub layers
    layerA.perspective = 100

    layerB = new Layer
        parent: layerA
        rotationX: 30
        rotationY: 30

<a id="layer.flat"></a>
## layer.flat &lt;boolean&gt;

开启或禁用所有子图层的3D属性。
>Enable or disable 3D properties for all children of the layer.

    # Enable flat on its children
    layerA = new Layer
        width: 200
        height: 200
        x: 100
        y: 100
        clip: false
        flat: true

    # Rotate horizontally
    layerA.rotationX = 45

    # With flat enabled, adjusting z has no effect
    layerB = new Layer
        parent: layerA
        z: 25

<a id="layer.backfaceVisible"></a>
## layer.backfaceVisible &lt;boolean&gt;

定义一个图层没有面对屏幕时是否可见。如果你想让一个图层旋转180度之后的反面不可见就可以用将属性禁用。
>Defines whether a layer should be visible when not facing the screen. This is useful when an element is rotated, and you don't want to see its backside.

    layerA = new Layer
    layerA.backfaceVisible = false

<a id="layer.rotation"></a>
## layer.rotation &lt;number&gt;

设置一个图层相对于它的变换中心的旋转角度。它的范围是从0到360，默认是0，即不旋转。
>Sets the rotation, relative to its transform origin. The rotation is defined in degrees between 0 and 360. The default value is 0.

    layerA = new Layer
    layerA.rotation = 45

<a id="layer.rotationX"></a>
## layer.rotationX &lt;number&gt;

设置一个图层相对于它的变换中心绕x轴旋转角度。它的范围是从0到360，默认是0，即不旋转。
>Sets the x rotation, relative to its transform origin. The rotation is defined in degrees between 0 and 360. The default value is 0.

    layerA = new Layer
    layerA.rotationX = 45

<a id="layer.rotationY"></a>
## layer.rotationY &lt;number&gt;

设置一个图层相对于它的变换中心绕Y轴旋转角度。它的范围是从0到360，默认是0，即不旋转。
>Sets the y rotation, relative to its transform origin. The rotation is defined in degrees between 0 and 360. The default value is 0.

    layerA = new Layer
    layerA.rotationY = 45

<a id="layer.rotationZ"></a>
## layer.rotationZ &lt;number&gt;

设置一个图层相对于它的变换中心绕Z轴旋转角度。它的范围是从0到360，默认是0，即不旋转。它和`layer.rotation`一样。
>Sets the z rotation, relative to its transform origin. The rotation is defined in degrees between 0 and 360. Same as layer.rotation.

    layerA = new Layer
    layerA.rotationZ = 45

<a id="layer.scale"></a>
## layer.scale &lt;number&gt;

设置一个图层相对于变换中心的缩放倍数。默认缩放倍数是1，即原始大小。当这个数字变小时这个图层会跟着变小，反之亦然。
>Sets the scale, relative to its transform origin. The default scale is 1. Any number smaller then one will decrease the size and vice versa.

    layerA = new Layer
    layerA.scale = 2

<a id="layer.scaleX"></a>
## layer.scaleX &lt;number&gt;

设置一个图层水平方向相对于变换中心的缩放倍数。默认缩放倍数是1，即原始大小。当这个数字变小时这个图层会跟着变小，反之亦然。
>Sets the horizontal scale, relative to its transform origin. The default scale is 1. Any number smaller then one will decrease the size and vice versa.

    layerA = new Layer
    layerA.scaleX = 2

<a id="layer.scaleY"></a>
## layer.scaleY &lt;number&gt;

设置一个图层垂直方向相对于变换中心的缩放倍数。默认缩放倍数是1，即原始大小。当这个数字变小时这个图层会跟着变小，反之亦然。
>Sets the vertical scale, relative to its transform origin. The default scale is 1. Any number smaller then one will decrease the size and vice versa.

    layerA = new Layer
    layerA.scaleY = 2

<a id="layer.parent"></a>
## layer.parent &lt;Layer object&gt;

设置一个图层的父图层。如果你想将一个图层设置为顶层根图层，你可以将它的父图层设置为`null`。（别名：`superLayer`）
>Sets the parent for this layer. You can set the parent to null if you want the layer to live at the root of your document. (Alias: superLayer)

    layerA = new Layer
    layerB = new Layer

    layerB.parent = layerA

    print layerB.parent
    # Output: <Object:Layer layerA>

<a id="layer.children"></a>
## layer.children &lt;array&gt;

一个图层的所有子图层。（别名：`subLayers`）
>All the child layers of this layer. (Alias: subLayers)

    layerA = new Layer

    layerB = new Layer
        parent: layerA

    layerC = new Layer
        parent: layerA

    print layerA.children
    # Output: [<Object:Layer layerB>, <Object:Layer layerC>]

<a id="layer.childrenWithName"></a>
## layer.childrenWithName(name)

通过图层名称获取一个图层的子图层。（别名：`subLayersByName`）
>All child layers of this layer, filtered by name. (Alias: subLayersByName)

### 参数

* **name** — 表示图层名称的字符串。


    layerA = new Layer

    layerB = new Layer
        name: "navigation"
        parent: layerA

    layerC = new Layer
        name: "button"
        parent: layerA

    print layerA.childrenWithName("button")
    # Output: [<Object:Layer layerC>]

<a id="layer.siblings"></a>
## layer.siblings &lt;array&gt;

获取一个图层的所有兄弟图层。（别名: siblingLayers）
>All sibling layers of this layer. (Alias: siblingLayers)

    layerA = new Layer

    layerB = new Layer
        parent: layerA

    layerC = new Layer
        parent: layerA

    print layerA.siblings
    # Output: [<Object:Layer layerC>]

<a id="layer.siblingsWithName"></a>
## layer.siblingsWithName(name)

通过一个字符串匹配图层名称过滤筛选出来的所有兄弟图层。
>All sibling layers of this layer, filtered by name.

### 参数

* **name** — 一个表示图层名称的字符串。


    layerA = new Layer

    layerB = new Layer
        name: "navigation"
        parent: layerA

    layerC = new Layer
        name: "button"
        parent: layerA

    print layerB.siblingsWithName("button")
    # Output: [<Object:Layer name:button layerC>]

<a id="layer.descendants"></a>
## layer.descendants &lt;数组&gt;

获取一个图层的所有的后代图层。这些后代图层可以包含很多层级，所以它的子图层的子图层也是其后代图层。
>All descendant layers of this layer. These include layers that are nested multiple levels deep, so also the child layers of its own child layers.

    layerA = new Layer

    layerB = new Layer
        parent: layerA

    layerC = new Layer
        parent: layerB

    print layerA.descendants
    # Output: [<Object:Layer layerB>, <Object:Layer layerC>]

<a id="layer.ancestors"></a>
## layer.ancestors &lt;数组&gt;

获取一个图层的所有祖先图层。这些祖先图层可以包含很多层级，因此它的父图层的父图层也是其祖先图层。
>All ancestor layers of this layer. These include layers that are nested multiple levels deep, so also the parent layers of its own parent layer.

    layerA = new Layer

    layerB = new Layer
        parent: layerA

    layerC = new Layer
        parent: layerB

    print layerC.ancestors
    # Output: [<Object:Layer layerB>, <Object:Layer layerA>]

<a id="layer.addChild"></a>
## layer.addChild(layer)

给一个图层添加一个子图层，该方法将会自动将该图层设置为新添加的图层的父图层。（别名：addSubLayer）
>Add a layer as a child to this layer. This will set the parent of the added layer. (Alias: addSubLayer)

### 参数

* **layer** — 一个图层对象。


    layerA = new Layer
    layerB = new Layer

    layerA.addChild(layerB)

    print layerB.parent
    # Output: <Object:Layer layerA>

<a id="layer.removeChild"></a>
## layer.removeChild(layer)

移除从一个图层的子图层中移除一个图层。（别名：removeSubLayer）
>Remove a layer from the children of this layer. (Alias: removeSubLayer)

### 参数

* **layer** — 一个图层对象。


    layerA = new Layer
    layerB = new Layer
        parent: layerA

    layerA.removeChild(layerB)

    print layerB.parent
    # Output: null

<a id="layer.index"></a>
## layer.index &lt;number&gt;

这个图层的顺序索引值。同级图层中索引值（同`z`值）大的图层将会绘制在上层，索引值小的图层被绘制在底部。
>The order index for this layer. Sibling layers with a higher index (and the same z value) will drawn on top of this layer, and those with a lower index below.

图层索引值按照插入顺序增长。如果此时同级的几个图层中最大索引值是5，而你又在该层级中添加了一个图层，那么它的索引值就是6（5+1），而且后来插入的图层总是在上层。
>The layer index increases by order of insertion. So if you add a layer as a child and the highest sibling index value is 5, the index of the inserted layer will be 6 (5 + 1). Or, the last inserted layer will always be on top.

    layerA = new Layer
    layerB = new Layer

    # Draw layerB on top
    layerA.index = 2
    layerB.index = 1

<a id="layer.placeBefore"></a>
## layer.placeBefore(layer)

将该图层放置在另一个图层前面，这将会至少改变一个图层的`index`属性。这个方法只对拥有相同父图层的或者都没有父图层的图层有效。
>Places this layer before another layer. This changes the layer.index property for at least one of the layers. This method only works on layers that have the same parent, or no parent at all.

### 参数

* **layer** — 一个图层对象。


    layerA = new Layer
    layerB = new Layer

    # Draw layerB on top
    layerB.placeBefore(layerA)

<a id="layer.placeBehind"></a>
## layer.placeBehind(layer)

将该图层放置在另一个图层后面，这将会至少改变一个图层的`index`属性。这个方法只对拥有相同父图层的或者都没有父图层的图层有效。
>Places this layer behind another layer. This changes the layer.index property for at least one of the layers. This method only works on layers that have the same parent, or no parent at all.

### 参数

* **layer** — 一个图层对象。


    layerA = new Layer
    layerB = new Layer

    # Draw layerB on top
    layerA.placeBehind(layerB)

<a id="layer.bringToFront"></a>
## layer.bringToFront()

将该图层放置在具有相同父图层的所有图层前面。
>Places this layer in front of all other layers with the same parent.

    layerA = new Layer
    layerB = new Layer
    layerC = new Layer

    # Draw layerA on top
    layerA.bringToFront()


<a id="layer.sendToBack"></a>
## layer.sendToBack()

将该图层放置在具有相同父图层的所有图层后面。
>Places this layer behind all other layers with the same parent.

    layerA = new Layer
    layerB = new Layer
    layerC = new Layer

    # Draw layerC last
    layerC.sendToBack()

<a id="layer.html"></a>
## layer.html &lt;string&gt;

给图层插入HTML内容。插入的可以是任何HTML元素，从文本到输入框表单，或者画布、SVG都是可以的。
>Insert HTML content into this layer. The html can be anything, from text, to input and form elements to canvas or SVG content.

如果你需要获取其中的某个元素，要等到Framer将其全部渲染完成之后。想要引用某一个DOM元素，使用`layer.querySelector`或`layer.querySelectorAll`。
>If you need to target any of the created elements, remember that they are only available after Framer rendered them. To reliably get a reference to a DOM element, use layer.querySelector or layer.querySelectorAll.

如果插入的元素需要用户交互，最好设置该图层的[ignoreEvents](#layer.ignoreEvents)为`false`。为了保留图层结构，一般在这个图层创建完毕之后你第一次设置HTML时将HTML内容添加进去。
>If the content that gets inserted needs user interaction, it's best to set layer.ignoreEvents to false. To retain the layer structure, the content is placed within an element that gets created when you set HTML for the first time.

    layerA = new Layer

    # Add simple text content
    layerA.html = "Hello"

    # Add inline styled text content
    layerA.html = "I'm <span style='color:red'>Koen</span>"

    # Add an input field
    layerA.html = "<input type='text' value='Hello'>"

    # Add a div with a canvas element and get a reference
    layerA.html = "<div><canvas id='canvas'></canvas></div>"
    canvasElement = layerA.querySelectorAll("#canvas")

<a id="layer.style"></a>
## layer.style &lt;object&gt;

获取或设置图层的CSS样式。
>Set or get CSS style properties for the layer.

除了使用标准CSS属性名方式以外，你还可以使用驼峰命名法。比如`layer.style["border-color"]`和`layer.style.borderColor`是一样的，具体可以参见[这里](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Properties_Reference)。
>Next to the standard CSS property names you can also camelCase naming. For example, layer.style["border-color"] is the same as layer.style.borderColor. For a full list see this overview.

    layerA = new Layer

    # Modify a single style property
    layerA.style["outline"] = "1px solid red"

    # Modify set of style properties
    layerA.style =
        "outline": "1px solid red",
        "padding": "10px"

    # Get a specific style property
    print layerA.style["outline"]
    # Output: "1px solid red"

<a id="layer.computedStyle"></a>
## layer.computedStyle()

获取一个图层上所有已经应用的CSS样式属性。需要注意的是这个操作很耗浏览器性能。关于所有最终计算出的样式参考请查看[这里](https://developer.mozilla.org/en-US/docs/Web/API/Window/getComputedStyle)。
>Get all the current applied CSS style properties for the layer. Note that this is an expensive operation for the browser. For a full reference on computed style, see this overview.

    layerA = new Layer
    layerA.backgroundColor = "red"

    print layer.computedStyle()["background-color"]
    # Output: "red"

<a id="layer.classList"></a>
## layer.classList &lt;ClassList object&gt;

一个图层的所有样式类列表，也包括一些添加类、移除类或者检查类的方法，完整的方法列表参见[这里](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList)。
>A list of class attributed for the layer. Also contains methods to add, remove, toggle and check for classes. For a full reference, see this overview.

    layerA = new Layer

    # Add the class .red
    layerA.classList.add("red")

    # Remove the class .red
    layerA.classList.remove("red")

    # Toggle the class .red
    layerA.classList.toggle("red")

    # See if the layer has class .red
    print layerA.classList.contains("red")
    # Output: true

<a id="layer.destroy"></a>
## layer.destroy()

这个方法将会从层级中销毁一个图层，同时也会移除它的所有侦听事件以及子图层。
>This will remove a layer from the hierarchy and remove all its listeners. If the layer has children they will be destroyed too.

    layerA = new Layer
    layerA.destroy()

<a id="layer.copy"></a>
## layer.copy()

这个方法将会复制一个图层以及该图层的所有子图层。这些图层将会和被复制的图层拥有相同的属性和外观，但是原有的事件监听不会被复制过来。
>This will copy a layer and all its children. The layers will have all the same properties as their copied counterparts (same position and looks). The event listeners will not be copied.

    layerA = new Layer
    layerB = new Layer
        parent: layerA

    layerC = layerA.copy()

<a id="layer.copySingle"></a>
## layer.copySingle()

这个方法将单独复制一个图层而不复制其子图层，同样地时间监听不会被复制过来。
>This will copy a layer without its children. Event listeners aren't copied.

    layerA = new Layer
    layerB = new Layer
        parent: layerA

    layerC = layerA.copySingle()

<a id="layer.blur"></a>
## layer.blur &lt;number&gt;

给图层添加一个高斯模糊，它的值是用像素来定义的，默认值是0。
>Adds a gaussian blur to the layer. Gaussian blur is defined in pixels. The default value is 0.

    layerA = new Layer
    layerA.blur = 10

<a id="layer.bringhtness"></a>
## layer.brightness &lt;number&gt;

调节一个图层的亮度。它的值是一个数字，当它为0时该图层就完全变黑，而当它等于多少时该图层完全变白则取决于你的图层或图片颜色。
>Brightens or darkens a layer. Brightness is defined with a number. Setting brightness to 0 produces a completely black layer, while the value that produces a completely white layer depends on the color of your layer or image.

    layerA = new Layer
    layerA.brightness = 10

<a id="layer.saturate"></a>
## layer.saturate &lt;number&gt;

调节一个图层的饱和度。它的值在0到100之间，0表示完全移除饱和度，默认值是100。
>Saturates a layer. Saturation is defined with a number between 0 and 100 where 0 removes all saturation and 100 is default.

    layerA = new Layer
    layerA.saturate = 50

<a id="layer.hueRotate"></a>
## layer.hueRotate &lt;number&gt;

调节图层的色相。它的值的范围是是0到360，默认值为0。
>Sets the hue of a layer. The hue rotation is defined in degrees between 0 and 360. The default value is 0.

    layerA = new Layer
    layerA.hueRotate = 180

<a id="layer.contrast"></a>
## layer.contrast &lt;number&gt;

设置图层对比度，它的值的范围是从0到100，0表示完全移除对比度。默认值是100。
>Sets the contrast of a layer. Contrast is defined with a number between 0 and 100 where 0 is removes all contrast. The default value is 100.

    layerA = new Layer
    layerA.contrast = 50

<a id="layer.invert"></a>
## layer.invert &lt;number&gt;

颜色反转。`Invert`的值的范围从0到100，它将会把一个图层所有颜色和亮度进行反转。当你设置为100时，它会将一个图层的所有颜色转为互补色，默认值为0。
>Inverts the color of a layer. Invert is defined with a number between 0 and 100. The invert property inverts all colors and brightness values of a layer. Setting invert to 100 on a colored layer replaces all hues with their complementary colors. The default value is 0.

    layerA = new Layer
    layerA.invert = 100

<a id="layer.grayscale"></a>
## layer.grayscale &lt;number&gt;

`Grayscale`会将所有颜色转为灰度颜色。它的值是从0到100，当设置为100时则处于完全灰度状态，默认值是0.
>Grayscale converts all colors to gray. Grayscale is defined with a number between 0 and 100 where 100 turns all colors to a shade of gray. The default value is 0.

    layerA = new Layer
    layerA.grayscale = 100

<a id="layer.sepia"></a>
## layer.sepia &lt;number&gt;

给图层添加一个褐色色调，使其呈现老照片效果。它的值是从0到100，默认值是0。
>Adds a sepia tone to your layer. Sepia is defined with a number between 0 to 100. The default value is 0.

    layerA = new Layer
    layerA.sepia = 100

<a id="layer.shadowX"></a>
## layer.shadowX &lt;number&gt;

设置x轴上的投影方向。正值将会在图层的右边缘产生投影，负值会在图层的左边缘产生投影，不过只有当设置了`shadowColor`属性时才可以看见投影。
>Defines the shadow direction on the x-axis. A positive value will produce a shadow from the right edge of a layer, whereas a negative value will produce a shadow from the left edge. A visible shadow will only appear if the shadowColor property is also defined.

    layerA = new Layer
    layerA.shadowX = 10

<a id="layer.shadowY"></a>
## layer.shadowY &lt;number&gt;

设置x轴上的投影方向。正值将会在图层的下边缘产生投影，负值会在图层的上边缘产生投影，不过只有当设置了`shadowColor`属性时才可以看见投影。
>Defines the shadow direction on the y-axis. A positive value will produce a shadow from the bottom edge of a layer, whereas a negative value will produce a shadow from the top edge. A visible shadow will only appear if the shadowColor property is also defined.

    layerA = new Layer
    layerA.shadowY = 10

<a id="layer.shadowBlur"></a>
## layer.shadowBlur &lt;number&gt;

给投影的`shadowX`或`shadowY`添加高斯模糊，`shadowBlur`的值是一个数字，默认为0。
>Adds a Gaussian blur to the shadowX or shadowY property. shadowBlur is defined with a number. The default value is 0.

    layerA = new Layer
    layerA.shadowY = 1
    layerA.shadowBlur = 4

<a id="layer.shadowSpread"></a>
## layer.shadowSpread &lt;number&gt;

让投影向四周扩展。投影会按照给定的值向外扩展，如果给定的值是负值，投影将会缩小。如果`shadowX`、`shadowY`、`shadowBlur`同时设置为0，投影将会和描边一样。只有同时设置`shadowColor`才会出现一个可见的投影。
>Makes shadows larger in all directions. The shadow is expanded by the given value. Negative values cause the shadow to contract. If shadowX, shadowY and shadowBlur are all set to 0, this will appear as a border. A visible shadow will only appear if the shadowColor property is also defined.

    layerA = new Layer
    layerA.shadowY = 1
    layerA.shadowBlur = 4
    layerA.shadowSpread = 2

<a id="layer.shadowColor"></a>
## layer.shadowColor &lt;string&gt;

设置投影的颜色，颜色的值是一个 CSS 颜色格式的字符串。
>Sets the color of a layers shadow. The color is expressed as a string in the CSS color format.

    layerA = new Layer
    layerA.shadowY = 1
    layerA.shadowBlur = 4
    layerA.shadowColor = "rgba(0,0,0,0.2)"

<a id="layer.borderRadius"></a>
## layer.borderRadius &lt;number&gt;

设置图层的圆角半径。当你想要创建一个圆形图层时，只需要将它的圆角半径设置很大，或者设置为宽或高的一半。
>Rounds the corners of a layer in pixels. To create circles, set the property to a high value (50-100) or divide the layers width/height by two.

    layerA = new Layer
    layerA.borderRadius = 3

    # To create a circle:
    layerA.borderRadius = layerA.width/2

<a id="layer.borderColor"></a>
## layer.borderColor &lt;string&gt;

设置图层的描边颜色，颜色的值是一个 CSS 颜色格式的字符串。
>Set the border color of this layer. The color is expressed as a string in the css color format.

    layerA = new Layer
    layerA.borderColor = "red"
    layerA.borderWidth = 2

<a id="layer.borderWidth"></a>
## layer.borderWidth &lt;number&gt;

设置图层描边的宽度。
>Set the width of the layer border in pixels.

    layerA = new Layer
    layerA.borderWidth = 2
    layerA.borderColor = "red"

<a id="layer.animate"></a>
## layer.animate(options)

让图层开始做动画运动。它的选项包含了这个图层需要执行动画的属性值以及做这个动画的方式。运行此函数时，将会使用该动画选项创建一个新的`Animation`对象。通过此对象，你可以让她停止或者反向。如下例所示，这个动画的执行时间是5秒。
>Start animating this layer. The animation options describe the properties it needs to animate to and how to animate. Running this method will create a new Animation Object with the animationOptions, which you can use to stop or reverse the animation. Here, the duration of the animation is 5 seconds.

    layerA = new Layer

    # Animate scale and rotation
    layerA.animate
        properties:
            scale: 0.5
            rotation: 90
        time: 5

在下面的例子中，动画每次重复都会延迟 2 秒。
>In the example below, there is a 2 second delay between every repeat.

    # Repeat and delay the animation
    layerA.animate
        properties:
            x: 100
        repeat: 5
        delay: 2

<a id="layer.animateStop"></a>
## layer.animateStop()

立即停止该图层上的所有动画。
>Stop all running animations on this layer immediately.

    layerA = new Layer

    # Stop an animation immediately
    layerA.animate
        properties:
            x: 100

    layerA.animateStop()

<a id="layer.animations"></a>
## layer.animations()

返回当前图层上的所有动画对象。
>Returns all the current running animations for this layer.

    layerA = new Layer

    layerA.animate
        properties:
            x: 100

    layerA.animate
        properties:
            y: 100

    print layerA.animations()
    # Output: [<Object Animation>, <Object Animation>]

<a id="layer.isAnimating"></a>
## layer.isAnimating &lt;boolean&gt;

检测一个图层是否在执行动画，该属性是只读的。
>See if a layer is animating. This property is readonly.

    layerA = new Layer

    layerA.animate
        properties:
            x: 100

    print layerA.isAnimating
    # Result: True

<a id="layer.stateSwitch"></a>
## layer.stateSwitch(name)

立即不带动画过渡地切换状态。（`layer.stateSwitch()`取代了`layer.states.switchInstant()`）
>Instantly switch to a state without animating. (layer.stateSwitch() deprecated layer.states.switchInstant())

### 参数

* **name** — 一个表示状态名称的字符串。


    layerA = new Layer

    layerA.states.stateA =
        x: 100

    layerA.stateSwitch("stateA")

<a id="layer.stateCycle"></a>
## layer.stateCycle(states, options)

在一个图层的所有状态之间循环，一旦循环到最后一个状态将回到第一个状态继续循环。如果你不想让它按照定义状态的代码顺序循环，你可以提供一个包含几个状态的数组作为循环顺序。
>Cycle through all the layer states. Once we reach the end of the cycle we start at the beginning again. You can provide an array of state names for the ordering, if you don’t it will order based on when a state was added.

你还可以给它提供一个动画选项参数来控制它循环过渡时的动画。（`layer.stateCycle()` 取代了 `layer.states.next()`）
>You can also add an animation options parameter to change the animation for a cycle.(layer.stateCycle() deprecated layer.states.next())

### 参数

* **states** — 包含一些状态名的数组（可选）。
* **options** — 一个包含动画选项的对象，可能包含 `curve` 、`time` 等（可选）。


    layerA = new Layer

    layerA.states =
        stateA:
            x: 100
        stateB:
            x: 200

    # Every time we call this we cycle to the next state
    layerA.stateCycle(["stateA", "stateB"])

<a id="layer.stateNames"></a>
## layer.stateNames &lt;Array&gt;

一个只读的属性，它会返回你给一个图层添加的所有状态名。
>A read-only property that returns an array with names of all states assigned to a layer.

    layerA = new Layer

    layerA.states =
        stateA:
            x: 100
        stateB:
            y: 100

    print layerA.stateNames
    # Result: ["stateA", "stateB"]

<a id="layer.convertPointToCanvas"></a>
## layer.convertPointToCanvas(point)

把一个图层上的点的坐标转换成画布上的点坐标。
>Converts a point from a layer to the Canvas.

    point =
        x: 20
        y: 40

    layer = new Layer

    pointInCanvas = layer.convertPointToCanvas(point)

<a id="layer.convertPointToScreen"></a>
## layer.convertPointToScreen(point)

把一个图层上的点的坐标转换成设备屏幕上的点坐标。
>Converts a point from a layer to the Screen.

    point =
        x: 20
        y: 40

    layer = new Layer

    pointInScreen = layer.convertPointToCanvas(point)

<a id="layer.convertPointToLayer"></a>
## layer.convertPointToLayer(point, layer)

把一个图层上的点的坐标转换成另一个图层上的点坐标。
>Converts a point from a layer to another layer.

    point =
        x: 20
        y: 40

    layerA = new Layer
    layerB = new Layer

    pointInLayerB = layerA.convertPointToLayer(point, layerB)

<a id="layer.on"></a>
## layer.on(eventName, handler)

开始监听一个图层上的事件。
>Start listening to an event on this layer.

当一个监听事件的函数被调用时，他有两个参数可供使用，第一个是关于这个事件的一些信息。基于不同的事件，这个`event`中可能包含鼠标位置、鼠标增量等信息。第二个参数一般是的那个钱事件所发生的图层。
>When an event is called the first argument is the event information. Depending on the specific event this can contain mouse positions, mouse deltas etc. The second argument is always the layer that the event occurred to.

    layerA = new Layer
    layerA.name = "layerA"

    layerA.on Events.Click, (event, layer) ->
        print "Clicked", layer.name

    # Output: "Clicked", "layerA"

<a id="layer.off"></a>
## layer.off(eventName, handler)

停止监听某个事件。
>Stop listening to an event on this layer.

    layerA = new Layer
    layerA.name = "layerA"

    clickHandler = (event, layer) ->
        print "This layer was clicked", layer.name

    layerA.on(Events.Click, clickHandler)
    layerA.off(Events.Click, clickHandler)
