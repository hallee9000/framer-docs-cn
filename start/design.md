# 设计模式

## 设计

##### 在这一节，我们将对 Framer 的设计模式进行简要介绍。它是代码模式最好的搭档。尤其擅长响应式的设计。通过设计模式，你可以在 Framer 中快速画出原型界面，并通过代码将其变成高保真原型。

Framer 的设计模式和很多其它设计工具类似，都包含了画布、设备预览以及各种快捷工具。很很多其它设计工具一样，Framer 也提供了插入图层和文本，使用属性调节面板进行设计样式调整。就这点来看，你是可以很快上手的。

![](/images/learn/design/intro-design@2x.png)

Framer 设计模式独特之处在于其响应式的布局设置。因为我们是为了交互设计工作而生的，所以我们的图形化工具在响应式布局及图层层级可以自判断。他可以自动识别相对位置和对齐，能够帮你节省时间，对于响应式设计更加高效。

你可以仅使用设计模式，也可以将其和代码模式及云协作结合使用，来完整你的工作流。

<a id="canvas"></a>
## 画布

##### 这是你尝试想法和模拟页面流的主要区域。可以直接在画布上拖拽出一个画板或者选取内置的各种设备大小的画板。

Framer 设计模式下提供一块空白的画布，你可以在上面快速画出一些概念或原型。你可以直接在上面拖拽，也可以导入图像或图标，或者是画出多个画板作为一整个 APP 的页面流程图。

如果你打算直接在设计模式下的画布中进行设计，那么你在上面画的任意图层都不会有一个画板父图层。如果你将图层放置于 x:0 和 y:0 处，当你切换到代码模式时该图层将会处于预览窗口的左上角。如果你只是做一个局部的动效，就可以直接在画布上绘制。但如果你要做一个复杂的或响应式的多页面 APP ，我们推荐使用画板。

你可以随意地放大缩小画板，去整体预览或调整细节，按你喜爱的方式使用它吧。
[了解更多](/learn/code#preview)

<a id="frames"></a>
## 框架
##### 使用我们的“框架”工具可以创建响应式的布局，它内置了桌面、iOS 、Android 的预设。

点击 Framer 左上角的框架图标，或者按 F 键就可以快速插入一个框架。在 Framer 右侧你可以看到有一个内置的常用设备屏幕列表。如果你想要自定义一个框架，你可以在点击框架图表之后在画布中拖拽绘制。

框架没有一个固定的宽高，但是依赖于你选择的设备。在一个框架内部拖拽出另一个框架，他们会自动调整层级。框架还可以在你改变尺寸时将内部元素自适应，保持按钮、卡片和选项卡完全地跟随适应。

当屏幕中有了一个或多个框架，当你再次添加框架时 Framer 会自动猜测新的框架的位置。

[了解更多](/learn/code#frames)

<video loop autoplay poster="/images/learn/design/artboard-poster.png">
	<source src="/images/learn/design/artboard.mp4" type="video/mp4">
</video>

<!-- <a id="artboards"></a>
## 画板

画板可以满足你的自适应要求。你可以使用画板按顺序展示每一个页面，自适应出多尺寸版本。

在 Framer 中，画板的尺寸不再受限于最初填写的值，而是根据你选择的设备自适应。因为 Framer 的自动布局规则，画板可以在设计时改变尺寸，而里面的内容也会相应地跟着自动适应。

点击设计模式下左上角的画板图标，就可以插入一个画板。提示：你也可以按快捷键 A 来插入一个画板。Framer 会提供一些预置的设备，基本包含了当前常见的各种尺寸的屏幕。当然，你也可以点击画板图标来绘制一个自定义尺寸的画板。

为了帮你节省时间，Framer 会猜测你的下一个画板应该放在哪。当你的画布中有一或多个画板时，当你再次插入一个画板 Framer 会使用顺序预测的技术来建议你它的位置。

从画板到代码 -->


<a id="layers"></a>
## 图层&形状

##### 图层可以自动适应布局或层级，而使用形状你可以绘制出细节丰富的图标。

插入矩形、圆形、多边形或者是星形，然后以此为基础创作出更加复杂的图形。你也可以使用快捷键来提高效率，比如 `R` 可以插入矩形，`O` 可以插入圆形，`P` 可以插入多边形，`S` 可以插入星形。双击图层可以进一步编辑，你还可以使用布尔操作进行图层的相加、相减、相交和排除。

你还可以插入或者操作文字图层，图片图层，或者是 GIF 动画。你可以使用 `T` 快捷键快速插入文字图层。

除了一些常见的图层类型，你还可以直接将 gif 动图拖进 Framer 。`.gif` 图片在 Framer 中和其他图层一样，它会自动播放。

[了解更多](/learn/code#layers)

<video loop autoplay poster="/images/learn/design/gif-poster.png">
	<source src="/images/learn/design/gif.mp4" type="video/mp4">
</video>

<a id="targeting"></a>
## 代码目标

为了能够在代码模式下使用你在设计模式下创建的图层，你需要将其设置为代码目标。只对需要的图层设置代码目标可以让你的文档保持整洁，编程也变得简单。

只有设置了代码目标的图层（目前只能对 frame 设置代码目标）才能够在代码中使用，而且可以在代码模式下的图层列表区看见。

给图层设置代码目标很简单，只需要在设计模式下点击图层结构区每个图层右边的图标，或者右击选取“Rename to Target（重命名到代码目标）”，此时图层名称变成了输入框。如果你在此之前已经给某个图层重命名，那么Framer会自动纠正不正确的命名格式（比如带有空格等），使其在代码模式下可用。如果你没有给它重命名，则会被提示给它重命名。当你在重命名时，有便会出现提示语告诉你在代码模式下怎样获取该图层对象。

在代码结构区，具有代码目标的图层右侧会有一个图标。如果你想取消它的代码目标，直接右击并选择“Delete Target（删除目标）”或者“Rename Target（重命名目标）”。

<!-- <video loop autoplay poster="/images/learn/design/targeting-poster.png">
	<source src="/images/learn/design/targeting.mp4" type="video/mp4">
</video> -->

<a id="layout"></a>
## 布局 & 层级

##### Framer 专注于自动层级和响应式布局，Framer满足你的现代界面设计需求。

### 自动层级

当你在画布上画出一个图层时，Framer能够根据它的位置来确定图层的层级。图层层级顺序也能够体现在图层结构面板中。

通过这种方式，几乎所有的图层都会依据父子关系在画布中按顺序排放，你再也不用手动给它们分组了。

<video loop autoplay poster="/images/learn/design/auto-hierarchy-poster.png">
	<source src="/images/learn/design/auto-hierarchy.mp4" type="video/mp4">
</video>

### 父图层 & 子图层

理解父子图层的概念很重要。比如说，把一个圆形图层放置在一个方形图层中间，会使得方形图层自动变为圆形图层的父图层。和在方形图层中的其他图层一样，圆形图层是它的子图层。其实，画板就是导航条的父图层，而导航条又是很多图层的子图层，包括顶栏文字、电池图标以及菜单按钮等。

一旦父子图层关系确立，子图层就会跟随父图层。当你改变尺寸、移动父图层时，子图层也将跟着变化。当你需要设计多尺寸界面时会感到很方便。

<video loop autoplay poster="/images/learn/design/resize-parent-poster.png">
	<source src="/images/learn/design/resize-parent.mp4" type="video/mp4">
</video>

想要检查图层是否对齐，或者他们之间的间隙？你可以在任何时候拖动图层或者在图层结构面板区调整顺序来改变图层层级，你还可以右击选择“delete from hierarchy（从层级中删除）”。

### 自动响应式布局

当你当你在画板上绘制图层时，Framer会自动猜测布局的规则。你的作品是响应式的，可以在任何设备上预览。想要了解更多关于自动布局的规则，请查看图层属性

### 图层列表层级

不像其他设计软件一样，在Framer设计模式下图层时不需要分组的，它会通过图层之间的父子层级来进行自动分组。在图层结构面板中图层的层级是以缩进的形式展现的，这会对你的响应式布局有很大帮助。

![](/images/learn/design/layer-hierarchy@2x.png)

<a id="properties"></a>
## 属性

##### 改变图层的尺寸、圆角、位置、填充色、投影、透明度样式。使用自动对齐和实时模拟来准确地定位图层。

### 对齐属性

在设计模式下，你可以在画板右侧看到一个属性调节面板。和其它图像设计软件一样，这里包含了许多工具，你可以用来给图层设置外观。在属性调节面板顶部，有一些对齐工具，可以帮助你更好地处理图层的自适应。

<video loop autoplay poster="/images/learn/design/align-poster.png">
	<source src="/images/learn/design/align.mp4" type="video/mp4">
</video>

### 画板属性

你也可以改变画板的属性，比如更改背景色，尺寸或位置等。为了测试滑板的自适应特性，你可以一次选取一个或多个画板然后切换设备，观察其属性同时变化。如果你所有的图层都按照正确的方式对齐了，它将会自动地去适应新画板尺寸。

<video loop autoplay poster="/images/learn/design/responsive-poster.png">
	<source src="/images/learn/design/responsive.mp4" type="video/mp4">
</video>

### 图层样式

你可以从图层列表中选取一个图层查看其属性，也可以直接在画布上选中图层以查看。Framer 拥有图形化设计工具的所有样式属性调节工具。

**渐变**在 Framer 是基于 CSS 色彩模式的，也就是说只需要两端色值和一个角度就可以定义一个渐变。当你改变图层尺寸时，图层上的渐变是不会受影响的，而是会自动去适应新的尺寸。无论你是在设计模式下还是在代码模式下创建的渐变，都是自适应的。

<video loop autoplay poster="/images/learn/design/gradients-poster.jpg">
	<source src="/images/learn/design/gradients.mp4" type="video/mp4">
</video>

**边框**可以帮助你给图层添加边缘，你可以控制边框的颜色、宽度和样式。由于Framer 是基于 web 技术的，所以你可以单独地给图层上、下、左、右添加不同的边框样式。

**多层阴影**允许你给图层创建多个阴影效果。从外阴影到内阴影，你可以将多个不同效果的阴影相结合。你还可以对其中某一个阴影做动画，在代码模式下你可以通过图层的 `shadow` 属性给阴影设置动画，让你的原型更有趣。

**滤镜效果**可以让你做出一些特殊的图层，包括图层的色彩混合、物体模糊、背景模糊等。当然还有对比度、灰度、色相、反向、饱和度和褐色滤光等照片滤镜。代码模式也支持这些滤镜特性，所以你可以用它实现一些类似于 iOS 动态模糊或 instagram 照片滤镜编辑的效果。

<video loop autoplay poster="/images/learn/design/effects-poster.jpg">
	<source src="/images/learn/design/effects.mp4" type="video/mp4">
</video>

### 图层定位

当你讲一个图层（子）放置在另一个图层（父）的上面，Framer会自动识别其位置，并预判当父图层或画板改变尺寸时它该怎样被固定。这将会大大加快你的工作效率。当然了，你也可以随时通过右侧的属性调节面板中的位置工具来改变固定点。

举个例子，当你把一个菜单条图层（子）放置在一个选项卡图层（父）的右侧，Framer 将会自动预判你的菜单图层要始终和选项卡右侧对齐。你也可以在任何时候使用属性面板手动去改变这个规则。为了让你在手动调整时有一个直观的印象，你可以在右侧的属性面板里看到一个实时模拟。通过这个实时模拟，你可以看到当前调整地图层在界面中是怎样自适应的。

### 图层尺寸

为了提高你的工作效率，Framer会在你改变父图层（包含画板）尺寸时，自动改变子图层的尺寸。

<video loop autoplay poster="/images/learn/design/anchoring-poster.png">
	<source src="/images/learn/design/anchoring.mp4" type="video/mp4">
</video>

### 图层裁切

因为Framer的图层是基于父子图层关系来实现分组的，所以裁切和遮罩的处理也有些不同。想要对某个图层进行遮罩，就将这个图层放在它父图层的内部，选中父图层并点击右侧属性面板中的 Clip （裁切），那么子图层超出父图层以外的部分就变成不可见的了。

### 文字对齐属性

在 Framer 中，文字是一种特殊的图层，它有很多特殊的自动识别属性。一个文字图层的文字对齐方式是依据其在父图层（或者画板）中的位置决定的。

比如说，当你把一个图层放置在一个导航图层的左侧时，文字会自动左对齐。无论你怎样改变父图层的尺寸或者放大缩小。你也可以在右侧的属性调节面板中使用位置工具手动改变其对齐规则。

<video loop autoplay poster="/images/learn/design/text-align-poster.png">
	<source src="/images/learn/design/text-align.mp4" type="video/mp4">
</video>

### 改变文字尺寸

在 Framer 中，改变文字尺寸和文字图层尺寸都可以改变字体大小。改变文字大小将改变图层的边界，可以用这个特性来用字号决定文本块大小。

<video loop autoplay poster="/images/learn/design/text-size-poster.png">
	<source src="/images/learn/design/text-size.mp4" type="video/mp4">
</video>

<a id="exporting"></a>
## 导出

##### 你可以导出屏幕、资源，或者是复制 CSS 属性值以供开发使用。

Framer 的导出功能和你预想的一样，你可以同时导出多种分辨率的一个框架或者形状。你只需要选择一个图层，点击右下角的导出按钮就可以导出了。你还可以自定义一些导出的设置，比如给导出资源添加后缀，或者点击后缀的下拉菜单选择是以文件名后缀区分还是以文件夹名称区分。

<div class="row">
	<div class="col-sm-6">
		<h3>格式</h3>
		<p class="shortcut">
			<span class="hotkey">PNG</span>
			<span class="hotkey">JPG</span>
			<span class="hotkey">PDF</span>
			<span class="hotkey">WEBP</span>
		</p>
	</div>
	<div class="col-sm-6">
		<h3>尺寸</h3>
		<p class="shortcut">
			<span class="hotkey">.5x</span>
			<span class="hotkey">1x</span>
			<span class="hotkey">1.5x</span>
			<span class="hotkey">2x</span>
			<span class="hotkey">3x</span>
			<span class="hotkey">4x</span>
		</p>
	</div>
</div>

<video loop autoplay>
	<source src="/images/learn/design/export.mp4" type="video/mp4">
</video>

### 快速导出
你可以右击一个图层快速导出。你可以选择复制图片或者使用快捷键 `CMD + C` 来复制选中项，接着可以粘贴到其他地方，比如在文档中，在原型软件中或是在聊天软件中粘贴。

<video loop autoplay>
	<source src="/images/learn/design/export-quick.mp4" type="video/mp4">
</video>

### CSS & SVG 导出
右击图层选择复制 CSS 可以复制样式代码，或者选择复制 SVG 可以复制 SVG 图形代码。接下来你可以将复制的代码粘贴到代码编辑器中使用，加速开发流程。

<video loop autoplay>
	<source src="/images/learn/design/export-css.mp4" type="video/mp4">
</video>

### 导出预设
Framer 有一些内置的导出预设。iOS 和 Android 预设包含了所有开发需要的资源尺寸，你也可以点击导出面板的 `+` 来添加自定义的导出设置。

<div class="row">
	<div class="col-sm-6">
		<h3>iOS 尺寸预设</h3>
		<p class="shortcut">
			<span class="hotkey">1x</span>
			<span class="hotkey">2x</span>
			<span class="hotkey">3x</span>
		</p>
	</div>
	<div class="col-sm-6">
		<h3>Android 尺寸预设</h3>
		<p class="shortcut">
			<span class="hotkey">1x</span>
			<span class="hotkey">1.5x</span>
			<span class="hotkey">2x</span>
			<span class="hotkey">3x</span>
			<span class="hotkey">4x</span>
		</p>
	</div>
</div>

<video loop autoplay>
	<source src="/images/learn/design/export-presets.mp4" type="video/mp4">
</video>

<a id="additional-features"></a>
## 其他特性

##### 在这一节我们将学习一下Framer中其它的一些可用工具。你可以在图层列表中右击某个图层，或者在画布中右击以查看这些功能。

### 向前 & 向后

使用这两个菜单可以快速调整图层层级顺序，选中一个图层点击靠前将会把这个图层往图层列表的上面移动，而靠后则相反。当你改变一个图层的层级顺序时，它的所有子图层也会跟随移动。

### 复制

选择一个图层或画板右击，选择“duplicate（复制）”将恢复至并粘贴它到画布中，复制出来的图层或画板和之前一模一样，包括内部子图层。复制的画板将会放在在原画板右边，而复制的图层将会再远图层的上方堆叠。

### 删除

选中一个画板或图层，右击选择“delete（删除）”将会删掉所选画板或图层及其子图层。

### 从层级中删除

如果只想删除父图层而保留子图层，可以选中它右击选择“delete from hierarchy（从层级中删除）”。这将会删掉该图层，并使其子图层回到初始层级。

### 添加父图层

选择一个或多个图层，右击选择“add parent（添加父图层）”将会将它们作为一组放在一个不可见的父图层下。使用自动响应式布局，他们将会表现得像同一个图层一样，改变父图层尺寸将不会影响他们。

<a id="shortcuts"></a>
## 快捷键

<div class="row">
	<div class="col-sm-6">
		<h3>工具</h3>
		<p class="shortcut"><span class="hotkey">A</span>画板</p>
		<p class="shortcut"><span class="hotkey">R</span>矩形图层</p>
		<p class="shortcut"><span class="hotkey">O</span>圆形图层</p>
		<p class="shortcut"><span class="hotkey">T</span>文字图层</p>
		<p class="shortcut"><span class="hotkey">Z</span>放大缩小</p>
	</div>
	<div class="col-sm-6">
		<h3>画布</h3>
		<p class="shortcut"><span class="hotkey">⌘</span><span class="hotkey">2</span>切换到代码模式</p>
		<p class="shortcut"><span class="hotkey">⌘</span><span class="hotkey">+</span>放大视图</p>
		<p class="shortcut"><span class="hotkey">⌘</span><span class="hotkey">-</span>缩小视图</p>
		<p class="shortcut"><span class="hotkey">⌘</span><span class="hotkey">0</span>缩放到实际尺寸</p>
		<p class="shortcut"><span class="hotkey">⌘</span><span class="hotkey">1</span>使画布居中</p>
		<p class="shortcut"><span class="hotkey">Space</span><span class="hotkey">Drag</span>拖动画布</p>
	</div>
</div>

### 编辑

<div class="row">
	<div class="col-sm-6">
		<p class="shortcut"><span class="hotkey">⌘</span><span class="hotkey">Arrows</span>Objects Size</p>
		<p class="shortcut"><span class="hotkey">⇧</span><span class="hotkey">⌘</span><span class="hotkey">Arrows</span>Units By 10</p>
		<p class="shortcut"><span class="hotkey">0 - 9</span>Change Opacity</p>
		<p class="shortcut"><span class="hotkey">⌥</span>Show Distance</p>
		<p class="shortcut"><span class="hotkey">⌘</span><span class="hotkey">D</span>Duplicate</p>
	</div>
	<div class="col-sm-6">
		<p class="shortcut"><span class="hotkey">⌥</span><span class="hotkey">Drag</span>Duplicate</p>
		<p class="shortcut"><span class="hotkey">⌥</span><span class="hotkey">⌘</span><span class="hotkey">C</span>Copy Style</p>
		<p class="shortcut"><span class="hotkey">⌥</span><span class="hotkey">⌘</span><span class="hotkey">V</span>Paste Style</p>
		<p class="shortcut"><span class="hotkey">⌃</span><span class="hotkey">C</span>Color Picker</p>
		<p class="shortcut"><span class="hotkey">⌘</span><span class="hotkey">A</span>Select all layers</p>
	</div>
</div>

### 布置

<div class="row">
	<div class="col-sm-6">
		<p class="shortcut"><span class="hotkey">⌥</span><span class="hotkey">⌘</span><span class="hotkey">↑</span>移动到前面</p>
		<p class="shortcut"><span class="hotkey">⌥</span><span class="hotkey">⌘</span><span class="hotkey">↓</span>移动到后面</p>
		<p class="shortcut"><span class="hotkey">⌘</span><span class="hotkey">;</span>隐藏</p>
		<p class="shortcut"><span class="hotkey">⌘</span><span class="hotkey">L</span>锁定选择</p>
	</div>
	<div class="col-sm-6">
		<p class="shortcut"><span class="hotkey">⌘</span><span class="hotkey">Enter</span>插入父图层</p>
		<p class="shortcut"><span class="hotkey">⌘</span><span class="hotkey">Delete</span>从层级移除</p>
	</div>
</div>

### 排版

<div class="row">
	<div class="col-sm-6">
		<p class="shortcut"><span class="hotkey">⌘</span><span class="hotkey">B</span>加粗文字</p>
		<p class="shortcut"><span class="hotkey">⌘</span><span class="hotkey">I</span>将文字变斜体</p>
		<p class="shortcut"><span class="hotkey">⌘</span><span class="hotkey">U</span>添加下划线</p>
		<p class="shortcut"><span class="hotkey">⌘</span><span class="hotkey">T</span>改变字体</p>
	</div>
</div>

<a id="importing"></a>
## 导入

如果你想使用其它设计工具设计静态元素再导入Framer添加动效，我们提供了 Sketch 、Photoshop 和 Figma 的一键导入。

### 开始

喜欢使用 Sketch, Figma 或者 Photoshop 进行设计？没关系，Framer 的导入功能可以和他们无缝衔接，你可以在他们之间来回切换。导入之后就可以使用Framer的代码模式给它们添加动效了。

打开 Framer 并切换到代码模式，同时打开一个已保存的 .sketch, Figma or .psd 文件，点击左侧边栏下面的 Import（导入） 图标。此时Framer会自动识别到当前打开的文档，请确保在此之前你已经保存了设计文件。你也可以在弹出的提示框里面选择你需要的尺寸。

![](/images/learn/design/ss-import-sheet@2x.png)

### 选择图层

Framer 会将设计文件中的一个组（非空）作为一个图层，所以图层需要事先被分好组并命名，但个图层将会被忽略。

一旦你成功导入设计图，将会在代码区的顶部看见如下代码：

    # Import file "design"
    sketch = Framer.Importer.load("imported/design@1x")

这段代码就包含了所有你导入的图层。默认情况下，这个文件的变量名是你刚才的文件名，你也可以重命名以便引用内部图层时更加方便。

现在，你可以访问到你所导入的设计图中的一个叫做 layerA 的分组：

    # Import file "design"
    sketch = Framer.Importer.load("imported/design@1x")

    # Set the opacity of layerA
    sketch.layerA.opacity = 0.5

在其它组内的组叫做children。在下面的例子中，这个组有两个子组。你可以直接选去它们，而无需考虑层级。

如果你不想让一个组在Framer中可选，你可以取消分组。给一个组的命名末尾添加 * 会把它变成一个没有子图层的图层，如果不想要这个组直接在末尾加 - 。

![](/images/learn/design/ss-target-hierarchy@2x.png)

### 多图层选取

你也可以同时选取多个图层。当你想要同时对多个图层进行动画时，或者隐藏某一个图层组时会很方便。

你可以使用for 循环来处理，你可以选取导入的所有图层或者某个特定组下的所有图层。

![](/images/learn/design/ss-target-multiple@2x.png)

## 常见问题

### 导入后我的图层怎样放置？

导入 Framer 之后，你的图层会按照之前的坐标转换成 Framer 中坐标。如果你没有使用画板，请确保所有图层在一个坐标为 `(0, 0)` 的图层组下面。

坐标为 `(0, 0)` 的图层在 Framer 中会处于画布的左上角的坐标原点，而当其坐标为负数时就会跑到画布以外。

![](/images/learn/design/ss-xandy@2x.png)

### 导入的设计中可以包含画板吗？

当然可以，你的画板也会被导入的。导入之后，最左侧的画板会被自动设置坐标为 `(0, 0)` ，其他画板的坐标都是相对于它的，这样你就可以将不同的画板串在一起形成多屏应用。

![](/images/learn/design/ss-artboards@2x.png)

### 导入之后之前的隐藏图层在 Framer 中有什么特别的吗？

隐藏图层也会被导入，但是 `visibility` 属性会被默认设置为 `false` 。

![](/images/learn/design/ss-visibility@2x.png)
