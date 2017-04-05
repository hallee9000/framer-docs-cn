# Animation

`Animation`对象用来管理作用于图层上的动画，一般它是由图层的`animate`方法所创建的。唯一不同之处在于，动画对象不会立即执行，需要你使用`start()`方法来特别指定执行。
>Animation objects manage animations targeted on a layer. This is what is created by the layer’s animate function. The only difference is that animation objects don’t start immediately, you have to explicitly execute start().

动画选项允许你自定义动画的运动曲线、时间、延迟等。一个图层可以同时执行多个动画，但是如果你给同一个属性定义了两个动画，则只会以最后一个为准。
>The animation options allow you to define curves, timing, delays and more. Layers can run multiple animations at the same time. If animations affect the same layer properties, only the last one will run.

### 属性值

* **layer** — 一个图层对象，需要执行动画的图层。
* **properties** or **state** — 一个包含了动画最终属性值的对象，或者是一个状态对象。
* **options** — 一个包含了所有动画选项的对象，如动画曲线、时间等（可选）。

#### 示例: 图层和属性变化

这里我们给layerA设置一个新的动画。动画开始后这个图层就会从0水平移动到100.需要注意的是，有很多可选的动画参数我们没有写，那么这个动画就默认执行1秒，使用`ease`曲线。
>Here, we create a new Animation for layerA. Once we start the animation, it will move horizontally from 0 to 100. Note that we left out many optional arguments. By default, the animation will take 1 second, with an ease curve.

    layerA = new Layer

    # Animate the layer to the right
    animationA = new Animation
        layer: layerA
        properties:
            x: 100

#### 示例：图层和状态

使用一个状态对象来代替属性对象，以此来控制图层动画。
>Animate a layer using a layer state by inserting the State object instead of layer properties.

    layerA = new Layer

    layerA.states.stateA =
        x: 100

    # Animate the layer to the right
    animationB = new Animation layerA,
        layerA.states.stateA

    animationB.start()

#### 示例：多属性动画和时间

我们可以对多个属性同时执行动画。下面的代码就是在5秒内让图层的x坐标和透明度同时变化。
>Multiple properties can be animated at once. Here, we animate the x and opacity properties, with a duration of 5 seconds.

    layerA = new Layer

    # Animate multiple properties for 5 seconds
    animationC = new Animation layerA,
        x: 100
        opacity: 0.5
        options:
            time: 5

    animationC.start()

#### 示例：重复和延迟

当启用重复选项时，动画结束时变化的属性就会立即恢复到开始的状态。下面的例子中，图层的动画每次重复之间会有2秒的延迟。
>When using repeat, the end values of properties will be reset to their starting position instantly. In the example below, there is a 2 second delay between every repeat.

    layerA = new Layer

    # Repeat an animation 5 times, delay for 2 seconds
    animationD = new Animation layerA,
        x: 100
        options:
            repeat: 5
            delay: 2

    animationD.start()

<a id="animation.curves"></a>
## 动画曲线

* **Bezier.linear** — 匀速运动。
* **Bezier.ease** — 慢速进入，然后变快，最后慢速结束。
* **Bezier.easeIn** — 缓慢进入。
* **Bezier.easeOut** — 缓慢结束。
* **Bezier.easeInOut** — 缓慢进入，缓慢结束。
* **Spring** — 带阻尼的弹性曲线。

#### 示例: Bezier

    layerA = new Layer

    # Animate with a bezier curve
    animationA = new Animation layerA,
        x: 100
        opacity: 0.5
        options:
            curve: Bezier(0.25, 0.1, 0.25, 1)

#### 示例: Spring

默认弹性曲线可以和时间属性一起使用。
>The default spring can be used along with the time property.

* **damping** — 反弹力。
* **mass** — 运动图层的质量（可选）。
* **velocity** — 开始速度（可选）。


    layerA = new Layer

    # Animate with a spring curve
    animationA = new Animation layerA,
        x: 100
        options:
            curve: Spring(damping: 0.5)
            time: 0.5

#### 示例: Classic Spring

古典弹性曲线不可以和时间属性一起使用。
>The classic spring cannot be used with the time property.

* **tension** — 弹性张力。
* **friction** — 弹性重力。
* **velocity** — 初始速度（可选）。
* **tolerance** — 动画结束前的最小值（可选）。


    layerA = new Layer

    # Animate with a spring curve
    animationA = new Animation layerA,
        x: 100
        options:
            curve: Spring(tension: 250, friction: 25)

<a id="animation.properties"></a>
## Animatable Properties

只有数值型图层属性和颜色属性才可以被执行动画。
>Only numeric layer properties and color can be animated:

1. x, y, z
2. minX, midX, maxX
3. minY, midY, maxY
4. width, height
5. opacity
6. rotation, rotationX, rotationY, rotationZ
7. scale scaleX, scaleY, scaleZ
8. originX, originY, perspective
9. scrollX, scrollY
10. borderRadius, borderWidth
11. shadowX, shadowY, shadowBlur, shadowSpread
12. blur, brightness, saturate
13. hueRotate, contrast, invert, grayscale, sepia

### 多属性动画

你可以同时执行一个图层的不同属性动画，但是不能对同一个属性同时执行动画。如果你给一个图层的一个属性写了两个动画，那么前面的那个动画就不会执行。
>You can start multiple animations targeting the same layer, as long as they don’t target the same properties. If you start two animations both targeting x for the same layer, the first one will be cancelled.

### 性能

大部分属性的动画只需要GPU渲染，他们就会表现地很平滑。但是也有一些属性动画需要CPU参与渲染，这些就比较耗性能：
>Most properties benefit from GPU accelerated drawing. You can animate many of them smoothly. But some properties need to involve the CPU to animate, and are therefore more expensive to render:

1. width
2. height
3. scrollX
4. scrollY
5. borderRadius
6. borderWidth

<a id="animation.start"></a>
## animation.start()

开始一个动画。
>Start the animation.

    layerA = new Layer

    animationA = new Animation layerA,
        x: 100

    # Nothing will move until we start
    animationA.start()

<a id="animation.stop"></a>
## animation.stop()

停止一个动画。
>Stop the animation.

    layerA = new Layer

    animationA = new Animation layerA,
        x: 100

    animationA.start()

    # Stop the animation
    animationA.stop()

<a id="animation.reverse"></a>
## animation.reverse()

创建一个反向动画，即所有属性值变化和既定的相反(但不会立即执行)。
>Create a new animation with all reverse values.

    layerA = new Layer

    animationA = new Animation layerA,
        x: 100

    animationB = animationA.reverse()

    # 在两个动画之间运动
    animationA.on Events.AnimationEnd, animationB.start
    animationB.on Events.AnimationEnd, animationA.start

    animationA.start()

<a id="animation.reset"></a>
## animation.reset()

将图层重置到初始状态。
>Reset the layer to its default state.

    layerA = new Layer

    animationA = new Animation layerA,
        x: 100

    animationA.start()

    # On animation end reset the animation
    animationA.on Events.AnimationEnd, ->
        animationA.reset()

<a id="animation.restart"></a>
## animation.restart()

将图层重置到初始状态并再次开始执行动画。
>Reset the layer to its default state and start the animation again.

    layerA = new Layer

    animationA = new Animation layerA,
        x: 100

    animationA.start()

    # On animation end restart the animation
    animationA.on Events.AnimationEnd, ->
        animationA.restart()

<a id="animation.finish"></a>
## animation.finish()

停止动画并跳到结束状态。
>Stop the currently active animation and jump to its end state.

    layerA = new Layer

    animationA = new Animation layerA,
        x: 100,
        time: 3

    animationA.start()

    # Finish the animation after a 1 second delay
    Utils.delay 1, ->
        animationA.finish()
