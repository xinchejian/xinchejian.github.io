---
layout: post
status: publish
published: true
title: RC Transmitter reverse-engineering attempt
author:
  display_name: rngadam
  login: rngadam
  email: rngadam@gmail.com
  url: ''
author_login: rngadam
author_email: rngadam@gmail.com
wordpress_id: 141
wordpress_url: http://xinchejian.com/?p=141
date: '2010-12-26 12:32:39 +0800'
date_gmt: '2010-12-26 04:32:39 +0800'
categories:
- robot
tags:
- A.R.T.
comments:
- id: 21774
  author: Dave woods
  author_email: Davedwood@facebook.com
  author_url: http://Google
  date: '2013-11-28 18:12:01 +0800'
  date_gmt: '2013-11-28 10:12:01 +0800'
  content: What are you tryin to do with th tx chip, and the arduino, are u tryn to
    change frequency or change the rx chip?
---
<p>Kind of a failed attempt, but I thought my approach was interesting.</p>
<p>The RC remote has a board to do the control based on four contact switch (Up, Down, Left, Right). &nbsp;The IC on the board says "TX-2-G, A1019265". &nbsp;I couldn't find the datasheet or the IC online (I think this might be similar to the <a href="http:&#47;&#47;www.datasheetarchive.com&#47;TX2C%20ATS302T-datasheet.html">TX2C<&#47;a> ATS302T which is available on <a href="http:&#47;&#47;item.taobao.com&#47;item.htm?id=3199233926">Taobao<&#47;a>)&nbsp;, so I thought I would try to figure out the circuit by looking at it. &nbsp;Kind of inconvenient because the components are on one side while the circuit trace is in the other.</p>
<p>Flipping over the board constantly is annoying and it's rather hard to follow. &nbsp;Best would be to see both sides at the same time, no?</p>
<p>So this is what I did:</p>
<ol>
<li> took a picture of both sides in macro mode<&#47;li>
<li>cropped both pictures<&#47;li>
<li>created layers using <a href="http:&#47;&#47;www.gimp.org&#47;">GIMP<&#47;a> (a cross-platform OpenSource software similar to Photoshop)<&#47;li>
<li>Put each image on their layers<&#47;li>
<li>Change opacity of top layer<&#47;li>
<li>"Image > Transform > Flip Horizontally" one of the image<&#47;li>
<li>Move one of the image until screw holes on both align<&#47;li><br />
<&#47;ol><br />
[gallery link="file"]</p>
<p>Much easier then to figure out what is connected to what, but still difficult...</p>
<p>Anyway, I decided to try instead to buy a&nbsp;TX2C and follow its datasheet to re-create the circuit. &nbsp;In the meantime, I've removed the board entirely from the remote control body and I'll connect to that directly with the Arduino.</p>
