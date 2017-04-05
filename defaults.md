# Defaults

Framer.Defaults允许你在一开始就默认覆盖图层和动画的一些属性。比如说，你想让所有图层背景都是浅蓝色以便看见它们，你就可以用这个颜色覆盖它的背景色属性。

    # Override the default background color for layers 
    Framer.Defaults.Layer.backgroundColor = "red"
     
    # Override the default corner radius for layers 
    Framer.Defaults.Layer.borderRadius = 10
 
    layerA = new Layer
     
    print layerA.backgroundColor
    # Output: "red" 
     
    print layerA.borderRadius
    # Output: 10 

这个例子是设置默认动画曲线。需要注意的是layer.states的改变也会遵循该曲线，除非你是用layer.states.animationOptions来定义的。

    # Override the default animation options for all Animations 
    Framer.Defaults.Animation =
        curve: "spring(100,10,0)"
     
    # Override the default corner radius for layers 
    Framer.Defaults.Layer.borderRadius = 10
     
    layerA = new Layer
     
    layerA.animate
        properties:
            x: 100
     
    # The animation will now use the "spring(100,10,0)" curve 
