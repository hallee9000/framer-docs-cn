# Events

事件是可以监听的，通过监听事件你可以知到在什么时候发生了什么从而给于反馈。事件可以是用户引起的，比如一个触摸或者点击，也可以是动画所引起，比如动画结束也是一个事件。在Framer中，大多数对象都支持事件监听，但你用到最多的是监听图层上的事件。
>Events are things that you can listen for. They can originate from the user, like a touch or click, or from an animation that ends. Most objects support event listening in Framer, but you will most often listen for events on layers.

但一个事件监听函数被调用时，它的第一个参数一般是该事件信息，这些信息取决于事件类型，可能包含鼠标位置、鼠标增量等，第二个参数一般是你需要监听该事件的图层。
>When an event is called, the first argument is the event information. Depending on the event, this can contain mouse positions, mouse deltas etc. The second argument is always the layer that the event occurred to.

你可以使用`on`方法来监听一个事件：
>To listen for an event, you can use the on function:

    layerA = new Layer
    layerA.name = "Layer A"
     
    layerA.on Events.Click, (event, layer) ->
        print "Clicked", layer.name
     
    # 输出: "Clicked", "Layer A" 

停止监听一个事件，可以使用`off`方法：
>To stop listening for an event, you can use the off function:

    layerA = new Layer
    layerA.name = "Layer A"
     
    clickHandler = (event, layer) ->
        print "Clicked", layer.name
     
    layerA.on(Events.Click, clickHandler)
    layerA.off(Events.Click, clickHandler)

<a id="Tap"></a>
## Tap Events（触击事件）

触击事件在电脑上是点击事件（[Click](#events.click)），在手持设备上是触摸事件（[Touch](#events.touch)），它接受[手势事件属性](#events.properties)。
>Tap events receive the gesture event properties.


* **Events.Tap** — 触击一个图层时。
* **Events.SingleTap** — 和Tap一样。
* **Events.DoubleTap** — 快速触击图层两次。


    layerA = new Layer
     
    layerA.on Events.Tap, (event) ->
        print "Tap"

    layerA = new Layer
     
    layerA.on Events.DoubleTap, (event) ->
        print "Double tap"

### Tap事件简写

    # For Events.Tap 
    layerA.onTap ->
        print "Tap"
     
    # For Events.SingleTap 
    layerA.onSingleTap ->
        print "Single tap"
     
    # For Events.DoubleTap 
    layerA.onDoubleTap ->
        print "Double tap"

<a id="ForceTap"></a>
## ForceTap Events（压力触摸事件）

压力触摸事件接受[手势事件属性](#events.properties)。
>ForceTap events receive the gesture event properties.

* **Events.ForceTap** — 压力触摸事件发生时。
* **Events.ForceTapChange** — 触摸的压感改变时。
* **Events.ForceTapStart** — 开始压力触摸时。
* **Events.ForceTapEnd** — 结束压力触摸时。


    layerA = new Layer
     
    layerA.on Events.ForceTap, (event) ->
        print "Force tap"

### ForceTap事件简写

    # For Events.ForceTap 
    layerA.onForceTap ->
        print "Force tap"
     
    # For Events.ForceTapChange 
    layerA.onForceTapChange ->
        print "Change of force tap pressure"
     
    # For Events.ForceTapStart 
    layerA.onForceTapStart ->
        print "Start force tap"
     
    # For Events.ForceTapEnd 
    layerA.onForceTapEnd ->
        print "End force tap"

<a id="LongPress"></a>
## LongPress Events（长按事件）

长按事件接受[手势事件属性](#events.properties)。
>LongPress events receive the gesture event properties.


* **Events.LongPress** — 长按事件发生时。
* **Events.LongPressStart** — 长按开始时。
* **Events.LongPressEnd** — 长按结束时。


    # Detect a long press 
    layer.on Events.LongPress, (event) ->
        print "Long press"

### LongPress事件简写

    # For Events.LongPress 
    layerA.onLongPress ->
        print "Long press"
     
    # For Events.LongPressStart 
    layerA.onLongPressStart ->
        print "Start long press"
     
    # For Events.LongPressEnd 
    layerA.onLongPressEnd ->
        print "End long press"

<a id="Swipe"></a>
## Swipe Events（扫滑事件）

滑动事件接受[手势事件属性](#events.properties)。
>Swipe events receive the gesture event properties.

### Basic

* **Events.Swipe** — 手指在一个图层上滑动时。
* **Events.SwipeStart** — 开始在图层上滑动时。
* **Events.SwipeEnd** — 结束在图层上滑动时。


    layerA = new Layer
     
    layerA.on Events.Swipe, (event) ->
        print event.distance

### Swipe事件简写

    # For Events.Swipe 
    layerA.onSwipe ->
        print "Currently swiping"
     
    # For Events.SwipeStart 
    layerA.onSwipeStart ->
        print "Start swiping"
     
    # For Events.SwipeEnd 
    layerA.onSwipeEnd ->
        print "End swiping"

### Up

* **Events.SwipeUp** — 向上滑动时。
* **Events.SwipeUpStart** — 向上滑动开始时。
* **Events.SwipeUpEnd** — 向上滑动结束时。


    layerA = new Layer
     
    layerA.on Events.SwipeUp, (event) ->
        print event.distance

### SwipeUp事件简写

    # For Events.SwipeUp 
    layerA.onSwipeUp ->
        print "Currently swiping up"
     
    # For Events.SwipeUpStart 
    layerA.onSwipeUpStart ->
        print "Start swiping up"
     
    # For Events.SwipeUpEnd 
    layerA.onSwipeUpEnd ->
        print "End swiping up"

### Right

* **Events.SwipeRight** — 向右滑动时。
* **Events.SwipeRightStart** — 向右滑动开始时。
* **Events.SwipeRightEnd** — 向右滑动结束时。


    layerA = new Layer
     
    layerA.on Events.SwipeRight, (event) ->
        print event.distance

### SwipeRight事件简写

    # For Events.SwipeRight 
    layerA.onSwipeRight ->
        print "Currently swiping right"
     
    # For Events.SwipeRightStart 
    layerA.onSwipeRightStart ->
        print "Start swiping right"
     
    # For Events.SwipeRightEnd 
    layerA.onSwipeRightEnd ->
        print "End swiping right"

### Down

* **Events.SwipeDown** — 向下滑动时。
* **Events.SwipeDownStart** — 向下滑动开始时。
* **Events.SwipeDownend** — 向下滑动结束时。


    layerA = new Layer
     
    layerA.on Events.SwipeDown, (event) ->
        print event.distance

### SwipeDown事件简写

    # For Events.SwipeDown 
    layerA.onSwipeDown ->
        print "Currently swiping down"
     
    # For Events.SwipeDownStart 
    layerA.onSwipeDownStart ->
        print "Start swiping down"
     
    # For Events.SwipeDownEnd 
    layerA.onSwipeDownEnd ->
        print "End swiping down"

### Left

* **Events.SwipeLeft** — 向左滑动时。
* **Events.SwipeLeftStart** — 向左滑动开始时。
* **Events.SwipeLeftEnd** — 向左滑动结束时。


    layerA = new Layer
     
    layerA.on Events.SwipeLeft, (event) ->
        print event.distance

### SwipeLeft事件简写

    # For Events.SwipeLeft 
    layerA.onSwipeLeft ->
        print "Currently swiping left"
     
    # For Events.SwipeLeftStart 
    layerA.onSwipeLeftStart ->
        print "Start swiping left"
     
    # For Events.SwipeLeftEnd 
    layerA.onSwipeLeftEnd ->
        print "End swiping left"

<a id="Pan"></a>
## Pan Events（滑动事件）

滑动事件接受[手势事件属性](#events.properties)。
>Pan events receive the gesture event properties.


* **Events.Pan** — 往任意方向滑动事件。
* **Events.PanStart** — 开始滑动时。
* **Events.PanMove** — 滑动事件发生的时候。
* **Events.PanEnd** — 结束滑动事件时。
* **Events.PanLeft** — 向左滑动时。
* **Events.PanRight** — 向右滑动时。
* **Events.PanUp** — 向上滑动时。
* **Events.PanDown** — 向下滑动时。


    layerA = new Layer
     
    # Detect a panning gesture 
    layerA.on Events.Pan, (event) ->
        print event.distance

### Pan事件简写

    # For Events.Pan 
    layerA.onPan ->
        print "Currently panning"
     
    # For Events.PanStart 
    layerA.onPanStart ->
        print "Start panning"
     
    # For Events.PanMove 
    layerA.onPanMove ->
        print "Currently panning"
     
    # For Events.PanEnd 
    layerA.onPanEnd ->
        print "End panning"
     
    # For Events.PanLeft 
    layerA.onPanLeft ->
        print "Panning left"
     
    # For Events.PanRight 
    layerA.onPanRight ->
        print "Panning right"
     
    # For Events.PanUp 
    layerA.onPanUp ->
        print "Panning up"
     
    # For Events.PanDown 
    layerA.onPanDown ->
        print "Panning down"

<a id="Pinch"></a>
## Pinch Events（双指捏放事件）

双指捏放事件接受[手势事件属性](#events.properties)。
>Pinch events receive the gesture event properties.

* **Events.Pinch** — 双指在屏幕上捏合或放远时。
* **Events.PinchStart** — 开始捏放时。
* **Events.PinchEnd** — 结束捏放时。


    layerA = new Layer
    layerA.pinchable.enabled = true
     
    layerA.on Events.Pinch, ->
        print layerA.scale, layerA.rotation

### Pinch事件简写

    # For Events.Pinch 
    layerA.onPinch ->
        print "Currently pinching"
     
    # For Events.PinchStart 
    layerA.onPinchStart ->
        print "Start pinching"
     
    # For Events.PinchEnd 
    layerA.onPinchEnd ->
        print "End pinching"

<a id="Scale"></a>
## Scale Events（缩放事件）

缩放事件接受[手势事件属性](#events.properties)。
>Scale events receive the gesture event properties.


* **Events.Scale** — 使用两指缩放图层时。
* **Events.ScaleStart** — 开始缩放时。
* **Events.ScaleEnd** — 结束缩放时。


    layerA = new Layer
    layerA.pinchable.enabled = true
     
    layerA.on Events.Scale, ->
        print layerA.scale

### Scale事件简写

    # For Events.Scale 
    layerA.onScale ->
        print "Currently scaling"
     
    # For Events.ScaleStart 
    layerA.onScaleStart ->
        print "Start scaling"
     
    # For Events.ScaleEnd 
    layerA.onScaleEnd ->
        print "End scaling"

<a id="Rotate"></a>
## Rotate Events（双指旋转事件）

旋转事件接受[手势事件属性](#events.properties)。
>Rotate events receive the gesture event properties.

* **Events.Rotate** — 使用两指旋转图层时。
* **Events.RotateStart** — 开始旋转时。
* **Events.RotateEnd** — 结束旋转时。


    layerA = new Layer
    layerA.pinchable.enabled = true
     
    layerA.on Events.Rotate, ->
        print layerA.rotation

### Rotate事件简写

    # For Events.Rotate 
    layerA.onRotate ->
        print "Currently rotating"
     
    # For Events.RotateStart 
    layerA.onRotateStart ->
        print "Start rotating"
     
    # For Events.RotateEnd 
    layerA.onRotateEnd ->
        print "End rotating"

<a id="Touch"></a>
## Touch Events（触摸事件）

* **Events.TouchStart** — 开始触摸/点击时。
* **Events.TouchMove** — 按住拖动或鼠标拖动时。
* **Events.TouchEnd** — 结束触摸/点击时。


    layerA = new Layer
 
    # Returns the event and the layer 
    layerA.on Events.TouchStart, (event, layer) ->
        print event, layer

### Touch事件简写

    # For Events.TouchStart 
    layerA.onTouchStart ->
        print "Start touch"
     
    # For Events.TouchMove     
    layerA.onTouchMove ->
        print "Touch move"
     
    # For Events.TouchEnd 
    layerA.onTouchEnd ->
        print "End touch"

<a id="Click"></a>
## Click Events（点击事件）

* **Events.Click** — 点击或触摸时（在手机上无延迟，电脑上会有300ms延迟用以确定是否是双击）。


    layerA = new Layer
     
    # Returns the event and the layer 
    layerA.on Events.Click, (event, layer) ->
        print event, layer

### Click事件简写

    # For Events.Click 
    layerA.onClick ->
        print "Click"

<a id="Mouse"></a>
## Mouse Events（鼠标事件）

* **Events.MouseUp** — 松开鼠标左键时。
* **Events.MouseDown** — 鼠标左键被按下时。
* **Events.MouseOver** — 鼠标指针移到图层上面时。
* **Events.MouseOut** — 鼠标指针移出图层上面时。
* **Events.MouseMove** — 鼠标指针移动时。
* **Events.MouseWheel** — 滚动鼠标滚轮时。


    layerA = new Layer
     
    # Returns the event and the layer 
    layerA.on Events.MouseOver, (event, layer) ->
        print event, layer

### Mouse事件简写

    # For Events.mouseup 
    layerA.onMouseUp ->
        print "mouseup"
     
    # For Events.MouseDown 
    layerA.onMouseDown ->
        print "mousedown"
     
    # For Events.MouseOver 
    layerA.onMouseOver ->
        print "mouseover"
     
    # For Events.MouseOut 
    layerA.onMouseOut ->
        print "mouseout"
     
    # For Events.MouseMove 
    layerA.onMouseMove ->
        print "mousemove"
     
    # For Events.MouseWheel 
    layerA.onMouseWheel ->
        print "mousewheel"

<a id="Animation"></a>
## Animation Events（动画事件）

* **Events.AnimationStart** — 一个动画开始时。
* **Events.AnimationStop** — 一个动画停止（不一定结束，`stop()`函数可以中途停止它）时。
* **Events.AnimationEnd** — 一个动画结束时。


    layerA = new Layer
     
    layerA.animate
        properties:
            x: 100
     
    # Returns the animation and the layer 
    layerA.on Events.AnimationEnd, (animation, layer) ->
        print animation, layer

### Animation事件简写

    # For Events.AnimationStart 
    layerA.onAnimationStart ->
        print "Animation started"
     
    # For Events.AnimationStop 
    layerA.onAnimationStop ->
        print "Animation stopped"
     
    # For Events.AnimationEnd     
    layerA.onAnimationEnd ->
        print "Animation ended"

<a id="State"></a>
## State Events（状态事件）

* **Events.StateWillSwitch** — 即将转换到另一个状态时。
* **Events.StateDidSwitch** — 刚好转换到另一个状态时。


    layerA = new Layer
     
    layerA.states.add
        rotate:
            rotation: 90
     
    layerA.states.switch("rotate")
     
    # 返回旧状态、新状态以及该图层的所有状态
    layerA.on Events.StateDidSwitch, (from, to, states) ->
        print from, to, states

### State事件简写

    # For Events.StateWillSwitch 
    layerA.onStateWillSwitch ->
        print "Will switch state"
     
    # For Events.StateDidSwitch 
    layerA.onStateDidSwitch ->
        print "Did switch state"

<a id="Drag"></a>
## Drag Events（拖放事件）

* **Events.Move** — 图层在移动时。
* **Events.DragStart** — 开始拖动图层时。
* **Events.Drag** — 图层被拖动时。
* **Events.DragEnd** — 结束拖动图层时。
* **Events.DragAnimationStart** — 开始弹性/动量动画时。
* **Events.DragAnimationEnd** — 结束弹性/动量动画时。
* **Events.DirectionLockStart** — 开始锁定方向时。


    layerA = new Layer
    layerA.draggable.enabled = true
     
    # Returns the offset (x, y), layer.draggable and the layer 
    layerA.on Events.Move, (offset, draggable, layer) ->
        print offset, draggable, layer

    layerA = new Layer
    layerA.draggable.enabled = true
     
    # Returns the event, layer.draggable and the layer 
    layerA.on Events.DragStart, (event, draggable, layer) ->
        print event, draggable, layer

### Drag事件简写

    # For Events.Move 
    layerA.onMove ->
        print "Moving"
     
    # For Events.DragStart 
    layerA.onDragStart ->
        print "Start of drag"
     
    # For Events.Drag     
    layerA.onDrag ->
        print "Dragging"
     
    # For Events.DragEnd     
    layerA.onDragEnd ->
        print "End of drag"
     
    # For Events.DragAnimationStart     
    layerA.onDragAnimationStart ->
        print "Start of drag animation"
     
    # For Events.DragAnimationEnd     
    layerA.onDragAnimationEnd ->
        print "End of drag animation"
     
    # For Events.DirectionLockStart     
    layerA.onDirectionLockStart ->
        print "Start of direction lock"

<a id="Scroll"></a>
## Scroll Events（滚动事件）

* **Events.Move** — 图层在移动时。
* **Events.ScrollStart** — 开始滚动时。
* **Events.Scroll** — 图层滚动时。
* **Events.ScrollEnd** — 图层结束滚动时。
* **Events.ScrollAnimationDidStart** — 弹性/动量动画开始时。
* **Events.ScrollAnimationDidEnd** — 弹性/动量动画结束时。


    scroll = new ScrollComponent
    layerA = new Layer
        parent: scroll.content
     
    # Returns the event, layer.draggable and the layer 
    scroll.on Events.ScrollStart, (event, draggable, layer) ->
        print event, draggable, layer

### Scroll事件简写

    # For Events.Move 
    scroll.onMove ->
        print "Moving"
     
    # For Events.ScrollStart 
    scroll.onScrollStart ->
        print "Start of scroll"
     
    # For Events.Scroll     
    scroll.onScroll ->
        print "Scrolling"
     
    # For Events.ScrollEnd     
    scroll.onScrollEnd ->
        print "End of scroll"
     
    # For Events.ScrollAnimationDidStart     
    scroll.onScrollAnimationDidStart ->
        print "Start of scroll animation"
     
    # For Events.ScrollAnimationDidEnd     
    scroll.onScrollAnimationDidEnd ->
        print "End of scroll animation"

<a id="EdgeSwipe"></a>
## EdgeSwipe Events（边缘扫滑事件）

边缘扫滑事件接受[手势事件属性](#events.properties)。
>EdgeSwipe events receive the gesture event properties.

### Basic

* **Events.EdgeSwipe** — 从屏幕的某一个边缘扫滑时。
* **Events.EdgeSwipeStart** — 开始边缘扫滑时。
* **Events.EdgeSwipeEnd** — 结束边缘扫滑时。


    # Swipe from any edge of the screen 
    Screen.on Events.EdgeSwipe, (event) ->
        print event.distance

### EdgeSwipe事件简写

    # For Events.EdgeSwipe 
    Screen.onEdgeSwipe ->
        print "Swiping from edge"
     
    # For Events.EdgeSwipeStart 
    Screen.onEdgeSwipeStart ->
        print "Start swiping from edge"
     
    # For Events.EdgeSwipeEnd 
    Screen.onEdgeSwipeEnd ->
        print "End swiping from edge"

### Top

* **Events.EdgeSwipeTop** — 从上边缘扫滑时。
* **Events.EdgeSwipeTopStart** — 开始从上边缘扫滑时。
* **Events.EdgeSwipeTopEnd** — 结束从上边缘扫滑时。


    # Swipe from the top edge of the screen 
    Screen.on Events.EdgeSwipeTop, (event) ->
        print event.distance

### EdgeSwipeTop事件简写

    # For Events.EdgeSwipeTop 
    Screen.onEdgeSwipeTop ->
        print "Swiping from top edge"
     
    # For Events.EdgeSwipeTopStart 
    Screen.onEdgeSwipeTopStart ->
        print "Start swiping from top edge"
     
    # For Events.EdgeSwipeTopEnd 
    Screen.onEdgeSwipeTopEnd ->
        print "End swiping from top edge"

### Right

* **Events.EdgeSwipeRight** — 从右边缘扫滑时。
* **Events.EdgeSwipeRightStart** — 开始从右边缘扫滑时。
* **Events.EdgeSwipeRightEnd** — 结束从右边缘扫滑时。


    # Swipe from the right edge of the screen 
    Screen.on Events.EdgeSwipeRight, (event) ->
        print event.distance

### EdgeSwipeRight事件简写

    # For Events.EdgeSwipeRight 
    Screen.onEdgeSwipeRight ->
        print "Swiping from right edge"
     
    # For Events.EdgeSwipeRightStart 
    Screen.onEdgeSwipeRightStart ->
        print "Start swiping from right edge"
     
    # For Events.EdgeSwipeRightEnd 
    Screen.onEdgeSwipeRightEnd ->
        print "Start swiping from right edge"

### Bottom

* **Events.EdgeSwipeBottom** — 从下边缘扫滑时。
* **Events.EdgeSwipeBottomStart** — 开始从下边缘扫滑时。
* **Events.EdgeSwipeBottomEnd** — 结束从下边缘扫滑时。


    # Swipe from the bottom edge of the screen 
    Screen.on Events.EdgeSwipeBottom, (event) ->
        print event.distance

### EdgeSwipeBottom事件简写

    # For Events.EdgeSwipeBottom 
    Screen.onEdgeSwipeBottom ->
        print "Swiping from bottom edge"
     
    # For Events.EdgeSwipeBottomStart 
    Screen.onEdgeSwipeBottomStart ->
        print "Start swiping from bottom edge"
     
    # For Events.EdgeSwipeBottomEnd 
    Screen.onEdgeSwipeBottomEnd ->
        print "End swiping from bottom edge"

### Left

* **Events.EdgeSwipeLeft** — 从左边缘扫滑时。
* **Events.EdgeSwipeLeftStart** — 开始从左边缘扫滑时。
* **Events.EdgeSwipeLeftEnd** — 结束从左边缘扫滑时。


    # Swipe from the left edge of the screen 
    Screen.on Events.EdgeSwipeLeft, (event) ->
        print event.distance

### EdgeSwipeLeft事件简写

    # For Events.EdgeSwipeLeft 
    Screen.onEdgeSwipeLeft ->
        print "Swiping from left edge"
     
    # For Events.EdgeSwipeLeftStart 
    Screen.onEdgeSwipeLeftStart ->
        print "Start swiping from left edge"
     
    # For Events.EdgeSwipeLeftEnd 
    Screen.onEdgeSwipeLeftEnd ->
        print "End swiping from left edge"

<a id="Transition"></a>
## Transition Events (过渡事件)

* **Events.TransitionStart** — 过渡开始事件.
* **Events.TransitionHalt** — 过渡中断事件，当一个过渡中断时发生。
* **Events.TransitionStop** — 过渡停止事件，当一个过渡完全完成时。
* **Events.TransitionEnd** — 过渡结束事件，当一个过渡完全完成时。


    layerA = new Layer
     
    flow = new FlowComponent
    flow.showOverlayRight(layerA)
     
    flow.on Events.TransitionStart, ->
        print "Transition started"

### Transition 事件简写

    # For Events.TransitionStart 
    flow.onTransitionStart ->
        print "Transition started"
     
    # For Events.TransitionHalt 
    flow.onTransitionHalt ->
        print "Transition halted"
     
    # For Events.TransitionStop 
    flow.onTransitionStop ->
        print "Transition stopped"
     
    # For Events.TransitionEnd 
    flow.onTransitionEnd ->
        print "Transition ended"

<a id="Value"></a>
## Value Events (值改变事件)

一般在滑块组件或者是范围组件中会用到值改变事件，而最小最大值事件一般只用于范围组件。
>The Value Change events can be used for the SliderComponent or the RangeSliderComponent. The min and max-value events can only be used with Range Sliders.


* **Events.SliderValueChange** — 滑块的值被改变时。
* **Events.SliderMinValueChange** — 最小值被改变时（只用于范围组件）。
* **Events.SliderMaxValueChange** — 最大值被改变时（只用于范围组件）。


    slider = new SliderComponent
        x: Align.center
        y: Align.center
     
    slider.on Events.SliderValueChange, ->
        print slider.value

### Slider 事件简写

    # For Events.SliderValueChange 
    slider.onValueChange ->
        print slider.value
     
    # For Events.SliderMinValueChange 
    range.onMinValueChange ->
        print range.minValue
     
    # For Events.SliderMaxValueChange 
    range.onMaxValueChange ->
        print range.maxValue

<a id="Change"></a>
## Change Events（属性改变事件）

`change`事件允许你监听一些属性在何时被改变，下面是所有你可以监听的属性值。
>The "change" event allows you to listen to properties as they're changing. Below is a full overview of properties you can listen for:

* **"change:x"** — x坐标改变。
* **"change:y"** — y坐标改变。
* **"change:point"** — 新的x、y坐标。
* **"change:width"** — 宽度变化。
* **"change:height"** — 高度变化。
* **"change:size"** — 尺寸变化。
* **"change:frame"** — 位置或尺寸变化。
* **"change:scale"** — 图层被缩放。
* **"change:rotation"** — 图层被旋转。
* **"change:borderRadius"** — 圆角半径变化。
* **"change:currentPage"** — 当前页变化。
* **"change:style"** — 新的样式声明。
* **"change:html"** — 新的HTML声明。
* **"change:children"** — 添加或者移除子图层。
* **"change:parent"** — 添加或者移除父图层。

举个例子，你可以在图层执行动画时获取它的`x`值变化。注意这里获取的是它真实可能包含小数的像素值。
>For example, you can get the x position of a layer while it's animating. Note that it'll return the exact, sub-pixel values.

    layerA = new Layer
     
    layerA.animate
        properties:
            x: 100
     
    layerA.on "change:x", ->
        print layerA.x

使用`change`事件，你可以结合`modulate`很容易地通过一个图层的属性变化来控制另一个图层。在下面的例子中，我们旋转一个图层时，另一个图层会对应水平移动。
>The "change" events can be used to link property changes to one another, with modulate. In the example below, we'll rotate the layer. The returned values are used to move the second layer horizontally.

    layerA = new Layer
    layerB = new Layer
        x: 100
 
    # We rotate layerA from 0 to 180 degrees. 
    layerA.animate
        properties:
            rotation: 180
     
    # When the rotation value from layerA changes 
    layerA.on "change:rotation", ->
     
        # Use the values to move layerB from 100 to 300 
        x = Utils.modulate(layerA.rotation, [0, 180], [100, 300], true)
        layerB.x = x

<a id="Properties"></a>
## Gesture Event Properties（手势事件属性）

每一个手势事件都会接收包含以下属性的一个对象。`touchCenter`、`touchDistance`、`touchOffset`、`scale`和`rotation`这几个属性只在多点触控的情况下才有。
>Every gesture receives an event object with the following set of properties. The touchCenter, touchDistance, touchOffset, scale and rotation properties only return values when using multi-touch Events.

### Positioning（位置）

* **event.point** — 当前鼠标或手指坐标值。
* **event.start** — 初始时鼠标或手指坐标值。
* **event.previous** — 前一次触发该事件时鼠标或手指坐标值。


    layerA = new Layer
    layerA.pinchable.enabled = true
     
    layerA.on Events.Pinch, (event) ->
        print event.point

### Offset（偏移）

* **event.offset** — 当前`x`和`y`的偏移量。
* **event.offsetTime** — 从开始到当前偏移的时间。
* **event.offsetAngle** — 从开始到当前偏移的角度。
* **event.offsetDirection** — 从开始到当前偏移的方向。


    layerA = new Layer
     
    layerA.on Events.Pan, (event) ->
        print event.offset

### Deltas（增量）

* **event.delta** — 距离上次事件`x`和`y`的偏移量。
* **event.deltaTime** — 距离上次事件偏移的时间。
* **event.deltaAngle** — 距离上次事件偏移的角度。
* **event.deltaDirection** — 距离上次事件偏移的方向。


    layerA = new Layer
     
    layerA.on Events.Swipe, (event) ->
        print event.delta

### Velocity & Force（速度和力量）

* **event.velocity** — 在`x`和`y`方向上的速度。
* **event.force** — 按压力度。


    layerA = new Layer
     
    layerA.on Events.Swipe, (event) ->
        print event.velocity

### Input（输入）

* **event.fingers** — 触控点数量。
* **event.touchCenter** — 触控的两指中心点坐标。
* **event.touchDistance** — 触控的两指距离。
* **event.touchOffset** — 触控的两指在`x`和`y`方向上的偏移。


    layerA = new Layer
     
    layerA.on Events.Rotate, (event) ->
        print event.fingers

### Scale & Rotation（缩放和旋转）

* **event.scale** — 两只缩放比例。
* **event.scaleDirection** — 当前缩放方向（`up`或`down`）。
* **event.rotation** — 两指旋转角度。


    layerA = new Layer
    layerA.pinchable.enabled = true
     
    layerA.on Events.Pinch, (event) ->
        print event.scaleDirection

<a id="touchEvent"></a>
## Events.touchEvent(event)

从手机事件中提取出触摸事件。
>Extract the touch event from a given event on mobile.

    layerA = new Layer
     
    layerA.on Events.Click, (event, layer) ->
        myTouchEvent = Events.touchEvent(event)

<a id="wrap"></a>
## Events.wrap(event)

将一个DOM包裹，用以跟踪在它身上发生的事件并在需要时销毁它们。如果你想给一个元素绑定事件，你可以这样写：
>Wrap a given DOM Element so we can keep track of the events and destroy them when needed. If you want to bind events to arbitrary dom element you should use this.

    Events.wrap(window).addEventListener "resize", (event) ->
        print "Page is resizing"
