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
<div>A.R.T.: Autonomous Robot Toy ^_^</div></p>
<div>Some theory gleaned related to PWM and RF</div></p>
<div><em>Disclaimer: this is my first contact with PWM and RF... Feel free to correct me.</em></div></p>
<div></div></p>
<div><strong>General PWM introduction</strong></div></p>
<div><strong><br />
</strong></div></p>
<div>Using the Arduino to do drive the transmitter circuit would be a temporary hack. &nbsp;Best would be to be a simple circuit using a few dedicated IC to achieve the same (specifically the <a href="http://www.datasheetarchive.com/pdf-datasheets/Datasheets-23/DSA-446609.html">TX2C</a>).</div></p>
<div></div></p>
<div><strong>Generating correct Pulse Modulation</strong></div></p>
<div></div></p>
<div>I'm trying to have Arduino output a PWM that will in turn drive the transmitter (using a crystal oscillator at a specific frequency) on/off to achieve the needed pulses.</div></p>
<div></div></p>
<div>According to "<a href="http://electronics.howstuffworks.com/rc-toy2.htm">How Stuff Works</a>", &nbsp;RC control is four pulses that are 2.1 milliseconds long, with 700-microsecond intervals.</div></p>
<div></div></p>
<div>The pulse segment, which tells the antenna what the new information is, uses 700-microsecond pulses with 700-microsecond intervals. &nbsp;The number of pulses will tell what order to execute:</div></p>
<div>
<ul>
<li>Forward: 16 pulses</li>
<li>Reverse: 40 pulses</li>
<li>Forward/Left: 28 pulses</li>
<li>Forward/Right: 34 pulses</li>
<li>Reverse/Left: 52 pulses</li>
<li>Reverse/Right: 46 pulses</li><br />
</ul><br />
</div><br />
also:</p>
<div>
<ul>
<li>RC control is 2.1 ms HIGH + 0.7ms LOW for a total of 2.8ms.</li>
<li>This represents a duty of 2.1/2.8 = 75% duty cycle and a frequency of 1/0.00028 = ~3571 Hz.</li>
<li>Pulse segment duty cycle is 50% (since pulse = interval) with a frequency of 1s/1.4ms (0.7ms+0.7ms) 714Hz.</li><br />
</ul><br />
</div></p>
<div>With the <a href="http://www.arduino.cc/en/Tutorial/PWM">Arduino, we can specify duty cycle</a> and track a certain total duration, but we still need a way to specify frequency.</div></p>
<div></div></p>
<div>According to the Secrets of <a href="http://arduino.cc/en/Tutorial/SecretsOfArduinoPWM">Arduino PWM</a> and the <a href="http://mil.ufl.edu/~achamber/servoPWMfaq.html">Servo PWM FAQ</a> the Arduino (or rather, the ATMega168 that it uses) has a 16Mhz clock with prescalers (1, 8, 64, 256, or 1024) that can divide this to a "timer". Final precise control is done by using an integer in the ICR. &nbsp;The microcontroller will count up to ICR and then count down back to 0, turning to HIGH everytime it gets to zero.</div></p>
<div></div></p>
<div>Can probably dig this out of the ATMega168 doc: &nbsp;http://www.atmel.com/dyn/resources/prod_documents/doc2545.pdf</div></p>
<div></div></p>
<div>The equation is: desired_frequency = system_clock / (2*prescaler_value*ICR)</div></p>
<div>(1/0.00028) = 16e6/ (2*prescaler*x) or x = (16e6*2.8e-4)/(2*prescaler)</div></p>
<div></div></p>
<div>where prescaler...</div></p>
<div>
<ul>
<li>1: 2240</li>
<li>8: 280</li>
<li>64: 35</li>
<li>256: 8.75</li>
<li>1024: 2.1875</li><br />
</ul><br />
</div></p>
<div>...we can thus use prescaler value 1,8,64 + corresponding ICR value. &nbsp;We cannot use 256 and 1024 because their results are fractional.</div></p>
<div></div></p>
<div>Same exercise with the pulse segment:</div></p>
<div>(1/0.0014) = 16e6 / (2*prescaler*x) or x = (16e6*1.4e-3)/(2*prescaler)</div></p>
<div></div></p>
<div>where prescaler...</div></p>
<div>
<ul>
<li>1: 11200</li>
<li>8: 1400</li>
<li>64: 175</li>
<li>256: 43.75</li>
<li>1024: 10.9375</li><br />
</ul><br />
</div></p>
<div>...we can use either 1, 8 or 64 prescaler (the other two are fractional values).</div></p>
<div></div></p>
<div>Higher prescale is better generally as lower timer also reduces power consumption.</div></p>
<div></div></p>
<div>The <a href="http://www.et06.dk/atmega_timers/">ATmega timers script</a> should be useful at some point, but I don't understand the output right now...</div></p>
<div></div></p>
<div><strong>How do I turn this knowledge into an Arduino embedded program?</strong></div></p>
<div></div></p>
<div>I have no idea yet! I did try to manually create a PWM here by using sleeps:</div></p>
<div><a href="https://github.com/rngadam/ART/blob/master/rf_control/rf_control.pde">https://github.com/rngadam/ART/blob/master/rf_control/rf_control.pde</a></div></p>
<div></div></p>
<div>...and feed that into an hacked together RF circuit based on what I could figure out from the circuit but it... obviously doesn't do much</div></p>
<div></div></p>
<div>I've come to the conclusion that buying the IC chip that does the same work and use the provided schematics... would be a lot easier...</div></p>
