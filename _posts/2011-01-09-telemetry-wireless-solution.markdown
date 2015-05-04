---
layout: post
status: publish
published: true
title: ART Telemetry wireless solution
author:
  display_name: rngadam
  login: rngadam
  email: rngadam@gmail.com
  url: ''
author_login: rngadam
author_email: rngadam@gmail.com
wordpress_id: 339
wordpress_url: http://xinchejian.com/?p=339
date: '2011-01-09 01:56:13 +0800'
date_gmt: '2011-01-08 17:56:13 +0800'
categories:
- robot
- arduino
tags:
- robot
- arduino
- A.R.T.
comments:
- id: 56
  author: Sam
  author_email: sam.zamen@gmail.com
  author_url: ''
  date: '2011-01-24 05:54:22 +0800'
  date_gmt: '2011-01-23 21:54:22 +0800'
  content: "I've used the databridge modules from starman electric (www.starmanelectric.com),
    and they are very easy to setup for this type of application. They wern't the
    cheapest, but they worked great and I got them up and running within a few minutes
    vs a few hours of frustration with other modules. I'm located in Germany, and
    my order was shipped from the US with no problem. I'm sure they will ship to China
    too.\r\n\r\nSam"
- id: 57
  author: david
  author_email: david@xinchejian.com
  author_url: ''
  date: '2011-01-24 08:47:32 +0800'
  date_gmt: '2011-01-24 00:47:32 +0800'
  content: Sam, thanks for the info.
---
<div id="_mcePaste">Been researching wireless solutions to transmit in real-time sensor and decision information from ART in addition to possibly enabling minimal controls (on/off/behavior switch) and perhaps even wireless firmware updates.</div></p>
<div id="_mcePaste"></div></p>
<div>My criteria:</div></p>
<div>
<ul>
<li>Low-cost (<200RMB, preferably <100RMB)</li>
<li>Simplex or half-duplex OK</li>
<li>Low-bandwidth (>1,200 bit/s)</li>
<li>Low-power (<100 mAh)</li>
<li>Medium-range (500m-1000m)</li>
<li>TTL or SPI interface</li><br />
</ul><br />
</div></p>
<div id="_mcePaste">One of the main issue is that I cannot find a clear reference to the spectrum allocation in China (The US has a very convenient Frequency Allocations Chart: <a href="http://en.wikipedia.org/wiki/Frequency_allocation">http://en.wikipedia.org/wiki/Frequency_allocation</a>).</div></p>
<div></div></p>
<div id="_mcePaste">I know that 2.4Ghz is good worldwide (such as what the Nordic nRF240L uses) but that has a very limited range (50m-100m). So is Bluetooth and to a certain degree Wifi (and they are pretty expensive too).</div></p>
<div></div></p>
<div>There are these:</div></p>
<div>
<ul>
<li>PTR8000+ [Nordic nRF905 (433/868/915MHz)]
<ul>
<li><a href="http://www.nordicsemi.com/index.cfm?obj=product&amp;act=display&amp;pro=83">http://www.nordicsemi.com/index.cfm?obj=product&amp;act=display&amp;pro=83</a></li>
<li><a href="http://item.taobao.com/item.htm?id=6062297954 ">http://item.taobao.com/item.htm?id=6062297954 </a>(50RMB!)</li>
<li><a href="http://www.techtoys.com.hk/RF_Modules/Nordic_905/nRF905_rev1_4.pdf">http://www.techtoys.com.hk/RF_Modules/Nordic_905/nRF905_rev1_4.pdf</a></li>
<li>tops out at 500m LOS</li><br />
</ul><br />
</li></p>
<li>Laipac Tech RF 900DV(900 mhz)
<ul>
<li><a href="http://www.laipac.com/easy_900dv_eng.htm">http://www.laipac.com/easy_900dv_eng.htm</a></li><br />
</ul><br />
</li></p>
<li>Laipac ASK Transmitters (315 mhz)
<ul>
<li><a href="http://www.laipac.com/easy_900dv_eng.htm">http://www.laipac.com/easy_315a_eng.htm</a></li><br />
</ul><br />
</li></p>
<li>Databridge
<ul>
<li><a href="http://www.starmanelectric.com/OrderDataBridge/tabid/71/Default.aspx">http://www.starmanelectric.com/OrderDataBridge/tabid/71/Default.aspx</a></li>
<li>http://www.starmanelectric.com/LinkClick.aspx?fileticket=REf/38lk/L4%3d&amp;tabid=75&amp;mid=456</li>
<li>Expensive (87$USD) and not available here?</li><br />
</ul><br />
</li></p>
<li>JZ871 Data RF transceiver for wireless telemetry system (433 MHz or 868Mhz/915Mhz)
<ul>
<li><a href="http://www.laipac.com/easy_900dv_eng.htm">http://www.alibaba.com/product-gs/252550553/RF_data_transceiver.html</a></li>
<li><a href="http://www.jizhuo.com/download/product_images/f/cn_f__101.pdf">http://www.jizhuo.com/download/product_images/f/cn_f__101.pdf</a></li>
<li>I'm guessing if Alibaba is selling it, it's ok in China? Or is it exactly just an export product?</li><br />
</ul><br />
</li><br />
</ul><br />
</div></p>
<div id="_mcePaste">Last one actually looks better than the Nordic on paper, but from what I gathered the price is pretty high. &nbsp;I wonder about the price and why I can't find it on Taobao...</div></p>
