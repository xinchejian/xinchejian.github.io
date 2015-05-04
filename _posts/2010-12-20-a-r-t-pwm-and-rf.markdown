---
layout: post
status: publish
published: true
title: A.R.T., PWM and RF
author:
  display_name: rngadam
  login: rngadam
  email: rngadam@gmail.com
  url: ''
author_login: rngadam
author_email: rngadam@gmail.com
wordpress_id: 177
wordpress_url: http://xinchejian.com/?p=177
date: '2010-12-20 01:39:27 +0800'
date_gmt: '2010-12-19 17:39:27 +0800'
categories:
- robot
- arduino
tags:
- A.R.T.
comments: []
---
<div>A.R.T.: Autonomous Robot Toy ^_^<&#47;div></p>
<div>Some theory gleaned related to PWM and RF<&#47;div></p>
<div><em>Disclaimer: this is my first contact with PWM and RF... Feel free to correct me.<&#47;em><&#47;div></p>
<div><&#47;div></p>
<div><strong>General PWM introduction<&#47;strong><&#47;div></p>
<div><strong><br />
<&#47;strong><&#47;div></p>
<div>Using the Arduino to do drive the transmitter circuit would be a temporary hack. &nbsp;Best would be to be a simple circuit using a few dedicated IC to achieve the same (specifically the <a href="http:&#47;&#47;www.datasheetarchive.com&#47;pdf-datasheets&#47;Datasheets-23&#47;DSA-446609.html">TX2C<&#47;a>).<&#47;div></p>
<div><&#47;div></p>
<div><strong>Generating correct Pulse Modulation<&#47;strong><&#47;div></p>
<div><&#47;div></p>
<div>I'm trying to have Arduino output a PWM that will in turn drive the transmitter (using a crystal oscillator at a specific frequency) on&#47;off to achieve the needed pulses.<&#47;div></p>
<div><&#47;div></p>
<div>According to "<a href="http:&#47;&#47;electronics.howstuffworks.com&#47;rc-toy2.htm">How Stuff Works<&#47;a>", &nbsp;RC control is four pulses that are 2.1 milliseconds long, with 700-microsecond intervals.<&#47;div></p>
<div><&#47;div></p>
<div>The pulse segment, which tells the antenna what the new information is, uses 700-microsecond pulses with 700-microsecond intervals. &nbsp;The number of pulses will tell what order to execute:<&#47;div></p>
<div>
<ul>
<li>Forward: 16 pulses<&#47;li>
<li>Reverse: 40 pulses<&#47;li>
<li>Forward&#47;Left: 28 pulses<&#47;li>
<li>Forward&#47;Right: 34 pulses<&#47;li>
<li>Reverse&#47;Left: 52 pulses<&#47;li>
<li>Reverse&#47;Right: 46 pulses<&#47;li><br />
<&#47;ul><br />
<&#47;div><br />
also:</p>
<div>
<ul>
<li>RC control is 2.1 ms HIGH + 0.7ms LOW for a total of 2.8ms.<&#47;li>
<li>This represents a duty of 2.1&#47;2.8 = 75% duty cycle and a frequency of 1&#47;0.00028 = ~3571 Hz.<&#47;li>
<li>Pulse segment duty cycle is 50% (since pulse = interval) with a frequency of 1s&#47;1.4ms (0.7ms+0.7ms) 714Hz.<&#47;li><br />
<&#47;ul><br />
<&#47;div></p>
<div>With the <a href="http:&#47;&#47;www.arduino.cc&#47;en&#47;Tutorial&#47;PWM">Arduino, we can specify duty cycle<&#47;a> and track a certain total duration, but we still need a way to specify frequency.<&#47;div></p>
<div><&#47;div></p>
<div>According to the Secrets of <a href="http:&#47;&#47;arduino.cc&#47;en&#47;Tutorial&#47;SecretsOfArduinoPWM">Arduino PWM<&#47;a> and the <a href="http:&#47;&#47;mil.ufl.edu&#47;~achamber&#47;servoPWMfaq.html">Servo PWM FAQ<&#47;a> the Arduino (or rather, the ATMega168 that it uses) has a 16Mhz clock with prescalers (1, 8, 64, 256, or 1024) that can divide this to a "timer". Final precise control is done by using an integer in the ICR. &nbsp;The microcontroller will count up to ICR and then count down back to 0, turning to HIGH everytime it gets to zero.<&#47;div></p>
<div><&#47;div></p>
<div>Can probably dig this out of the ATMega168 doc: &nbsp;http:&#47;&#47;www.atmel.com&#47;dyn&#47;resources&#47;prod_documents&#47;doc2545.pdf<&#47;div></p>
<div><&#47;div></p>
<div>The equation is: desired_frequency = system_clock &#47; (2*prescaler_value*ICR)<&#47;div></p>
<div>(1&#47;0.00028) = 16e6&#47; (2*prescaler*x) or x = (16e6*2.8e-4)&#47;(2*prescaler)<&#47;div></p>
<div><&#47;div></p>
<div>where prescaler...<&#47;div></p>
<div>
<ul>
<li>1: 2240<&#47;li>
<li>8: 280<&#47;li>
<li>64: 35<&#47;li>
<li>256: 8.75<&#47;li>
<li>1024: 2.1875<&#47;li><br />
<&#47;ul><br />
<&#47;div></p>
<div>...we can thus use prescaler value 1,8,64 + corresponding ICR value. &nbsp;We cannot use 256 and 1024 because their results are fractional.<&#47;div></p>
<div><&#47;div></p>
<div>Same exercise with the pulse segment:<&#47;div></p>
<div>(1&#47;0.0014) = 16e6 &#47; (2*prescaler*x) or x = (16e6*1.4e-3)&#47;(2*prescaler)<&#47;div></p>
<div><&#47;div></p>
<div>where prescaler...<&#47;div></p>
<div>
<ul>
<li>1: 11200<&#47;li>
<li>8: 1400<&#47;li>
<li>64: 175<&#47;li>
<li>256: 43.75<&#47;li>
<li>1024: 10.9375<&#47;li><br />
<&#47;ul><br />
<&#47;div></p>
<div>...we can use either 1, 8 or 64 prescaler (the other two are fractional values).<&#47;div></p>
<div><&#47;div></p>
<div>Higher prescale is better generally as lower timer also reduces power consumption.<&#47;div></p>
<div><&#47;div></p>
<div>The <a href="http:&#47;&#47;www.et06.dk&#47;atmega_timers&#47;">ATmega timers script<&#47;a> should be useful at some point, but I don't understand the output right now...<&#47;div></p>
<div><&#47;div></p>
<div><strong>How do I turn this knowledge into an Arduino embedded program?<&#47;strong><&#47;div></p>
<div><&#47;div></p>
<div>I have no idea yet! I did try to manually create a PWM here by using sleeps:<&#47;div></p>
<div><a href="https:&#47;&#47;github.com&#47;rngadam&#47;ART&#47;blob&#47;master&#47;rf_control&#47;rf_control.pde">https:&#47;&#47;github.com&#47;rngadam&#47;ART&#47;blob&#47;master&#47;rf_control&#47;rf_control.pde<&#47;a><&#47;div></p>
<div><&#47;div></p>
<div>...and feed that into an hacked together RF circuit based on what I could figure out from the circuit but it... obviously doesn't do much<&#47;div></p>
<div><&#47;div></p>
<div>I've come to the conclusion that buying the IC chip that does the same work and use the provided schematics... would be a lot easier...<&#47;div></p>
