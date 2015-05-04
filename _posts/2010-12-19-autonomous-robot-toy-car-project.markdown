---
layout: post
status: publish
published: true
title: Autonomous Robot Toy Car Project
author:
  display_name: rngadam
  login: rngadam
  email: rngadam@gmail.com
  url: ''
author_login: rngadam
author_email: rngadam@gmail.com
wordpress_id: 181
wordpress_url: http://xinchejian.com/?p=181
date: '2010-12-19 13:04:28 +0800'
date_gmt: '2010-12-19 05:04:28 +0800'
categories:
- android
- arduino
tags:
- A.R.T.
comments:
- id: 707
  author: Weihua Ju
  author_email: jackie.ju@gmail.com
  author_url: ''
  date: '2011-09-08 03:59:25 +0800'
  date_gmt: '2011-09-07 19:59:25 +0800'
  content: I'd like see a diagram showing how the control board connected with moto
    :)
- id: 875
  author: rngadam
  author_email: rngadam@gmail.com
  author_url: ''
  date: '2011-09-21 17:50:48 +0800'
  date_gmt: '2011-09-21 09:50:48 +0800'
  content: "It doesn't attach to the motor, I use the transmitter to send commands
    (as if the robot car was talking to itself...)\r\n\r\nLet me work on some updated
    documentation for the wiki (http:&#47;&#47;wiki.xinchejian.com)"
---
<div>I bought an <a href="http:&#47;&#47;item.taobao.com&#47;item.htm?id=7905841099">RC car from Taobao<&#47;a> at the extremely cheap price of 67RMB (shipping included! 10$USD!)!<&#47;div></p>
<div>For that price, you get an RC remote, a rechargeable Ni-Cd 400mAh&#47;6V battery pack, the radio transmitter (27.145Mhz). Wheels have rubber, autonomy and range is decent although the chassis is very very cheap plastic obviously.<&#47;div></p>
<div>The downsides: on wood floor, it tends to spin so any autonomous program would need to constantly adjust based on sensor (distance ranging) input. It also has propulsion motors on a simple shock so the base isn&rsquo;t totally flat with the ground.<&#47;div></p>
<div>The transmitter needed two AA batteries (not included!) so on Friday I ran out late at night to buy a pair of them (6RMB) and went on an excursion in the cold night to acquire a bunch of precision screwdrivers (25RMB, although really they&rsquo;re worth 15). Pretty difficult achievement since this is after 9pm on a Friday night!<&#47;div></p>
<div>While charging the battery, I used my new screwdrivers and removed the plastic cover. I also took a look at the electronics for the transmitter. The transmitter is very simple, with 4 contact switches, what I assume is a Pulse Modulation IC, a couple of capacitors and resistances. &nbsp;The way an RC transmitter works is described informatively on "<a href="http:&#47;&#47;electronics.howstuffworks.com&#47;rc-toy2.htm">How Stuff Works<&#47;a>".<&#47;div></p>
<div>As an hack, I hook up the four switches to each emitter pin of a ULN2803APG (a simple IC that is basically 8 NPN transistors) with the base controlled by the Arduino itself. This lets me control the car with a very simple program to test Forward, Backward, Left and Right.<&#47;div></p>
<div>The challenges ahead:<&#47;div></p>
<div>1) finding a distance ranging solutions<&#47;div></p>
<div>The robot needs to know how far walls and various objects are&hellip;<&#47;div></p>
<div>a) either IR (<a href="http:&#47;&#47;www.acroname.com&#47;robotics&#47;info&#47;articles&#47;sharp&#47;sharp.html">Sharp IR<&#47;a>)<&#47;div></p>
<div>The GP2Y0A700 looks like one with the longest range, but it&rsquo;s also very expensive (around 50$USD). The next one, GP2Y0A02, is about 15$USD with a range of 20cm-150cm. I probably want a bunch (3?) so I this is probably more cost effective.<&#47;div></p>
<div>b) or ultrasonic (such as the <a href="http:&#47;&#47;item.taobao.com&#47;item.htm?id=4130599681">Parallax Ping<&#47;a> or <a href="http:&#47;&#47;www.seeedstudio.com&#47;depot&#47;ultra-sonic-range-measurement-module-p-626.html?cPath=84_90&amp;zenid=93540aaf65d1a2170d41992feec85547">SeeedStudio Ultrasonic Range Measurement module<&#47;a>)<&#47;div></p>
<div>c) probably a combination of them<&#47;div></p>
<div>2) need to mount the Arduino, a breadboard and the sensors on the car. This will probably require a custom aluminium plate that I can mount using the screwholes that were used for the plastic cover.<&#47;div></p>
<div>3) Figuring out how to control the motors.<&#47;div></p>
<div>
Two ways;<&#47;div></p>
<div>a) remove the current control board and substitute my own. This means an H-bridge that would let me control the motors both ways (Texas Instruments L293NE or Texas Instruments SN754410)<&#47;div></p>
<div>b) create my own RC transmitter.<&#47;div></p>
<div>
I&rsquo;m favoring (b) right now and I went out to buy a bunch of 27.145Mhz crystals at electronics town (10RMB for 8!)<&#47;div></p>
