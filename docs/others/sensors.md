# Sensors
You can access native sensors of mobile devices, like the accelerometer in realtime. These can be accessed from within the Snippets menu of Framer, too. Orientation, Compass and Motion are supported on iOS and Android.

<a id="orientation"></a>
## Orientation
The deviceorientation event allows you to detect the physical device orientation. The 3 properties below are especially useful for prototyping. 
Learn more here.

* **alpha** — device motion around the z axis from 0 to 360
* **beta** — device motion around the x axis from -180 to 180
* **gamma** — device motion around the y axis from -90 to 90


	# Preview on a mobile device 
	window.addEventListener "deviceorientation", (event) ->
	    print "gamma: " + event.gamma

<a id="compass"></a>
## Compass
The webkitCompassHeading property can be used alongside orientation to align with the compass heading on iOS devices. Learn more here.

	# Preview on a mobile device 
	window.addEventListener "deviceorientation", (event) ->
	    if event.webkitCompassHeading
	        heading = event.webkitCompassHeading
	    else
	        heading = event.alpha
	 
	    print "heading: " + heading

<a id="motion"></a>
## Motion
The devicemotion event allows you to detect the device acceleration. The 3 properties below are especially useful for prototyping. Learn more here.

* **acceleration.x** — acceleration around the west to east axis
* **acceleration.y** — acceleration around the south to north axis
* **acceleration.z** — acceleration around the down to up axis


	# Preview on a mobile device 
	window.addEventListener "devicemotion", (event) ->
	    print "x:" + event.acceleration.x
	    print "y: " + event.acceleration.y
	    print "z: " + event.acceleration.z

