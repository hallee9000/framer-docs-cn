# States

每一个状态都描述了一个图层的不同属性和值。你可以添加或移除状态，也可以在状态之间转换，而状态之间的转换可以带有动画效果也可以不带，并且你可以为每一个状态设置他单独的动画选项。
>States are sets of layer properties and values. You can add, remove or switch between states. State switching can be done with or without an animation, and you can define different animation options for individual states too.

<a id="states.add"></a>
## layer.states.add(name, states)

该方法用来给某个图层添加一个状态。每一个状态都是图层的一系列属性和值的集合。你可以通过一个状态名对应一个属性集合对象一个个地添加状态，也可以一次性添加多个状态。
>Adds a layer state. Each layer state is a collection of layer properties and values. You can add them one by one with a name and property object or all at once with an object containing the layer names and properties.

每个图层都有一个初始状态，叫做“default”，包含了该图层刚被创建时的属性和值的集合。
>There is always a "default" state, containing the property values that the layer was created with.

### 参数

* **name** — 表示状态名的字符串.
* **states** — 包含一个状态下图层的一些属性值集合.


    layerA = new Layer
 
    # 添加一个状态 
    layerA.states.add
        stateA:
            x: 500
            opacity: 0.5
     
    # 添加多个状态 
    layerA.states.add
        stateA:
            x: 500
            opacity: 0.5
     
        stateB:
            x: 200
            opacity: 1

<a id="states.remove"></a>
## layer.states.remove(name)

通过状态名称移除一个状态。
>Remove a layer state by name.

### 参数

* **name** — 表示状态名的字符串.
    

    layerA = new Layer
 
    layerA.states.add
        stateA:
            x: 500
            opacity: 0.5
 
    layerA.states.remove("stateA")

<a id="states.switch"></a>
## layer.states.switch(name)

切换到一个新状态，该方法将会让图层移动化的形式其换到新状态。默认情况下它使用`layer.states.animationOptions`所定义的动画属性。
>Switch to a new state. This will animate the layer to the new state. By default, it will use the layer.states.animationOptions.

### 参数

* **name** — 表示状态名的字符串.


    layerA = new Layer
     
    layerA.states.add
        stateA:
            x: 500
            opacity: 0.5
     
    layerA.states.switch("stateA")

<a id="states.switchInstant"></a>
## layer.states.switchInstant(name)

直接切换到新状态，中间没有过渡动画。
>Switch to a new state without animating.

### 参数

* **name** — 表示状态名的字符串.


    layerA = new Layer
     
    layerA.states.add
        stateA:
            x: 500
            opacity: 0.5
     
    layerA.states.switchInstant("stateA")

<a id="states.current"></a>
## layer.states.current <string>

当前状态的名称。
>The name of the current state.

### 参数

* **name** — A string, the title of the state.


    layerA = new Layer
     
    layerA.states.add
        stateA:
            x: 500
            opacity: 0.5
     
    layerA.states.switchInstant("stateA")
 
    
    print layerA.states.current
    # Output: stateA 

## layer.states.next(states)

Switches to the next state. If we reach the end of the states we start at the beginning again. You can provide an array of state names for the ordering. If you don't provide an array with state names it will use the ordering by when a state got added.

Arguments

states — One or multiple strings.


    layerA = new Layer
     
    layerA.states.add
        stateA:
            x: 500
            opacity: 0.5
     
        stateB:
            x: 200
            opacity: 1
 
    # Every time we call this we cycle through the states 
    layerA.states.next("stateA", "stateB")

## layer.states.animationOptions &lt;object&gt;

Set the animation options for the state machine. By default, the global animation options will be used.

    layerA = new Layer
     
    layerA.states.add
        stateA:
            x: 500
            opacity: 0.5
     
        stateB:
            x: 200
            opacity: 1
     
    layerA.states.animationOptions =
        curve: "spring(100, 10, 0)"
     
    layerA.states.switch("stateA")

These animation options will now be used for all state switches. To set different animation options for individual states, you can include them directly within the switch statement.

    # Switch to stateB with a spring curve 
    layerA.states.switch("stateB", curve: "spring(400, 30, 0)")
     
    # Switch to stateB with an easing curve 
    layerA.states.switch("stateB", time: 1, curve: "ease")

