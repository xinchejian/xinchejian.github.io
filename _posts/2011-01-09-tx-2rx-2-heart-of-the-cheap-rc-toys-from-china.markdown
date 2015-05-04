---
layout: post
status: publish
published: true
title: 'TX-2/RX-2: Heart of the cheap RC Toys from China'
author:
  display_name: David Li
  login: david
  email: david@xinchejian.com
  url: ''
author_login: david
author_email: david@xinchejian.com
wordpress_id: 350
wordpress_url: http://xinchejian.com/?p=350
date: '2011-01-09 19:13:31 +0800'
date_gmt: '2011-01-09 11:13:31 +0800'
categories:
- robot
- arduino
tags:
- robot
- arduino
comments:
- id: 60
  author: sajid zaman
  author_email: engr.sajidzaman@gmail.com
  author_url: ''
  date: '2011-01-25 02:37:01 +0800'
  date_gmt: '2011-01-24 18:37:01 +0800'
  content: "salam,\r\nthanks for this, the circuit yoou paste is not clearly seen
    so plz sir upload this circuit in pdf forment.thanks"
- id: 704
  author: Weihua Ju
  author_email: jackie.ju@gmail.com
  author_url: ''
  date: '2011-09-08 00:45:07 +0800'
  date_gmt: '2011-09-07 16:45:07 +0800'
  content: 'Sorry for the newbie question: What''s usage of H-Bridge ? Thanks.'
- id: 1034
  author: fuu
  author_email: ex5_dream1161@yahoo.com
  author_url: ''
  date: '2011-10-19 22:53:07 +0800'
  date_gmt: '2011-10-19 14:53:07 +0800'
  content: where you get this ic...? where can i buy?
- id: 1035
  author: David Li
  author_email: david@xinchejian.com
  author_url: ''
  date: '2011-10-20 00:02:50 +0800'
  date_gmt: '2011-10-19 16:02:50 +0800'
  content: you should be able to find them on Taobao. ;)
- id: 1043
  author: Alan
  author_email: al.ninjav@gmail.com
  author_url: ''
  date: '2011-10-24 05:58:01 +0800'
  date_gmt: '2011-10-23 21:58:01 +0800'
  content: "Hi. My son has a couple of cheap Chinese RC cars - all with 27Mhz RC transmitter/receivers.
    On of the cars I checked uses this RX-2 chip and I have a transmitter that uses
    a 27Mhz crystal. I want to try and replace the transmitter's crystal for a different
    frequency and match it up with the receiver circuit of the car so that we don't
    interfere with each other when racing together.\r\n\r\nIs it possible to adjust
    the receiver circuit by just adjusting the OSC resistor on the RX-2 chip to a
    different resistance value? Or do I have to adjust the components for the RF circuit
    as well?\r\n\r\nMany thanks. Your post was very helpful so far."
- id: 1807
  author: Alexandar
  author_email: podkonjak7@gmail.com
  author_url: http://xinchejian.com/2011/01/09/tx-2rx-2-heart-of-the-cheap-rc-toys-from-china/
  date: '2012-01-26 21:18:28 +0800'
  date_gmt: '2012-01-26 13:18:28 +0800'
  content: How to create joistyck for RX-2
- id: 2421
  author: Husham
  author_email: hushamsamir.nsn@gmail.com
  author_url: ''
  date: '2012-04-05 02:26:37 +0800'
  date_gmt: '2012-04-04 18:26:37 +0800'
  content: "datasheet for this ic availiable in below website\r\nhttp://www.datasheetarchive.com/\r\njust
    type RX2 in the search box"
- id: 11278
  author: reyes aryelle l.
  author_email: reyesaryelle@yahoo.com
  author_url: ''
  date: '2013-01-04 15:49:12 +0800'
  date_gmt: '2013-01-04 07:49:12 +0800'
  content: its the transistor switching  or biasing to be able to change motor  rotation.
    either forward or reverse
- id: 11279
  author: reyes aryelle l.
  author_email: reyesaryelle@yahoo.com
  author_url: ''
  date: '2013-01-04 15:52:08 +0800'
  date_gmt: '2013-01-04 07:52:08 +0800'
  content: yes.. resistor in oscillator is for setting up the frequency to be generated..
    u must adjust the rx too.
- id: 17021
  author: sampath
  author_email: sampath1.info@gmail.com
  author_url: ''
  date: '2013-04-26 08:04:40 +0800'
  date_gmt: '2013-04-26 00:04:40 +0800'
  content: can i get a RC transmeter in 5-10 MHz. thanks
- id: 21505
  author: hameda
  author_email: tipaza@hotmail.com
  author_url: http://kjuytr
  date: '2013-11-13 20:13:29 +0800'
  date_gmt: '2013-11-13 12:13:29 +0800'
  content: eletomytr
- id: 28546
  author: Luigi
  author_email: caccaculo@live.it
  author_url: ''
  date: '2014-11-16 21:51:38 +0800'
  date_gmt: '2014-11-16 13:51:38 +0800'
  content: "Hi. I have two cheap car chinese. I would try to use both together. I
    have fix one of this with a resistence of 470Kohm in tx and rx. but when i use
    together, the cars don't move because there is a interference. Anyone have a suggest
    to fix it?\r\nRegards\r\n\r\nI hope to be clear with my english!"
---
<p>To get ready for the Robot Contest event on 1/16, I order the RMB 58 RC cars from Taobao. This RC car is good size and properly built. Originally, I wanted to go with the route of replacing the control board with Arduino and drive everything there. </p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http://xinchejian.com/wp-content/uploads/2011/01/IMG_0193.jpg" alt="IMG_0193.JPG" title="IMG_0193.JPG" border="0" width="500" height="373" /></p>
<p>As I was trying to hook up the motor to Arduino, I realized that there wasn't any <a href="http://en.wikipedia.org/wiki/H-bridge">H Bridge</a> and it was way too cold to go out and get it. Hmm... I figure there must be some H Bridge on the control board I just rip out of the car.  </p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http://xinchejian.com/wp-content/uploads/2011/01/IMG_0216.jpg" alt="IMG_0216.jpg" title="IMG_0216.jpg" border="0" width="500" height="417" /></p>
<p>As I located the two H bridge on the board, I notice the RX-2 chip. Out of curiosity, I decide to google for this chip. To a pleasant surprise, I found <a href="http://xinchejian.com/?attachment_id=345">RX-2/TX-2 Datasheet in Chinese</a> and <a href="http://xinchejian.com/?attachment_id=347">guide</a> for exactly the board in the car and remote.</p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http://xinchejian.com/wp-content/uploads/2011/01/IMG_0215.jpg" alt="IMG_0215.jpg" title="IMG_0215.jpg" border="0" width="536" height="509" /></p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http://xinchejian.com/wp-content/uploads/2011/01/untitled.jpg" alt="untitled.jpg" title="untitled.jpg" border="0" width="500" height="201" /></p>
<p>Decide to replace RX-2 in the car with Arduino so the H-Bridge on board can be reused and the RF for the remote can still work. Still trying to figure out what I am going to do with those remote control signal. A few facts about RX-2/TX-2 chip I found is that the RC frequency can be adjusted by different resistance from 100K to 500K Ohm between OSCI/OSCO pins. </p>
<p><img style="display:block; margin-left:auto; margin-right:auto;" src="http://xinchejian.com/wp-content/uploads/2011/01/untitled1.jpg" alt="untitled.jpg" title="untitled.jpg" border="0" width="500" height="195" /></p>
