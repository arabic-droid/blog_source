---
title: "Get with the program(ming)!"
layout: "post"
permalink: "/2011/06/get-with-programming.html"
uuid: "2083469111000580787"
guid: "tag:blogger.com,1999:blog-6728560442491983758.post-2083469111000580787"
date: "2011-06-10 12:13:00"
updated: "2011-06-10 12:26:02"
description: 
blogger:
    siteid: "6728560442491983758"
    postid: "2083469111000580787"
    comments: "0"
categories: 
author: 
    name: "Paul D'Ambra"
    url: "https://plus.google.com/114260096260757534167?rel=author"
    image: "//lh5.googleusercontent.com/-nN3yNuaSWDs/AAAAAAAAAAI/AAAAAAAABQU/ESeyTW5Duf0/s512-c/photo.jpg"
---

Twice recently I've hit the same problem with two different mobile phone vendor's websites. Vodafone (displayed here) and 3. When I type a phone number I split it into three sections using white space. "nnnn nnn nnnn" that's how I remember numbers. That's not uncommon I don't think...

<!--more-->

<a onblur="try {parent.deselectBloggerImageGracefully();} catch(e) {}" href="http://1.bp.blogspot.com/-5j1jDK3JAss/TfIK0Q-_reI/AAAAAAAAAO0/LyikHIbRnj0/s1600/idiots.png"><img style="float:left; margin:0 10px 10px 0;cursor:pointer; cursor:hand;width: 400px; height: 78px;" src="http://1.bp.blogspot.com/-5j1jDK3JAss/TfIK0Q-_reI/AAAAAAAAAO0/LyikHIbRnj0/s400/idiots.png" border="0" alt=""id="BLOGGER_PHOTO_ID_5616563578313092578" /></a>
 nor is it odd to use a dash.<br /><br />So why do I need to learn how your website wants phone numbers formatted.<br /><br />Whack some javascript on your page... you *must* be using it for something!<br /><br />var correctedNumber = numberTypedOnForm.replace(" ","").replace("-","");<br /><br />and with that massive development cost you aren't going to make someone type a number twice just to satisfy your database server. Yes, not everyone will have javascript turned on and it won't catch everyone's weird way of typing phone numbers<br /><br />"(nnnn)-nn-nn-nn-n" <br /><br />but it's about not introducing a pain point for customers when you don't have to<br /><br /><br />If you want to be really fancy you could<br /><br />var correctedNumber = numberTypedOnForm.replace("/\D/g","");<br /><br />Computers are supposed to make our lives easier but it's up to *you* website developers to help them help us.<br /><br />Arseholes!
</div>