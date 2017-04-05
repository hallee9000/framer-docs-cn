# Canvas
画布对象包含了整个文档的所有像素点的尺寸。如果窗口尺寸变化，它也会跟着变化。

<a id="canvas.backgroundColor"></a>
## Canvas.backgroundColor &lt;字符串&gt;

给画布设置背景颜色。

    # Change the canvas background color 
    Canvas.backgroundColor = "#28affa"

<a id="canvas.image"></a>
## Canvas.image &lt;字符串&gt;

给图层设置背景图片，你可以写一个本地路径也可以写一个线上链接。这个背景图片将会覆盖整个画布，而且不会被拉伸。

    # Local images 
    Canvas.image = "images/background.png"
     
    # Hosted images 
    Canvas.image = "http://framerjs.com/background.png"

<a id="canvas.width"></a>
## Canvas.width &lt;数字&gt;

整个文档当前的像素宽度（只读）。

    print Canvas.width
    # Output: 640 

<a id="canvas.height"></a>
## Canvas.height &lt;数字&gt;

整个文档当前的像素高度（只读）。

    print Canvas.height
    # Output: 480

<a id="canvas.size"></a>
## Canvas.size &lt;对象&gt;

整个文档当前的像素宽度和高度（只读）。

    print Canvas.size
    # Output: { width:640, height: 480 } 

<a id="canvas.frame"></a>
## Canvas.frame &lt;对象&gt;

整个文档当前的像素宽度、高度、x坐标、y坐标（只读）。

    print Canvas.frame
    # Output: { x:0, y:0, width:640, height: 480 } 

