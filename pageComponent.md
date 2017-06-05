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

    # Define second page 
    pageTwo = new Layer
        width: page.width
        height: page.height
        backgroundColor: "#90D7FF"
     
    # Add the second page to the right 
    page.addPage(pageTwo, "right")

>Another way to go about adding content is by using a for-loop.

    # Create a new PageComponent and only allow horizontal scrolling. 
    page = new PageComponent
        width: Screen.width
        height: Screen.height
        scrollVertical: false
        backgroundColor: "#fff"
     
    # Create 5 new layers and add them to the page.content 
    for number in [0...5]
        pageContent = new Layer
            width: page.width
            height: page.height
            x: page.width * number
            backgroundColor: Utils.randomColor(0.5)
            parent: page.content
     
        # Visualize the current page number 
        pageContent.html = pageContent.html = number + 1
     
        # Center the current page number 
        pageContent.style =
            "font-size" : "100px",
            "font-weight" : "100",
            "text-align" : "center",
            "line-height" : "#{page.height}px"

<a id="pageComponent.originX"></a>
## page.originX <number>


>Defines how pages will be horizontally snapped to. The origin is defined as a number between 0 and 1, where 0 is the left-edge and 1 the right-edge. The default value is 0.5, the center.

page = new PageComponent
page.originX = 0

page.originY <number>

Defines how pages will be vertically snapped to. The origin is defined as a number between 0 and 1, where 0 is the top-edge and 1 the bottom-edge. The default value is 0.5, the center.

page = new PageComponent
page.originY = 0

page.velocityThreshold <number>

The velocityThreshold influences the role velocity plays in snapping to a different page. Besides the scrolling distance, the PageComponent also takes your scrolling speed (velocity) into account.

page = new PageComponent
page.velocityThreshold = 0.2

To better understand the effects of adjusting the velocityThreshold, you can print out your velocity after scrolling. If you want switching between pages to be based mostly on distance, increase the velocityThreshold.

# Increase the velocityThreshold 
page.velocityThreshold = 5
 
# After switching between pages, print the velocity 
page.on Events.ScrollEnd, ->
    print Math.abs(page.velocity.x)

page.animationOptions <object>

Set the animation options for the PageComponent. This defines the animation that occurs on ScrollEnd, when snapping to a page.

page = new PageComponent
 
page.animationOptions =
    curve: Bezier.ease
    time: 0.25

page.currentPage <Layer object>

Get the current page layer. (Read-only)

page = new PageComponent
 
# Get the current page layer 
print page.currentPage

Note that you have to have pages within the page.content layer. You can also listen to the "change:currentPage" event to get the new currentPage, after it has been changed.

page = new PageComponent
 
# When the current page changes, print the new one 
page.on "change:currentPage", ->
    print page.currentPage

page.closestPage <Layer object>

Get the closest page layer. (Read-only)

page = new PageComponent
 
# Get the current page layer 
print page.closestPage

Note that you have to have pages within the page.content layer. You can also listen to the Scroll event to get the page closest page while scrolling.

# Create a new PageComponent and only allow horizontal scrolling. 
page = new PageComponent
 
# Print the closest page while scrolling 
page.on Events.Scroll, ->
    print page.closestPage

page.nextPage(direction, currentPage)

Get the next page. Takes two arguments: direction and the currentPage. By default, the direction is set to "right" and the currentPage will be the first page.

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

We can also set the currentPage to any other page. For instance, we can look which layer is at the left of the second page.

# Get the page to the left of pageTwo 
print page.nextPage("left", pageTwo)
 
# Returns pageOne 

page.previousPage <Layer object>

Get the previous page. Effectively the same as getting the page on the left using page.nextPage("left"). (Read-only)

page = new PageComponent
 
# Get the previous page 
print page.previousPage

page.snapToPage(page, animate, animationOptions)

Snap to a specific page. Takes three arguments: a page.content layer, animate (true or false) and animation options. By default, animate is set to true and the animationCurve use a spring curve.

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

In the example above, we can customize the scrolling animation by defining custom animationOptions as well.

# Define a slower easing curve 
page.snapToPage(
    pageTwo
    true
    animationOptions = time: 2
)

page.snapToNextPage(direction, animate, animationOptions)

Snap to a specific the next page. Takes three arguments: direction, animate (true or false) and animation options. By default, the direction is set to "right" and animate is true.

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

This allows you to snap to pages in any direction. For example, we can start on the first page by snapping to it without animating, and then animate back to the first page.

# Start at page two by default 
page.snapToPage(pageTwo, false)
 
# Scroll back to the page at its left, which is pageOne 
page.snapToNextPage("left", true)

page.snapToPreviousPage()

Snaps to the previous page. It keeps track of all previously visited pages, included the direction.

page = new PageComponent
 
# Snap to the previous page 
page.snapToPreviousPage()

page.addPage(direction)

Add a new page to the page.content layer of the PageComponent. It takes two arguments: a layer (page) and a direction ("right" or "bottom").

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

If you're looking to add pages to the left, you can initially add them to the right, and instantly switch to a different page, using snapToPage().

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

page.horizontalPageIndex(page)

Get the index for a page component with horizontal pages. This is a number between 0 and the number of pages minus 1.

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

page.verticalPageIndex(page)

Get the index for a page component with vertical pages. This is a number between 0 and the number of pages minus 1.

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

