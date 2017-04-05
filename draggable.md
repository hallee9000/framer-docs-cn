# Draggable

图层可以被垂直拖放，也可以被水平拖放，或者同时垂直水平拖放。在拖放时还可以模拟因惯性晃来晃去的效果。如果想让拖放在某个位置停止，你还可以限定拖放的区域范围。虽然限定了拖放范围，但还是可以允许其被拖拽出去，但是默认地它会被弹回来。

<a id="draggable.enabled"></a>
## layer.draggable.enabled &lt;布尔值&gt;

让图层可已以被拖放。

    layerA = new Layer
    layerA.draggable.enabled = true

<a id="draggable.horizontal"></a>
## layer.draggable.horizontal &lt;布尔值&gt;

开启或者关闭水平方向的拖放。

    layerA = new Layer
    layerA.draggable.enabled = true
 
    #Disable horizontal dragging 
    layerA.draggable.horizontal = false

<a id="draggable.vertical"></a>
## layer.draggable.vertical &lt;布尔值&gt;

开启或者关闭垂直方向的拖放。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    #Disable vertical dragging 
    layerA.draggable.vertical = false

<a id="draggable.speedX"></a>
## layer.draggable.speedX &lt;数字&gt;

改变水平方向拖动的速度。它的值是鼠标每移动一像素被拖动元素所移动的像素值，默认值是1。当设置的值小于1时，拖动时元素移动距离将会小于鼠标移动距离。当其值为0时，水平方向拖拽就被禁止了。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    # Make horizontal dragging slow 
    layerA.draggable.speedX = 0.1
     
    # Make horizontal dragging fast 
    layerA.draggable.speedX = 10

<a id="draggable.speedY"></a>
## layer.draggable.speedY &lt;数字&gt;

改变垂直方向拖动的速度。它的值是鼠标每移动一像素被拖动元素所移动的像素值，默认值是1。当设置的值小于1时，拖动时元素移动距离将会小于鼠标移动距离。当其值为0时，垂直方向拖拽就被禁止了。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    # Make vertical dragging slow 
    layerA.draggable.speedY = 0.1
     
    # Make vertical dragging fast 
    layerA.draggable.speedY = 10

<a id="draggable.constraints"></a>
## layer.draggable.constraints &lt;对象&gt;

拖拽区域，即限制图层可以被拖动的范围。如果你给constraints设置了x和y属性，那么图层在DragStart（开始拖动）时会自动定位到这个坐标点，在你点击时它就会以过渡动画的形式移动过去。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    # Set dragging constraints 
    layerA.draggable.constraints =
        x: 0
        y: 0
        width: 200
        height: 200

<a id="draggable.constraintsOffset"></a>
## layer.draggable.constraintsOffset &lt;对象&gt;

获取可拖动图层相对于其拖动范围的位置偏移。如果你将constraints设置为{ x: 100, y: 100 }，而图层默认的初始位置在坐标原点（0,0），此时就可以通过constraintsOffset来计算他当前相对于拖拽区域的偏移，结果是{ x:-100, y:-100 } 。当你拖动它时他就会立即被弹回到拖拽区域。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    # Set dragging constraints 
    layerA.draggable.constraints =
        x: 100
        y: 100
        width: 200
        height: 200
 
    # Get the constraintsOffset 
    print layerA.draggable.constraintsOffset
 
    # Returns { x:-100, y:-100 } 

<a id="draggable.isBeyondConstraints"></a>
## layer.draggable.isBeyondConstraints &lt;布尔值&gt;

查看当前可拖拽图层是否超出了拖拽区域（只读）。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    # Set dragging constraints 
    layerA.draggable.constraints =
        x: 100
        y: 100
        width: 400
        height: 400
 
    # On move, see if the layer is beyond constraints or not 
    layerA.on Events.Move, ->
        print layerA.draggable.isBeyondConstraints

<a id="draggable.overdrag"></a>
## layer.draggable.overdrag &lt;布尔值&gt;

启用或禁用是否允许超出拖拽区域。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    layerA.draggable.constraints =
        x: 0
        y: 0
        width: 200
        height: 200
     
    # Disable dragging beyond constraints 
    layerA.draggable.overdrag = false

<a id="draggable.overdragScale"></a>
## layer.draggable.overdragScale &lt;数字&gt;

设置超出拖拽区域时的拖拽阻力。其值是一个0到1的数字，默认为0.5。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    layerA.draggable.constraints =
        x: 0
        y: 0
        width: 200
        height: 200
 
    # Increase resistance when dragging beyond constraints 
    layerA.draggable.overdragScale = 0.25

<a id="draggable.momentum"></a>
## layer.draggable.momentum &lt;布尔值&gt;

开启或禁用拖拽时的动量/惯性模拟，默认是开启的。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    # Disable momentum 
    layerA.draggable.momentum = false

<a id="draggable.momentumOptions"></a>
## layer.draggable.momentumOptions &lt;对象&gt;

拖拽后动量模拟的详细设置。

    layerA = new Layer
    layerA.draggable.enabled = true
         
    # Define friction and tolerance of momentum 
    layerA.draggable.momentumOptions =
        friction: 2.1
        tolerance: 0.1

<a id="draggable.bounce"></a>
## layer.draggable.bounce &lt;布尔值&gt;

当拖动超出拖拽区域时，动量模拟是否启用弹性动画。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    layerA.draggable.constraints =
        x: 0
        y: 0
        width: 200
        height: 200
 
    # Snap back after dragging beyond constraints 
    layerA.draggable.bounce = false

<a id="draggable.bounceOptions"></a>
## layer.draggable.bounceOptions &lt;对象&gt;

当拖动超出拖拽区域时，动量模拟的弹性动画详细设置。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    layerA.draggable.constraints =
        x: 0
        y: 0
        width: 200
        height: 200
     
    # Define friction, tension and tolerance of bounce 
    layerA.draggable.bounceOptions =
        friction: 40,
        tension: 200,
        tolerance: 0.0001

<a id="draggable.velocity"></a>
## layer.draggable.velocity &lt;对象&gt;

当前拖拽图层的速度，它是只读的。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    # On DragMove, print the x and y velocity 
    layerA.draggable.on Events.DragMove, ->
        print layerA.draggable.velocity

<a id="draggable.direction"></a>
## layer.draggable.direction <string>

当前拖拽的方向，会返回"up", "down", "left" 或 "right"中的一个，它也是只读的。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    # Print the current direction 
    layerA.on Events.DragMove, ->
        print layerA.draggable.direction

<a id="draggable.angle"></a>
## layer.draggable.angle &lt;数字&gt;

当前拖动的角度（角度制），它是只读的。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    # Print the current angle 
    layerA.on Events.DragMove, ->
        print layerA.draggable.angle

<a id="draggable.updatePosition"></a>
## layer.draggable.updatePosition(point)

这个方法可以让你覆盖之前设置的最终值。你可以给拖动添加自定义行为，让该图层在固定的距离范围内迅速移动。

### 参数

* **point** — An object with x and y properties.


    layerA = new Layer
    layerA.draggable.enabled = true
     
    # Round numbers to a set amount 
    round = (number, nearest) ->
        Math.round(number / nearest) * nearest
     
    # Drag in increments of 20px 
    layerA.draggable.updatePosition = (point) ->
        point.x = round(point.x, 20)
        point.y = round(point.y, 20)
        return point

<a id="draggable.directionLock"></a>
## layer.draggable.directionLock &lt;布尔值&gt;

在拖动距离超过某一上限之后，限定你只能在垂直和水平中的一个方向进行拖动。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    # Allow dragging only in one direction at a time 
    layerA.draggable.directionLock = true

<a id="draggable.directionLockThreshold"></a>
## layer.draggable.directionLockThreshold &lt;对象&gt;

锁定方向的上限。x和y的值代表在它锁定方向之前你可以在两个方向上拖动的距离。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    # Snap horizontally after dragging 50px 
    # Snap vertically instantly 
    layerA.draggable.directionLock = true
     
    layerA.draggable.directionLockThreshold =
        x: 50
        y: 0

<a id="draggable.pixelAlign"></a>
## layer.draggable.pixelAlign &lt;布尔值&gt;

在拖动时是否对齐像素，用以取消子像素抗锯齿。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    # Snap to pixel while dragging 
    layerA.draggable.pixelAlign = true

<a id="draggable.isDragging"></a>
## layer.draggable.isDragging &lt;布尔值&gt;

判断现在某个图层是否正在被拖动（松开后动画时返回的是false），它是只读的。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    # Check if the layer is being dragged 
    layerA.on Events.DragMove, ->
        print layerA.draggable.isDragging

<a id="draggable.isAnimating"></a>
## layer.draggable.isAnimating &lt;布尔值&gt;

判断当前图层是否正在进行模拟动量或弹性动画，它是只读的。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    # Check if the layer is animating 
    layerA.on Events.DragMove, ->
        print layerA.draggable.isAnimating

<a id="draggable.isMoving"></a>
## layer.draggable.isMoving &lt;布尔值&gt;

判断当前图层是否在移动，无论是因为拖动移动还是因为模拟动量或弹性动画，它是只读的。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    # Check if the layer is moving 
    layerA.on Events.DragMove, ->
        print layerA.draggable.isMoving

<a id="draggable.offset"></a>
## layer.draggable.offset &lt;对象&gt;

获取当前可拖动图层相对于屏幕的位置信息（x和y坐标），它是只读的。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    # Get the x and y position of the layer 
    layerA.on Events.DragMove, ->
        print layerA.draggable.offset

<a id="draggable.layerStartPoint"></a>
## layer.draggable.layerStartPoint &lt;对象&gt;

获取开始拖动时该图层的位置信息（只读）。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    # On DragStart, get the current x and y position  
    layerA.on Events.DragStart, ->
        print layerA.draggable.layerStartPoint

<a id="draggable.cursorStartPoint"></a>
## layer.draggable.cursorStartPoint &lt;对象&gt;

获取开始拖动时光标相对于画布的位置信息（只读）。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    # On DragStart, get x and y position of the cursor 
    layerA.on Events.DragStart, ->
        print layerA.draggable.cursorStartPoint

<a id="draggable.layerCursorOffset"></a>
## layer.draggable.layerCursorOffset &lt;对象&gt;

获取光标相对于该可拖动图层的位置偏移。如果你拖动该图层的左上角，将会返回`{ x: 0, y: 0 }`（只读）。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    # Get the cursor position within the layer 
    layerA.on Events.DragStart, ->
        print layerA.draggable.layerCursorOffset

<a id="draggable.propagateEvents"></a>
## layer.draggable.propagateEvents &lt;布尔值&gt;

设置可拖动图层的事件传播属性，默认为`true`。当你在`ScrollComponents`和`PageComponents`等嵌套组件里面添加可拖动图层时，该属性就会派上用场。

比如说你想在`scroll.content`图层中添加一个可拖动图层。默认情况下，拖动该图层时`scroll.content`图层也会跟着被拖动，这是因为他们都监听到拖动事件了。

想要在拖动可拖动图层时让`scroll.content`保持不动，即阻止某个子图层的拖动事件传播到它的父图层，把`propagateEvents`设置为`false`就可以了，它对于所有嵌套图层都是有效的。

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
