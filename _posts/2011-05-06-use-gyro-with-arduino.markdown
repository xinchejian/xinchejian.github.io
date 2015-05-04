---
layout: post
status: publish
published: true
title: Use Gyro with Arduino | 在Arduino上使用陀螺仪控制舵机
author:
  display_name: heqichen
  login: heqichen
  email: heqichen@yahoo.com.cn
  url: ''
author_login: heqichen
author_email: heqichen@yahoo.com.cn
wordpress_id: 974
wordpress_url: http://xinchejian.com/?p=974
date: '2011-05-06 03:35:47 +0800'
date_gmt: '2011-05-05 19:35:47 +0800'
categories:
- quadcopter
- arduino
tags: []
comments: []
---
<h1>在Arduino上使用陀螺仪控制舵机</h1><br />
<i>May 1st, 2011</i></p>
<p>今天拿到了四轴飞行器的一个重要部件，就是陀螺仪。^_^ 下面这张图上的就是了，这是一个三轴陀螺仪，seeedstudio GROVE套装的一个部件。</p></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http://xinchejian.com/wp-content/uploads/2011/05/untitled1.jpg" alt="Untitled" title="untitled.jpg" border="0"/></p>
<p>这个陀螺仪使用ITG3200芯片，可以直接使用了I2C接口连接到Arduino上面。默认的地址是0x68，但是可以修改成0x69，只要将板子上的JP1连起来就可以修改。接口四个针脚的定义就像下面这张图中所画的。</p></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http://xinchejian.com/wp-content/uploads/2011/05/untitled2.jpg" alt="Untitled" title="untitled.jpg" border="0"/></p>
<p>是的。。你没看错，他们用红色作为地线  -_-b</p></p>
<p>舵机就是最简单的使用pwm的口就可以了。最后链接成下面这张图中的样子。</p></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http://xinchejian.com/wp-content/uploads/2011/05/untitled3.jpg" alt="Untitled" title="untitled.jpg" border="0"/></p>
<p>我写了一个程序，代码在下方，能够做到让陀螺仪的转动直接反应在舵机的摇臂上面。但是，这样也会遇到问题，就是当动的次数比较多的时候，舵机的角度就会越来越大，直到超过最大的范围，所以这也是陀螺仪不是很精确的地方。另外就是，在陀螺仪静止的情况下，z轴的输出不为0，始终为-1。也就是说，这个陀螺仪的零点可能是不准确的，同时，正负转动的也有可能有差别，不知道这回对将来飞控算法带来多大的影响。</p></p>
<p>最后用到的程序就是下面这段。</p></p>
<pre class="code">
#include <Wire.h><br />
#include <Servo.h></p>
<p>#define GYRO_ADDR  0x68</p>
<p>Servo servo;</p>
<p>int currentPos;</p>
<p>void setup()<br />
{<br />
  Wire.begin();<br />
  initGyro();<br />
  servo.attach(2);<br />
  currentPos = 90;<br />
  //Serial.begin(9600);<br />
  pinMode(3, INPUT);<br />
}</p>
<p>void loop()<br />
{<br />
  int x;<br />
  int v;<br />
  x = readx();<br />
  v = ready();<br />
  v = readz();<br />
  currentPos = currentPos + x;</p>
<p>  int buttonState;<br />
  buttonState = digitalRead(3);<br />
  if (buttonState == HIGH)<br />
  {</p>
<p>    currentPos = 90;<br />
  }<br />
  else<br />
  {<br />
    //Serial.println("LOW");<br />
  }</p>
<p>  servo.write(currentPos);</p>
<p>}</p>
<p>int readx()<br />
{<br />
  int x;<br />
  x = readGyro(0x1d, 0x1e);<br />
  return x;<br />
}</p>
<p>int ready()<br />
{<br />
  int y;<br />
  y = readGyro(0x1f, 0x20);<br />
  return y;<br />
}</p>
<p>int readz()<br />
{<br />
  int z;<br />
  z = readGyro(0x21, 0x22);<br />
  return z;<br />
}</p>
<p>char readGyro(unsigned char addrH, unsigned char addrL)<br />
{<br />
  char ret;<br />
  Wire.beginTransmission(GYRO_ADDR);<br />
  Wire.send(addrH);<br />
  Wire.endTransmission();<br />
  Wire.requestFrom(GYRO_ADDR, 1);<br />
  if (Wire.available() > 0)<br />
  {<br />
    ret = Wire.receive();<br />
  }<br />
  Wire.beginTransmission(GYRO_ADDR);<br />
  Wire.send(addrL);<br />
  Wire.endTransmission();<br />
  Wire.requestFrom(GYRO_ADDR, 1);<br />
  if (Wire.available() > 0)<br />
  {<br />
    ret != Wire.receive()<<8;<br />
  }</p>
<p>  return ret;<br />
}</p>
<p>void initGyro()<br />
{<br />
  Wire.beginTransmission(GYRO_ADDR);<br />
  Wire.send(0x3E);<br />
  Wire.send(0x80);  //send a reset to the device<br />
  Wire.endTransmission(); //end transmission</p>
<p>  Wire.beginTransmission(GYRO_ADDR);<br />
  Wire.send(0x15);<br />
  Wire.send(0x00);   //sample rate divider<br />
  Wire.endTransmission(); //end transmission</p>
<p>  Wire.beginTransmission(GYRO_ADDR);<br />
  Wire.send(0x16);<br />
  Wire.send(0x18); // &plusmn;2000 degrees/s (default value)<br />
  Wire.endTransmission(); //end transmission<br />
}<br />
</pre></p>
<p>程序当中Wire库就是使用I2C，具体文档可以看下面的链接。</p><br />
<a href="http://arduino.cc/en/Reference/Wire">http://arduino.cc/en/Reference/Wire</a><br />
<embed src="http://player.youku.com/player.php/sid/XMjYzMTg2ODQ0/v.swf" quality="high" width="480" height="400" align="middle" allowScriptAccess="sameDomain" type="application/x-shockwave-flash"></embed><br />
<a href="http://v.youku.com/v_show/id_XMjYzMTg2ODQ0.html">http://v.youku.com/v_show/id_XMjYzMTg2ODQ0.html</a></p>
