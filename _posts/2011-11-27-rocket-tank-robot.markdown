---
layout: post
status: publish
published: true
title: Source to Rocket's tank robot | rockets的坦克机器人的程序及策略
author:
  display_name: rockets
  login: rockets
  email: rockets.cn@gmail.com
  url: ''
author_login: rockets
author_email: rockets.cn@gmail.com
wordpress_id: 1932
wordpress_url: http://xinchejian.com/?p=1932
date: '2011-11-27 23:33:20 +0800'
date_gmt: '2011-11-27 15:33:20 +0800'
categories:
- Uncategorized
tags:
- arduino 机器人比赛 策略
comments: []
---
<p>我使用的是RP5 Tracked Mobile Tank Bas及arduinoDFRduino Duemilanove 328 (Arduino Compatible)Motor Shield For Arduino<br />
使用的传感器是Adjustable Infrared Sensor Switch总共使用了三个。</p>
<p>我的传感器布置在坦克中部前方、右前方及右中部。主要策略是贴边走。<br />
程序中的命名因为事前编程以为比赛方向为顺时针，而比赛时则为逆时针，因此没有来得及改名字而已。<br />
以下为程序。</p>
<p>int E1 = 5;<br />
int M1 = 4;<br />
int E2 = 6;<br />
int M2 = 7;//着部分是motor shield的定义<br />
int front=8;<br />
int leftfront=9;<br />
int leftback=10;//传感器定义</p>
<p>void setup()<br />
{<br />
    pinMode(M1, OUTPUT);<br />
    pinMode(M2, OUTPUT);<br />
    pinMode(front,INPUT);<br />
    pinMode(leftfront,INPUT);<br />
    pinMode(leftback,INPUT);<br />
 }<br />
 void foward()//前进函数定义<br />
 {<br />
    digitalWrite(M1,HIGH);<br />
    digitalWrite(M2, HIGH);<br />
    analogWrite(E1, 255);   //PWM调速<br />
    analogWrite(E2, 255);   //PWM调速<br />
     }<br />
     void back()//后退函数定义<br />
     {<br />
    digitalWrite(M1,LOW);<br />
    digitalWrite(M2, LOW);<br />
    analogWrite(E1, 255);   //PWM调速<br />
    analogWrite(E2, 255);   //PWM调速<br />
  }<br />
  void rightgo()//右转函数定义<br />
  {<br />
    digitalWrite(M1,HIGH);<br />
    digitalWrite(M2, LOW);<br />
    analogWrite(E1, 255);   //PWM调速<br />
    analogWrite(E2, 255);   //PWM调速<br />
  }<br />
  void leftgo()//左转函数定义<br />
  {<br />
    digitalWrite(M1,LOW);<br />
    digitalWrite(M2, HIGH);<br />
    analogWrite(E1, 255);   //PWM调速<br />
    analogWrite(E2, 255);   //PWM调速<br />
  }</p>
<p>void loop()<br />
{<br />
if (digitalRead(9)==1)//策略为如果右中部如果一直保持触发即贴住墙就好了，如果没有就向右转，直到接触到墙壁。<br />
{<br />
  rightgo();<br />
delay(600);<br />
}<br />
  if (digitalRead(8)==1&amp;&digitalRead(10)==1)<br />
{  foward();<br />
delay(500);<br />
}<br />
 else if(digitalRead(8)==0&amp;&digitalRead(10)==1)<br />
{leftgo();<br />
delay(500);}</p>
<p>else if (digitalRead(10)==0&amp;&digitalRead(10)==1)<br />
{<br />
rightgo();<br />
delay(100);<br />
}</p>
<p>else leftgo();</p>
<p>}</p>
<p>程序以上<br />
请各位指正批评。<br />
另外附上我使用设备的购买地址<br />
http://www.dfrobot.com/index.php?route=product/product&path=36&product_id=114<br />
http://www.dfrobot.com/index.php?route=product/product&product_id=69<br />
http://www.dfrobot.com/index.php?route=product/product&filter_tag=Arduino&product_id=49<br />
http://www.dfrobot.com/index.php?route=product/product&path=35&product_id=96<br />
http://www.dfrobot.com/index.php?route=product/product&path=35_39&product_id=264</p>
