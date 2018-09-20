# 颜色

Color对象可以用来定义、判断、修改和混合颜色。颜色可以使用一个字符串或者一个对象来定义。所有颜色都会被转换为`r, g, b`, `h, s, l`和一个`a`值（透明度）。

    bg = new BackgroundLayer
        backgroundColor: "#28affa"
     
    print bg.backgroundColor
    # <Color "#28affa"> 

支持的颜色模式：CSS名称、HEX、RGB、RGBA、HSL和HSLA。

    # 多种方式定义同一个颜色: 
    blue = new Color("blue")
    blue = new Color("#28AFFA")
    blue = new Color("rgb(255, 0, 102)")
    blue = new Color("rgba(255, 0, 102, 1)")
    blue = new Color("hsl(201, 95, 57)")
    blue = new Color("hsla(201, 95, 57, 1)")

你也可以新建一个颜色对象，传入字符串或者对象：

    # Define a color with a HEX string 
    bg = new BackgroundLayer
        backgroundColor: new Color("#fff")
     
    # Define a color with an RGB object 
    layerA = new Layer
        backgroundColor: new Color(r: 255, g: 255, b: 255)
     
    # Define a color with an HSL object 
    layerB = new Layer
        backgroundColor: new Color(h: 360, s: 1, l: 1, a: 1)

<a id="models"></a>
## 颜色模式

你可以给图层的背景颜色、文字颜色和阴影颜色添加过渡动画。通常情况下颜色过渡使用HUSL格式的色值。你可以通过colorModel属性来指明需要通过哪种方式过渡，支持rgb、hsl和husl。

    bg = new BackgroundLayer
        backgroundColor: "blue"
     
    # Animate in RGB 
    bg.animate
        properties:
            backgroundColor: "red"
        colorModel: "rgb"

<a id="lighten"></a>
## color.lighten(amount)

对颜色添加白色并减淡。

### 参数

* **amount** — 数字，0到100，默认是10。


    # Create a new color, lighten it 
    blue = new Color("#28affa").lighten(20)
         
    layerA = new Layer
        backgroundColor: blue

<a id="darken"></a>
## color.darken(amount)

给颜色添加黑色并加深。

### 参数

* **amount** — 数字，0到100，默认为10。


    # Create a new color, darken it 
    blue = new Color("#28affa").darken(20)
     
    layerA = new Layer
        backgroundColor: blue

<a id="saturate"></a>
## color.saturate(amount)

增加颜色的饱和度。

### 参数

* **amount** — 数字，从0到100，默认为10。


    # Create a new Color, saturate it 
    blue = new Color("#877DD7").saturate(100)
     
    layerA = new Layer
        backgroundColor: blue

<a id="desaturate"></a>
## color.desaturate(amount)

减小颜色的饱和度。

### 参数

* **amount** — 数字，从0到100，默认为10。


    # Create a new Color, desaturate it 
    blue = new Color("#28affa").desaturate(25)
     
    layerA = new Layer
        backgroundColor: blue

<a id="grayscale"></a>
## color.grayscale()

将一个颜色的饱和度降为0。

    # Create a new Color 
    yellow = new Color("yellow")
     
    # Convert it to gray 
    gray = yellow.grayscale()
     
    layerA = new Layer
        backgroundColor: gray

<a id="gray"></a>
## color.gray(amount, alpha)

生成灰度颜色。

### 参数

* **amount** — 数字，代表变成灰度颜色的程度。

* **alpha** — 代表透明度。(可选的)


    layer = new Layer
    layer.backgroundColor = Color.gray(0.5)

<a id="mix"></a>
## Color.mix(colorA, colorB, fraction, limit, model)

将任意两个用户定义的颜色进行混合。参数fraction定义了两种颜色之间的分配比例，默认是0.5。

### 参数

* **colorA** — 一个色值，第一个颜色。

* **colorB** — 一个色值，第二个颜色。

* **fraction** — 数字，从0到1。（可选）

* **limit** — 布尔值，默认为false。（可选）

* **model** — 字符串，混合时使用的颜色模式。（可选）


    # Mix red with yellow 
    orange = Color.mix("red", "yellow", 0.5)

limit代表在颜色变换时是否可以超出范围。在使用Utils.modulate来控制颜色变换范围时这个值就可以派上用场了。如下，设置limit为true，在颜色变换过程中就不会超过第二个颜色。

    # Create new Layer 
    layerA = new Layer
        backgroundColor: "red"
     
    # Enable dragging 
    layerA.draggable.enabled = true
     
    # On move, transition its color to yellow 
    layerA.on Events.Move, (offset) ->
     
        # Map the dragging distance to a number between 0 and 1 
        fraction = Utils.modulate(offset.x, [0, Screen.width], [0,1], true)
     
        # Mix the colors, enable the limit, transition in HUSL 
        layerA.backgroundColor =
            Color.mix("red", "yellow", fraction, true, "husl")

<a id="random"></a>
## Color.random()

随机返回一个颜色。

    random = Color.random()

<a id="isColor"></a>
## Color.isColor(value)

判断一个值是否是颜色对象或颜色字符串，是的话返回true，不是返回false。

### 参数

* **value** — 对象或者字符串，一个颜色。


    print Color.isColor(new Color "red") # true 
    print Color.isColor("red") # true 

<a id="isColorObject"></a>
## Color.isColorObject(value)

判断这个值是否是一个合法的颜色对象，是的话返回true，不是返回false。

### 参数

* **value** — 对象，代表一个颜色。


    print Color.isColorObject(new Color "red") # true 
    print Color.isColorObject("red") # false 

<a id="isColorString"></a>
## Color.isColorString(value)

判断这个值是否是一个合法的颜色字符串，是的话返回true，不是返回false。

### 参数

* **value** — 字符串，代表颜色。


    print Color.isColorString("red") # true 
    print Color.isColorString("#28affa") # true 

<a id="toHexString"></a>
## Color.toHexString()

返回一个颜色的十六进制值。

### 参数

* **value** — 颜色对象或颜色字符串。


    blue = new Color("blue")
    print blue.toHexString() # "#0000ff" 

<a id="toRgbString"></a>
## Color.toRgbString()

返回一个颜色的RGB值。

### 参数

* **value** — 颜色对象或颜色字符串。


    blue = new Color("blue")
    print blue.toRgbString() # "rgb(0, 0, 255)" 

<a id="toHslString"></a>
## Color.toHslString()

返回一个颜色的HSL值。

### 参数

* **value** — 颜色对象或颜色字符串。


    blue = new Color("blue")
    print blue.toHslString() # "hsl(240, 100%, 50%)" 