# SVGLayer
SVGLayer 可以帮助你创建或者引用代码或设计模式下的 SVG 元素，并设置它们的路径、填充色、描边等等。

<a id="svg"></a>
## svg.svg &lt;string | svg&gt;
`svg`属性可以直接传入一段完整的 SVG 元素代码。

    shape = new SVGLayer
        svg: "<svg><rect width='200' height='200' fill='#0AF' />"

当然你也可以通过这个属性去访问 svg 元素。

    print shape.svg
    # <SVGElement {}> 

<a id="path"></a>
## svg.path &lt;layer&gt;
读取 svg 图形的 `path` 属性。需要注意的是，只有仅包含一个 `path` 的图形才可以使用这个属性。

    shape = new SVGLayer
        svg: "<svg><path d='M0 0 H 200 V 200 H 0 L 0 0' fill='#0AF' />"

    print shape.path
    # <SVGPathElement {}> 

结合 `point` 属性，你可以让图层沿着一段 SVG 路径运动。

    shape = new SVGLayer
        svg: "<svg><path d='M0 0 H 200 V 200 H 0 L 0 0' />"
        stroke: "#CCC"
     
    layer = new Layer
        size: 100
     
    layer.animate
        point: shape.path

<a id="fill"></a>
## svg.fill &lt;layer&gt;
设置 SVG 图层的填充色。

    shape = new SVGLayer
        svg: "<svg><path d='M0 0 H 200 V 200 H 0 L 0 0' />"
        fill: "#0AF"

<a id="stroke"></a>
## svg.stroke &lt;string&gt;
设置 SVG 图层的描边颜色。

    shape = new SVGLayer
        svg: "<svg><rect width='200' height='200' />"
        stroke: "#0AF"

<a id="strokeWidth"></a>
## svg.strokeWidth &lt;number&gt;
你可以使用 `strokeWidth` 属性调节图形的描边宽度。

    shape = new SVGLayer
        svg: "<svg><rect width='200' height='200' />"
        stroke: "#0AF"
        strokeWidth: 10

