# MIDIComponent

一个MIDI控制器可以给电脑发送信号，类似于键盘或鼠标。通常大部分的MIDI控制器上面会有按钮、滑块和旋钮，他们会和软件连接。市面上有各种各样的MIDI控制器，一般是使用USB和电脑相连。当然，也有一些MIDI控制软件，通过蓝牙连接。
>A MIDI controller sends signals to your computer, similar to a keyboard or a mouse. Most commonly MIDI controllers have buttons, sliders and knobs that you can hook up to software. There is a wide variety of hardware MIDI controllers available on the market, many of them connect over USB. There are also MIDI controller apps, that connect over Bluetooth.

`MIDIComponent`可以让你用 MIDI 控制器连接 Framer 和支持 MIDI API 的浏览器。
>The MIDIComponent gives you the ability to work with MIDI controllers directly in Framer and in browsers that support the Web MIDI API.

### Get Started

* 连接一个 MIDI 设备
* 打开Framer并复制以下代码进去


    midi = new MIDIComponent
 
    midi.onValueChange (value, info) ->
    print value, info

现在，当你改动 MIDI 设备上的按钮时，会发现屏幕上实时打印出一些值。比如当你把一个控制按钮从头移到尾时：
>Now, when you change a button on the MIDI device you will see the values being printed, for example if you move a control from the start to end position:

    » 0, {source:"111955983", channel:1, control:2}
    » 1, {source:"111955983", channel:1, control:2}
    » 2, {source:"111955983", channel:1, control:2}
    …
    » 125, {source:"111955983", channel:1, control:2}
    » 126, {source:"111955983", channel:1, control:2}
    » 127, {source:"111955983", channel:1, control:2}

默认情况下，`MIDIComponent` 会监听 MIDI 设备上任意频段的所有按钮的信号。你可以使用上面打印出来的第一个数字值去过滤，只监听某几个信号变化。比如你可以使用这种方式让控制按钮 2 和一个滑块组件的值关联起来：
>By default, MIDIComponent will listen to MIDI signals from all controls and note buttons on all devices coming over any channel. You can use the properties you see printed above to filter the signal events. That way you can hook up control number 2 to a slider, for example:

    midi = new MIDIComponent
        control: 2
     
    slider = new SliderComponent
        point: Align.center
        max: 127
     
    midi.onValueChange (value) ->
        slider.value = value


>The output values from MIDI are always between 0 and 127, but if you want to use the value to set a property that has a different range, you can use min and max to modulate the value for you. For example, the RGB components in a color range from 0 to 255, so you can use:

    midi = new MIDIComponent
        min: 0
        max: 255
     
    midi.onValueChange (value) ->
        Screen.backgroundColor = new Color
            r: value, g: 0, b: 0

<a id="min"></a>
## MIDIComponent.min &lt;number&gt;

>The value that will be send as the minimum value to the onValueChange handler. The default value is 0.

<a id="max"></a>
## MIDIComponent.max &lt;number&gt;

>The value that will be send as the maximum value to the onValueChange handler. The default value is 127.

<a id="control"></a>
## MIDIComponent.control &lt;number&gt;

>The number of the control, between 0 and 127. Filters out events not coming from this control.

>To find the correct control number, you can use the extra information send to the handler of onValueChange.

<a id="channel"></a>
## MIDIComponent.channel &lt;number&gt;

>A number between 1 and 16 representing the channel. Filters out all events not coming from this channel.

>To find the current channel of a control, you can use the extra information send to the handler of onValueChange.

<a id="source"></a>
## MIDIComponent.source &lt;string&gt;

>The source to listen to. Filters out all events not coming from this source.

>Each MIDI device has a unique source ID that is managed by the system. In general, the source ID should be stable, so that if you reconnect a device to the same computer, you should get the same ID. Note that the source ID will not be the same between different browsers and Framer.

>To find the source ID, you can use the extra information send to the handler of onValueChange.

<a id="onValueChange"></a>
## MIDIComponent.onValueChange(handler)

>Handle MIDI signal events.

>The handler gets two parameters, first the value of the signal and second an object with more information about the origin.

	midi = new MIDIComponent
	 
	# Print the identifier of the control sending the change 
	midi.onValueChange (value, info) ->
	  print info.control

>See the Get Started section for more examples.

### Properties

>The info parameter is an object with the following properties:

* **control** — the identifier of the control (knob, slider, etc.) sending the signal.
* **channel** — the channel the signal is send over.
* **source** — the identifier of the device sending the signal.
* **type (optional)** — "note" if the signal is coming from a note, the value represents the velocity, 0 means the note is off.
