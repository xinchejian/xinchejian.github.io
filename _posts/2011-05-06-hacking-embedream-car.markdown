---
layout: post
status: publish
published: true
title: <!--:en-->Hacking Embedream Car<!--:--><!--:zh-->嵌入之梦-圆梦小车开发<!--:-->
author:
  display_name: heqichen
  login: heqichen
  email: heqichen@yahoo.com.cn
  url: ''
author_login: heqichen
author_email: heqichen@yahoo.com.cn
wordpress_id: 980
wordpress_url: http://xinchejian.com/?p=980
date: '2011-05-06 03:43:00 +0800'
date_gmt: '2011-05-05 19:43:00 +0800'
categories:
- quadcopter
- robot
- arduino
tags:
- robot
- arduino
comments: []
---
<h1>嵌入之梦-圆梦小车开发<&#47;h1><br />
<i>May 1st, 2011<&#47;i></p>
<p>今天看到一台嵌入之梦的小车，但是上电之后发了疯似的乱跑，所以刷之。但新车间却没有网络，没办法，自己一点一点试。。结果如下<&#47;p></p>
<pre class="code">CT1	接受pwm，控制速度<br />
CT2	前进控制信号，高电位转动<br />
CT3	后退控制信号，高电位转动<br />
<&#47;pre></p>
<p>但是由于小车上的UNO与我的Ubuntu连接有问题，貌似只有Windows是好的，Mac OS有时也会出问题。所以最后车上改用了Mega 1280。<&#47;p></p>
<p>但是又发现一个问题，就是Arduino使用USB供电的时候很正常，然而，使用车上接出来的5V电源时，程序就会混乱，完全没有一点规律。猜测可能是由于电机转动导致整个系统的电压下降，无法提供足够的电压给Arduino的板子上。这大概也是之前uno不会发疯的原因。没办法，在小车上再接一块9V层叠式电池，作为Arduino的电源。最后终于行了。<&#47;p></p>
<p>后面程序的作用是往前走，遇到前方有物体是后退，打弯，然后继续往前，一个简单的壁障程序。没有用到速度控制。下面就是这个小车最后的样子，手机拍的，将就看吧<&#47;p></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http:&#47;&#47;xinchejian.com&#47;wp-content&#47;uploads&#47;2011&#47;05&#47;untitled4.jpg" alt="Untitled" title="untitled.jpg" border="0"&#47;></p>
<p>左侧照<&#47;p></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http:&#47;&#47;xinchejian.com&#47;wp-content&#47;uploads&#47;2011&#47;05&#47;untitled5.jpg" alt="Untitled" title="untitled.jpg" border="0"&#47;></p>
<p>右侧照<&#47;p></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http:&#47;&#47;xinchejian.com&#47;wp-content&#47;uploads&#47;2011&#47;05&#47;untitled6.jpg" alt="Untitled" title="untitled.jpg" border="0"&#47;></p>
<p>再来一张<&#47;p></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http:&#47;&#47;xinchejian.com&#47;wp-content&#47;uploads&#47;2011&#47;05&#47;untitled7.jpg" alt="Untitled" title="untitled.jpg" border="0"&#47;></p>
<p><embed src="http:&#47;&#47;player.youku.com&#47;player.php&#47;sid&#47;XMjYzMzY0NzA0&#47;v.swf" quality="high" width="480" height="400" align="middle" allowScriptAccess="sameDomain" type="application&#47;x-shockwave-flash"><&#47;embed><br />
<a href="http:&#47;&#47;v.youku.com&#47;v_show&#47;id_XMjYzMzY0NzA0.html">http:&#47;&#47;v.youku.com&#47;v_show&#47;id_XMjYzMzY0NzA0.html<&#47;a></p>
<p>用到的程序就是下面的<&#47;p></p>
<pre class="code">
&#47;&#47;Author:	HE Qichen<br />
&#47;&#47;Email:	heqichen(a)gaishi.vicp.net<br />
&#47;&#47;Website:	http:&#47;&#47;gaishi.vicp.net<br />
&#47;&#47;Date:	2011-5-1</p>
<p>int status;</p>
<p>#define LEFT_SPEED   6<br />
#define LEFT_FORWARD  7<br />
#define LEFT_BACKWARD  8</p>
<p>#define RIGHT_SPEED  10<br />
#define RIGHT_FORWARD  11<br />
#define RIGHT_BACKWARD  12</p>
<p>#define ULTRASONIC_ECHO  3<br />
#define ULTRASONIC_TRIG  4</p>
<p>#define NORMAL_SPEED  100<br />
#define STOP_SPEED  0</p>
<p>void setup()<br />
{<br />
  Serial.begin(9600);<br />
  setupMove();<br />
  setupUltrasonic();<br />
}</p>
<p>void loop()<br />
{<br />
  unsigned int d;<br />
  moveForward();<br />
  d = readDistance();<br />
  Serial.println(d, DEC);<br />
  if (d < 700)<br />
  {<br />
    moveBackward();<br />
    delay(500);<br />
    turnLeft();<br />
    delay(200);<br />
  }<br />
}</p>
<p>void moveForward()<br />
{<br />
  analogWrite(LEFT_SPEED, NORMAL_SPEED);<br />
  digitalWrite(LEFT_BACKWARD, LOW);<br />
  digitalWrite(LEFT_FORWARD, HIGH);<br />
  analogWrite(RIGHT_SPEED, NORMAL_SPEED);<br />
  digitalWrite(RIGHT_BACKWARD, LOW);<br />
  digitalWrite(RIGHT_FORWARD, HIGH);<br />
}</p>
<p>void moveBackward()<br />
{<br />
  analogWrite(LEFT_SPEED, NORMAL_SPEED);<br />
  digitalWrite(LEFT_BACKWARD, HIGH);<br />
  digitalWrite(LEFT_FORWARD, LOW);<br />
  analogWrite(RIGHT_SPEED, NORMAL_SPEED);<br />
  digitalWrite(RIGHT_BACKWARD, HIGH);<br />
  digitalWrite(RIGHT_FORWARD, LOW);<br />
}</p>
<p>void turnLeft()<br />
{<br />
  analogWrite(LEFT_SPEED, NORMAL_SPEED);<br />
  digitalWrite(LEFT_BACKWARD, HIGH);<br />
  digitalWrite(LEFT_FORWARD, LOW);<br />
  analogWrite(RIGHT_SPEED, NORMAL_SPEED);<br />
  digitalWrite(RIGHT_BACKWARD, LOW);<br />
  digitalWrite(RIGHT_FORWARD, HIGH);<br />
}</p>
<p>void turnRight()<br />
{<br />
  analogWrite(LEFT_SPEED, NORMAL_SPEED);<br />
  digitalWrite(LEFT_BACKWARD, LOW);<br />
  digitalWrite(LEFT_FORWARD, HIGH);<br />
  analogWrite(RIGHT_SPEED, NORMAL_SPEED);<br />
  digitalWrite(RIGHT_BACKWARD, HIGH);<br />
  digitalWrite(RIGHT_FORWARD, LOW);<br />
}</p>
<p>void moveStop()<br />
{<br />
  analogWrite(LEFT_SPEED, STOP_SPEED);<br />
  digitalWrite(LEFT_BACKWARD, LOW);<br />
  digitalWrite(LEFT_FORWARD, LOW);<br />
  analogWrite(RIGHT_SPEED, STOP_SPEED);<br />
  digitalWrite(RIGHT_BACKWARD, LOW);<br />
  digitalWrite(RIGHT_FORWARD, LOW);<br />
}</p>
<p>void setupMove()<br />
{<br />
  pinMode(LEFT_SPEED, OUTPUT);<br />
  pinMode(LEFT_FORWARD, OUTPUT);<br />
  pinMode(LEFT_BACKWARD, OUTPUT);<br />
  pinMode(RIGHT_SPEED, OUTPUT);<br />
  pinMode(RIGHT_FORWARD, OUTPUT);<br />
  pinMode(RIGHT_BACKWARD, OUTPUT);</p>
<p>  analogWrite(LEFT_SPEED, STOP_SPEED);<br />
  digitalWrite(LEFT_FORWARD, LOW);<br />
  digitalWrite(LEFT_BACKWARD, LOW);<br />
  analogWrite(RIGHT_SPEED, STOP_SPEED);<br />
  digitalWrite(RIGHT_FORWARD, LOW);<br />
  digitalWrite(RIGHT_BACKWARD, LOW);<br />
}</p>
<p>unsigned int readDistance()<br />
{</p>
<p>  int duration;<br />
  digitalWrite(ULTRASONIC_TRIG, LOW);<br />
  delayMicroseconds(2);<br />
  digitalWrite(ULTRASONIC_TRIG, HIGH);<br />
  delayMicroseconds(5);<br />
  digitalWrite(ULTRASONIC_TRIG, LOW);</p>
<p>  &#47;&#47; The same pin is used to read the signal from the PING))): a HIGH<br />
  &#47;&#47; pulse whose duration is the time (in microseconds) from the sending<br />
  &#47;&#47; of the ping to the reception of its echo off of an object.<br />
  duration = pulseIn(ULTRASONIC_ECHO, HIGH);<br />
  return duration;</p>
<p>}</p>
<p>void  setupUltrasonic()<br />
{<br />
  pinMode(ULTRASONIC_TRIG, OUTPUT);<br />
  pinMode(ULTRASONIC_ECHO, INPUT);</p>
<p>  digitalWrite(ULTRASONIC_TRIG, LOW);<br />
}<br />
<&#47;pre></p>
