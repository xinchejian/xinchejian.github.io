---
layout: post
status: publish
published: true
title: Visual Programming Language for Arduino (1)
author:
  display_name: David Li
  login: david
  email: david@xinchejian.com
  url: ''
author_login: david
author_email: david@xinchejian.com
wordpress_id: 472
wordpress_url: http://xinchejian.com/?p=472
date: '2011-02-05 23:08:14 +0800'
date_gmt: '2011-02-05 15:08:14 +0800'
categories:
- arduino
tags:
- arduino
- ide
comments: []
---
<p>To make Arduino easier for non-programmers, I decided to start a visual programming environment similar to <a href="http://scratch.mit.edu/" target="_blank">Scratch</a> for Arduino. </p></p>
<h3>Similar Projects around the Web</h3></p>
<p><a href="http://www.modk.it/" target="_blank">Modkit</a> is a similar project but at the time I wanted to start the project, it was in a closed alpha. Also, it seems that modkit is going to be proprietary and I want an open source VPL for Arduino. By the way, <a href="http://www.modk.it/crimpcards" target="_blank">Modkit CrimpCards</a> is an awesome idea and design. </p></p>
<p><a href="http://seaside.citilab.eu/scratch/arduino" target="_blank">S4A</a> (Scratch for Arduino) is another interesting project but it's for using Scratch with Arduino instead of programming for Arduino. </p></p>
<p><a href="http://web.media.mit.edu/~mellis/" target="_blank">David Mellis</a> over at MIT Media Lab also has a project called "Scratch for Arduino" but no detail yet. David is also one of the creator of Arduino platform. </p></p>
<h3>Arduino IDE and OpenBlocks</h3></p>
<p>Fork <a href="https://github.com/arduino/Arduino" target="_blank">the source of Arduino IDE</a> hosted on github to host my version <a href="https://github.com/taweili/Arduino" target="_blank">here</a>. Next stop is to find a library for the visual programming. I found a project called <a href="http://education.mit.edu/openblocks" target="_blank">OpenBlocks</a> developed as part of the <a href="http://education.mit.edu/projects/starlogo-tng" target="_blank">MIT StarLogo NG</a>. Open Blocks is also used in Google's Android development tool <a href="http://appinventor.googlelabs.com/about/" target="_blank">App Inventor</a>. </p></p>
<p>Both Arduino IDE and Open Blocks are written in Java so the integration should be smooth. Since I have done by share of Java, I decided to also use this opportunities to look into a few alternative languages running on JVM to implement this. Since I have done mostly Ruby for the past few years, <a href="http://jruby.org/">JRuby</a> looks pretty good. The language I really want to use is <a href="http://clojure.org/">Clojure</a> but it seems it's a bit tricky to use it embedded in a Java app. Will give both a try and see how it goes. </p></p>
<h1>Let the hacking beging!</h1></p>
<p>Hopefully, we will have a running version in the next few weeks. </p>
