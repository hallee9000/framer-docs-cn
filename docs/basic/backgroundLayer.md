# BackgroundLayer

背景图层其实也是一种普通图层，只不过他会充满整个窗口，因此它会覆盖整个画布。如果一个背景图层还有父图层，那么他就会继承父级图层的尺寸。

    layerA = new BackgroundLayer
        backgroundColor: "white"

你可以通过backgroundColor给其定义一个背景色，支持rgb和hex色值。

    # Hex value for white 
    layerA = new BackgroundLayer
        backgroundColor: "#ffffff"
     
    # RGB value for white 
    layerA = new BackgroundLayer
        backgroundColor: "rgb(255,255,255)"
     
    # RGBA value for white 
    layerA = new BackgroundLayer
        backgroundColor: "rgba(255,255,255,1)"