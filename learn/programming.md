<a id="intro"></a>
<h2 class="h2-first">简介</h2>

##### 对于表达动效来说，编程是十分强大的工具。你可以使用简单的代码语句去描述复杂的行为，比如逻辑运算、变量及循环等。虽然编程正逐渐变得简单，但是对于大多数设计师来说刚开始学习还是很具有挑战性的。这一章节的主要目的就是帮助你进入代码的世界，同时教会你如何高效地使用代码。

想在 Framer 中编程，你无须知道所有代码的知识点。你只需要了解一些基础知识，就可以上手写代码了，并不断提高。有一件很重要的事你需要记住，那就是通常解决一个问题会有一个更好的办法，多看文档。即使那些高手写代码也通常会参考别人的代码，来汲取灵感。

![](/images/learn/programming/ss-programming@2x.webp)

如果你遇到一个问题被困住了，你可以先自己根据错误提示思考一下，再去谷歌搜索，实在找不到可以去社区提问。

错误是不可避免的，这是写代码的常态——写代码->出错->解决->继续。无论你学到什么阶段，这都是你工作中的常见流程。在刚开始的时候，你会花费大量时间去解决一些很小的语法错误，这可能会让你绝望，但你要知道只是因为代码要求精确所致。任何错误的 `.` ， `,` 和 `[` 单词拼写不对都会导致错误发生，并且有时候你很难发现。但是当你不断解决，经验丰富时，你会发现进步很快。

许多用户选择 Framer 是因为写几行 CSS 就可以创建一个图层，但这会帮助你学到很多东西，越走越远。你越往后就会接触到计算、变量和函数等。从小处做起，逐渐积累，不断钻研。

<a id="primer"></a>
## 前言

### CoffeeScript

Framer 是基于 CoffeeScript 构建的。CoffeeScript 是一个更加简化的 JavaScript ，写起来更加清晰高效，同时它还可以帮助你避免一些在 JavaScript 中经常遇到的错误。

我们选择 CoffeeScript 是因为它的属性对齐写法很符合设计师的日常工作习惯。而学会了这一门语言对你入门其它相似编程语言 JavaScript 或 Swift 也有帮助。

CoffeeScript 和其他语言最大的不同之处是它依赖于缩进或空格来表示代码结构，而不是使用大括号。这使得代码的可读性大大增加，但也会引起问题。

### 缩进

空白符（制表符或空格）是 CoffeeScript 中很重要的一部分。尽管缩进的代码很方便阅读，但是却时常会因为缩进不对导致错误。尽管在代码编辑器中你可以通过全选的方式看到每一个缩进是制表符还是空格，但你还是常常会忽略它，所以我们建议你在写代码时使用一种符号，不要混合使用两种缩进方式。

### 大小写

一般情况下，编程的代码对大小写是敏感的。举个例子，你定义了一个变量 `box` ，它和变量 `Box` 是不一样的。刚开始你要刻意地强迫自己注意，但过一段时间就会适应了。

### 审查

有时候你可能需要输出一些值，来检查代码当前运行的状态。你可以使用 `print` 方法，就像下面一样：

    print "Hello" # Prints Hello 
    print 10 + 1 # Prints 11 

<a id="variables"></a>
## 变量

变量是用来存储信息的。一般我们会使用有意义的单词来定义一个变量，这对你之后阅读代码很有帮助。你可以将变量想象成一个存储信息的容器。

一个最简单的变量定义像这样，我们在变量 `container` 中存储了一些字符，而当我们想要使用这些字符时就可以使用这个变量来代替了。

    container = "Something in it"

你可以给变量随意命名，只要它是一个单独的词句。

    boxA = "Something"
    boxB = 12345 # A variable can be a number too 

在 Framer 中我们经常将图层存储在一个变量中。图层是 Framer 中的基本元素，所有的界面都是由图层构建的。你可以去[图层的文档](/docs/layer)了解更多，现在让我们使用 `new` 关键词创建一个图层并将其存储在变量中。

    myLayer = new Layer

假如说现在你想要创建多个图层，它们都有着一样的宽度，那么你可能会写多个创建图层的代码，重复地定义它们的宽度。但是现在如果你想要改变它们的宽度，就要一个个地去修改了。但是假如你使用了变量，就只需要定义一次，在修改时也只需要修改一次。

    screenWidth = 400
     
    myLayerA = new Layer
        width: screenWidth
     
    myLayerB = new Layer
        width: screenWidth

所有的图层宽度都只使用一个变量 `screenWidth` ，即使需要修改也只要修改定义的地方。

<a id="numbers"></a>
## 数值

在 Framer 中，你经常会用数字来表示位置、尺寸、不透明度等，数字也可以被用来进行计算。

许多图层属性都是用数字表示的，如果你熟悉 CSS 的话，你会注意到有一点不同之处是我们在写图层的属性时是不会添加 `px` 及类似的单位。我们只需要直接写上数值，而它的单位会自动根据当前的属性被加上。

    layerA = new Layer
        width: 200
        height: 200
        opacity: 0.5

你也可以使用一些计算符号，比如 `+` 、`-` 、`*` 、`/` 等来对数字进行计算，这些计算符号在编程术语中叫做操作符。

    print (400 + 100 / 10) * 6

给图层属性赋予计算出来的值也是可以的。

    layerA.width = 500 / 2

甚至你可以在计算时将图层属性值和数字结合运算，比如说现在你想让一个图层的宽度是另一个图层宽度的一半：

    layerA.width = layerB.width / 2

有时候你还可以使用一个值来重新计算它自己。就像下面这个例子，你想将图层向右移动一点位置，在原来的横坐标基础上增加 100 ，就可以这么写：

    # layerA.x is 200 by default 
    layerA.x = layerA.x + 100

<a id="strings"></a>
## 字符串

字符串是一段文本，在代码中我们使用单引号或者双引号包裹它来标记。在 Framer 中我们经常使用字符串来定义颜色值、图层名称或者是 HTML 内容。字符串可以是一个单词也可以是一个句子。

    layerA = new Layer
        name: "button"
        html: "click me"

你可以使用 `+` 来计算数字，在字符串中你也可以使用加号对两个字符串进行计算，不过这里的加号表示将两个字符串连接起来。

    # This code: 
    print "click" + "me"
     
    # Is the same as: 
    print "clickme"

你也可以将字符串和变量使用加号连接在一起。

    name = "Koen"
    city = "Amsterdam"
 
    print "Hello my name is " + name + " and I live in " + city
    # Hello my name is Koen and I live in Amsterdam 

这样的操作在很多地方很有用，但是阅读起来却很费劲。所以我们推荐使用字符串模板来做动态文本。

    print "Hello my name is #{name} and I live in #{city}"
    # Hello my name is Koen and I live in Amsterdam 

你还可以在字符串模板中添加一些简单的计算：

    age = 25
     
    print "I’m #{age} now and #{age + 10} in ten years from now."
    # I’m 25 now and 35 in ten years from now. 

<a id="booleans"></a>
## 布尔值

布尔值类型的变量只有两个值：`true` 或 `false` ，你可以想象成一个开关，它经常被用来开启或禁用某一项特性。

我们经常使用布尔值来开启或关闭一些属性，比如图层的可见与否是它的 `visible` 属性决定的，而图层的可拖动与否是它的 `draggable.enabled` 决定的。

layerA.visible = false
layerB.draggable.enabled = true

我们可以通过 `not` 来将一个布尔值反转。

    # Switches the visibility of a layer 
    layer.visible = not layer.visible

你可以使用逻辑关键词 `and` 或 `or` 来连接布尔值，使用 `and` 连接表示只有两个值都为 `true` 时整个表达式的值才为 `true` ，而使用 `or` 连接表示两个值中有一个值为 `true` 时整个表达式的值就为 `true` 。

    print layerB.visible and layerC.visible # false 
    print layerB.visible or layerC.visible # true 

<a id="conditionals"></a>
## 条件

在现实中我们根据一个条件来做决定，在代码中这叫做“部分执行条件”，这是因为当遇到一个条件时，只执行代码的一个部分。

在下面的例子中，我们通过点击一个图层来切换另一个图层的可见性。使用 `if` 语句，你可以检测一个图层是否可见。

    button = new Layer
     
    # Place a layer in the center 
    layerA = new Layer
        point: Align.center
     
    button.onClick ->
        if layerA.visible
            layerA.visible = false
        else
            layerA.visible = true

除了对属性进行检测，你还可以对一些值进行检测或比较。常见的数值比较有大于和小于判断，他们被称作比较操作符。如下示例，一旦你把 `layerA` 拖动到 `marker` 下面，他的色值就会变成红色。

    layerA = new Layer
    layerA.draggable.enabled = true
     
    marker = new Layer
        x: Align.center
        y: Align.center
     
    layerA.onDrag ->
        if layerA.y > marker.y
            layerA.backgroundColor = "red"

因为 `if` 语句检测的是布尔值，你可以将多个条件使用逻辑连接符连接成一个条件进行判断。

    layerA.onDrag ->
        if layerA.x > marker.x and layerA.y > marker.y
            layerA.backgroundColor = "red"
        else
            layerA.backgroundColor = "green"

<a id="arrays"></a>
## 循环 & 数组

循环和数组可以帮助你一次创建或编辑多个元素。想象一下一个图层列表、属性列表或动画列表。如果你能很好地运用它们，就能够避免写重复代码。

如下代码，我们创建了三个属性相同的图层：

    layerA = new Layer
        size: 50
        backgroundColor: "blue"
     
    layerB = new Layer
        size: 50
        backgroundColor: "blue"
     
    layerC = new Layer
        size: 50
        backgroundColor: "blue"

这看起来很繁琐，我们可以使用 `for` 循环来简化这段代码。首先我们需要一个数组，有多少个图层，这个数组里面就有多少数字。我们可以这样写 `[1..3]` ，它是数组 `[1, 2, 3]` 的简写形式，你们的数字起始值都是可以自己定义的。

    for index in [1..3]
        layer = new Layer
            size: 50
            backgroundColor: "blue"

`index` 是在循环过程中表示当前数值的变量，整个循环过程中，它从 0 开始，接着变成 1 ，最后变成 3 。

因为它是一个数字，我们可以使用它来进行计算，使图层放置在合适的位置形成一个列表。

    for i in [1..3]
        layer = new Layer
            size: 50
            backgroundColor: "blue"
            y: i * 200

上面的代码会依次将图层放置在 `y` 坐标为 200 、400 、600 的位置。你可以在数组中放任何类型的数据，但是最常见的用法是在其中放入很多图层，然后很方便地使用循环一次性的改变它们的属性。

    layerA = new Layer
    layerB = new Layer
    layerC = new Layer
     
    # Put all the layers in an array so we can loop them 
    layers = [layerA, layerB, layerC]
     
    for layer in layers
        layer.size = 50
        layer.backgroundColor = "blue"

### 循环中的事件

在循环中给图层添加事件会有一个错误，很多初学者都遇到过这个问题。在下面的代码中，你预期的结果是点击哪一个图层哪一个图层就改变颜色，然而运行结果却是点哪一个都是最后一个图层改变颜色。

    layerA = new Layer x: 0
    layerB = new Layer x: 220
    layerC = new Layer x: 440
     
    layers = [layerA, layerB, layerC]
     
    for layer in layers
        layer.onClick ->
            layer.backgroundColor = "blue"

这是因为代码中的一个概念——作用域——导致的，后面会有涉及到。这里的解决方法是使用 `this` 关键字，像下面这样写就可以了。

    for layer in layers
        layer.onClick ->
            this.backgroundColor = "blue"

<a id="functions"></a>
## 函数

函数可以让你在某一时刻执行一段代码块，或者是多次重复执行一段代码块。函数通常被用在事件中，或者是使用函数组织代码。

函数的基本格式包含一个单箭头 `->` 和一个空格。一旦定义好一个函数，你就可以多次调用这个函数，每一次调用可以传入不同参数。让我们创建一个简单的函数并多次地执行它。

    sayHello = ->
        print "Hello!"
        print "How are you?"
     
    sayHello()
    sayHello()
    sayHello()

注意在一个函数内部的每一行缩进，我们称之为函数体。在上面的实例中，函数执行的时机是我们定的，下面的例子中我们可以让 Framer 决定执行的时机。除了点击，也可以是其他事件。

    layerA = new Layer
     
    layerA.onClick ->
        layerA.rotation = layerA.rotation + 10

你可能注意到了上面例子中的函数是没有名字的，不像 `sayHello` 函数一样。如果我们给它命名，也是可以这样执行的。

    layerA = new Layer
     
    rotate = ->
        layerA.rotation = layerA.rotation + 10
     
    layerA.onClick(rotate)

就像一个数学公式一样，一个函数可以有多个输入和一个输出。比如说你想讲数学式子 `y = x * 10` 转换成一个函数：

    y = (x) ->
        return x * 10
     
    print y(10) # Prints 100 

但是更加程序化的写法是使用有意义的命名。比如下面的函数和上面的功能一模一样，只是变量的名字改变了，却更加易读。

    timesTen = (someNumber) ->
        return someNumber * 10
     
    print timesTen(10) # Prints 100 

函数的输入是参数，输出是返回值。比如我们前面举的一个例子，我们想使用这个函数来多次旋转一个图层。

    layerA = new Layer
     
    layerB = new Layer
        x: Align.right
     
    rotate = (layer) ->
        layer.rotation = layer.rotation + 10
     
    # Now, we can pass in any layer! Neat. 
     
    layerA.onClick ->
        rotate(layerA)
     
    layerB.onClick ->
        rotate(layerB)

多个参数使用逗号分隔开，这里我们添加第二个参数——旋转的角度。

    # Multiple parameters 
    rotate = (layer, degrees) ->
        layer.rotation = layer.rotation + degrees
     
    layerA.onClick ->
        rotate(layerA, 10)

如果你发现你在使用某个定义的函数时总是会使用一个固定的值传给参数，就可以将这个值作为参数的默认值。现在当你调用这个参数时，就可以忽略这个参数，它就会使用之前定义的默认值。

    rotate = (layer, degrees = 10) ->
        layer.rotation = layer.rotation + degrees
     
    # 10 degrees 
    rotate(layerA)
     
     # 50 degrees 
    rotate(layerB, 50)


在下面的例子中，你可以看到我们是如何通过一个函数获取两个图层中比较宽的那一个的宽度，并将此宽度赋给图层 `layerC` 。

    largestWidth = (firstLayer, secondLayer) ->
        if firstLayer.width > secondLayer.width
            return firstLayer.width
        else
            return secondLayer.width
     
    layerC = new Layer
        width: largestWidth(layerA, layerB)

<a id="objects"></a>
## 对象

对象是一组结构化的数据，它在 Framer 中应用十分广泛，从图层到动画都是对象。

你可以把对象看作是组织数据的以一种方式，它里面有一对对的索引（`key`）和值（`value`），就好像地址簿里面记录的姓名和地址一样。在代码中，我们使用缩进来表示它的结构。

    people =
        koen: "123 Main Street"
        sara: "456 Wall Street"
        jorn: "789 Arts Street"
     
    print people.koen

在 Framer 中我们会经常使用 对象，但是最常见的是在创建图层时给图层一系列初始选项。

    myLayer = new Layer
        x: 200
        y: 200
        backgroundColor: "red"

对象的每个索引的值可以是任何数据类型，甚至是另一个对象。在 Framer 中，你也会看到这种嵌套对象，比如新建一个动画对象时给它的选项值（注意双层缩进）。

    layer.animate
        x: 100
        y: 200
        backgroundColor: "red"
        options:
            curve: Spring(damping: 0.5)
            time: 0.5

现在让我们回到最初创建的简单对象，通过索引获取值有两种方式，一种是通过点标记法，另一种是把索引当做字符串，如下：

    ages =
        koen: 33
        jorn: 32
        ben: 21
     
    print ages.koen # 33
    print ages["ben"] # 21

基于字符串的方式可以让你动态的创建一些对象的索引，比如创建一个包含多个状态的对象：

    layerA = new Layer
     
    # Add states within a loop 
    for i in [1..3]
        layerA.states["state#{i}"] =
            y: i * 200

你也可以循环获取对象的索引和值，和循环数组不一样的是你要用 `for...of` 而不是 `for...in` 。

    people =
        koen: 33
        jorn: 32
        ben: 21
     
    for key, value of people
        print key, value
     
    # Or more logically named 
    for name, age of people
        print name, age

<a id="classes"></a>
## 类

类是可以被扩展或者改变行为的对象。比如说 Framer 中的每一个组件都是扩展自 `Layer` 类，我们将其成为 `Layer` 的子类。

子类可以继承父类的基本功能属性，还可以被添加一些新的特性，比如 `ScrollComponent` 的新特性是包含了可滚动区域。

我们可以使用关键字 `new` 给类来构建一个实例对象。在此过程中将会调用这个类特定的构造函数并返回一个实例。如下，`layerA` 是一个包含了 `Layer` 的实例的变量。

    layerA = new Layer

创建你自己的子类很容易。如果在你的原型中有很多不一样的按钮，你就可以创建一个按钮基类，在其中定义按钮的颜色和尺寸。

    # Create Class 
    class Button extends Layer
        constructor: (options) ->
     
            # Get default layer functionality 
            super(options)
     
            # Set default properties 
            @width = 300
            @height = 100
            @backgroundColor = "maroon"
     
    # Create button 
    button = new Button

`@` 符号指向 `Button` 类本身。不过这个按钮目前还不够灵活，因为我们给它定义的宽度会被构造器函数的语句覆盖。

    # This does not work 
    button = new Button
        width: 250
     
    # This will work 
    button.width = 250

为了能够使我们在初次创建按钮时可以自定义宽度，我们可以改一下构造函数中的代码。这里我们借用第三方库 lodash 的 [defaults](https://lodash.com/docs#defaults) 方法来合并自定义选项和默认选项：

    class Button extends Layer
        constructor: (options) ->
            super _.defaults options,
                width: 300
                height: 100
                backgroundColor: "maroon"
     
    # Works! 
    button = new Button
        width: 250

我们也可以给按钮类添加自定义的方法。

    class Button extends Layer
        constructor: (options) ->
            super _.defaults options,
                width: 300
                height: 100
     
            # Deactivate by default 
            @deactivate()
     
        activate: ->
            @backgroundColor = "red"
     
        deactivate: ->
            @backgroundColor = "maroon"

现在，我们就可以在每一个按钮实例中调用这些方法了，比如我们可以这样给按钮添加一些交互特性：

    button.onTapStart ->
        @activate()
     
    button.onTapEnd ->
        @deactivate()

我们还可以在构造函数中给按钮添加点击事件监听，这样每一个按钮实例就都继承了这个交互特性。

    class Button extends Layer
        constructor: (options) ->
            super _.defaults options,
                width: 300
                height: 100
     
            # Deactivate by default 
            @deactivate()
     
            # Add events handlers 
            @onTapStart ->
                @activate()
     
            @onTapEnd ->
                @deactivate()
     
        activate: ->
            @backgroundColor = "red"
     
        deactivate: ->
            @backgroundColor = "maroon"

### 比较循环、对象和类

在代码中，通常我们可以通过多种方式达到一个目的，比如在一个循环中创建两个蓝色的图层：

    for i in [1..2]
        new Layer
            backgroundColor: "blue"

或者使用函数：

    createLayer = (backgroundColor) ->
        new Layer
            backgroundColor: backgroundColor
     
    createLayer("blue")
    createLayer("blue")

或者使用类：

    class BlueLayer extends Layer
        constructor: (options) ->
            super
            @backgroundColor = "blue"
     
    new BlueLayer
    new BlueLayer

可以看见，在代码中答案不是唯一的，也没有正确答案。所以，如果某一天你学地更加深入了再回来改掉以前写的一些糟糕的代码是很正常的。你也不必陷进一个地方出不来，换一种方法说不定会柳暗花明。

<a id="scope"></a>
## 作用域

在编程中，作用域是指一个变量所处的代码块范围。有时候，你能否得到一个变量的值取决于它的作用域结束于何处。

当你在循环中使用事件时，会遇到一个经典的作用于错误，让我们看一下当你点击时发生了什么：

    for i in [0...3]
        layer = new Layer
            backgroundColor: "blue"
            y: i * 250
     
        layer.onClick ->
            layer.backgroundColor = "red"

上面的代码不会按照你预想流程的运行，而是无论你点击哪一个图层总是第三个图层变成红色。为什么呢？这是因为我们在 `onClick` 函数中使用了一个变量 `layer` 来存储每次点击的图层，可是每次循环 `layer` 的值都会改变。

背景颜色只会在你点击之后改变，而在此时变量 `layer` 早已经变成了最后一次循环之后的值——第三个图层。我们可以这样解决：

### 使用 "this"

除了使用变量来指代被点击的图层，我们还可以使用 `this` 。`this` 是一个特殊的变量，它的只取决于你在代码的哪个地方使用它。在事件中，`this` 往往指代发生该事件的图层。

    for i in [0...3]
        layer = new Layer
            backgroundColor: "blue"
            y: i * 250
     
        layer.onClick ->
            this.backgroundColor = "red"

你也可以使用 `@` 作为 `this` 的缩写。

    layer.onClick ->
        @backgroundColor = "red"

### 使用 “do”

另一种解决方法是使用 `do` 来“捕捉”变量。比如说，你需要在事件处理代码中使用它“捕捉”图层变量。

    button = new Layer
     
    for i in [1..3]
     
        layer = new Layer
            backgroundColor: "blue"
            y: i * 250
     
        do (layer) ->
            button.onClick ->
                layer.backgroundColor = "red"

点击 `button` 可以改变所有循环创建的图层的颜色，如果没有使用 `do` 只会改变最后一个图层的颜色。
