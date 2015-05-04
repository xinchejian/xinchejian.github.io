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
<div id="_mcePaste">Been researching wireless solutions to transmit in real-time sensor and decision information from ART in addition to possibly enabling minimal controls (on&#47;off&#47;behavior switch) and perhaps even wireless firmware updates.<&#47;div></p>
<div id="_mcePaste"><&#47;div></p>
<div>My criteria:<&#47;div></p>
<div>
<ul>
<li>Low-cost (<200RMB, preferably <100RMB)<&#47;li>
<li>Simplex or half-duplex OK<&#47;li>
<li>Low-bandwidth (>1,200 bit&#47;s)<&#47;li>
<li>Low-power (<100 mAh)<&#47;li>
<li>Medium-range (500m-1000m)<&#47;li>
<li>TTL or SPI interface<&#47;li><br />
<&#47;ul><br />
<&#47;div></p>
<div id="_mcePaste">One of the main issue is that I cannot find a clear reference to the spectrum allocation in China (The US has a very convenient Frequency Allocations Chart: <a href="http:&#47;&#47;en.wikipedia.org&#47;wiki&#47;Frequency_allocation">http:&#47;&#47;en.wikipedia.org&#47;wiki&#47;Frequency_allocation<&#47;a>).<&#47;div></p>
<div><&#47;div></p>
<div id="_mcePaste">I know that 2.4Ghz is good worldwide (such as what the Nordic nRF240L uses) but that has a very limited range (50m-100m). So is Bluetooth and to a certain degree Wifi (and they are pretty expensive too).<&#47;div></p>
<div><&#47;div></p>
<div>There are these:<&#47;div></p>
<div>
<ul>
<li>PTR8000+ [Nordic nRF905 (433&#47;868&#47;915MHz)]
<ul>
<li><a href="http:&#47;&#47;www.nordicsemi.com&#47;index.cfm?obj=product&amp;act=display&amp;pro=83">http:&#47;&#47;www.nordicsemi.com&#47;index.cfm?obj=product&amp;act=display&amp;pro=83<&#47;a><&#47;li>
<li><a href="http:&#47;&#47;item.taobao.com&#47;item.htm?id=6062297954 ">http:&#47;&#47;item.taobao.com&#47;item.htm?id=6062297954 <&#47;a>(50RMB!)<&#47;li>
<li><a href="http:&#47;&#47;www.techtoys.com.hk&#47;RF_Modules&#47;Nordic_905&#47;nRF905_rev1_4.pdf">http:&#47;&#47;www.techtoys.com.hk&#47;RF_Modules&#47;Nordic_905&#47;nRF905_rev1_4.pdf<&#47;a><&#47;li>
<li>tops out at 500m LOS<&#47;li><br />
<&#47;ul><br />
<&#47;li></p>
<li>Laipac Tech RF 900DV(900 mhz)
<ul>
<li><a href="http:&#47;&#47;www.laipac.com&#47;easy_900dv_eng.htm">http:&#47;&#47;www.laipac.com&#47;easy_900dv_eng.htm<&#47;a><&#47;li><br />
<&#47;ul><br />
<&#47;li></p>
<li>Laipac ASK Transmitters (315 mhz)
<ul>
<li><a href="http:&#47;&#47;www.laipac.com&#47;easy_900dv_eng.htm">http:&#47;&#47;www.laipac.com&#47;easy_315a_eng.htm<&#47;a><&#47;li><br />
<&#47;ul><br />
<&#47;li></p>
<li>Databridge
<ul>
<li><a href="http:&#47;&#47;www.starmanelectric.com&#47;OrderDataBridge&#47;tabid&#47;71&#47;Default.aspx">http:&#47;&#47;www.starmanelectric.com&#47;OrderDataBridge&#47;tabid&#47;71&#47;Default.aspx<&#47;a><&#47;li>
<li>http:&#47;&#47;www.starmanelectric.com&#47;LinkClick.aspx?fileticket=REf&#47;38lk&#47;L4%3d&amp;tabid=75&amp;mid=456<&#47;li>
<li>Expensive (87$USD) and not available here?<&#47;li><br />
<&#47;ul><br />
<&#47;li></p>
<li>JZ871 Data RF transceiver for wireless telemetry system (433 MHz or 868Mhz&#47;915Mhz)
<ul>
<li><a href="http:&#47;&#47;www.laipac.com&#47;easy_900dv_eng.htm">http:&#47;&#47;www.alibaba.com&#47;product-gs&#47;252550553&#47;RF_data_transceiver.html<&#47;a><&#47;li>
<li><a href="http:&#47;&#47;www.jizhuo.com&#47;download&#47;product_images&#47;f&#47;cn_f__101.pdf">http:&#47;&#47;www.jizhuo.com&#47;download&#47;product_images&#47;f&#47;cn_f__101.pdf<&#47;a><&#47;li>
<li>I'm guessing if Alibaba is selling it, it's ok in China? Or is it exactly just an export product?<&#47;li><br />
<&#47;ul><br />
<&#47;li><br />
<&#47;ul><br />
<&#47;div></p>
<div id="_mcePaste">Last one actually looks better than the Nordic on paper, but from what I gathered the price is pretty high. &nbsp;I wonder about the price and why I can't find it on Taobao...<&#47;div></p>
