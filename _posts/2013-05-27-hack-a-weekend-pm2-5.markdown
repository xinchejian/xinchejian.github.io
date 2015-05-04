---
layout: post
status: publish
published: true
title: Hack-a-weekend PM2.5 | Hack-a-weekend PM2.5
author:
  display_name: nihaopaul
  login: nihaopaul
  email: nihaopaul@gmail.com
  url: ''
author_login: nihaopaul
author_email: nihaopaul@gmail.com
wordpress_id: 4678
wordpress_url: http://xinchejian.com/?p=4678
date: '2013-05-27 16:25:14 +0800'
date_gmt: '2013-05-27 08:25:14 +0800'
categories:
- arduino
- hackerspace
- competition
- art
- electronics
tags: []
comments: []
---
<p><!--:en--><br />
<h2>Hack-a-weekend PM2.5</h2><br />
<a href="http://xinchejian.com/wp-content/uploads/2013/05/351-027_giraffe_push_up.gif"><img class="size-full wp-image-4679 alignnone" alt="351-027_giraffe_push_up" src="http://xinchejian.com/wp-content/uploads/2013/05/351-027_giraffe_push_up.gif" width="300" height="232" /></a></p>
<p>This weekend Valentin wanted to do a little hack-a-weekend as a surprise, he had ordered parts throughout the week and unveiled the weekend plan on wednesday to a few people, what he wanted to do was represent the PM2.5 data we've all heard about in some fun way. His initial idea involved those push button dolls that collapse when you press them from the bottom.</p>
<p>So with all the different PM2.5 sensors he could find the challenge began saturday. first was how do these things work! not exactly rocket science but they do mean looking up the datasheets to get the schematics and a little trial and error. then it was deciding what form it should take, perhaps a representation of a tree would be ideal! so with 3d printed parts the tree was assembled with rubber bands, unfortunately both the bands and 3d printed parts just were not working very well.</p>
<p><a href="http://xinchejian.com/wp-content/uploads/2013/05/IMG_20130526_180103.jpg"><img class="alignleft size-medium wp-image-4682" alt="IMG_20130526_180103" src="http://xinchejian.com/wp-content/uploads/2013/05/IMG_20130526_180103-300x225.jpg" width="300" height="225" /></a>The 3d printed parts were scrapped in favor of Ping Pong balls just because we had (100's) left over from a little prank on Lucio's locker, and string!</p>
<p><a href="http://xinchejian.com/wp-content/uploads/2013/05/IMG_20130526_235609.jpg"><img class="alignright" alt="IMG_20130526_235609" src="http://xinchejian.com/wp-content/uploads/2013/05/IMG_20130526_235609-225x300.jpg" width="225" height="300" /></a>Finally the little thing was built, hooked into the pachube/cosm/xively (or what ever you want to call yourself today) and data is starting to flow, we also had built a 2nd one so we can contrast the information and see which one is accurate to whats being captured (outside) just 800m from us at the US embassy in Shanghai.</p>
<p>so without further a-du meet the tree! well its version 1 of the tree sitting on top of burty, so we can spend some time understanding it's readings before making a permanent one with the choosen sensor.</p>
<p>if you're looking for the data, you can find it here, we're not stating any facts and not guaranteeing the data either as we have nothing to calibrate against: <a href="https://xively.com/feeds/135383882">https://xively.com/feeds/135383882</a></p>
<p>the code can be found on <a href="https://github.com/xinchejian/pm2.5-arduino">https://github.com/xinchejian/pm2.5-arduino</a></p>
<p>The pm25-tree is the data from the tree using a <a href="http://www.seeedstudio.com/wiki/Grove_-_Dust_Sensor">seeedstudio dust sensor</a> - which doesn't seem to be there accurate, where as the pm25 is test data from a sharp sensor which so far is accurate but blowing smoke across it did not change it where as the seeedstudio one did change, only time will tell.</p>
<p>stay tuned for more from Valentin<!--:--></p>
