---
layout: post
status: publish
published: true
title: First successful autonomous run of A.R.T.
author:
  display_name: rngadam
  login: rngadam
  email: rngadam@gmail.com
  url: ''
author_login: rngadam
author_email: rngadam@gmail.com
wordpress_id: 158
wordpress_url: http://xinchejian.com/?p=158
date: '2010-12-27 00:44:38 +0800'
date_gmt: '2010-12-26 16:44:38 +0800'
categories:
- robot
- arduino
tags:
- A.R.T.
comments:
- id: 9
  author: haixiao.sun
  author_email: haixiao.sun@gmail.com
  author_url: ''
  date: '2010-12-27 09:10:26 +0800'
  date_gmt: '2010-12-27 01:10:26 +0800'
  content: Wow, That is really wonderful.... now i know who black out the Xindanwei
    while I am leaving. :) Cheers, Ricky!!!
---
<p>Today was a day of many firsts for me:</p>
<ul>
<li>First time I made holes in a piece of wood with a Dremel</li>
<li>First time I bought tie-wraps in China</li>
<li>First time I blew up the fuse for Xindanwei putting everyone in the dark when I tried to solder</li>
<li>First time I've connected the Vin for an Arduino Dueminalove (instead of the external power header or USB)</li>
<li>First time I've read values from an infrared sensor (E18-D80NK with a <a href="http://www.61mcu.com/upload/E18-D80NK-DATASHEET-0410.pdf">Chinese only datasheet</a>)</li>
<li><strong><a href="http://www.youtube.com/watch?v=Vtc--IvJSNY">First time I got an autonomous robot to be, well, autonomous - by myself!</a> (<a href="http://www.youtube.com/watch?v=Vtc--IvJSNY">video</a>)</strong></li><br />
</ul><br />
[gallery link="file"]</p>
<p>It's neither very nice looking or very impressive when it runs, but I'm still very happy with the results. &nbsp;I planned something electro-mechanical with a tiny bit of embedded software all by myself (with some help from Niko with the Dremel and H&eacute;q&iacute;ch&eacute;n /&nbsp;何琪辰 to buy the tie-wraps!). I planned, executed and... got the results I wanted!</p>
<p>The simplistic code that I used:</p>
<pre>const int FORWARD =  2;<br />
const int REVERSE =  3;<br />
const int LEFT = 4;<br />
const int RIGHT =  5;  </p>
<p>const int INFRARED_FORWARD = A0;<br />
const int INFRARED_REVERSE = A1;<br />
const int MINIMUM_INFRARED_READING = 500;<br />
int current_reverse = LEFT;<br />
int alt_forward = RIGHT;</p>
<p>char current_state;</p>
<p>void setup() {<br />
  pinMode(FORWARD, OUTPUT);<br />
  pinMode(REVERSE, OUTPUT);<br />
  pinMode(LEFT, OUTPUT);<br />
  pinMode(RIGHT, OUTPUT);<br />
  pinMode(INFRARED_FORWARD, INPUT);<br />
  pinMode(INFRARED_REVERSE, INPUT);<br />
  Serial.begin(9600);<br />
}</p>
<p>char update_state(char state, int reason) {<br />
  char previous_state = current_state;<br />
  if(state != current_state) {<br />
    current_state = state;<br />
    Serial.print(current_state);<br />
    Serial.println(reason);<br />
  }<br />
  return previous_state;<br />
}<br />
void loop(){<br />
    // always check if we can go forward<br />
    int value = analogRead(INFRARED_FORWARD);<br />
    if(value >= MINIMUM_INFRARED_READING) {<br />
        // maybe we were correcting, so check that<br />
        char last_state = update_state('F', value);<br />
        digitalWrite(current_reverse, LOW);<br />
        digitalWrite(REVERSE, LOW);<br />
        if(last_state == 'R') {<br />
          // we just successfully exited a bad loop, turn for a bit for half a second<br />
          digitalWrite(alt_forward, HIGH);<br />
          digitalWrite(FORWARD, HIGH);<br />
          delay(1000);<br />
          digitalWrite(alt_forward, LOW);<br />
        }<br />
        digitalWrite(FORWARD, HIGH);<br />
    } else {<br />
      // otherwise, still correcting, keep off<br />
      digitalWrite(FORWARD, LOW);<br />
      // we want to try to find an alt path<br />
      int value = analogRead(INFRARED_REVERSE);<br />
      if(value >= MINIMUM_INFRARED_READING) {<br />
        //still have some ability to go backward<br />
        update_state('R', value);<br />
        digitalWrite(current_reverse, HIGH);<br />
        digitalWrite(REVERSE, HIGH);<br />
      } else {<br />
        // whooaah, even backward is not possible, we're stuck<br />
        digitalWrite(current_reverse, LOW);<br />
        digitalWrite(REVERSE, LOW);<br />
        update_state('S', value);<br />
      }<br />
    }<br />
}</pre><br />
Wins:</p>
<ul>
<li>Wooden board and tie-wraps work exceptionally well to prototype the physical arrangement</li>
<li>Using the breadboard to prototype the electronics also works well</li>
<li>The Arduino "Vin" to provide current in the board header works very well (and can seamlessy switch between USB and that without resetting!)</li>
<li>Sticking the RF transmitter board directly on the robot and controlling the motors with that from the Arduino works well</li>
<li>The LED that comes on when an obstacle is detected by the infrared sensors is very useful for debugging (need to keep that in mind when using other &nbsp;sensors)</li>
<li>It works!</li><br />
</ul><br />
Losses:</p>
<ul>
<li>Uses Alkaline AA batteries (I want to switch to the exact same Rechargeable NiCad as the car uses)</li>
<li>I spent too much time working with Sketchup instead of manually testing the mechanical design first (and then Sketchup)</li>
<li>There's not much around Xindanwei in terms of computer, electronic or small mechanical stores, so I should plan ahead to shop on Beijing road</li>
<li>The infrared sensors that I found in the pile of stuff in Xinchejian work, but more like "on/off" sensors (don't seem to have any linearity in the distance)</li>
<li>No bumper (the infrared sensor was crashing into the walls...)</li>
<li>Making an obstacle course big enough is annoying</li>
<li>I had forgotten to make the holes to attach the sensors (more holes == better)</li>
<li>No on/off switch so have to manually remove the connections to turn off power</li>
<li>You can never have enough tie-wraps... We only had four at Xinchejian before I bought a pack of 500 for 15RMB (but really, worth about 5RMB)</li>
<li>I need to learn how to solder... without blowing fuses...</li><br />
</ul></p>
