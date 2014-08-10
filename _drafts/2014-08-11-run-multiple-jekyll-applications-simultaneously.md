---
layout: post
title:  "Run multiple Jekyll Applications simultaneously"
date:   2014-08-11 10:30:00
categories: jekyll code-snippets
---

I had to run 2 Jekyll Applications while working on an Article about [How to build a blog in 30 minutes][article]{target: "blank"}. Here is how I did it:

- Change the PORT while serving
- In _config.yml
  - add `port: 5000`
- Start Jekyl
  - `jekyll serve`

It should now start Jekyll on port 5000. This way you can manage to run multiple Jekyll Applications simultaneously.

<br/>

> Feel free to leave your comment with respect and courtesy. I sincerely appreciate your support!

<div class="pull-right"><strong>Krishnaprasad Varma</strong></div>
<div class="clearfix"></div>


[article]: /blog/2014/08/09/how-to-build-a-blog-in-30-minutes/ "How to build a blog in 30 minutes"