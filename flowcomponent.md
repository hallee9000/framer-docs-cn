# FlowComponent

`FlowComponent`帮助你在不同页面之间过渡转换。它主要构建在两个功能之上：通过`showNext`跳到一个新页面，通过`showPrevious`跳回到上一个页面。你也可以使用它来设计一个[弹出层](/docs#flow.showOverlayCenter)，如模态框，或者[固定元素](/docs#flow.header)如切换标签。`FlowComponent`会触发过渡事件，点击[这里](/docs#events.transition)学习它。

>The FlowComponent helps you transition and navigate between multiple screens. It’s built on two basic functions: showNext to transition to a new layer, and showPrevious to cycle back through previous layers. You can also use it to design overlays like modals, and fixed elements like a tab bar. The FlowComponent fires Transition events. Learn more about them here.

### 属性

* **layer** — 执行跳转的图层对象。
* **options** — 一个包含动画选项的对象，比如动画时间、曲线等（可选）。


    # Create layer 
    layerA = new Layer
        size: Screen.size
     
    # Create FlowComponent 
    flow = new FlowComponent
     
    # Show the layer 
    flow.showNext(layerA, animate: true)

<a id="flowComponent.showNext"></a>
## flow.showNext(layer, options)

这个方法可以让你过渡到一个新图层。默认情况下，它将会以动画的形式过渡到新图层，除非是第一个添加到 `FlowComponent` 中的图层。当它的宽高超出父图层的大小，那么它是可以被滚动查看的，当然可以被自动检测到是水平还是垂直滚动。

>Transition to a new layer. By default, it will animate to the layer, except if it’s the first layer added to the FlowComponent. If the width or height of the layer exceeds that of its parent, it will become scrollable. It also automatically detects whether to become vertically or horizontally scrollable.

### 参数

* **layer** — 一个图层对象。
* **options.animate** — 布尔值，设置图层变换是否需要动画（可选）。
* **options.scroll** — 布尔值，设置图层是否可滚动（可选）。


    # Create layer 
    layerA = new Layer
        size: Screen.size
     
    # Create FlowComponent 
    flow = new FlowComponent
     
    # Show the layer 
    flow.showNext(layerA)

设置 `animate` 为 `false` 可以关闭动画，这样图层跳转就没有过渡效果了。

>Set animate to false to switch between layers without a transition.

    # Create layers 
    layerA = new Layer
        size: Screen.size
        backgroundColor: "#00AAFF"
     
    layerB = new Layer
        size: Screen.size
        backgroundColor: "#FFCC33"
     
    # Create FlowComponent and show layer 
    flow = new FlowComponent
    flow.showNext(layerA)
 
    # Instantly show layerB on click 
    layerA.onClick ->
        flow.showNext(layerB, animate: false)

<a id="flowComponent.showPrevious"></a>
## flow.showPrevious(options)

过渡到前一个图层，默认情况下是以动画的形式跳转的。

>Transition to the previous layer. By default, it will animate to the layer.

### 参数

* **options.animate** — 布尔值，设置图层变换是否需要动画（可选）。
* **options.scroll** — 布尔值，设置图层是否可滚动（可选）。


    # Create layer 
    layerA = new Layer
    layerB = new Layer
     
    # Create FlowComponent 
    flow = new FlowComponent
    flow.showNext(layerA)
     
    # Switch to layerA on click 
    layerA.onClick ->
        flow.showNext(layerB)
     
    # Return to the previous on click 
    layerB.onClick ->
        flow.showPrevious()

<a id="flowComponent.showOverlayCenter"></a>
## flow.showOverlayCenter(layer, options)

在屏幕正中间覆盖一个图层，就像模态对话框一样。
>Overlay a layer from the center, like a modal dialog.

### 参数

* **layer** — 一个图层对象。
* **options.animate** — 布尔值，设置图层变换是否需要动画（可选）。
* **options.scroll** — 布尔值，设置图层是否可滚动（可选）。
* **options.modal** — 布尔值，设置该模态框是否可点击遮罩层关闭（可选）。


    # Create layer 
    layerA = new Layer
        size: Screen.size
     
    # Create FlowComponent 
    flow = new FlowComponent
     
    # Overlay the modal layer 
    flow.showOverlayCenter(layerA)

默认情况下参数 `modal` 被设置为 `false` ，如果你不想让它的遮罩层被点击时关闭并且能够跳转到前一页，你可以将其设为 `true`。
>The modal argument is set to false by default. If you would like the overlay to be clickable and return to the previous screen, you can enable this boolean.

    # Create layer 
    layerA = new Layer
        backgroundColor: "#00AAFF"
        size: Screen.size
     
    layerB = new Layer
        borderRadius: 40
        backgroundColor: "#FFF"
        size: 500
     
    # Create FlowComponent 
    flow = new FlowComponent
    flow.showNext(layerA)
     
    # Show modal, overlay is not clickable 
    layerA.onClick ->
        flow.showOverlayCenter(layerB, modal: true)

<a id="flowComponent.showOverlayTop"></a>
## flow.showOverlayTop(layer, options)

从顶部覆盖一个图层，类似于消息提示。
>Overlay a layer from the top, like a notification screen.

### 参数

* **layer** — 一个图层对象。
* **options.animate** — 布尔值，设置图层变换是否需要动画（可选）。
* **options.scroll** — 布尔值，设置图层是否可滚动（可选）。
* **options.modal** — 布尔值，设置该模态框是否可点击遮罩层关闭（可选）。


    # Create layer 
    layerA = new Layer
        size: Screen.size
     
    # Create FlowComponent 
    flow = new FlowComponent
     
    # Overlay the layer 
    flow.showOverlayTop(layerA)

<a id="flowComponent.showOverlayRight"></a>
## flow.showOverlayRight(layer, options)

从右侧覆盖一个图层。
>Overlay a layer from the right.

### 参数

* **layer** — 一个图层对象。
* **options.animate** — 布尔值，设置图层变换是否需要动画（可选）。
* **options.scroll** — 布尔值，设置图层是否可滚动（可选）。
* **options.modal** — 布尔值，设置该模态框是否可点击遮罩层关闭（可选）。


    # Create layer 
    layerA = new Layer
        size: Screen.size
     
    # Create FlowComponent 
    flow = new FlowComponent
     
    # Overlay the layer 
    flow.showOverlayRight(layerA)

<a id="flowComponent.showOverlayBottom"></a>
## flow.showOverlayBottom(layer, options)

从底部覆盖一个图层。
>Overlay a layer from the bottom.

### 参数

* **layer** — 一个图层对象。
* **options.animate** — 布尔值，设置图层变换是否需要动画（可选）。
* **options.scroll** — 布尔值，设置图层是否可滚动（可选）。
* **options.modal** — 布尔值，设置该模态框是否可点击遮罩层关闭（可选）。


    # Create layer 
    layerA = new Layer
        size: Screen.size
     
    # Create FlowComponent 
    flow = new FlowComponent
     
    # Overlay the layer 
    flow.showOverlayBottom(layerA)

## flow.showOverlayLeft(layer, options)

Overlay a layer from the left.

Arguments

layer — A layer object.
options.animate — A boolean, sets whether the layer animates. (Optional)
options.scroll — A boolean, sets whether the layer becomes scrollable. (Optional)
options.modal — A boolean, sets whether the overlay becomes clickable. (Optional)
# Create layer 
layerA = new Layer
    size: Screen.size
 
# Create FlowComponent 
flow = new FlowComponent
 
# Overlay the layer 
flow.showOverlayLeft(layerA)

flow.transition(layer, transition, options)

Create a custom transition. The transitions use states internally to cycle back and forward. There are three layers (current, next and background) with two states each (back and forward). If you don’t define a specific state, the FlowComponent assumes you don’t want to animate that layer.

Arguments

layer — A layer object.
transition — A function with the animation states.
options.animate — A boolean, sets whether the layer animates. (Optional)
options.scroll — A boolean, sets whether the layer becomes scrollable. (Optional)
# Custom transition 
scaleTransition = (nav, layerA, layerB, overlay) ->
    transition =
        layerA:
            show:
                scale: 1.0
                opacity: 1
            hide:
                scale: 0.5
                opacity: 0
        layerB:
            show:
                scale: 1.0
                opacity: 1
            hide:
                scale: 0.5
                opacity: 0
 
# Create layers 
layerA = new Layer
    backgroundColor: "#00AAFF"
    size: Screen.size
 
layerB = new Layer
    backgroundColor: "#FFCC33"
    size: Screen.size
 
# Create FlowComponent 
flow = new FlowComponent
flow.showNext(layerA)
 
# Switch to layerB with custom transition 
layerA.onClick ->
    flow.transition(layerB, scaleTransition)

The custom transition is a function that returns an object with states. Inside the function you have access to the arguments current FlowComponent, layerA, layerB and the overlay. If you don’t pass states for layerA, layerB or the overlay, it will leave the layer as is on a transition.

flow.header <layer>

Add a sticky header to a scrollable screen, like a a fixed navigation bar.

# Create navigation layer 
navBar = new Layer
 
# Create FlowComponent 
flow = new FlowComponent
 
# Anchor layer to the top 
flow.header = navBar

flow.footer <layer>

Add a sticky footer to a scrollable screen, like a a fixed tab bar.

# Create tab bar layer 
tabBar = new Layer
 
# Create FlowComponent 
flow = new FlowComponent
 
# Anchor layer to the bottom 
flow.footer = tabBar

