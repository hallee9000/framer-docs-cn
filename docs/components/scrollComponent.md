# ScrollComponent

一个滚动组件可以让内容变成可滚动的。它可以模拟动量及弹性等物理特性，也有很多事件可以监听，这使得你可以很容易地按自己的需求定制。
>A ScrollComponent is used to scroll content. It implements momentum and spring physics, allows for customization, and emits different events.

滚动组件是由两个图层组成的，一个蒙在外面的遮罩图层——也就是该组件自身，它内部有一个可以在一个范围内拖动的内容图层。它会自动地依据内容图层的子图层尺寸来控制自身的尺寸。
>The ScrollComponent is built with two layers. The ScrollComponent itself is a layer that masks its content. It has a content layer that has draggable enabled and constraints configured. It automatically manages the size of the content layer based on the total size of the sub layers of the content layer.

    # 创建一个新的ScrollComponent 
    scroll = new ScrollComponent
        width: 100
        height: 100
     
    # 放进一个图层
    layerA = new Layer
        parent: scroll.content

你也可以使用滚动组件包裹一个已经存在的图层，只需要使用`ScrollComponent.wrap()`方法。`ScrollComponent`会将自己插入内容图层和它的父图层之间。如果你是从 Sketch 或者 Photoshop 导入设计图，并且像让它们变成可以滚动的，就可以使用这种方法。更详细的内容看[这里](/docs/#scroll.wrap)。
>You can also wrap an existing layer within a ScrollComponent, using ScrollComponent.wrap(). The ScrollComponent will insert itself in-between the content and its super layer. This is useful when you've imported designs from Sketch or Photoshop and want to make a layer scrollable. You can learn more about wrapping in the learn section.

    layerA = new Layer
        width: 300
        height: 300
     
    scroll = ScrollComponent.wrap(layerA)

<a id="content"></a>
## scroll.content &lt;layer&gt;

添加滚动内容的图层。要给该组件添加滚动内容时，先创建一个新图层再将其父图层设为 `scroll.content` ，当图层内容超出时只会截取显示 `scroll.content` 尺寸那么大的部分。
>The layer to add content to. To add content, create a new Layer and set its parent to the scroll.content layer. When the content doesn't fit the ScrollComponent it will be clipped.

    scroll = new ScrollComponent
        width: 100
        height: 100
     
    layerA = new Layer
        parent: scroll.content
        image: "images/bg.png"
        width: 100
        height: 200

<a id="contentInset"></a>
## scroll.contentInset &lt;object&gt;

滚动内容和外层之间的间隙，你可以通过此属性定义可滚动内容的内边距。
>Inset for the content. This will give your content extra padding between the constraints and the actual content layers.

    scroll = new ScrollComponent
        width: 100
        height: 100
     
    layerA = new Layer
        parent: scroll.content
        image: "images/bg.png"
        width: 100
        height: 200
     
    scroll.contentInset =
        top: 20
        right: 0
        bottom: 20
        left: 0

<a id="speedX"></a>
## scroll.speedX &lt;number&gt;

水平滚动速度，它的值是 0 到 1 之间的数字，默认值为 1。
>Horizontal scrolling speed, number between 0 and 1. Default value is 1.

    scroll = new ScrollComponent
     
    layerA = new Layer
        parent: scroll.content 
     
    scroll.speedX = 0.5

<a id="speedX"></a>
## scroll.speedY &lt;number&gt;

垂直滚动速度，它的值是 0 到 1 之间的数字，默认值为 1。
>Vertical scrolling speed, number between 0 and 1. Default value is 1.

    scroll = new ScrollComponent
     
    layerA = new Layer
        parent: scroll.content 
     
    scroll.speedY = 0.5

<a id="scroll"></a>
## scroll.scroll &lt;boolean&gt;

启用或禁用可滚动功能，默认是开启的，如果你设置为 `false` ，则水平和垂直两个方向的滚动都会被禁止。
>Enable or disable scrolling. Enabled by default. If you set this to false, it will set both scrollVertical and scrollHorizontal to false.

    scroll = new ScrollComponent
     
    layerA = new Layer
        parent: scroll.content
     
    scroll.scroll = false

<a id="scrollHorizontal"></a>
## scroll.scrollHorizontal &lt;boolean&gt;

启用或禁用水平滚动。
>Enable or disable horizontal scrolling.

    scroll = new ScrollComponent
     
    layerA = new Layer
        parent: scroll.content
     
    scroll.scrollHorizontal = false

<a id="scrollVertical"></a>
## scroll.scrollVertical &lt;boolean&gt;

启用或禁用垂直滚动。
>Enable or disable vertical scrolling.

    scroll = new ScrollComponent
     
    layerA = new Layer
        parent: scroll.content
     
    scroll.scrollVertical = false


<a id="scrollX"></a>
## scroll.scrollX &lt;number&gt;

水平滚动的坐标值。
>Horizontal scroll location.

    scroll = new ScrollComponent
     
    layerA = new Layer
        parent: scroll.content
     
    scroll.scrollX = 250

<a id="scrollY"></a>
## scroll.scrollY &lt;number&gt;

垂直滚动的坐标值。
>Vertical scroll location.

    scroll = new ScrollComponent
     
    layerA = new Layer
        parent: scroll.content 
     
    scroll.scrollY = 250

<a id="scrollPoint"></a>
## scroll.scrollPoint &lt;object&gt;

通过 `x` 和 `y` 坐标来定义滚动的位置。
>Define the scroll location with x and y properties.

    scroll = new ScrollComponent
     
    layerA = new Layer
        parent: scroll.content
     
    scroll.scrollPoint =
        x: 0
        y: 50

<a id="scrollFrame"></a>
## scroll.scrollFrame &lt;object&gt;

滚动内容可视部分。
>Visible scroll frame.

    scroll = new ScrollComponent
     
    layerA = new Layer
        parent: scroll.content
     
    scroll.scrollFrame =
        x: 0
        y: 250
        width: 250
        height: 250

<a id="velocity"></a>
## scroll.velocity &lt;number&gt;

当前滚动的速度和方向，单位是像素每秒。
>Current scroll speed and direction in pixels per second at this current time.

    scroll = new ScrollComponent
 
    # On scroll, print the velocity 
    scroll.on Events.Scroll, ->
        print scroll.velocity

<a id="direction"></a>
## scroll.direction &lt;string&gt;

当前滚动方向，返回的值是`up`、`down`、`left`或`right`中的一个。滚动方向和你的拖动方向是相反的：当你向下拖动时，实际上是滚到上面（想看上面的内容）。它是只读的。
>Current scrolling direction. Returns "up", "down", "left", or "right". The scrolling direction is the inverse of the direction of the drag action: when dragging downwards, you're effectively scrolling upwards. (Read-only)

    scroll = new ScrollComponent
     
    # On scroll, print the direction 
    scroll.on Events.Scroll, ->
        print scroll.direction

<a id="directionLock"></a>
## scroll.directionLock &lt;boolean&gt;

设置方向锁定，也就是当某个方向移动幅度不够大时该方向就会被锁定。
>Snap to horizontal/vertical direction after a certain threshold.

    scroll = new ScrollComponent
     
    # Allow dragging only in one direction at a time 
    scroll.directionLock = true

<a id="directionLockThreshold"></a>
## scroll.directionLockThreshold &lt;object&gt;

锁定方向需要的最小距离。`x`和`y`表示在方向锁定之前你所能够拖动的最大距离。
>The thresholds for lock directions. The x and y values represent the distance you can drag in a certain direction before it starts locking.

    scroll = new ScrollComponent
     
    # Snap horizontally after dragging 50px 
    # Snap vertically instantly 
    scroll.directionLock = true
     
    scroll.directionLockThreshold =
        x: 50
        y: 0

<a id="angle"></a>
## scroll.angle &lt;number&gt;

当前拖动的角度，它和你拖动方向的角度是相反的，因为当你向下拖动时实际上是要滚到上面（只读）。向右拖动是 0 度，向下拖动是 -90 度，向上拖动是 90 度。
>Current scrolling angle (in degrees). The scrolling angle is the inverse of the direction of the drag action: when dragging downwards, you're effectively scrolling upwards. (Read-only)

    scroll = new ScrollComponent
     
    # On scroll, print the angle 
    scroll.on Events.Scroll, ->
        print scroll.angle

<a id="isDragging"></a>
## scroll.isDragging &lt;boolean&gt;

该图层是否正在被拖动（当你松开它但它还在运动时返回的是 `false` ）。它是只读的。
>Whether the layer is currently being dragged (returns false when animating). (Read-only)

    scroll = new ScrollComponent
 
    # Check if the layer is being dragged 
    scroll.onMove ->
        print scroll.isDragging

<a id="isMoving"></a>
## scroll.isMoving &lt;boolean&gt;

此时内容区域是否正在移动，不管是你在拖动它还是它在自己运动都是正在移动。它是只读的。
>Whether the content is currently moving, either by dragging or by a momentum/bounce animation. (Read-only)

    scroll = new ScrollComponent
     
    # Check if the layer is moving 
    scroll.onMove ->
        print scroll.isMoving

<a id="closestContentLayer"></a>
## scroll.closestContentLayer(originX, originY)

获得和`ScrollComponent`最近的内容图层，它是由图层的变换中心决定的。一个图层的变换中心的值是一个介于 0 到 1 之间的数字，(0,0) 表示变换中心处于图层的左上角，(0.5, 0.5) 表示处于图层中心，(1,1) 表示处于图层右下角。
>Get the layer closest to the ScrollComponent, depending on the defined origin. The origin is defined as numbers between 0 and 1, where (0,0) is the top-left corner, (0.5, 0.5) the center, and (1,1) the bottom-right corner.

默认值是 (0,0) ，这意味着当计算哪个内容图层距离 `ScrollComponent` 最近时是计算它们左上角间的距离。
>The default values are (0,0). This means that it calculates the distance from the top-left of the ScrollComponent to the top-left of the content layers.

    scroll = new ScrollComponent
     
    # Create content layers 
    layerA = new Layer
        parent: scroll.content
        name: "layerA"
        x: 0
        y: 0
     
    layerB = new Layer
        parent: scroll.content
        name: "layerB"
        x: 50
        y: 50
 
    # Get the Layer of which the center point is closest 
    # to the center point of the ScrollComponent 
    print scroll.closestContentLayer(0.5, 0.5)

<a id="closestContentLayerForScrollPoint"></a>
## scroll.closestContentLayerForScrollPoint(originX, originY)

获取和特定点最近的内容图层。
>Get the content layer closest to a specific point.

    scroll = new ScrollComponent
     
    # Create content layers 
    layerA = new Layer
        parent: scroll.content
        name: "layerA"
        x: 0
        y: 0
     
    layerB = new Layer
        parent: scroll.content
        name: "layerB"
        x: 50
        y: 50
     
    # Get the layer of which the top-left 
    # corner is closest to x: 50, y: 25 
    print scroll.closestContentLayerForScrollPoint(
        x: 50
        y: 25
    )
     
    # Returns layerB 

你可以自己调节图层的变换中心，以此来决定距离计算的方式。默认的变换中心是 (0,0) ，这意味着当计算哪个内容图层距离 `ScrollComponent` 最近时是计算它们左上角间的距离。
>You can adjust the origin values to define how the distance is calculated. The default values are (0,0). This means that it calculates the distance from the top-left of the ScrollComponent to the top-left of the content layers.

    scroll = new ScrollComponent
     
    # Create content layers 
    layerA = new Layer
        parent: scroll.content
        name: "layerA"
        x: 0
        y: 0
     
     
    layerB = new Layer
        parent: scroll.content
        name: "layerB"
        x: 50
        y: 50
     
    # With the origins set to the center, 
    # layerA becomes the closest 
    print scroll.closestContentLayerForScrollPoint({ x: 50, y: 25 }, 0.5, 0.5)
     
    # Returns layerA 

<a id="scrollToPoint"></a>
## scroll.scrollToPoint(point, animate, animationOptions)

让内容滚动到某个特定点，可以选择带动画效果或者不带。
>Scroll to a specific point, optionally animating.

### 参数

* **point** — 一个包含 `x` 和 `y` 的对象.
* **animate** — 一个布尔值，默认为 `true`（可选）。
* **animationOptions** — 一个包含时间、动画曲线、动画延迟和重复次数的对象（可选）。


    scroll = new ScrollComponent

    # Scroll content to x: 200, y: 100 
    scroll.scrollToPoint(
        x: 200, y: 100
        true
        curve: Bezier.ease
    )
     
    # Scroll very slowly 
    scroll.scrollToPoint(
        x: 200, y: 100
        true
        curve: Bezier.ease, time: 10
    )

<a id="scrollToLayer"></a>
## scroll.scrollToLayer(layer, originX, originY, animate, animationOptions)

滚动到指定图层，不过你只可以指定滚动到 `scroll.content` 的子图层的位置。
>Scroll to a specific layer. You can only scroll to layers that are children of the scroll.content layer.

### 参数

* **layer** — 一个图层对象。
* **originX** — 一个 0 到 1 之间的数字（可选）。
* **originY** — 一个 0 到 1 之间的数字（可选）。
* **animate** —一个布尔值，默认为 `true`（可选）。
* **animationOptions** — 一个包含时间、动画曲线、动画延迟和重复次数的对象（可选）。


    # Create ScrollComponent 
    scroll = new ScrollComponent
        width: 500
        height: 500
     
    # Define Background 
    layerA = new Layer
        x: 500
        y: 1000
        image: "bg.png"
        parent: scroll.content
     
    # Scroll to this layer 
    scrollerA = new Layer
        parent: scroll.content
    
    scroll.scrollToLayer(scrollerA)

`originX` 和 `originY` 需要滚动到图层中的哪个点，它的默认值是 0,0 ，也就是左上角。
>The originX and originY arguments define the point within the layer that will be scrolled to. The default values are 0,0 - which is the top-left corner.

    scroll.scrollToLayer(
        layerA
        0.5, 0
        true
        time: 2
    )

<a id="scrollToLayer"></a>
## scroll.scrollToLayer(originX, originY)

滚动到最近的内容图层，你可以指定变换中心。一个图层的默认变换中心是 (0,0) 表示变换中心处于图层的左上角，而 (0.5, 0.5) 表示处于图层中心，(1,1) 表示处于图层右下角。
>Scroll to the closest content layer, using the given origin. The default values are (0,0) which is the top-left corner, (0.5, 0.5) the center, and (1,1) the bottom-right corner.

### 参数

* **originX** — 介于 0 到 1 之间的数字。
* **originY** — 介于 0 到 1 之间的数字。


    scroll = new ScrollComponent

    layerA = new Layer
        parent: scroll.content
        x: 75
        y: 75
     
    # Scroll to the center of layerA 
    scroll.scrollToClosestLayer(0.5, 0.5)

<a id="mouseWheelEnabled"></a>
## scroll.mouseWheelEnabled &lt;boolean&gt;

启用或者禁用鼠标滚动，默认是禁用的。当设置为 `true` 时你可以拖动它滚动也可以通过鼠标控制滚动。
>Enable or disable scrolling with mousewheel. Disabled by default. When set to true, layers can be scrolled both by dragging and with the mouse.

    scroll = new ScrollComponent
        width: 100
        height: 100
     
    # Allow scrolling with mouse 
    scroll.mouseWheelEnabled = true
     
    layerA = new Layer
        parent: scroll.content
        image: "images/bg.png"
        width: 100
        height: 200

<a id="wrap"></a>
## scroll.wrap(layer)

使用 `ScrollComponent` 包裹一个图层，使其变为可滚动的。如果你想把导入的设计图变成可以滚动的就可以这样写。
>Wraps a layer within a new ScrollComponent. This is useful to create scrollable layers out of imported layers.

    # Import files from Sketch 
    sketch = Framer.Importer.load "imported/Scrollable"
     
    # Wrap the "content" layer group 
    scroll = ScrollComponent.wrap(sketch.content)

现在，`scroll` 就是一个代表可滚动组件的的变量，它把你包裹的图层变成了可滚动内容。你可以通过给 `scroll` 设置一些属性来调节滚动效果，如动量模拟、允许越界、弹性模拟等。
>Now, scroll is the variable name of the ScrollComponent. This also automatically wraps your layer within a ScrollContent layer, which you can select to adjust certain properties like momentum, overdrag or bounce.

    # Import files from Sketch 
    sketch = Framer.Importer.load "imported/Scrollable"
     
    # Wrap the "content" layer group 
    scroll = ScrollComponent.wrap(sketch.content)
     
    # Change scroll properties 
    scroll.scrollHorizontal = false
    scroll.speedY = 0.5
     
    # Change scroll.content properties 
    scroll.content.draggable.momentum = true
    scroll.content.draggable.overdrag = false
    scroll.content.draggable.bounce = false

<a id="updateContent"></a>
## scroll.updateContent()

重新计算滚动区域尺寸和拖动范围，也会影响 `contentInset` 的值。
>Re-calculates and updates the size of the content and the dragging constraints. It also accounts for the contentInset.

如果你想要更改图层的尺寸，就可以相应的去更新 `ScrollComponent` 的尺寸。
>If you're looking to change the size of your content layers, you can call it to update the size of your ScrollComponent accordingly.

    scroll = new ScrollComponent
     
    # Update the contents of the ScrollComponent 
    scroll.updateContent()

<a id="copy"></a>
## scroll.copy()

复制一个 `ScrollComponent` ，包括它的内容图层和各项属性。
>Copies a ScrollComponent, including its content and properties.

    scroll = new ScrollComponent
     
    layerA = new Layer
        parent: scroll.content
     
    # Copy the ScrollComponent 
    scrollB = scroll.copy()

<a id="propagateEvents"></a>
## scroll.propagateEvents &lt;boolean&gt;

设置可拖动内容图层的“事件传播”属性，默认是 `true` 。当你想要嵌套 `ScrollComponents` 和 `PageComponents` 时需要用到它。
>Set the propagateEvents property of the draggable content layer. Set to true by default. This is useful when working with nested ScrollComponents or PageComponents.

假如有这么一个场景：你想要在一个 `scroll.content` 内放另外一个可滚动图层。默认情况下，滚动内层图层时，外层的 `scroll.content` 也会滚动，这是因为它们在同时监听拖动事件。
>Let's say you'd like to have a draggable layer within the scroll.content layer. By default, moving the layer will also move the scroll.content. This is because both layers will listen to the dragging events.

为了阻止任何滚动事件从底层图层传播到父图层，可以将它的 `propagateEvents` 设置为 `false` 。它对于任何嵌套的可拖动图层都是其作用的。
>To prevent any draggable children from passing events to its parent, set propagateEvents to false. This applies to all nested draggable layers.

    scroll = new ScrollComponent
        width: Screen.width,
        height: Screen.height
     
    scroll.content.backgroundColor = "#28affa"
     
    layerA = new Layer
        parent: scroll.content,
        backgroundColor: "#fff"
     
    layerA.draggable.enabled = true
     
    # Setting propagateEvents to false allows you to drag layerA 
    # without also scrolling within the ScrollComponent 
    layerA.draggable.propagateEvents = false

