---
redirect_from:
  - /post/36874234521/facebook-open-graph-custom-action-and-object
  - /post/36874234521
layout: post
title: "Facebook Open Graph custom action and object"
date: 2012-11-30 10:41:00 +0000
tags: ["facebook", "opengraph", "action", "object", "pixel-art", "drawing", "draw"]
tumblr_id: 36874234521
---
Did you know that every drawing at Draw! is a custom object at Facebook Open Graph?

![The draw action has been approved](/assets/img/facebook-open-graph-custom-action-and-object/A88fHa2CYAAE3JV.png)

Here’s an example object: [http://developers.facebook.com/tools/debug/og/object?q=http%3A%2F%2Fdrawbang.com%2Fdrawings%2Fcf546feca101cd445023bb23d46c3f0b06d73940.png](http://developers.facebook.com/tools/debug/og/object?q=http%3A%2F%2Fdrawbang.com%2Fdrawings%2Fcf546feca101cd445023bb23d46c3f0b06d73940.png)

You can see that object type is *drawbang:drawing*, this is a drawing at Draw! as Open Graph knows it.

It’s that simple, when you save a new drawing at Draw! a new object is created through the *drawbang:draw* custom action.

It’ll be visible in your *activities list* in your profile page (see example below) and you can see all your drawings in a *collection* of your latest pixel art pieces!

![Profile activities including a new drawing](/assets/img/facebook-open-graph-custom-action-and-object/A88iLTJCMAAha4v.png)
