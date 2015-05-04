---
layout: post
status: publish
published: true
title: EmbeDream YM4 and Arduino Uno
author:
  display_name: David Li
  login: david
  email: david@xinchejian.com
  url: ''
author_login: david
author_email: david@xinchejian.com
wordpress_id: 511
wordpress_url: http://xinchejian.com/?p=511
date: '2011-03-05 21:44:23 +0800'
date_gmt: '2011-03-05 13:44:23 +0800'
categories:
- Uncategorized
tags:
- robot
- arduino
- embedream
- fira
comments: []
---
<style>
#ym4-arduino-uno img<br />
{<br />
	margin:5px;<br />
	padding:5px;<br />
	display:block;<br />
}</p>
<p></style></p>
<div id="ym4-arduino-uno">
<p>Another weekend night of hacking fun hooking up a Arduino Uno with <a href="http://xinchejian.com/?p=487" target="_blank">YM4 robotic car</a> from <a href="http://www.embedream.com/" target="_blank">EmbeDream</a>. The YM4 is a well designed <a href="http://www.fira.net/" target="_blank">FIRA</a> compliant robot car with built in power supply. The left and right wheels are controlled independently and the built in feedback from wheels. </p></p>
<p>The break out board for the YM4 is easy to work with. The H-bridge control are CT1, CT2, and CT3. CT1 control the speed with PWM and CT2/CT3 decide the direction of the wheel. This is the same configuration for both wheels. The following is a quick sketch to get YM4 going forward.</p></p>
<pre><code><br />
#define RIGHT_CTRL_1 5<br />
#define RIGHT_CTRL_2 6<br />
#define RIGHT_CTRL_3 7</p>
<p>#define LEFT_CTRL_1 11<br />
#define LEFT_CTRL_2 12<br />
#define LEFT_CTRL_3 13</p>
<p>void setup()<br />
{<br />
 pinMode(RIGHT_CTRL_2, OUTPUT);<br />
 pinMode(RIGHT_CTRL_3, OUTPUT);<br />
 pinMode(LEFT_CTRL_2, OUTPUT);<br />
 pinMode(LEFT_CTRL_3, OUTPUT);<br />
}</p>
<p>void loop()<br />
{<br />
  digitalWrite(RIGHT_CTRL_2, 0);<br />
  digitalWrite(RIGHT_CTRL_3, 1);<br />
  analogWrite(RIGHT_CTRL_1, 128);<br />
  digitalWrite(LEFT_CTRL_2, 0);<br />
  digitalWrite(LEFT_CTRL_3, 1);<br />
  analogWrite(LEFT_CTRL_1, 128);<br />
}<br />
</code></pre></p>
<p>Now, the TODO list</p></p>
<ul>
<li>Find a more secure way to protect the Uno board and protect it from bumping into objects when robot start to run</li>
<li>Figure out how and where to attach sensors: ultrasonic distance and infra red for distance and obstacle sensing</li><br />
</ul></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http://xinchejian.com/wp-content/uploads/2011/03/DSC_7415.jpg" alt="DSC 7415" title="DSC_7415.JPG" border="0"/></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http://xinchejian.com/wp-content/uploads/2011/03/DSC_7417.jpg" alt="DSC 7417" title="DSC_7417.JPG" border="0"/></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http://xinchejian.com/wp-content/uploads/2011/03/DSC_7421.jpg" alt="DSC 7417" title="DSC_7417.JPG" border="0"/></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http://xinchejian.com/wp-content/uploads/2011/03/DSC_7422.jpg" alt="DSC 7417" title="DSC_7417.JPG" border="0"/></p>
<p></div></p>
