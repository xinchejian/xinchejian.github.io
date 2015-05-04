---
layout: post
status: publish
published: true
title: <!--:en-->Adding servo to RC car<!--:--><!--:zh-->遥控小车的改造<!--:-->
author:
  display_name: heqichen
  login: heqichen
  email: heqichen@yahoo.com.cn
  url: ''
author_login: heqichen
author_email: heqichen@yahoo.com.cn
wordpress_id: 999
wordpress_url: http://xinchejian.com/?p=999
date: '2011-05-06 03:56:41 +0800'
date_gmt: '2011-05-05 19:56:41 +0800'
categories:
- robot
- arduino
tags:
- robot
- arduino
comments: []
---
<h1>遥控小车的改造</h1><br />
<i>May 3rd, 2011</i></p>
<p>今天完成了遥控车的改造，这是自主控制的第一步。这辆车是在淘宝上买的，结构很简单，控制很简陋。方向就是将电机打死，这时候电流会非常大，而且对于将来的自主移动的精细控制带来不利因素。所以很早就想把它改成舵机控制的了，下面就是整个改造的过程。</p></p>
<p>这就是需要改造的部分。</p></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http://xinchejian.com/wp-content/uploads/2011/05/NewImage.png" alt="NewImage" title="NewImage.png" border="0" width="400" height="300" /></p>
<p>先将需要改造的部分画下来，便于设计框架结构。我不是机械出身的，所以就画个大概吧。</p></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http://xinchejian.com/wp-content/uploads/2011/05/NewImage1.png" alt="NewImage" title="NewImage.png" border="0" width="400" height="300" /></p>
<p>结构图完成</p></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http://xinchejian.com/wp-content/uploads/2011/05/NewImage2.png" alt="NewImage" title="NewImage.png" border="0" width="400" height="300" /></p>
<p>在图纸上设计新的结构</p></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http://xinchejian.com/wp-content/uploads/2011/05/NewImage3.png" alt="NewImage" title="NewImage.png" border="0" width="400" height="300" /></p>
<p>根据设计切割材料</p></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http://xinchejian.com/wp-content/uploads/2011/05/NewImage4.png" alt="NewImage" title="NewImage.png" border="0" width="400" height="300" /></p>
<p>最后完成的样子，由于是临时电路，也就没固定，看上去有点像垃圾车-_-b</p></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http://xinchejian.com/wp-content/uploads/2011/05/NewImage5.png" alt="NewImage" title="NewImage.png" border="0" width="400" height="300" /></p>
<p>改造部分的特写</p></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http://xinchejian.com/wp-content/uploads/2011/05/NewImage6.png" alt="NewImage" title="NewImage.png" border="0" width="400" height="300" /></p>
<p>再来一张</p></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http://xinchejian.com/wp-content/uploads/2011/05/NewImage7.png" alt="NewImage" title="NewImage.png" border="0" width="400" height="300" /></p>
<p>这些只是机械部份，然后就是控制部份。由于舵机能够转动的角度范围到180度，而该车的转向轮仅能转动在30-40度之间。同时，自主移动机器人目标是在Arduino上面开发。所以我就一步到位，先用Arduino读取天地飞的pwm信号，然后经过转换，输出新的pwm信号给舵机，这样就不会因为卡住而损坏舵机了。</p></p>
<p>最后效果如下</p></p>
<p class="video">
<embed src="http://player.youku.com/player.php/sid/XMjYzOTc2NzA4/v.swf" quality="high" width="480" height="400" align="middle" allowScriptAccess="sameDomain" type="application/x-shockwave-flash"></embed><br />
<a href="http://v.youku.com/v_show/id_XMjYzOTc2NzA4.html">http://v.youku.com/v_show/id_XMjYzOTc2NzA4.html</a><br />
</p></p>
<p>使用的程序非常简单，如下：</p></p>
<pre class="code">
<p>#include <Servo.h></p>
<p>//Author:	HE Qichen<br />
//Date:	2011-5-3<br />
//Website:	http://gaishi.vicp.net<br />
//Email:	heqichen(a)gaishi.vicp.net</p>
<p>Servo directionServo;</p>
<p>void setup()<br />
{<br />
  pinMode(2, INPUT);<br />
  directionServo.attach(3);</p>
<p>}</p>
<p>void loop()<br />
{<br />
  int t, a;<br />
  t = pulseIn(2, HIGH);<br />
  a = map(t, 1000, 2000, 65, 115);<br />
  directionServo.write(a);</p>
<p>}<br />
</pre></p>
