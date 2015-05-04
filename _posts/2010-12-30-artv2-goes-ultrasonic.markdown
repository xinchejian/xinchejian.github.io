---
layout: post
status: publish
published: true
title: 'ARTv2 goes Ultrasonic! '
author:
  display_name: rngadam
  login: rngadam
  email: rngadam@gmail.com
  url: ''
author_login: rngadam
author_email: rngadam@gmail.com
wordpress_id: 289
wordpress_url: http://xinchejian.com/?p=289
date: '2010-12-30 23:56:02 +0800'
date_gmt: '2010-12-30 15:56:02 +0800'
categories:
- robot
- arduino
tags:
- A.R.T.
comments:
- id: 40
  author: '&raquo; Chaotic Robo Event 新车间 [Xinchejian]'
  author_email: ''
  author_url: http://xinchejian.com/?p=457
  date: '2011-01-17 20:07:08 +0800'
  date_gmt: '2011-01-17 12:07:08 +0800'
  content: '[...] kicks off the event with A.R.T. and gave a short introduction to
    how he got started with the project and how ART was [...]'
---
<p>The day started with a breakfast next to ARTv2 at Xindanwei/Xinchejian. 潘先生 (aka Panda) had left me an idea on the whiteboard for how to read a continuously rotating sensor without the cables getting twisted. I then had Chinese class with Susan Dai for four hours (2 in the morning and 2 in the afternoon).  When I came back, I messed around with controlling the servo for doing sensor sweeps.</p>
<p>In the evening, during an impromptu Xinchejian show-and-tell with people having a meeting at Xindanwei, I had the following exchange:</p>
<p><strong>Me</strong>: ...since we don't have many working sensors, I'm waiting for the ultrasonic sensors we ordered... BTW, Xu, any news about them?<br />
<strong> Xu</strong>: Oh, they're at my desk!<br />
<strong> Me</strong>: <em>screams like a little girl</em><br />
<strong> Xu</strong>: ... ok, I'll go get them now...</p>
<p>So yeah, I finally got my 10 (!) ultrasonic sensors (<a href="http://iteadstudio.com/store/index.php?main_page=product_info&amp;cPath=9&amp;products_id=52">HC-SR04</a>) this evening, just in time as I had worked out how to control the servo to do sensor sweeps (left and right on 180 degrees). &nbsp;BTW, if you're a Xinchejian member, please feel free to borrow one or two to try them out.</p>
<p>They're affordable (<a href="http://item.taobao.com/item.htm?id=3097091977">37RMB on Taobao</a> or 5.60$USD), ridiculously easy to install and seem to work as advertised, although I haven't benchmarked much.  I've also spent quite a bit of time this evening on a <a href="https://github.com/rngadam/ART/blob/master/ART_Control3/ART_Control3.pde">reasonably workable controller with a state machine</a> but only had time to test it once before I had to call it a day.  I can probably use more sensors (on the sweeper, sideways, looking backward), but I'm thinking that I really need to combine them with infrared sensors as there's a longer delay than infrared in detecting obstacles and they can work at angles simultaneously.</p>
<p>Anyway, more testing and experiments are in order.</p>
<p>[gallery]</p>
