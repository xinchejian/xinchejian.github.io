---
layout: post
status: publish
published: true
title: Design a Block Language for Arduino
author:
  display_name: David Li
  login: david
  email: david@xinchejian.com
  url: ''
author_login: david
author_email: david@xinchejian.com
wordpress_id: 479
wordpress_url: http://xinchejian.com/?p=479
date: '2011-02-07 01:02:43 +0800'
date_gmt: '2011-02-06 17:02:43 +0800'
categories:
- arduino
tags:
- arduino
- ide
- block languang
- programming
comments:
- id: 26262
  author: Antonio Roberto Zago
  author_email: facebook.antonioroberto.zago@example.com
  author_url: https://facebook.com/profile.php?id=100000619935099
  date: '2014-06-19 08:39:40 +0800'
  date_gmt: '2014-06-19 00:39:40 +0800'
  content: oi
---
<p>I have been playing around with OpenBlocks. It's a very flexible environment to create a new block language. When it comes to design one for Arduino, I found myself wondering between two different styles of design. <&#47;p></p>
<h3>Design I<&#47;h3></p>
<p>The first design is of course to follow the <a href="http:&#47;&#47;www.arduino.cc&#47;en&#47;Reference&#47;HomePage">Arduino Language Reference<&#47;a> closely. However, the resulting block language seems to be a bit too "verbose?" Or should I say "busy" since it's really a graphical representation of the textual program. Here is a sample of what it looks like for the equivalence of codes here.<&#47;p></p>
<pre style="padding-left:30px">
void setup() {<br />
  pinMode(1, INPUT);<br />
  pinMode(2, OUTPUT);<br />
}<br />
void loop() {<br />
  if (digitalRead(1) == HIGH) {<br />
    digitalWrite(2, LOW);<br />
  }<br />
}<br />
<&#47;pre></p>
<p>
<img style="display:block; margin-left:auto; margin-right:auto;" src="http:&#47;&#47;xinchejian.com&#47;wp-content&#47;uploads&#47;2011&#47;02&#47;vpl-1.jpg" alt="Vpl 1" title="vpl-1.jpg" border="0"&#47;><br />
<&#47;p></p>
<h3>Design II<&#47;h3></p>
<p>Since the block language is targeted at the beginner of Arduino and programming, most of time, we talk about "When the button on pin 1 is pushed, I want the LED on pin 2 to light up." There is a much natural way to map this statement into an intuitive block language by building the blocks around the pin. Here is how it may look like:<&#47;p></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http:&#47;&#47;xinchejian.com&#47;wp-content&#47;uploads&#47;2011&#47;02&#47;vpl-2.jpg" alt="Vpl 2" title="vpl-2.jpg" border="0"&#47;></p>
<p>This language is more concise and easier to understand. The language itself should provide enough meta info to infer the setup codes. However, in order to do this, the language may need a little runtime (OS?) to be compiled along with the Sketch but it seems to be worth the effort. <&#47;p></p>
<p>The OpenBlocks codes I am playing around with the idea is available at my <a href="https:&#47;&#47;github.com&#47;taweili&#47;openblocks&#47;tree&#47;ant">'ant' branch openblocks<&#47;a> on github. Appreciate any feedback on this. <&#47;p></p>
