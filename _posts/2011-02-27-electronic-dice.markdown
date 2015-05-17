---
layout: post
status: publish
published: true
title: Electronic Dice
author:
  display_name: David Li
  login: david
  email: david@xinchejian.com
  url: ''
author_login: david
author_email: david@xinchejian.com
wordpress_id: 501
wordpress_url: http://xinchejian.com/?p=501
date: '2011-02-27 11:31:02 +0800'
date_gmt: '2011-02-27 03:31:02 +0800'
categories:
- arduino
tags:
- arduino
- cubscout
- engineer badge
comments: []
---
<p>Got a chance to introduce Arduino to the boy scout at YCIS. It was a fun afternoon working with the boys and the parents. Here are more on the design of the electronic dice. Look forward to seeing the boys completing the system next week. </p></p>
<p>The tool used to design the dice is <a href="http://fritzing.org" target="_blank">Fritzing</a>. It's an open source design program for interactive electronics. The functionalities of the dice is pretty straight forward: when the button is press, the LEDs start to flash and on the release of the button, one of the LED is randomly picked.</p></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="/uploads/2011/02/untitled.jpg" alt="Untitled" title="untitled.jpg" border="0"/></p></p>
<p>
<img style="display:block; margin-left:auto; margin-right:auto;" src="/uploads/2011/02/untitled1.jpg" alt="Untitled" title="untitled.jpg" border="0"/><br />
</p></p>
<p><a href="http://arduino.cc" target="_blank">Arduino</a> is used to drive the dice logics. Arduino is a popular open source microcontroller for building interactive electronics. It comes with an easy-to-use IDE that can be downloaded <a href="http://arduino.cc/en/Main/Software" target="_blank">here.</a> </p></p>
<p>
<img style="display:block; margin-left:auto; margin-right:auto;" src="/uploads/2011/02/untitled2.jpg" alt="Untitled" title="untitled.jpg" border="0"/><br />
</p></p>
<p>The complete program of the dice is here. Just connect up the Arduino board to the computer using the USB cable and launch the IDE to upload the program. Would be fun to see some tinkering with the program to provide different behavior of the dice. </p></p>
<pre><code><br />
#define RANDOM 1<br />
#define PICKED 2<br />
#define BOUNCEDELAY 50</p>
<p>int state;<br />
void setup()<br />
{<br />
  pinMode(7, INPUT);<br />
  pinMode(2, OUTPUT);<br />
  pinMode(3, OUTPUT);<br />
  pinMode(4, OUTPUT);<br />
  state = 1;<br />
  Serial.begin(9600);<br />
}</p>
<p>int reading = 0;<br />
int button = 0;<br />
int last_button = 0;<br />
int picked = 0;</p>
<p>void loop()<br />
{<br />
  if (state == RANDOM) {<br />
    digitalWrite(2, HIGH);<br />
    digitalWrite(3, LOW);<br />
    digitalWrite(4, LOW);<br />
    delay(50);<br />
    digitalWrite(2, LOW);<br />
    digitalWrite(3, HIGH);<br />
    digitalWrite(4, LOW);<br />
    delay(50);<br />
    digitalWrite(2, LOW);<br />
    digitalWrite(3, LOW);<br />
    digitalWrite(4, HIGH);<br />
    delay(50);<br />
  } else if (state == PICKED) {<br />
    digitalWrite(2, LOW);<br />
    digitalWrite(3, LOW);<br />
    digitalWrite(4, LOW);<br />
    digitalWrite(picked, HIGH);<br />
  }</p>
<p>  reading = digitalRead(7);<br />
  if (reading == last_button) {<br />
    button = reading;<br />
  } else {<br />
   last_button = reading;<br />
  }</p>
<p>  if (button == 1) {<br />
    state = RANDOM;<br />
  } else {<br />
    state = PICKED;<br />
    if (button != last_button) {<br />
      picked = random(3) + 2;<br />
    }<br />
  }<br />
}<br />
</code></pre></p>
