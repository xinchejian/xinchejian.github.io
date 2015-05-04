---
layout: post
status: publish
published: true
title: Hacking YN460 flash with Arduino
author:
  display_name: David Li
  login: david
  email: david@xinchejian.com
  url: ''
author_login: david
author_email: david@xinchejian.com
wordpress_id: 2358
wordpress_url: http://xinchejian.com/?p=2358
date: '2012-01-26 15:55:59 +0800'
date_gmt: '2012-01-26 07:55:59 +0800'
categories:
- shanzhai
- arduino
- china
tags:
- strobist
- photography
- arudino
- yn460
comments:
- id: 1870
  author: Hacking
  author_email: GladsteinTholen41@hotmail.com
  author_url: http://www.evilhax.us
  date: '2012-01-30 15:33:39 +0800'
  date_gmt: '2012-01-30 07:33:39 +0800'
  content: Thank you for the good writeup. It in fact used to be a entertainment account
    it. Look complex to far added agreeable from you! By the way, how could we keep
    up a correspondence?
- id: 2988
  author: net0040
  author_email: net0040@gmail.com
  author_url: ''
  date: '2012-04-20 17:50:24 +0800'
  date_gmt: '2012-04-20 09:50:24 +0800'
  content: "感谢您的工作,关于Hacking YN460 flash with Arduino项目 ，确切的问题：\r\n1、驱动YN460时，使用何种形式的引闪器，因为460本身不带PC接口，需要带PC接口的热靴驱动吧？比如海鸥的SC-2？\r\n2、
    \ 从arduino输出的信号，经过光隔，是否可以直接驱动引闪器，我看过一些资料，应该不可以。\r\n  闪光灯在它的PC同步&#47;热靴接口会有非常高的电压，请问在光藕之后，是否您还采用了某种更强的输出隔离（比如直流控制直流的固态继电器）？\r\n我手头的设备无法测算这个电压。所以希望得到您的帮助。\r\n
    \r\n第一个问题有些冒昧，且不够清晰，所以才再次打扰，如果可能，能否给我看看您的连接简图以及采用的元器件型号。我真的希望学习这个项目。\r\n关于延时我想可以在arduino中调整。所以最想了解的还是从arduino输出到驱动YN460这部分的细节。\r\n
    \r\n再次感谢。"
- id: 4731
  author: Marcus Wolschon
  author_email: Marcus@Wolschon.biz
  author_url: ''
  date: '2012-07-11 19:39:48 +0800'
  date_gmt: '2012-07-11 11:39:48 +0800'
  content: "How did you control the YN460 ?\r\nDo you think this can be done using
    a smaller Atmel-board to integrate it into the housing?\r\nI'm working on a 3D
    printed alternative housing to include an RF flash trigger, power jack and an
    integrated umbrella-holder."
---
<p><!--:en-->YN460 is a nice Chinese made flash for photography. The first hack is to enable controlling the power and flash trigger with Arduino. In the following video, the Arduino runs a 3 second step that trigger at its 7 power level.</p>
<p>Next step, adding network capacity to the flash and control it from iPhone!</p>
<p><object width="400" height="225" classid="clsid:d27cdb6e-ae6d-11cf-96b8-444553540000" codebase="http:&#47;&#47;download.macromedia.com&#47;pub&#47;shockwave&#47;cabs&#47;flash&#47;swflash.cab#version=6,0,40,0"><param name="flashvars" value="intl_lang=en-us&amp;photo_secret=c6aa8c81af&amp;photo_id=6755282987" &#47;><param name="allowFullScreen" value="true" &#47;><param name="src" value="http:&#47;&#47;www.flickr.com&#47;apps&#47;video&#47;stewart.swf?v=109786" &#47;><param name="allowfullscreen" value="true" &#47;><embed width="400" height="225" type="application&#47;x-shockwave-flash" src="http:&#47;&#47;www.flickr.com&#47;apps&#47;video&#47;stewart.swf?v=109786" flashvars="intl_lang=en-us&amp;photo_secret=c6aa8c81af&amp;photo_id=6755282987" allowFullScreen="true" allowfullscreen="true" &#47;><&#47;object><!--:--><!--:zh-->永诺YN460是一个由国产的优秀的闪光灯。</p>
<p>第一步我们将其改造成能用arduino控制电源和闪光触发，在下面的视频里，arduino控制闪光灯以7档的输出并按3秒一个间隔的方式进行触发。</p>
<p>下一步，我们将加入网络控制并希望能用iphone来控制！</p>
<p><object width="400" height="225" classid="clsid:d27cdb6e-ae6d-11cf-96b8-444553540000" codebase="http:&#47;&#47;download.macromedia.com&#47;pub&#47;shockwave&#47;cabs&#47;flash&#47;swflash.cab#version=6,0,40,0"><param name="flashvars" value="intl_lang=en-us&amp;photo_secret=c6aa8c81af&amp;photo_id=6755282987" &#47;><param name="allowFullScreen" value="true" &#47;><param name="src" value="http:&#47;&#47;www.flickr.com&#47;apps&#47;video&#47;stewart.swf?v=109786" &#47;><param name="allowfullscreen" value="true" &#47;><embed width="400" height="225" type="application&#47;x-shockwave-flash" src="http:&#47;&#47;www.flickr.com&#47;apps&#47;video&#47;stewart.swf?v=109786" flashvars="intl_lang=en-us&amp;photo_secret=c6aa8c81af&amp;photo_id=6755282987" allowFullScreen="true" allowfullscreen="true" &#47;><&#47;object><!--:--></p>
