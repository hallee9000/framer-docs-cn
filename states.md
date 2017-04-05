# States

图层状态时用来管理和组织一个图层不同的属性组合的。[animation](#animation)可以使用它作为一个动画目标，switch可以让你从一个状态跳到另一个，cycle可以让你的图层在一系列状态之间循环切换。
>Layer states manage and organize different combinations of layer properties. Animations can use them as a target. Switch lets you jump to another state instantly and cycle allows you to sequentially move from state to state.

你可以给一个状态定义任意的属性，比如它的位置坐标x和y。无法过渡变化的属性，比如一个图层的内部html，将会在状态切换动画最后直接变过去。
>You can add any layer property to a state, like x and y. Non-animatable layer properties like html will be set at the end of the state animation.

状态也可以设置动画选项，如延时、动画时长、运动曲线等，这样这个图层在任意状态之间切换时都会按照该选项来执行动画。
>States can have an animation options property. Which will be used whenever layers get animated to the defined state.

有三个预定义的状态你不可以使用或覆盖，因为它们在Framer中有特殊的用途。你可以通过`current`和`previous`来获取一个图层的当前状态名和前一个状态名。
>There are three pre-defined states that can't be overridden because they are already assigned to serve a purpose. You can get the state names for current and previous using their name property.

* **default** — 初始激活状态。
* **current** — 当前激活状态。
* **previous** — 之前激活的状态。

### 示例: 创建或者删除一个状态

    # Create a state 
    layerA.states.stateA =
        x: 100
     
    # Delete a state 
    delete layerA.states.stateA

### 示例: 拥有动画选项的状态定义

    # Create a state with animationOptions 
    layerA.states.stateA =
        x: 100
        animationOptions:
            curve: "spring"

### 示例: 执行状态变换动画

    # Create a state 
    layerA.states.stateA =
        x: 100
     
    # Animate to the state 
    layerA.animate("stateA")

### 示例: 跳转到另一个状态

    # Create a state 
    layerA.states.stateA =
        x: 100
     
    # Switch to the state without an animation 
    layerA.stateSwitch("stateA")

### 示例: 在状态之间循环变换

    # Set multiple states at once 
    layerA.states =
        stateA:
            x: 100
        stateB:
            x: 200
     
    # On a click, go back and forth between states. 
    layerA.onTap ->
        layerA.stateCycle("stateA", "stateB")

<a id="states.current"></a>
## layer.states.current &lt;object&gt;

返回当前激活的状态对象。
>Returns an object of the currently active state.

### 属性

* **name** — 一个只读属性，返回状态对象的名字。


    layerA = new Layer
     
    layerA.states.stateA =
        x: 500
        opacity: 0.5
     
    layerA.stateSwitch("stateA")
     
    print layerA.states.current
    # Output: <Object State> 
     
    print layerA.states.current.name
    # Output: stateA 


<a id="states.previous"></a>
## layer.states.previous &lt;object&gt;

返回上一个激活的状态名称。
>Returns an object of the previously active state.

### 属性

* **name** — 一个只读属性，返回状态对象的名字。


    layerA = new Layer
     
    layerA.states.stateA =
        x: 500
        opacity: 0.5
     
    layerA.stateSwitch("stateA")
     
    print layerA.states.previous
    # Output: <Object State> 

