# VideoLayer

我们可以通过视频图层来加载视频。视频图层包含一个`layer.player`对象，它是用来控制视频的。浏览器支持很多种视频，包括带有alpha通道的动画解码。
>A videoLayer loads a video. VideoLayers have a layer.player object to control the video. The browser supports many different types of video, including the Animation codec that supports alpha channels.

<a id="videoLayer.video"></a>
## videoLayer.video &lt;string&gt;

给视频图层设置播放源。
>Sets the video URL for the video layer.

	# 创建时设置
	layerA = new VideoLayer
	    video: "hello.mp4"
	 
	# 创建后改变
	layerA.video = "bye.mp4"

<a id="videoLayer.player"></a>
## videoLayer.player &lt;object&gt;

视频播放器的播放器对象。通过这个对象你可以控制视频，还可以监听视频播放、暂停等事件，点击[这里](http://www.w3school.com.cn/jsref/dom_obj_video.asp)查看所有支持的方法和属性。
>Player object for the video layer. Allows you to control the video and listen for playback events. See this overview of all video methods and properties.

	# 创建时设置播放源
	layerA = new VideoLayer
	    video: "hello.mp4"
	 
	# 允许自动播放
	layerA.player.autoplay = true
	 
	# 播放视频
	layerA.player.play()
	 
	# 跳到第 5 秒
	layerA.player.fastSeek(5)
	 
	# 监听暂停事件
	Events.wrap(layerA.player).on "pause", ->
	    print "Video paused"
