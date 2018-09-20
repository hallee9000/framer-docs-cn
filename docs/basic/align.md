# Align

Align函数帮助你迅速地把一个元素相对于它的父级摆放好位置。使用它们把一个图层放置在它的父级的上下左右或中间。它可以用在属性、状态或者动画中。

```coffeescript
    # Create a layer an position it in the center 
    layerA = new Layer
        x: Align.center
        y: Align.center
     
    # Create a state in the bottom right corner 
    layerA.states.add
        a:
            x: Align.right
            y: Align.bottom
        b:
            x: Align.left
            y: Align.top

    layerA.onTap -> layerA.states.next()
```

当你需要某个元素的坐标值的时候，Align函数可以动态地计算出它的坐标值。当你在某个状态把一个元素放在右下角，Align函数也可以计算，除非你在转换状态时改变了窗口大小。

你也可以选择性地使用偏移量。

```coffeescript
	layerA = new Layer
	    x: Align.center(-100) # 100 pixels left from the center 
	    y: Align.top(100) # 100 pixels from the top 
```

需要注意的是left和right只对x值起作用，top和bottom只对y值起作用，center对他们都起作用。在直接编程时，对比于layer.center() Align是一个更好的选择，因为它可以自适应。

<a id="bottom"></a>
## align.bottom(offset)

把图层置于它的父级的底部。如果没有父级，就放在设备屏幕底部。Bottom只对图层的y属性起作用，它可以作用在属性、状态及动画中。

### 参数

* **offset** — 数字(可选的)

```coffeescript
    layerA = new Layer
        y: Align.bottom
     
    layerB = new Layer
        y: Align.bottom(-100) # 100 pixels from the bottom 
```

<a id="center"></a>
## align.center(offset)

该方法可以把图层放在它的父图层的正中间。如果没有父图层，就默认放在屏幕正中间。在使用状态和动画的时候，它也可以作为一个属性值去使用。

### 参数

* **offset** — 数字(可选的).

```coffeescript
    layerA = new Layer
        x: Align.center
        y: Align.center
     
    layerB = new Layer
        x: Align.center(+100)
        y: Align.center(-100)
```

<a id="left"></a>
## align.left(offset)


把图层置于它的父图层的左侧，如果没有父图层，就默认放在屏幕左侧。这个方法只对x属性起作用。它也可以作为状态或者动画中的一个属性值。

### 参数

* **offset** — 数字(可选的).


    layerA = new Layer
        x: Align.left
     
    layerB = new Layer
        x: Align.left(100) # 100 pixels from the left 

<a id="right"></a>
## align.right(offset)

把图层置于它的父图层的右侧，如果没有父图层，就默认放在屏幕右侧。这个方法只对x属性起作用。它也可以作为状态或者动画中的一个属性值。

### 参数

* **offset** — 数字(可选的).


    layerA = new Layer
        x: Align.right
     
    layerB = new Layer
        x: Align.right(-100) # 100 pixels from the right 

<a id="top"></a>
## align.top(offset)

把图层置于它的父图层的顶部，如果没有父图层，就默认放在屏幕顶部。这个方法只对y属性起作用。它也可以作为状态或者动画中的一个属性值。

### 参数

* **offset** — 数字(可选的).


    layerA = new Layer
        y: Align.top
     
    layerB = new Layer
        y: Align.top(100) # 100 pixels from the top 