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
<p>To make Arduino easier for non-programmers, I decided to start a visual programming environment similar to <a href="http:&#47;&#47;scratch.mit.edu&#47;" target="_blank">Scratch<&#47;a> for Arduino. <&#47;p></p>
<h3>Similar Projects around the Web<&#47;h3></p>
<p><a href="http:&#47;&#47;www.modk.it&#47;" target="_blank">Modkit<&#47;a> is a similar project but at the time I wanted to start the project, it was in a closed alpha. Also, it seems that modkit is going to be proprietary and I want an open source VPL for Arduino. By the way, <a href="http:&#47;&#47;www.modk.it&#47;crimpcards" target="_blank">Modkit CrimpCards<&#47;a> is an awesome idea and design. <&#47;p></p>
<p><a href="http:&#47;&#47;seaside.citilab.eu&#47;scratch&#47;arduino" target="_blank">S4A<&#47;a> (Scratch for Arduino) is another interesting project but it's for using Scratch with Arduino instead of programming for Arduino. <&#47;p></p>
<p><a href="http:&#47;&#47;web.media.mit.edu&#47;~mellis&#47;" target="_blank">David Mellis<&#47;a> over at MIT Media Lab also has a project called "Scratch for Arduino" but no detail yet. David is also one of the creator of Arduino platform. <&#47;p></p>
<h3>Arduino IDE and OpenBlocks<&#47;h3></p>
<p>Fork <a href="https:&#47;&#47;github.com&#47;arduino&#47;Arduino" target="_blank">the source of Arduino IDE<&#47;a> hosted on github to host my version <a href="https:&#47;&#47;github.com&#47;taweili&#47;Arduino" target="_blank">here<&#47;a>. Next stop is to find a library for the visual programming. I found a project called <a href="http:&#47;&#47;education.mit.edu&#47;openblocks" target="_blank">OpenBlocks<&#47;a> developed as part of the <a href="http:&#47;&#47;education.mit.edu&#47;projects&#47;starlogo-tng" target="_blank">MIT StarLogo NG<&#47;a>. Open Blocks is also used in Google's Android development tool <a href="http:&#47;&#47;appinventor.googlelabs.com&#47;about&#47;" target="_blank">App Inventor<&#47;a>. <&#47;p></p>
<p>Both Arduino IDE and Open Blocks are written in Java so the integration should be smooth. Since I have done by share of Java, I decided to also use this opportunities to look into a few alternative languages running on JVM to implement this. Since I have done mostly Ruby for the past few years, <a href="http:&#47;&#47;jruby.org&#47;">JRuby<&#47;a> looks pretty good. The language I really want to use is <a href="http:&#47;&#47;clojure.org&#47;">Clojure<&#47;a> but it seems it's a bit tricky to use it embedded in a Java app. Will give both a try and see how it goes. <&#47;p></p>
<h1>Let the hacking beging!<&#47;h1></p>
<p>Hopefully, we will have a running version in the next few weeks. </p>
