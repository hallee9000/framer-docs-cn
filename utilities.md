# Utils

Utilities是Framer中的一些通用方法,他可以简化一些事情。比如，你可以通过它进行范围对应、设置定时或延时以及检测设备等等，具体内容请看下面。
>Utilities are custom functions in Framer, designed to make things easier to do. For example, they allow you to map values, set delays and intervals, detect devices and more. See below for a complete overview.

<a id="utilities.modulate"></a>
## Utils.modulate(value, [a, a], [b, b], limit)

它的作用是将一个数字在不同范围之间进行映射。当你启用`limit`进行限制时，返回的数字将不会超出`b`以外的范围。`limit`默认的值是`false`。
>Translates a number between two ranges. When you enable limit, it will never return a value outside of the b range. The default value for limit is false.

### 参数

* **value** — 一个变量，代表输入的值。
* **[a, a]** — 第一个数字范围。
* **[b, b]** — 第二个数字范围。
* **limit** — 布尔值，默认是`false`。 (可选)


    print Utils.modulate(0.5, [0, 1], [0, 100])
    # Output: 50

    print Utils.modulate(1, [0, 1], [0, 100])
    # Output: 100

你可以想象这种转换是将数字在不同的衡量标准下进行转换，就好像讲一个温度的数值从摄氏度转换到华氏度，或者将一个距离从千米转换到米。
>You can think of modulate as a way to convert numbers between different scales. Like going from Celcius to Farenheit, or Kilometers to Miles.

    # Convert to Celsius/Farenheit
    Utils.modulate(celcius, [0, 100], [32, 212])

如果你想要创建一个视差滚动效果使用它最合适不过。比如，你想要在一个滚动组件从0滚动到100的过程中让一个图层对应从0移动到10，就可以这么写：
>It's also useful for creating parallax effects on scroll. For example, you can move a layer from 0-10, when scrolling from 0-100.

    scroll = new ScrollComponent
        scrollHorizontal: false

    layerA = new Layer
        x: 100

    # Modulate the scrolling distance
    scroll.on Events.Move, ->
        y = Utils.modulate(scroll.scrollY, [0,100], [0,10])
        layerA.y = y

<a id="utilities.cycle"></a>
## Utils.cycle(values)

这个方法可以逐个输出一个数组的每一项。
>Creates a function that returns the next value of an array every time it's called.

### 参数

* **values** — 一个数组。


    cycler = Utils.cycle(["a", "b", "c"])

    print cycler() # Output: "a"
    print cycler() # Output: "b"
    print cycler() # Output: "c"
    print cycler() # Output: "a", returns to start

<a id="utilities.labelLayer"></a>
## Utils.labelLayer(layer, text)

这个方法可以快速给图层添加标签，并在图层中上下左右居中。
>Quickly add a label to a layer. By default, the text will be set in Menlo, and positioned in the center of the layer.

### 参数

* **layer** — 一个图层对象。
* **text** — 一个字符串。


    layerA = new Layer

    # Add a label to layerA  
    Utils.labelLayer(layerA, "Hello")

<a id="utilities.round"></a>
## Utils.round(value, decimals, increments, min, max)

这是数字的四舍五入方法.
>Rounds a number.

### 参数

* **value** — 一个浮点型数字。
* **decimals** — 小数点后需要保留的位数。(可选)
* **increments** — 取舍精度。(可选)
* **min** — 返回的最小值。(可选)
* **max** — 返回的最大值。(可选)


    print Utils.round(100.12345, 0) # Output 100
    print Utils.round(100.12345, 2) # Output 100.12
    print Utils.round(100.12345, 4) # Output 100.1234

<a id="utilities.randomChoice"></a>
## Utils.randomChoice(values)

从数组中随机选取一项。
>Select a random item in an array of values.

### 参数

* **values** — 一个数组。


    print Utils.randomChoice(["a", "b", "c"]) # Output: "c"
    print Utils.randomChoice(["a", "b", "c"]) # Output: "b"
    print Utils.randomChoice(["a", "b", "c"]) # Output: "b"
    print Utils.randomChoice(["a", "b", "c"]) # Output: "b"
    print Utils.randomChoice(["a", "b", "c"]) # Output: "a"

<a id="utilities.randomColor"></a>
## Utils.randomColor(opacity)

根据给定的透明度，随机生成一个颜色。（透明度是可选的）
>Creates a random color with a given opacity. The opacity is optional.

### 参数

opacity — 0到1之间的一个数。 (可选)


    layerA = new Layer
    layerA.backgroundColor = Utils.randomColor(0.5)

    print layerA.backgroundColor
    # Output: "rgba(124, 12, 33, 0.5)"

<a id="utilities.randomImage"></a>
## Utils.randomImage(layer or size)

随机生成一个高清壁纸分享网站unsplash上的图片链接。如果你传入图层`layer`或者尺寸`size`参数，它会对图片尺寸进行优化。
>Generate a random unsplash image url. If you optionally pass a layer or size, it will keep using the same image for that layer and optimize for the size.

### 参数

* **layer** — 图层。


    layer = new Layer
    layer.image = Utils.randomImage() # Unoptimized
    layer.image = Utils.randomImage(layer) # Preferred

<a id="utilities.randomNumber"></a>
## Utils.randomNumber(a, b)

随机生成一个`a`到`b`之间的数字。
>Generate a random number between a and b.

### 参数

* **a** — 一个数字，范围的起点。
* **b** — 一个数字，范围的终点。


    print Utils.randomNumber(0, 1) # Output: 0.2
    print Utils.randomNumber(0, 100) # Output: 22

<a id="utilities.delay"></a>
## Utils.delay(delay, handler)

延迟执行方法，就是在你定义的时间之后执行。
>Calls a funtion after a delay. Delay is defined in seconds.

### 参数

* **delay** — 一个数字，代表延迟的秒数。
* **handler** — 一个处理函数。


    Utils.delay 0.5, ->
        print "hello"

    # 0.5秒后输出"hello"

<a id="utilities.frameInset"></a>
## Utils.frameInset(frame, inset)

### 参数

* **frame** — 包含有x、y、width和height的一个对象。
* **inset** — 一个数字或者一个包含top、right、bottom和left的对象。


内嵌一个有具体像素值的框架。
>Inset a frame by a certain amount of pixels.

    print Utils.frameInset({x:0, y:0, width:100, height:100}, 10)
    # Output {x:10, y:10, width:80, height:80}

    print Utils.frameInset({x:0, y:0, width:100, height:100}, {top: 20})
    # Output {x:0, y:20, width:100, height:80}

<a id="utilities.interval"></a>
## Utils.interval(interval , handler)

每`x`秒执行一次一个函数。
>Calls a function every x seconds.

    Utils.interval 2, ->
        print "hello"

    # Output: "hello"
    # Output: "hello"
    # Output: "hello"
    # Output: "hello" etc...

<a id="utilities.debounce"></a>
## Utils.debounce(interval, handler)

创建一个方法，只在它最后一次被调用之后的`x`秒执行，别名是[_.debounce](http://lodash.com/docs#debounce)。
>Creates a function that will delay the calling of handler until after x seconds have elapsed since the last time it was invoked.
Alias to `_.debounce`.

### 参数

* **interval** — 一个数字，代表秒数。
* **handler** — 一个函数。


    handler = Utils.debounce 0.1, ->
        print "hello"

    for i in [1..100]
        handler()

    # Output: "hello" only once

<a id="utilities.insertCSS"></a>
## Utils.insertCSS(css)

注入一段CSS样式代码，不过你需要先给图层添加对应的类。
>Add css to a layer by wrapping it in a string and passing it as a parameter.

    layerA = new Layer
    layerA.classList.add("testClass")

    css = """
    .testClass {
        border: 1px solid #000;
    }
    """

    print Utils.insertCSS(css)

<a id="utilities.throttle"></a>
## Utils.throttle(interval, handler)

创建一个方法，它在`x`秒内至多执行一次，别名是[_.throttle](http://lodash.com/docs#throttle)。
>Creates a function that will call the wrapped function at most once per x seconds. Alias to _.throttle.

### 参数

* **interval** — 一个数字，代表秒数。
* **handler** — 一个函数。


    handler = Utils.throttle 0.1, ->
        print "hello"

    for i in [1..100]
        handler()

    # Output: "hello" only once

<a id="utilities.isWebKit"></a>
## Utils.isWebKit()

判断当前是否为WebKit内核浏览器。
>Returns whether this is a WebKit browser.

    print Utils.isWebKit() # Output true

<a id="utilities.isChrome"></a>
## Utils.isChrome()

判断当前是否为Chrome浏览器。
>Returns whether this is a Chrome browser.

    print Utils.isChrome() # Output true

<a id="utilities.isSafari"></a>
## Utils.isSafari()

判断当前是否为Safari浏览器。
>Returns whether this is a Safari browser.

    print Utils.isSafari() # Output true

<a id="utilities.isTouch"></a>
## Utils.isTouch()

判断当前是否为可触摸浏览器。
>Returns whether this is a touch enabled browser.

    print Utils.isTouch() # Output true

<a id="utilities.isDesktop"></a>
## Utils.isDesktop()

判断当前是否为桌面端浏览器。
>Returns whether this is a desktop browser.

    print Utils.isDesktop() # Output true

<a id="utilities.isPhone"></a>
## Utils.isPhone()

判断当前是否为手机设备。
>Returns whether this is a phone device.

    print Utils.isPhone() # Output true

<a id="utilities.isTablet"></a>
## Utils.isTablet()

判断当前是否为平板设备。
>Returns whether this is a tablet device.

    print Utils.isTablet() # Output true

<a id="utilities.isMobile"></a>
## Utils.isMobile()

判断当前是否为移动设备（手机或平板）。
>Returns whether this is a mobile device (phones and tables).

    print Utils.isMobile() # Output true
