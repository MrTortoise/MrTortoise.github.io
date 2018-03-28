---
layout: post
title:  "SVG: Getting started? P1 svg vs div vs canvas"
date:   2018-03-24 08:00:48 +0000
categories: svg tutorial drawing animation
---
# SVG vs div/css vs canvas

Time to figure out how to do some graphics. There are various options. This will be updated as I learn more.

## svg vs canvas vs div

### canvas

#### Pro

- great for images and graphics manipulation

#### Con

- its fairly low level, immediately writes to the buffer without retaining the object model
- This makes it fast, but it means it behaves very much like what you would get if you wrote your own game engine
- You do not get hit detection on objects (there are none) so you have to write that yourself
- you have to write your own UI, this inevitably leads you to reinvent html and hate life as you discover things like word wrap are very very hard in all but non trivial cases

#### Comment

I have very little interest in exploring this after reading about it. Have written many game engines and really do not want have to rebuild the vast amount of work it takes to get to something like svg or html and css. If I didn't want it in the browser i'd of just used a game engine ...

So I am unlikely to add more here.

### div / css

#### Pro

- css is powerful, you get hit events and event handlers
- can have hardware acceleration
- can easily cope with reorganizing layout
- is now hardware accelerated in some situations

#### con

- personally im not a huge fan of getting into css or its edge cases / browser stuff
- The strengths of html/css were flowing layouts - this may of changed

#### Comment

I am studying up to writ ea  version of 256, i will probably end up redoing the front end in both svg and div just so i understand the differences

### svg

#### Pro

- middle ground, build for graphics and animation
- can capture events as it is still an object model
- some really nice ways to scale and constrain text
- viewport can scale with window and have arbitrary size and origin
- looks the same and scales nicely
- can be produced from vector art programs

#### Con

- not really sure yet. Biggest seem sot be yet another language to learn.
- looks like injecting SVG on the fly (eg for animations) is [less than cool](https://stackoverflow.com/questions/8455773/svg-trigger-animation-with-event)

#### Comment

Will be spending most of my time playing with this. It looks interesting and flexible