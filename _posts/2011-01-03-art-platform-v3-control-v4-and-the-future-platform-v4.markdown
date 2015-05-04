---
layout: post
status: publish
published: true
title: ART Platform v3, Control v4 and the future platform v4
author:
  display_name: rngadam
  login: rngadam
  email: rngadam@gmail.com
  url: ''
author_login: rngadam
author_email: rngadam@gmail.com
wordpress_id: 305
wordpress_url: http://xinchejian.com/?p=305
date: '2011-01-03 18:54:32 +0800'
date_gmt: '2011-01-03 10:54:32 +0800'
categories:
- Uncategorized
- robot
- arduino
tags:
- A.R.T.
comments:
- id: 20
  author: '&raquo; CPLD 新车间 [Xinchejian]'
  author_email: ''
  author_url: http://xinchejian.com/?p=315
  date: '2011-01-03 23:14:37 +0800'
  date_gmt: '2011-01-03 15:14:37 +0800'
  content: '[...] I&#8217;ve mentioned in the previous blog post talking about adding
    more ultrasonic sensors connected to the Arduino , I&#8217;m looking at implementing
    some of the logic in digital logic gates external to the [...]'
- id: 283
  author: Jenn
  author_email: studio@paolodefaveri.it
  author_url: http://www.google.com/
  date: '2011-06-28 15:08:34 +0800'
  date_gmt: '2011-06-28 07:08:34 +0800'
  content: Wodernful explanation of facts available here.
- id: 12840
  author: AVC logo animation | Build a Robot
  author_email: ''
  author_url: http://www.build-robot.com/avc-logo-animation.html
  date: '2013-01-27 09:09:17 +0800'
  date_gmt: '2013-01-27 01:09:17 +0800'
  content: '[...] xinchejian.com/?p=305 [...]'
---
<p>I've been writing many, <a href="https://github.com/rngadam/ART/blob/master/ART_Control4/ART_Control4.pde">many iterations of both the software (the controller)</a> after updating the platform (sensors+chassis) itself to have an additional ultrasonic sensor looking backward.  So now, when I rotate the ultrasonic sensor, I read values in front (right side, angle looking right, looking forward and at angle to the left) and towards the back (left-side, side angle looking backward towards the left, angle straight on towards the back and angle looking backward towards the right).</p>
<p>So six values in total...  Having the servo rotate the sensors is necessary right now so as not to go over budget on the digital pins of the Arduino Dueminalove board as each of the two sensors require two signal cable (one for trigger and one for echo).</p>
<p>I've done many changes and many tests but I'm not yet satisfied with the controller for that particular configuration and I still have ideas that I need to implement to make the robot behavior interesting...</p>
<p>However, in the meantime, I'm also preparing for the next platform. I'm thinking of designing a circuit to select one ultrasonic sensor at a time out of four.  Since two sensors cannot be triggered simultaneously (they would interfere with each other) I would want to trigger one at a time and then wait for the echo.</p>
<p>To help with that task, I've discovered two wonderful OpenSource software:</p>
<ul>
<li><a href="http://fritzing.org/">Fritzing</a>: a very good design software that lets you design breadboard, schematic and final PCB layout with a library of parts (or very easy to create custom parts) in an optimized workflow</li>
<li><a href="http://www.kolls.net/gatesim/">Logic Gate Simulator</a>:  create and test logic gates design</li><br />
</ul><br />
For Fritzing, I also took the time to create a custom part for the HC-SR04 Ultrasonic Sensor.  I've done so by first drawing  vector graphics for the breadboard view, schematic view and PCB board in Inkscape.  I then created a new part, imported the just created images and then placing connections "squares" overlaid on the imported images.  Relatively easy, but I spent a lots of time getting the fonts right before discovering that the easiest way was to convert all text to paths (Path > Object to Path).</p>
<p>I've uploaded the HC-SR04 Fritzing part in the relevant <a href="http://code.google.com/p/fritzing/issues/detail?id=875">"user-contributed parts" bug</a> if you need it.</p>
<p>For Logic Gate Simulator, I first wrote down the truth table for the sensor selector ("when pin1 and pin2 are at 1, send trigger signal to sensor4 and receive echo from sensor4") and tested it, but I'm unsure on how to proceed next in terms of buying the necessary IC that would provide me with the AND/NOT logic gate that I need.</p>
<p>I also have to investigate how to change the simplistic Ultrasonic code that's been provided with the sensors to instead generate interrupts so I don't have to block the Arduino loop while waiting for the echo to come back. Same for getting the "stop now" button to actually work!<br />
[gallery]</p>
