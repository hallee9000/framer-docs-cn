# PageComponent

页面组件是基于滚动组件的，但是是为多页面展现而设计的，而不是像滚动组件一样展示连续的内容。它支持不同尺寸的内容页，并能够基于图层位置和滚动速度来对齐图层。
>The PageComponent is based on the ScrollComponent, but designed for displaying paginated instead of continuous content. It supports content layers of different sizes, and can snap to layers based on location and scroll velocity.

    # 创建一个新的 PageComponent 并只允许横向滚动
    page = new PageComponent
        width: Screen.width
        height: Screen.height
        scrollVertical: false
     
    # 创建第一个页面
    pageOne = new Layer
        width: page.width
        height: page.height
        parent: page.content
        backgroundColor: "#28affa"

创建第二个页面，点[这里](#pageComponent.addPage)了解`addPage`方法。
>Let's add a second page now. Read more about the addPage method.

    # 定义第二个页面
    pageTwo = new Layer
        width: page.width
        height: page.height
        backgroundColor: "#90D7FF"
     
    # 将第二个页面添加至右侧
    page.addPage(pageTwo, "right")

另外一种添加页面的方式是使用 `for` 循环。
>Another way to go about adding content is by using a for-loop.

    # 创建一个新的页面组件并只允许横向滚动
    page = new PageComponent
        width: Screen.width
        height: Screen.height
        scrollVertical: false
        backgroundColor: "#fff"
     
    # 创建五个新图层并添加至 page.content 
    for number in [0...5]
        pageContent = new Layer
            width: page.width
            height: page.height
            x: page.width * number
            backgroundColor: Utils.randomColor(0.5)
            parent: page.content
     
        # 让每个页面显示编号
        pageContent.html = pageContent.html = number + 1
     
        # 让当前页面中的数字居中显示
        pageContent.style =
            "font-size" : "100px",
            "font-weight" : "100",
            "text-align" : "center",
            "line-height" : "#{page.height}px"

<a id="originX"></a>
## page.originX &lt;number&gt;

定义当手指（鼠标）松开页面自由滑行之后，页面在水平方向上是如何停靠在页面组件容器中的。他的值是 0 到 1 之间的一个数字，0 表示停靠在容器左边缘，1 表示停靠在容器右边缘，默认是 0.5 停靠在中间。
>Defines how pages will be horizontally snapped to. The origin is defined as a number between 0 and 1, where 0 is the left-edge and 1 the right-edge. The default value is 0.5, the center.

    page = new PageComponent
    page.originX = 0

<a id="originY"></a>
## page.originY &lt;number&gt;

定义当手指（鼠标）松开页面自由滑行之后，页面在垂直方向上是如何停靠在页面组件容器中的。他的值是 0 到 1 之间的一个数字，0 表示停靠在容器上边缘，1 表示停靠在容器下边缘，默认是 0.5 停靠在中间。
>Defines how pages will be vertically snapped to. The origin is defined as a number between 0 and 1, where 0 is the top-edge and 1 the bottom-edge. The default value is 0.5, the center.

    page = new PageComponent
    page.originY = 0

<a id="velocityThreshold"></a>
## page.velocityThreshold &lt;number&gt;

速度临界值会影响最终停靠点，当你拖动之后松开手指（鼠标），`PageComponent` 会依据此时的滑行速度和滑行距离来决定滑到下一个页面还是后退至停在当前页。
>The velocityThreshold influences the role velocity plays in snapping to a different page. Besides the scrolling distance, the PageComponent also takes your scrolling speed (velocity) into account.

    page = new PageComponent
    page.velocityThreshold = 0.2

为了更好地理解速度临界值，你可以在每次滑行结束时输出此时的速度。如果你想更大程度上让距离来决定页面的切换，就调大速度临界值。
>To better understand the effects of adjusting the velocityThreshold, you can print out your velocity after scrolling. If you want switching between pages to be based mostly on distance, increase the velocityThreshold.

    # Increase the velocityThreshold 
    page.velocityThreshold = 5
 
    # After switching between pages, print the velocity 
    page.on Events.ScrollEnd, ->
        print Math.abs(page.velocity.x)

<a id="animationOptions"></a>
## page.animationOptions &lt;object&gt;

给页面组件设置动画选项，该选项用于松开手指（鼠标）时页面自动贴合的动画。
>Set the animation options for the PageComponent. This defines the animation that occurs on ScrollEnd, when snapping to a page.

    page = new PageComponent
     
    page.animationOptions =
        curve: Bezier.ease
        time: 0.25

<a id="currentPage"></a>
## page.currentPage &lt;Layer object&gt;

获得当前页面图层对象（只读）。
>Get the current page layer. (Read-only)

    page = new PageComponent
     
    # Get the current page layer 
    print page.currentPage

注意：必须要保证`page.content`内已添加页面图层。你也可以监听`change:currentPage`事件来获取到最新的页面图层。
>Note that you have to have pages within the page.content layer. You can also listen to the "change:currentPage" event to get the new currentPage, after it has been changed.

    page = new PageComponent
     
    # 当页面发生变动时，输出该页面图层对象
    page.on "change:currentPage", ->
        print page.currentPage

<a id="closestPage"></a>
## page.closestPage &lt;Layer object&gt;

获取最近的页面图层（只读）。
>Get the closest page layer. (Read-only)

    page = new PageComponent
     
    # Get the current page layer 
    print page.closestPage

注意：必须要保证 `page.content` 内已添加页面图层。你也可以监听 `Scroll` 事件来获取到最近的页面图层。
>Note that you have to have pages within the page.content layer. You can also listen to the Scroll event to get the page closest page while scrolling.

    # Create a new PageComponent and only allow horizontal scrolling. 
    page = new PageComponent
     
    # Print the closest page while scrolling 
    page.on Events.Scroll, ->
        print page.closestPage

<a id="nextPage"></a>
## page.nextPage(direction, currentPage)

获取下一个页面。该方法需要两个参数：方向和当前页面图层。默认情况下，方向参数为 `right` 且当前页面图层为第一个页面。
>Get the next page. Takes two arguments: direction and the currentPage. By default, the direction is set to "right" and the currentPage will be the first page.

    page = new PageComponent
        width: Screen.width
        height: Screen.height
     
    pageOne = new Layer
        width: page.width
        height: page.height
        parent: page.content
        backgroundColor: "#28affa"
     
    pageTwo = new Layer
        width: page.width
        height: page.height
        backgroundColor: "#90D7FF"
     
    page.addPage(pageTwo, "right")
    print page.nextPage()

当然，我们也可以设置当前图层为其它图层，比如通过下面的代码我们可以知道第二个页面的左边是那个页面。
>We can also set the currentPage to any other page. For instance, we can look which layer is at the left of the second page.

    # Get the page to the left of pageTwo 
    print page.nextPage("left", pageTwo)
     
    # Returns pageOne 

<a id="previousPage"></a>
## page.previousPage &lt;Layer object&gt;

获取前一个页面，实际上它和使用 `page.nextPage("left")` 来获取到左边的页面是一样的（只读）。
>Get the previous page. Effectively the same as getting the page on the left using page.nextPage("left"). (Read-only)

    page = new PageComponent
     
    # Get the previous page 
    print page.previousPage

<a id="snapToPage"></a>
## page.snapToPage(page, animate, animationOptions)

立即切换到某一个页面。它需要三个参数：一个 `page.content` 下的页面图层，是否动画（`true` 或者 `false`），以及动画选项。默认情况下是使用动画方式切换，并且动画曲线为一个弹性曲线。
>Snap to a specific page. Takes three arguments: a page.content layer, animate (true or false) and animation options. By default, animate is set to true and the animationCurve use a spring curve.

    page = new PageComponent
        width: Screen.width
        height: Screen.height
     
    pageOne = new Layer
        width: page.width
        height: page.height
        parent: page.content
        backgroundColor: "#28affa"
     
    pageTwo = new Layer
        width: page.width
        height: page.height
        backgroundColor: "#90D7FF"
     
    page.addPage(pageTwo, "right")
    
    # Automatically scroll to pageTwo 
    page.snapToPage(pageTwo)

继续使用上面的例子，我们可以通过自定义动画选项来自定义滚动动画。
>In the example above, we can customize the scrolling animation by defining custom animationOptions as well.

    # Define a slower easing curve 
    page.snapToPage(
        pageTwo
        true
        animationOptions = time: 2
    )

<a id="snapToNextPage"></a>
## page.snapToNextPage(direction, animate, animationOptions)

立即切换到下一个页面。它需要三个参数：方向，是否动画（`true` 或者 `false`），以及动画选项。默认情况下方向为 `right` ，并且以动画形式切换。
>Snap to a specific the next page. Takes three arguments: direction, animate (true or false) and animation options. By default, the direction is set to "right" and animate is true.

    page = new PageComponent
        width: Screen.width
        height: Screen.height
     
    pageOne = new Layer
        width: page.width
        height: page.height
        parent: page.content
        backgroundColor: "#28affa"
     
    pageTwo = new Layer
        width: page.width
        height: page.height
        backgroundColor: "#90D7FF"
     
    page.addPage(pageTwo, "right")
     
    # Automatically scroll to pageTwo 
    page.snapToNextPage()

这可以让你切换到任意方向的页面。比如我们可以先不带动画地切换到第二个页面，再让它带动画地切换回来。
>This allows you to snap to pages in any direction. For example, we can start on the first page by snapping to it without animating, and then animate back to the first page.

    # Start at page two by default 
    page.snapToPage(pageTwo, false)
     
    # Scroll back to the page at its left, which is pageOne 
    page.snapToNextPage("left", true)

<a id="snapToPreviousPage"></a>
## page.snapToPreviousPage()

切换到上一页，该方法可以帮你切换到上一个查看的页面。
>Snaps to the previous page. It keeps track of all previously visited pages, included the direction.

    page = new PageComponent
     
    # Snap to the previous page 
    page.snapToPreviousPage()

<a id="addPage"></a>
## page.addPage(direction)

给 `page.content` 添加一个新页面，他需要两个参数：一个页面图层和方向（ `right` 或 `bottom`）。
>Add a new page to the page.content layer of the PageComponent. It takes two arguments: a layer (page) and a direction ("right" or "bottom").

    page = new PageComponent
        width: Screen.width
        height: Screen.height
     
    # The first page, placed directly within the page.content 
    pageOne = new Layer
        width: page.width
        height: page.height
        parent: page.content
        backgroundColor: "#28affa"
     
    # Second page 
    pageTwo = new Layer
        width: page.width
        height: page.height
        backgroundColor: "#90D7FF"
     
    # Third page 
    pageThree = new Layer
        width: page.width
        height: page.height
        backgroundColor: "#CAECFF"
     
     
    # Add the second and third page to the right 
    page.addPage(pageTwo, "right")
    page.addPage(pageThree, "right")

如果你想在左侧添加一个页面，你可以先在它的右侧添加一个页面，再使用 `snapToPage()` 让它迅速切换到第二个页面，使其看起来像是以第二个页面为初始页。
>If you're looking to add pages to the left, you can initially add them to the right, and instantly switch to a different page, using snapToPage().

    page = new PageComponent
        width: Screen.width
        height: Screen.height
     
    pageOne = new Layer
        width: page.width
        height: page.height
        parent: page.content
        backgroundColor: "#28affa"
     
    pageTwo = new Layer
        width: page.width
        height: page.height
        backgroundColor: "#90D7FF"
     
    # Add a page to the right 
    page.addPage(pageTwo, "right")
     
    # Start at the second page by default 
    page.snapToPage(pageTwo, false)

<a id="horizontalPageIndex"></a>
## page.horizontalPageIndex(page)

获取水平排列的页面索引值，它的值处于 0 到页面数减 1 之间。
>Get the index for a page component with horizontal pages. This is a number between 0 and the number of pages minus 1.

    page = new PageComponent
        width: Screen.width
        height: Screen.height
     
    pageA = new Layer
        size: page.size
     
    pageB = new Layer
        size: page.size
     
    page.addPage(pageA, "right")
    page.addPage(pageB, "right")
     
    print page.horizontalPageIndex(pageA)
    # Prints: 0 
     
    print page.horizontalPageIndex(pageB)
    # Prints: 1 

<a id="verticalPageIndex"></a>
## page.verticalPageIndex(page)

获取垂直排列的页面索引值，它的值处于 0 到页面数减 1 之间。
>Get the index for a page component with vertical pages. This is a number between 0 and the number of pages minus 1.

    page = new PageComponent
        width: Screen.width
        height: Screen.height
     
    pageA = new Layer
        size: page.size
     
    pageB = new Layer
        size: page.size
     
    page.addPage(pageA, "bottom")
    page.addPage(pageB, "bottom")
     
    print page.verticalPageIndex(pageA)
    # Prints: 0 
     
    print page.verticalPageIndex(pageB)
    # Prints: 1 

