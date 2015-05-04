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
<p><&#47;style></p>
<div id="ym4-arduino-uno">
<p>Another weekend night of hacking fun hooking up a Arduino Uno with <a href="http:&#47;&#47;xinchejian.com&#47;?p=487" target="_blank">YM4 robotic car<&#47;a> from <a href="http:&#47;&#47;www.embedream.com&#47;" target="_blank">EmbeDream<&#47;a>. The YM4 is a well designed <a href="http:&#47;&#47;www.fira.net&#47;" target="_blank">FIRA<&#47;a> compliant robot car with built in power supply. The left and right wheels are controlled independently and the built in feedback from wheels. <&#47;p></p>
<p>The break out board for the YM4 is easy to work with. The H-bridge control are CT1, CT2, and CT3. CT1 control the speed with PWM and CT2&#47;CT3 decide the direction of the wheel. This is the same configuration for both wheels. The following is a quick sketch to get YM4 going forward.<&#47;p></p>
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
<&#47;code><&#47;pre></p>
<p>Now, the TODO list<&#47;p></p>
<ul>
<li>Find a more secure way to protect the Uno board and protect it from bumping into objects when robot start to run<&#47;li>
<li>Figure out how and where to attach sensors: ultrasonic distance and infra red for distance and obstacle sensing<&#47;li><br />
<&#47;ul></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http:&#47;&#47;xinchejian.com&#47;wp-content&#47;uploads&#47;2011&#47;03&#47;DSC_7415.jpg" alt="DSC 7415" title="DSC_7415.JPG" border="0"&#47;></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http:&#47;&#47;xinchejian.com&#47;wp-content&#47;uploads&#47;2011&#47;03&#47;DSC_7417.jpg" alt="DSC 7417" title="DSC_7417.JPG" border="0"&#47;></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http:&#47;&#47;xinchejian.com&#47;wp-content&#47;uploads&#47;2011&#47;03&#47;DSC_7421.jpg" alt="DSC 7417" title="DSC_7417.JPG" border="0"&#47;></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http:&#47;&#47;xinchejian.com&#47;wp-content&#47;uploads&#47;2011&#47;03&#47;DSC_7422.jpg" alt="DSC 7417" title="DSC_7417.JPG" border="0"&#47;></p>
<p><&#47;div></p>
