# 设备

设备组件模拟一个真实的设备，比如iPhone, iPad或Android。你可以调整设备显示比例、内容显示比例以及调整设备方向。当设备设置完成，就会在其屏幕内渲染你的原型。设备预览和镜像预览相匹配，也就是说，当你把设备设为iPhone并使用iPhone真机预览时，他就会在你的手机上全屏显示。

你也可以使用Framer.Device提前设置缩放比例和设备方向。

    Framer.Device.contentScale = 0.5
    Framer.Device.orientation = 90

本质上来讲，设备也是一些图层。所以你可以自己去定制，或给它添加一些行为。下面给出一些常见的例子，你可以在Github上查看完整资源。

    # Set a blurred background image 
    Framer.Device.background.image = "photo.jpg"
    Framer.Device.background.blur = 10
     
    # Get the screen dimensions for the current device 
    print Framer.Device.screen.width  # Output: 640 
    print Framer.Device.screen.height # Output: 480 

请注意：缩放以适应视图能够让内容按照屏幕比例渲染，有可能像素有些偏差。当视图比例设置为50%、100%时，你的内容将总是以像素对齐。如果浏览器支持的话，设备图像将会压缩为JPEG2000格式用以降低图片大小。

想要移动设备时，也只需要像普通图层一样改变x和y的值。

    # Set the Device position 
    Framer.Device.screen.x = 50
    Framer.Device.x = 50
     
    # Change from the current Device position 
    Framer.Device.screen.x += 50
    Framer.Device.x += 50


<a id="deviceType"></a>
## Device.customize(deviceType, screenWidth, screenHeight, deviceImage, deviceImageWidth, deviceImageHeight, devicePixelRatio)

自定义设备的图像和尺寸。如果你自定义的设备是一个手机或者 pad ，你需要注明它的 `deviceType` 属性，这样在你使用该设备尺寸打开预览时才会自动隐藏设备图片。

    # Define and set custom device 
    Framer.Device.customize
        deviceType: Framer.Device.Type.Tablet
        screenWidth: 720
        screenHeight: 1024
        deviceImage: "http://f.cl.ly/items/001L0v3c1f120t0p2z24/custom.png"
        deviceImageWidth: 800
        deviceImageHeight: 1214
        devicePixelRatio: 1

<a id="deviceType"></a>
## Device.deviceType &lt;字符串&gt;

渲染时使用的设备类型，下面是所有可用的选项。

### Fullscreen

全屏显示。

    Framer.Device.deviceType = "fullscreen"

### iPhone 6s

各种颜色的iPhone 6s。

    Framer.Device.deviceType = "apple-iphone-6s-gold"
    Framer.Device.deviceType = "apple-iphone-6s-rose-gold"
    Framer.Device.deviceType = "apple-iphone-6s-silver"
    Framer.Device.deviceType = "apple-iphone-6s-space-gray"

### iPhone 6+

各种颜色的iPhone 6plus。

    Framer.Device.deviceType = "apple-iphone-6s-plus-gold"
    Framer.Device.deviceType = "apple-iphone-6s-plus-rose-gold"
    Framer.Device.deviceType = "apple-iphone-6s-plus-silver"
    Framer.Device.deviceType = "apple-iphone-6s-plus-space-gray"

### iPhone 5s

各种颜色的iPhone 5s。

    Framer.Device.deviceType = "apple-iphone-5s-gold"
    Framer.Device.deviceType = "apple-iphone-5s-silver"
    Framer.Device.deviceType = "apple-iphone-5s-space-gray"

### iPhone 5c

各种颜色的iPhone 5c。

    Framer.Device.deviceType = "apple-iphone-5c-blue"
    Framer.Device.deviceType = "apple-iphone-5c-green"
    Framer.Device.deviceType = "apple-iphone-5c-red"
    Framer.Device.deviceType = "apple-iphone-5c-white"
    Framer.Device.deviceType = "apple-iphone-5c-yellow"

### iPad Mini

各种颜色的iPad Mini。

Framer.Device.deviceType = "apple-ipad-mini-4-silver"
Framer.Device.deviceType = "apple-ipad-mini-4-gold"
Framer.Device.deviceType = "apple-ipad-mini-4-space-gray"

### iPad Air

各种颜色的iPad Air。

    Framer.Device.deviceType = "apple-ipad-air-2-silver"
    Framer.Device.deviceType = "apple-ipad-air-2-gold"
    Framer.Device.deviceType = "apple-ipad-air-2-space-gray"

### iPad Pro

各种颜色的iPad Pro。

    Framer.Device.deviceType = "apple-ipad-pro-silver"
    Framer.Device.deviceType = "apple-ipad-pro-gold"
    Framer.Device.deviceType = "apple-ipad-pro-space-gray"

### Apple Watch 38mm

各种颜色的Apple Watch 38mm。

    Framer.Device.deviceType = "apple-watch-38mm-gold-black-leather-closed"
    Framer.Device.deviceType = "apple-watch-38mm-rose-gold-black-leather-closed"
    Framer.Device.deviceType = "apple-watch-38mm-stainless-steel-black-leather-closed"
     
    Framer.Device.deviceType = "apple-watch-38mm-black-steel-black-closed"
    Framer.Device.deviceType = "apple-watch-38mm-gold-midnight-blue-closed"
    Framer.Device.deviceType = "apple-watch-38mm-rose-gold-lavender-closed"
     
    Framer.Device.deviceType = "apple-watch-38mm-sport-aluminum-blue-closed"
    Framer.Device.deviceType = "apple-watch-38mm-sport-aluminum-fog-closed"
    Framer.Device.deviceType = "apple-watch-38mm-sport-aluminum-green-closed"
    Framer.Device.deviceType = "apple-watch-38mm-sport-aluminum-red-closed"
    Framer.Device.deviceType = "apple-watch-38mm-sport-aluminum-walnut-closed"
    Framer.Device.deviceType = "apple-watch-38mm-sport-aluminum-white-closed"
    Framer.Device.deviceType = "apple-watch-38mm-sport-space-gray-black-closed"

### Apple Watch 42mm

各种颜色的Apple Watch 42mm。

    Framer.Device.deviceType = "apple-watch-42mm-gold-black-leather-closed"
    Framer.Device.deviceType = "apple-watch-42mm-rose-gold-black-leather-closed"
    Framer.Device.deviceType = "apple-watch-42mm-stainless-steel-black-leather-closed"
     
    Framer.Device.deviceType = "apple-watch-42mm-black-steel-black-closed"
    Framer.Device.deviceType = "apple-watch-42mm-gold-midnight-blue-closed"
    Framer.Device.deviceType = "apple-watch-42mm-rose-gold-lavender-closed"
     
    Framer.Device.deviceType = "apple-watch-42mm-sport-aluminum-blue-closed"
    Framer.Device.deviceType = "apple-watch-42mm-sport-aluminum-fog-closed"
    Framer.Device.deviceType = "apple-watch-42mm-sport-aluminum-green-closed"
    Framer.Device.deviceType = "apple-watch-42mm-sport-aluminum-red-closed"
    Framer.Device.deviceType = "apple-watch-42mm-sport-aluminum-walnut-closed"
    Framer.Device.deviceType = "apple-watch-42mm-sport-aluminum-white-closed"
    Framer.Device.deviceType = "apple-watch-42mm-sport-space-gray-black-closed"

### Nexus

谷歌各个版本的Nexus设备。

    Framer.Device.deviceType = "google-nexus-4"
    Framer.Device.deviceType = "google-nexus-5x"
    Framer.Device.deviceType = "google-nexus-6p"
    Framer.Device.deviceType = "google-nexus-9"

### HTC One A9

各种颜色的的HTC One A9设备。

    Framer.Device.deviceType = "htc-one-a9-black"
    Framer.Device.deviceType = "htc-one-a9-white"

### HTC One M8

各种颜色的的HTC One M8设备。

    Framer.Device.deviceType = "htc-one-m8-black"
    Framer.Device.deviceType = "htc-one-m8-gold"
    Framer.Device.deviceType = "htc-one-m8-silver"

### Microsoft Lumia 950

各种颜色的微软Lumia 950设备。

    Framer.Device.deviceType = "microsoft-lumia-950-black"
    Framer.Device.deviceType = "microsoft-lumia-950-white"

### Samsung Note 5

各种颜色的三星Note 5设备。

    Framer.Device.deviceType = "samsung-galaxy-note-5-black"
    Framer.Device.deviceType = "samsung-galaxy-note-5-gold"
    Framer.Device.deviceType = "samsung-galaxy-note-5-pink"
    Framer.Device.deviceType = "samsung-galaxy-note-5-silver-titanium"
    Framer.Device.deviceType = "samsung-galaxy-note-5-white"

<a id="fullScreen"></a>
## Device.fullScreen &lt;布尔值&gt;

设置是否使用全屏显示原型，该属性独立于deviceType。

    # Render the device in fullscreen 
    Framer.Device.fullScreen = true

<a id="deviceScale"></a>
## Device.deviceScale &lt;数字 / 字符串&gt;

设备缩放比例，允许的值是0.5到1。

    Framer.Device.deviceScale = 0.5

<a id="setDeviceScale"></a>
## Device.setDeviceScale(scale, animate)

设置设备缩放比例，这个函数会有一个额外的动画选项animation（true或false）。允许的值是0.5到1。

    # Set device scale and animate 
    Framer.Device.setDeviceScale(0.5, true)

<a id="contentScale"></a>
## Device.contentScale &lt;数字&gt;

内容在自定义设备内的缩放比例，允许的范围是0.5到1。

    # Set content scale 
    Framer.Device.contentScale = 0.5

<a id="setContentScale"></a>
## Device.setContentScale(scale, animate)

内容的缩放比例，允许的范围是0.5到1，这个函数会有一个额外的动画选项animation（true或false）。

    # Set content scale and animate 
    Framer.Device.setContentScale(0.5, true)

<a id="orientation"></a>
## Device.orientation &lt;数字&gt;

设置设备的方向，允许的方向值是0到90（竖屏和横屏）。

    Framer.Device.orientation = 90

<a id="setOrientation"></a>
## Device.setOrientation(orientation, animate)

设置设备的方向，允许的方向值是0到90（竖屏和横屏），这个函数会有一个额外的动画选项animation（true或false）。

    # Set orientation and animate 
    Framer.Device.setOrientation(90, true)

<a id="orientationName"></a>
## Device.orientationName &lt;字符串&gt;

通过名称来设定设备方向，合法的选项就是“portrait”和“landscape”两个。“portrait”和“landscape”分别和设置设备方向为0度90度相对应。

    # Set orientation to either landscape or portrait 
    Framer.Device.orientationName = "landscape"
    Framer.Device.orientationName = "portrait"

<a id="rotateLeft"></a>
## Device.rotateLeft()

向左旋转设备。

    Framer.Device.rotateLeft()

<a id="rotateRight"></a>
## Device.rotateRight()

向右旋转设备。

    Framer.Device.rotateRight()
