---
layout: post
title:  "Setting Up a Blog with Jekyll, Github Pages, and AWS S3"
date:   2016-01-08 15:39:40
preview: http://placehold.it/300x300
---

<p>All the code for this blog is open source on github. Check it out at <a href="https://github.com/Andrew-Max/Andrew-Max.github.io">https://github.com/Andrew-Max/Andrew-Max.github.io</a></p>

<p>Disclaimer: The intended audience for this blog is everyone. My goal is to make it so you could try to repeat these steps with no technical knowledge. Unfortunately there is no way t write it without assuming the baseline of knowing git and running some basic command line commandes.If you don't already have these skills, I encourage you to check out codeschool.com which has some good free resources for learnig these things. If you can't follow something, reach out to me and let me know!</p>

<h1>Basic Rundown</h1>

<a href="">Right now I'm traveling South America</a> and I wanted to make a blog to document my trip. I didn't feel like learning wordpress and I don't like the fact that wordpress hides your code from you. Outside of wordpress, it seems like Jekyll is the easiest platform to create your own blog, and that's what I used here. Jekyll is written in Ruby, and feels fairly similar to writing Ruby on Rails code.
<br>

<br>
One of the big advantages of using Jekyll is that it has a github integration that allows you to serve the blog just by hosting it on github. That means no configuring or managing webservers and you don't even need a domain name. All I do to deploy my code is to push to the master branch of the related repo and the content at `andrew-max.github.io/` gets updated almost instantaneously.
<br>
<br>
One of the nice things that Wordpress gives you that Jekyll doesn't is dealing with creating image assets and hosting them but it's nearly free(cents per month) and pretty simple to do this yourslef on Amazon's `s3` cloud storage tool.
<br>
<br>
In this post I'll go through all the libraries and dependencies required to create a similiar blog, how to install them, and how I setup the content of the blog itself
<br>
<br>

<h1>Dependencies: What you need to create a similiar blog</h1>
<h2>Git and a Github Account</h2>
Github plays a crucial role in this setup, becuase they are doing all the work of serving the code for free just by pushing my code to github. <a href="https://git-scm.com/book/en/v2/Getting-Started-Installing-Git">There is a good guide for installing Git</a> and <a href="https://www.codecademy.com/learn/learn-git">some good free tutorials for learning it.</a>

<br>
<br>

<h2>Ruby, Gems, and Jekyll</h2>
This blog is built on Jekyll blogging library and parser which is in turn built on Ruby, and Ruby Gems. I recommend using <a href="https://rvm.io/">RVM</a> to install ruby and gems if you don't aleady have it. Use the <a href="https://rvm.io/rvm/install">RVM Installation Guide</a> to get started. The jekyll website also has a good guide for getting these installed at <a href="https://jekyllrb.com/docs/installation/">https://jekyllrb.com/docs/installation/</a>

<br>
<br>

<h2>An Amazon AWS account</h2>
This blog is photo heavy and relies on a cheap and reliable way to store and serve the photos. Amazon's s3 is perfect for this. <a href="https://www.amazon.com/ap/signin?openid.assoc_handle=aws&opnid.return_to=https%3A%2F%2Fsignin.aws.amazon.com%2Foauth%3Fresponse_type%3Dcode%26client_id%3Darn%253Aaws%253Aiam%253A%253A015428540659%253Auser%252Fawssignupportal%26redirect_uri%3Dhttps%253A%252F%252Fportal.aws.amazon.com%252Fbilling%252Fsignup%253Fredirect_url%253Dhttps%25253A%25252F%25252Faws.amazon.com%25252Fregistration-confirmation%2526state%253DhashArgs%252523%2526isauthcode%253Dtrue%26noAuthCookie%3Dtrue&openid.mode=checkid_setup&openid.ns=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0&openid.identity=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select&openid.claimed_id=http%3A%2F%2Fspecs.openid.net%2Fauth%2F2.0%2Fidentifier_select&action=&disableCorpSignUp=&clientContex1t=&marketPlaceId=&poolName=&authCookies=&pageId=aws.ssop&siteState=pre-register%2Cen_US&accountStatusPolicy=P1&sso=&openid.pape.preferred_auth_policies=MultifactorPhysical&openid.pape.max_auth_age=120&openid.ns.pape=http%3A%2F%2Fspecs.openid.net%2Fextensions%2Fpape%2F1.0&server=%2Fap%2Fsignin%3Fie%3DUTF8&accountPoolAlias=&forceMobileApp=0&language=en_US&forceMobileLayout=0">You can sign up for an aws account here</a>

<h2>And possibly a unix based machine(Mac or Linux)</h2>
<p>I would almost guarantee that everything I'm doing here could be done on Windows but I'm not sure what the differences would be and it may be more difficult. This blog assumes you are using mac or windows.</p>

