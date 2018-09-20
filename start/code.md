# 代码模式

## 代码

**在这一节，我们了解一下如何使用代码在 Framer 中创建交互动效，以及一些简单指示。**

不管你有没有代码知识，我们设计 Framer 代码的初衷都是为了让它变得有趣有价值。对于初学者来说，如果你了解基础的 HTML 、CSS 或 Javascript 知识，这将会对你的学习有一定帮助，但是渴望学习的心同样重要。很多设计师——大部分没有代码基础——开始使用Framer，到最后做了很多精彩的作品，并将此作为提升他们事业的工具。在此期间，我们也一直从他们的经验中汲取灵感，给Framer提供更加便利的工具以便设计师能够更快上手。

![](/images/learn/code/intro-code@2x.webp)

大致地读一下这段指南，让自己熟悉一下这些概念，但是你不必现在弄懂每一处。我们把Framer作为一个概念性学习工具。我们也一直在给Framer加一些新特性，来降低其学习曲线。从简化语法到自动编程到详细的错误提示到App内文档，Framer一直在帮助你成长。

如果你对这些基础知识已经很熟悉了，可以去我们的[编程指南](/learn/programming)学习更加复杂的内容，比如逻辑、变量和循环等。

## 工作流

**在 Framer 中你有三种方式给一个元素添加动效。在这篇指南中，我们将会给你讲解代码模式和设计模式之间的关系，以及如何从外部导入设计图并使用代码给其添加动效。**

为了有一个更加高效的工作流程，我们建议你直接在 Framer 设计模式下进行设计。你可以直接在画布上拖拽来绘制画布，也可以直接使用内置的不同设备尺寸画布。Framer 的设计模式是基于代码模式进行过优化的，所以在这里设计是极其直观和自适应的。继承、布局以及图层分组都是经过优化的，他可以更好的和代码模式相结合。当你完成设计部分时，只需要给需要添加交互的元素添加代码目标，就可以在代码模式下去使用它。

<a href="/learn/design#targeting" class="btn btn-primary-o">学习代码目标</a>

另外一种方式是从外部导入设计稿，你目前支持 Sketch, Figma 和 Photoshop 。你可以将设计软件中同一组的图层作为 Framer 中的一个图层，给它们添加动画，或者再回到你最爱的设计软件中微调。者只需要你几次点击，就可以将其它设计软件整合进 Framer 的工作流。

<a href="/learn/design#importing" class="btn btn-primary-o">学习如何导入</a>

最后，你也可以直接在代码模式下通过代码来创建图层。然而，我们不是很推荐这种方式，不过当你想在 Framer 中快速构建原型时却很方便。

<a id="preview"></a>
## 预览窗口

##### 在代码模式下，你可以看见右侧有一个实时预览的窗口，你在代码或设计中的任何改动都会实时更新到这里，你也可以直接在这里拖拽图层进行微调。

Framer 预览窗口提供实时反馈，无论你在设计模式还是代码模式下改动了什么。如果要重新播放动画，只需要使用快捷键 `CMD` + `R` 。默认情况下预览窗口是固定在右侧的，但是你可以把它分离，这样就可以获得更大的工作空间了。想要切换设备，只需要点击预览窗口的设备切换菜单。

如果你直接在画布上进行设计，那么这些图层不会有一个画板父图层。将你的图层放置于坐标 `x: 0` 和 `y: 0` 处，在预览窗口中爱图层将处于左上角。

![](/images/learn/code/intro-preview@2x.webp)

<!-- <a id="artboards"></a>
## 画板

##### 在 Framer 中画板不仅可以划分设计区域，它还是自适应的，在画板中的元素会根据画板尺寸变化进行自适应。

刚开始时，你可以选择一个主要设备尺寸画板进行设计，我们提供了很多预设尺寸，包括手表、手机、电脑、平板、电视等等。选定之后在代码模式下预览窗口就立即变成了你所选的尺寸，你可以点击预览窗口顶部的设备名，在下拉菜单中随时切换设备。

### 从设计到代码

如果你是在画板中进行设计的，那么在代码模式下使用它就很棒。画出一个画板之后，你在这个画板中所绘制的所有图层都会自动变成它的子图层。将一个画板设置为代码目标之后，它里面的元素在代码模式下也都可以看见。这使得制作页面跳转之类的交互变得简单。

    # Initialize FlowComponent
    flow = new FlowComponent

    #  Set up a flow from your artboards
    flow.showNext(ArtboardA)

    ArtboardA.onClick ->
        flow.showNext(ArtboardB)

    ArtboardB.onClick ->
        flow.showPrevious() -->

<a id="frames"></a>
## 框架
##### 框架不仅仅是一个占位符，它是为了响应式布局而生的。

你可以在一开始就选一个设备屏幕去设计。你可以从智能手表、手机、电脑、平板或者电视等设备中选择，选好之后在代码模式下就可以看到预览窗口已经将设计图适应为该尺寸了。如果你想看看它在其他尺寸设备下的状态，可以随时切换预览设备。

### 为代码而设计
你使用框架设计能够很好地转换到代码中。每一个框架都会被默认设定为它内部所有图层的父图层，所以给一个框架设定代码目标时，就默认给它的所有子图层也设定了。这样的话制作类似于 `FlowComponent` 这样的交互效果就变得简单多了。

    # Initialize FlowComponent
    flow = new FlowComponent

    #  Set up a flow from your Frames
    flow.showNext(FrameA)

    FrameA.onClick ->
        flow.showNext(FrameB)

    FrameB.onClick ->
        flow.showPrevious()

<a id="layers"></a>
## 图层

##### 如果你使用过一些视觉设计工具，那你一定对图层这个概念很熟悉。如果没有内容的话，一个图层就是一个矩形。但是在Framer中，图层中还可以包括图片、音频、文字等等。

### 插入 & 代码目标

想要插入图层，你只需要在设计模式下从左侧的图层工具直接拖拽过去，在切换到代码模式也可以看见。

当你在设计模式下设置好了图层的代码目标，就可以切换到代码模式下开始使用它了。想要对一个图层进行操作，只需要在代码模式下写上它的代码目标名字，并在后面添加你想要实现的代码逻辑。

    #  Target and animate a layer from your design
    my_layer.animate
        y: 200
        options:
            time: 1
            curve: Bezier.ease

### 属性

在 Framer 中插入的图层有很多种类型的属性，比如定义它的位置和样式的属性，以及你想要添加一些交互效果的属性。你在代码模式下可以使用代码覆盖这些属性值，比如你在设计模式下绘制了一个红色的图层，在代码模式下可以这样把他的背景色改成蓝色。

    # Background layer override
    background.backgroundColor = "#28affb"

一个图层有很多视觉化的属性，通过这些属性你可以对他它进行变换、缩放、隐藏等等。在设计模式下定义的外观样式在代码模式下仍然可以适用代码覆盖。

    # Override properties
    layerB.borderRadius = 4
    layerB.rotation = 45
    layerB.opacity = 0.5
    layerB.scale = 0.5

如果想要研究一个图层代码和属性之间的联系，你可以试试“自动编程”功能。在代码模式下，右击图层名选择添加动画，自动编程面板就会显示出来，你可以直接在上面调节各项属性，这在预览窗口中都可以看到实时变化。

在每个图层代码前面都有一个自动编程的图标，电吉他可以进行切换。你可以去[图层文档](/docs/layer)查看所有图层属性。

### 位置

一个图层的位置是由它的 `x` 和 `y` 属性决定的，这两个值定义了图层距离画布左上角的距离。

    # Position layerA
    layerA.x = 200
    layerA.y = 200

图层的位置也可以动态地去定义，比如要让一个图层的位置相对于另一个图层。加入我们现在想让图层 B 的坐标处于图层 A 的中心，就可以使用图层的 `midX` 和 `midY` 属性。你可以在[文档](/docs/layer#minX)中查看其他关于位置的属性。

    # Align to center of the x axis of layerA
    layerB.x = layerA.midX

    # Align to center of the y axis of layerA
    layerB.y = layerA.midY

你还可以使用 `Align` 对象来控制一个图层的对齐。图层的父子关系一般在设计模式下就被定义好了，但是你仍然可以在代码中更改它们。你也可以单独设定图层水平对期或垂直对齐， `Align` 对象的所有属性都在下面：

* Align.left (x)
* Align.right (x)
* Align.top (y)
* Align.bottom (y)
* Align.center (x and y)


    # Define layerA as the parent of layerB
    layerB.parent = layerA

    # Align layerB to the bottom right of its parent
    layerB.x = Align.right
    layerB.y = Align.bottom

### 层级

你可以在设计模式下对图层进行分组，也可以在代码模式下重新分组。处于另一个图层中的图层被叫做子图层，包含其他图层的图层叫做父图层。图层会从父图层继承一些属性，比如透明度和位置。

    # Two ways to define hierarchy
    layerB.parent = layerA
    layerA.addChild(layerB)

如果你想让一个图层相比于另一图层更加靠前（想想一下电脑屏幕是个桌面，上面放了一摞图层，越靠近你的图层越靠前），你可以使用图层的 `placeBefore` 方法，相反地，如果想靠后你可以使用 `placeBehind` 方法。

    layerA = new Layer
    layerB = new Layer

    # Place layerB on top
    layerB.placeBefore(layerA)

### 图层类型

图层可以是任何事物，想想一下背景图层、图片图层、视频图层、文字图层等等。在设计模式下你可以添加常规图层，在代码模式下你可以插入一些可交互元素作为图层，比如视频图层、音频图层。想要添加一个视频图层，你只需要把一个视频拖拽到代码模式下即可。

    # Video
    video = new VideoLayer
        video: "fish.mp4"

### 文字图层

在 Framer 中可以直接添加文字图层。为了保证文字内容或颜色可变，你可以在代码模式下使用 `TextLayer` 。文字图层具有一些特殊属性，他的长宽会根据文字长短自动计算出来。

    # Create text layer
    title = new TextLayer
        text: "Hello!"
大部分的文字图层样式是来自于 CSS 的，你可以在[文字图层文档](/docs/textLayer)里查看更多。

    # Create text layer
    title = new TextLayer
        text: "Hello!"
        fontSize: 64
        fontWeight: 600
        x: Align.center
        y: Align.center

你可以使用强大的文字模板功能来对文字进行操作或动画，设置动态文字内容时请使用 `{}` 将变量包裹。

    # Create text layer with template tag.
    layerA = new TextLayer
      text: "{speed}KM/h"

    # Set speed template tag value.
    layerA.template =
      speed: 50

    # Shorthand for when there's only one tag.
    layerA.template = 50
    # Both result in "50KM/h".

我们也可以使用文字模板来格式化文本，或产生值变化的动画。

    # Create text layer with template tags.
    layerA = new TextLayer
      text: "{speed}{unit}/h"

    # Format template value to only have 2 decimals.
    layerA.templateFormatter =
      speed: (value) ->
        Utils.round(value, 2)

    # Animate template value from 0 to 100.
    layerA.animate
      template:
        speed: 100
        unit: "KM"

如果只是一个动态文本，你可以使用下面的简写方式。

    # Format template value to only have 2 decimals.
    layerA.templateFormatter = (value) ->
      Utils.round(value, 2)

<a id="animate"></a>
## 动画
##### 几乎所有的图层属性都能进行动画，而且你还可以对多个属性进项过渡动画。除此之外，你还可以定义动画的运动曲线（匀速运动、加速运动等）、运动时间、延迟时间以及其它的各种动画选项。

### 开始

让我们从一个图层的透明度动画说起，你可以使用图层的 `animate` 属性来定义它的属性要变化到的值。

    layerA.animate
        opacity: 0.5

### 选项

你可以通过调节动画时间、曲线和延迟来对动画效果进行微调，如下是可调节的动画的一些选项。

* **time** (in seconds)
* **curve** (Bezier, Spring)
* **delay** (in seconds)
* **repeat** (amount of times)
* **colorModel** (rgb, hsl, husl)

动画的时间是以秒定义的，通过设置动画的 `options` 属性可以设置他的一些参数，他下面的各个选项定义要再往后缩进一级。

    # Animate with an easing curve
    layerA.animate
        rotation: 180
        borderRadius: 200
        options:
            curve: Bezier.ease
            time: 1

### 缓动曲线

我们可以使用动画的缓动曲线来描述动画动画的类型。你可以使用内置的一些曲线定义，比如匀速运动 `linear` 或者幻入缓出 `Bezier.ease` 等。Framer 中默认的动画曲线是缓入缓出，其他的内置曲线如下，你也可以去这个[网站](http://easings.net/)了解更多。

* **Bezier.ease**
* **Bezier.easeIn**
* **Bezier.easeOut**
* **Bezier.easeInOut**


    # Animate with an easing curve
    layerA.animate
        scale: 0.75
        options:
            curve: Bezier.ease
            delay: 0
            time: 1

### 弹性曲线

为了使得动画的效果接近现实中的物理效果，你应该使用弹性曲线。动画的弹性可以使用阻尼 `damping` 来描述，它也可以配合时间 `time` 一起使用。


    # Animate with a spring curve
    layerA.animate
        scale: 0.75
        options:
            curve: Spring(damping: 0.5)
            time: 0.5

<a id="states"></a>
## 状态

##### 通过状态，你可以定义一个图层的不同样式外观。一个图层可以有几个不同的状态，每个状态都有着不同的属性值。定义好状态之后，你就可以让图层在状态之间带动画或者不带动画地切换。

### 添加状态

你可以想象成使用状态来管理不同的动画，添加状态后就可以让它在不同状态间做动画。

在下面这个个例子中，图层刚开始的的不透明度是 100% ,然后你在代码中给它定义了一个新状态 `fade` ，让它在此状态下不透明度变成 0 。


    # A new state titled "fade"
    layerA.states.fade =
        opacity: 0

刚创建的图层都有一个默认状态 `default` ，所以你可以让它从默认状态 `default` 切换到 `fade` 状态。

    # Animate to the state
    layerA.animate("fade")

    # Instantly switch to the state
    layerA.stateSwitch("fade")

### 循环切换状态

你也可以在图层的状态之间循环切换，只需要使用 `stateCycle()` 方法。如同图层动画一样，你也可以给它的状态设置动画属性。

    # Add states and animation options
    layerA.states.rotate =
        rotation: 0
        animationOptions:
            time: 1
            curve: Bezier.ease

    # Cycle between states
    layerA.onTap ->
        layerA.stateCycle()

### 状态编辑

如果想覆盖掉一个状态，只需要给它添加一个同名状态就可以了。

    # Override third state
    layerA.states.rotate =
        rotation: 180

<a id="events"></a>
## 事件

##### 事件是由用户在图层上触发的，比如触摸、滑动、长按等。有了事件，你就可以让图层基于这些事件来做动画。Framer 提供了很多手势事件，比如触摸、滑动甚至更加高级的多点触控。

Framer 的所有事件中，最常见的就是 `onTap` 、 `onScroll` 这些。当然，也有些事件是由图层的动画、状态切换、页面切换触发的。在一些复杂的交互案例中，你可能会用到多点触控比如两指捏放。

    layerA.onTap ->
        ...
    layerA.onScroll ->
        ...
    layerA.onSwipe ->
        ...
    layerA.onAnimationEnd ->
        ...

最常见的事件使用就是当点击图层时切换它的状态。

    # Toggle states on tap
    settings.onTap ->
        settings.stateCycle()

### 示例：链式动画

你可以使用动画事件来链式地链接动画，比如当你使用 `AnimationEnd` 监听到一个动画结束时可以立即开始另一个动画。

    # Animation Events
    layerA.onAnimationStart ->
        ...
    layerA.onAnimationEnd ->
        ...

下面的代码是一个简单的链式动画，每个动画都有一个动画结束事件 `AnimationEnd` ，所以你可以无线连接动画过程。

    layerA.animate
        x: 80
        options:
            curve: Bezier.ease

    layerA.onAnimationEnd ->
        layerA.animate
            x: 0
            options:
                curve: Bezier.ease

<a id="draggable"></a>
## 拖放

##### 可拖动图层可以模拟物理的拖动效果，并且有一些自定义属性能够让你做一些不一样的事情。通过定义拖动的速度、方向，你可以实现一些特别的拖动效果。

#### 开始

让我们一起来创建一个可拖动图层。这很简单，你只需要设置它的 `draggable.enabled` 为 `true` 。现在，你可以用鼠标把它拖来拖去了。

你可以通过禁用水平或垂直方向的拖动，来限定可拖动的方向，他们默认都是开启的。你还可以定义拖动的速度，让图层在被拖动时做加速运动或者减速运动。

    # Make the layer draggable
    layerA.draggable.enabled = true

    # Prevent vertical dragging
    layerA.draggable.horizontal = true
    layerA.draggable.vertical = false

    # Alternative way by setting the speed
    layerA.draggable.speedX = 1
    layerA.draggable.speedY = 0

#### 范围

在大部分的场景下，你都是需要限定拖动范围的。比如，在常见的下拉刷新交互中，一般你最大只能拖动一定的距离，我们可以通过设置 `constraints` 来限定范围。

`constraints` 中包含 `x` 、`y` 、`width` 和 `height` 四个属性，你可以想象通过这四个值新画了一个图层，而这个新图层就是可拖动图层的可拖动范围。

    # Make the layer draggable
    layerA.draggable.enabled = true

    # Set the constraints frame
    layerA.draggable.constraints =
        x: 0
        y: 0
        width: 160
        height: 80

### 拖动超出、弹性和动量模拟

你应该都熟悉这几个术语，但可能不知道名字而已。让我们一个个看一下。

一个图层可以被拖出限定的区域，尽管你一放手它又跑了回去。这就叫做 `overdrag` 。想一下 iOS 的 Safari 浏览器，你上下拖动一个网页时有时候可以让它超出顶部或者底部。

当你朝着一个方向拖动图层，等它到达边界时会反弹回来，这就是 `bounce` ，这有点像橡皮筋。

最后，当你设置它的动量模拟 `momentum` 为 `false` 之后，虽然你还可以拖动它，但是却没有了在物理空间中拖动真实材料的感觉了。`momentum` 和 `bounce` 属性也可以自定义，你可以看看这个[示例](https://framer.cloud/vJWUh)。

    # Disable overdrag
    layerA.draggable.overdrag = false

    # Disable bounce
    layerA.draggable.bounce = false

    # Disable momentum
    layerA.draggable.momentum = false

### 事件

关于拖动有三个基本事件可以监听：`DragStart`、`DragMove` 和 `DragEnd` 。还有一个移动事件，它会在图层移动时触发。它不同于 `DragMove` 事件，因为它还包含图层被松开后的动量模拟动画。

    # Start dragging
    layerA.onDragStart ->
        layerA.animate
            scale: 1.1

    # After dragging
    layerA.onDragEnd ->
        layerA.animate
            scale: 1

### 拖动动画

除了上述的事件以外，在你设置 `momentum` 和 `bounce` 为 `true` 时还有两个特殊的事件：`DragAnimationDidStart` 和 `DragAnimationDidEnd` 。他们在拖动结束，也就是你松开鼠标之后，当图层仍然在运动时被触发。

    # After DragEnd, the DragAnimation starts
    layerA.onDragAnimationStart ->
        layerA.animate
            scale: 0.8

    # Starts with the momentum and bounce
    layerA.onDragAnimationEnd ->
        layerA.animate
            scale: 1

<a id="pinchable"></a>
## 可捏放

##### 可捏放图层可以被两指缩放或者旋转。通常我们在地图或相册应用中会看到这种操作，用来缩放或导航。

在 Framer 中，你可以按住 `alt` 键，然后移动鼠标，这样就可以在电脑上模拟两个触控点了。就像允许图层拖放一样，你可以设置图层的 `pinchable.enabled` 为 `true` 来开启图层的可捏放。

    layerA.pinchable.enabled = true

可捏放图层的可捏放特性有两个属性：`scale` 和 `rotate`，默认开启可捏放时它俩都会被开启。如果禁止了 `sacle` ，那么你只能对图层进行两指旋转，反之亦然。

    # Disable scale on pinch
    layerA.pinchable.scale = false

    # Disable rotation on pinch
    layerA.pinchable.rotate = false

### 捏放事件

关于捏放有三个基本事件：`onPinch`、`onPinchStart` 和 `onPinchEnd` 。让我们来用一下最后一个事件，开启图层可捏放，这是我们可以对图层进行两指捏放或旋转，然后在捏放事件结束时让他恢复原状。

    # Enable pinching
    layerA.pinchable.enabled = true

    # Animate back to original position
    layerA.onPinchEnd ->
        layerA.animate
            scale: 1
            rotation: 0
            options:
                curve: Spring(damping: 0.5)
                time: 0.5

### 平移事件

如果你同时开启了图层的可拖动和可捏放，那么这个图层就变成可平移的了。平移事件和拖动事件类似，唯一不同点在于它是多指拖动的。你可以使用 `onPan` 来检测平移事件。

    # Enable panning
    layerA.draggable.enabled = true
    layerA.pinchable.enabled = true

    # Animate back to original position
    layerA.onDragEnd ->
        layerA.animate
            scale: 1
            rotation: 0
            options:
                curve: Spring(damping: 0.5)
                time: 0.5

<a id="components"></a>
## 组件

##### 所谓组件，就是一个拥有很多图层，而且自带一些交互效果的组合。就像滑块组件，它可以帮助你快速创建一个滑块，而不需要从零开始一个个创建哪些图层。组件都是可以完全自定义的，因此你可以大胆地使用它们创造意想不到的效果。

Framer 中包含这些组件，下面我们简单介绍一下 Flow、Scroll 、Page 和 Slider 组件。

* **FlowComponent**
* **ScrollComponent**
* **PageComponent**
* **SliderComponent**
* **RangeSliderComponent**
* **MIDIComponent**

<a id="flow"></a>
## 流组件

##### 流组件可以帮助你快速创建多界面跳转，尤其对于将一些静态界面串联起来变成一个可交互的流程很有用。而且，流组件会保存你的页面跳转记录，你可以很方便的实现前进或回退。流组件提供的效果和原生 APP 一样过渡自然。当切换页面时，当前页面会自动移动到屏幕之外，而使用弹出层比如一个模态框时，下面会自动加上一个半透明的深色背景。

现在让我们一起给流组件添加第一个页面。你只需要使用 `showNext` 方法就可以把一个图层添加进去，第一次添加的图层不会有动画效果。

    # Create FlowComponent, show layerA
    flow = new FlowComponent
    flow.showNext(layerA)

### 切换界面

你可以使用 `showNext` 切换界面。

    # Create FlowComponent, show layer
    flow = new FlowComponent
    flow.showNext(layerA)

    # Switch screens on click
    layerA.onClick ->
        flow.showNext(layerB)

Framer 会记录你的界面切换路径，所以你可以使用 `showPrevious` 方法来回到上一个界面。

    # Switch to next screen
    layerA.onClick ->
        flow.showNext(layerB)

    # Switch to previous screen
    layerB.onClick ->
        flow.showPrevious()

### 浮层

使用下面的弹出浮层方法，你可以弹出任何图层。当浮层弹出时下面会自动被添加一个半透明的深色背景，一般我们使用浮层来显示一些非整页的内容，比如侧边栏或者是一个操作列表，你可以使用下面的方法来实现不同方向弹出。

* **showOverlayCenter**
* **showOverlayTop**
* **showOverlayRight**
* **showOverlayBottom**
* **showOverlayLeft**


    # Create FlowComponent
    flow = new FlowComponent

    # Modal and button are set up in the design tab

    # Switch back
    button.onClick ->
        flow.showOverlayCenter(modal)

### 可滚动

添加进流组件的页面图层如果超出了屏幕的宽高，会自动变成可滚动的。如果这个图层的高度超出了流组件的高度，那么就可以垂直滚动它；如果这个图层的宽度超出了流组件的宽度，那么就可以水平滚动它。你可以通过 `flow.scroll` （ flow 是你给流组件起的变量名）来获取到这个滚动组件，所有滚动组件的属性和事件都可以使用。

处于画板顶部和底部的图层会被自动识别为顶栏和低栏，比如我们常用的底部选项卡菜单和顶部导航条。不过只有当你的画板高度超出设备宽度时才会生效。

当然，你也可以使用流组件的 `footer` 或 `header` 属性来给它添加顶栏和低栏。这样添加的顶栏或底栏会一直固定在屏幕的上边缘或下边缘，即使跳转页面。

    # Set a fixed navigation bar (on top)
    flow.header = flowBar

    # Set a fixed tab bar (on bottom)
    flow.footer = tabBar

### 可滚动示例

你可以看看下面这个示例，观察一下设计模式下的画板是怎样变成可滚动的页面的，而它顶部和底部的图层又是如何变成固定的顶栏和底栏的。

#### [打开示例](https://framer.cloud/BXOXn)

<a id="scroll"></a>
## 滚动组件

##### 也许你已经对 iOS 内的平滑滚动很熟悉了，而实现它好像需要模拟好多现实世界中的物理状态，比如阻力、反弹等等。不过没关系，我们给你封装了滚动组件，替你完成了内部复杂的细节，你只需要对它进行一些重新定制就可以简单地实现类似效果。

一个滚动组件由两个图层组成，一个是最外层的图层也就是这个滚动组件本身，它就像是处于下方的一个遮罩层。

第二个图层是里面的内容图层，它已经被设置为可拖动了，而且包含了一个预设的滑动范围。它的尺寸是根据它的子图层计算得来的，一般情况下和你插入的图层一样大。

    # Create a ScrollComponent
    scroll = new ScrollComponent
        size: 120

    # Assign the content layers
    layerA.parent = scroll.content

    layerB.parent = scroll.content

和图层的可滚动属性一样，你可以给他限定可滚动方向。

    scroll.scrollHorizontal = true
    scroll.scrollVertical = false

### 包裹

给你的静态设计图赋予生命的一种好方法就是让它可以滚动，而让一个图层可滚动最简单的方法就是使用一个滚动组件包裹它，一般我们使用 `ScrollComponent.wrap()` 方法。

    # Wrap the content layers
    scroll = ScrollComponent.wrap(content)

### 内容嵌入

如果你想要给内嵌的内容周围添加一些空间，你可以使用 `contentInset` 属性。想想一下如果在一个列表的顶部有一个顶栏，你不想让用户拖动顶栏时列表也滑动，就可以使用这个属性》一个常见的例子是[ Twitter 的 iOS 客户端信息流滚动](https://framer.cloud/zpfFY)。

    # Create a ScrollComponent
    scroll = new ScrollComponent
        width: 120
        height: 120
        scrollHorizontal: false

    # Define the contentInset
    scroll.contentInset =
        top: 40
        bottom: 40
        right: 0
        left: 0

### 事件

滚动有三个基本事件：`ScrollStart` 、`Scroll`（或 `ScrollMove` ）和 `ScrollEnd` 。有了这些事件，你可以监听它们，然后获得当前滚动的坐标值。比如，你可以通过判断垂直滚动距离 `scroll.scrollY` 达到一定值之后才开始执行一个动画。

    # Create a ScrollComponent
    scroll = new ScrollComponent
        scrollHorizontal: false

    # Listen to the Scroll event
    scroll.onScroll ->
        if scroll.scrollY < -10

            layerA.animate
                scale: 1

### 滚动动画

和可拖动图层一样，如果开启了动量和弹性模拟我们还可以监听两个特别事件：`ScrollAnimationDidStart` 和 `ScrollAnimationDidEnd` ，它们都是在手指松开拖动结束之后发生的。

    # After Scroll, the ScrollAnimation starts
    scroll.onScrollAnimationDidStart ->
        layer.animate
            width: 100

    # After the scroll animation
    scroll.onScrollAnimationDidEnd ->
        layer.animate
            width: 120

<a id="page"></a>
## 页面组件

##### 页面组件可以帮助你轻而易举地把多个图层串联起来，形成一个整体的轮播或页面滑动。他承担了内部复杂的计算，让你可以聚焦于体验方面的调整。

页面组件可以让你轻松地在多个页面之间进行滑动切换，它是基于滚动组件的。

    # Create a PageComponent
    page = new PageComponent

    # Define first page layer
    layerA.parent = page.content

    # Define second page layer place it to the right
    layerB.parent = page.content
    layerB.x = 200

### 添加页面

你可以使用 `page.addPage()` 来添加页面，它会将你指定的图层添加在页面组件的右侧。当然，你也可以添加在底部。

    # Create a PageComponent
    page = new PageComponent

    # Add layerA to the right
    # Add layerB to the bottom
    page.addPage(layerA)
    page.addPage(layerB, "bottom")

### 包裹

如果想让你的静态图层变成可以滑动切换的几个页面，你只需要使用页面组件的 `PageComponent.wrap()` 方法来包裹它。

    # Wrap the content layer
    page = PageComponent.wrap(content)

### 排序与分类

检测页面是否正在切换可以使用 `change:currentPage` 事件，基于此你可以给页面组件添加切换的指示器。

    # Listen to any page switch
    page.on "change:currentPage", ->
        page.previousPage.animate
            opacity: 0.2
            scale: 0.8

        page.currentPage.animate
            opacity: 1
            scale: 1

也许你不一定想每次都从第一页开始，你可以使用 `snapToPage` 直接跳到某一页，可以以动画形式也可以直接跳过去。

    # Snap to the layer pageThree
    page.snapToPage(pageThree)

    # Snap with a custom animation curve
    page.snapToPage(pageTwo, true, curve: Spring)

### 页面索引

无论横滑还是纵滑，你都可以随时获取到页面索引。页面所引是当前页码减去 1 ，这意味着你的所有页面都是从第 0 页开始的，而不是 1 。你可以看一下下面这个页面指示器的示例，来了解如何使用页面组件的这些属性和方法。

    page.on "change:currentPage", ->
        for layer in indicators
            layer.animate
                opacity: 0.5

        current = page.currentPage
        i = page.horizontalPageIndex(current)

        indicators[i].animate
            opacity: 1

<a id="slider"></a>
## 滑块组件

##### 滑块组件可以被用来制作诸如进度条、音量调节、图像调节以及价格区间筛选等效果。有了滑块组件，当你设计调节类的动效时就不需要从零开始了。

滑块组件包含三个图层：组件自身、填充区和调节把手。其自身是一个滑槽，把手可以在上面滑动用来调整它的值，填充区则代表当前的值占了多少区域。你可以改变它的外观样式，就像改变其他图层外观样式一样。

滑块组件还有一些特殊的属性：

* **min** (最小值)
* **max** (最大值)
* **value** (初始值)
* **knobSize** (把手尺寸)


    # Create Slider
    slider = new SliderComponent
        min: 0
        max: 100
        value: 50
        knobSize: 40

    # Customize fill color
    slider.fill.backgroundColor = "#fff"

滑块本身就是个图层，所以你可以随意更改它的外观样式，对于把手和填充区也是一样的。

    # Customize slider
    slider.backgroundColor = "#DDD"

    # Customize fill
    slider.fill.backgroundColor = "#00AAFF"

    # Customize knob
    slider.knob.shadowY = 2
    Value Changes

使用 `onValueChange` 方法，你可以知道当前的值并在这个值改变时将其返回。

    # Create Slider
    slider = new SliderComponent
        min: 0
        max: 100
        value: 50

    # Get the current value
    slider.onValueChange ->
        print slider.value
