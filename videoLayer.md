VideoLayer

A videoLayer loads a video. VideoLayers have a layer.player object to control the video. The browser supports many different types of video, including the Animation codec that supports alpha channels.

videoLayer.video <string>

Sets the video URL for the video layer.

# Set on creation 
layerA = new VideoLayer
    video: "hello.mp4"
 
# Change afterwards 
layerA.video = "bye.mp4"

videoLayer.player <object>

Player object for the video layer. Allows you to control the video and listen for playback events. See this overview of all video methods and properties.

# Set on creation 
layerA = new VideoLayer
    video: "hello.mp4"
 
# Enable auto play 
layerA.player.autoplay = true
 
# Play the video 
layerA.player.play()
 
# Jump to 5 seconds 
layerA.player.fastSeek(5)
 
# Listen to paused playback 
Events.wrap(layerA.player).on "pause", ->
    print "Video paused"
