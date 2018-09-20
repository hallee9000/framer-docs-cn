# Gradient

`Gradient` 对象可以用来创建渐变样式或者动画。你需要使用两个颜色（开始色和结束色）以及一个表示方向的角度来描述一个渐变。
>The Gradient object can be used to create, customize and animate gradients. It consists of two colors (start, end) and an angle indicating its direction.

    gradient = new Gradient
        start: "#05F"
        end: "#0DF"

开始色和结束色也可以使用颜色对象。
>The start and end values also accept Color objects.

    gradient = new Gradient
        start: new Color("#05F")
        end: new Color("#0DF")

如果你想要画一个带有渐变背景色的图层，可以直接将创建的渐变对象赋给 `layer.gradient` 。
>You can apply a gradient to a layer directly by using the layer.gradient property.

    blue = new Gradient
        start: "#05F"
        end: "#0DF"
     
    layerA = new Layer
        gradient: blue

渐变对象的所有属性都是可以进行过渡动画的。
>All properties of the gradients object can be animated, too.

    blue = new Gradient
        start: "#05F"
        end: "#0DF"
     
    purple = new Gradient
        start: "#30F"
        end: "#B8F"
     
    layerA = new Layer
        gradient: blue
     
    layerA.animate
        gradient: purple

<a id="start"></a>
## gradient.start &lt;string&gt;

开始色，默认是黑色。
>The start color. Set to black by default.

    gradient = new Gradient
        start: "#05F"

<a id="end"></a>
## gradient.end &lt;string&gt;
结束色，默认是白色。
>The end color. Set to white by default.

    gradient = new Gradient
        start: "#05F"
        end: "#0DF"

<a id="angle"></a>
## gradient.angle &lt;number&gt;

渐变的方向角度，默认是 0° 。
>The angle of the gradient. Set to 0 by default.

    gradient = new Gradient
        start: "#0DF"
        end: "#05F"
        angle: 180

