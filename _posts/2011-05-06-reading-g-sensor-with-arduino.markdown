---
layout: post
status: publish
published: true
title: Reading g-sensor with Arduino | Arduino读取g-sensor数据
author:
  display_name: heqichen
  login: heqichen
  email: heqichen@yahoo.com.cn
  url: ''
author_login: heqichen
author_email: heqichen@yahoo.com.cn
wordpress_id: 985
wordpress_url: http://xinchejian.com/?p=985
date: '2011-05-06 03:48:47 +0800'
date_gmt: '2011-05-05 19:48:47 +0800'
categories:
- quadcopter
- robot
- arduino
tags:
- arduino
- g-sensor
comments:
- id: 205
  author: Aaron
  author_email: zhangyuhust@gmail.com
  author_url: http://www.drxlab.net
  date: '2011-05-06 10:30:27 +0800'
  date_gmt: '2011-05-06 02:30:27 +0800'
  content: G-sensor是四轴飞行器项目对这个传感器的代号，正确的译名是<b>加速度传感器</b>。另外，FreeScale的加速度传感器虽然便宜，但是质量和精度真的不太好，还不如国产的MEMSIC。
---
<h1>Arduino读取g-sensor数据</h1><br />
<i>May 2nd, 2011</i></p>
<p>在四轴飞行器上除了要有陀螺仪外，还要有个重要的传感器就是重力传感器。由于它们各自的误差，若使用单一的传感器会造成严重的精读问题，使飞行器丧失稳定性。所以要用两个传感器进行相互矫正。</p></p>
<p>现在重力传感器应用非常广，目前iphone等智能手机上都有重力传感器，包括笔者的一台山寨手机上都有重力传感器。</p></p>
<p>这次就是要用Android来读取重力传感器的数据。这个重力传感器模块是从淘宝购买的，模块非常简单，自己够买芯片来焊接也不成问题。根据它的datasheet，就能够知道如何使用这款重力加速度模块了。下面就进行详细的介绍</p></p>
<p>这个模块使用的芯片型号是MMA7260Q，(datasheet<a href="promotion/download/25270_MOTOROLA_MMA7260Q.pdf">下载</a>[PDF,229KB])，测试中的电路就是下面图片中的样子</p></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="/uploads/2011/05/untitled8.jpg" alt="Untitled" title="untitled.jpg" border="0"/></p>
<p>控制的目标是通过重力传感器的数据来控制舵机的转动。但是发现会有少量的抖动，于是在程序中加入了一个简单的滤波器，阶数没有仔细调，但是基本上能够进行控制了。</p></p>
<p class="video">
<embed src="http://player.youku.com/player.php/sid/XMjYzNjIyODIw/v.swf" quality="high" width="480" height="400" align="middle" allowScriptAccess="sameDomain" type="application/x-shockwave-flash"></embed><br />
<a href="http://v.youku.com/v_show/id_XMjYzNjIyODIw.html">http://v.youku.com/v_show/id_XMjYzNjIyODIw.html</a><br />
</p></p>
<p>下面是芯片的特写</p></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="/uploads/2011/05/untitled9.jpg" alt="Untitled" title="untitled.jpg" border="0"/><br />
<img style="display:block; margin-left:auto; margin-right:auto;" src="/uploads/2011/05/untitled10.jpg" alt="Untitled" title="untitled.jpg" border="0"/></p>
<p>下面是用到的代码</p></p>
<pre class="code">
#include <Servo.h></p>
<p>//Author:  HE Qichen<br />
//Email:  heqichen(a)gaishi.vicp.net<br />
//Website:  http://gaishi.vicp.net<br />
//Date:  2011-5-2</p>
<p>#define FILTER_LEVEL  3</p>
<p>class Filter<br />
{<br />
  private:<br />
    int buffer[FILTER_LEVEL];<br />
  public:<br />
    Filter()<br />
    {<br />
      int i;<br />
      for (i=0; i<FILTER_LEVEL; ++i)<br />
      {<br />
        buffer[i] = 0;<br />
      }<br />
    }<br />
    int filter(int value)<br />
    {<br />
      int i;<br />
      int sum;<br />
      for (i=0; i<FILTER_LEVEL-1; ++i)<br />
      {<br />
        buffer[i] = buffer[i+1];<br />
      }<br />
      buffer[FILTER_LEVEL-1] = value;<br />
      sum = 0;<br />
      for (i=0; i<FILTER_LEVEL; ++i)<br />
      {<br />
        sum += buffer[i];<br />
      }<br />
      return sum / FILTER_LEVEL;<br />
    }<br />
};</p>
<p>Servo testServo;<br />
Filter xFilter, yFilter, zFilter;</p>
<p>void setup()<br />
{<br />
  Serial.begin(9600);<br />
  testServo.attach(2);<br />
}</p>
<p>void loop()<br />
{<br />
  int gx, gy, gz;<br />
  gx = analogRead(A0);<br />
  gy = analogRead(A1);<br />
  gz = analogRead(A2);</p>
<p>  Serial.print("x: ");<br />
  Serial.print(gx, DEC);<br />
  Serial.print("  y: ");<br />
  Serial.print(gy, DEC);<br />
  Serial.print("  z: ");<br />
  Serial.println(gz, DEC);</p>
<p>  int fgx, fgy, fgz;<br />
  fgx = xFilter.filter(gx);<br />
  fgy = yFilter.filter(gy);<br />
  fgz = zFilter.filter(gz);<br />
  Serial.print("  fx: ");<br />
  Serial.print(fgx, DEC);<br />
  Serial.print("  fy: ");<br />
  Serial.print(fgy, DEC);<br />
  Serial.print("  fz: ");<br />
  Serial.println(fgz, DEC);</p>
<p>  testServo.write((fgz-100)/3);<br />
  //delay(10);</p>
<p>}</p>
<p></pre></p>
