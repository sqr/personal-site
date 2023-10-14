---
layout: post
title: "Cinema 4D R14 and Camera Mapping"
date: 2013-01-13 09:29:20 +0700
categories: video media
usemathjax: true
---

So recently i’ve been trying to create high quality renders in Cinema 4D, integrating 3D objects into real environments. Instead of using camera tracking, i gave camera mapping a try, using an old picture i shot in LA two years ago. Solving the camera was really easy thanks to the Camera Calibration tool in Cinema 4D R14 (and GSG of course). Once solved, building the geometry accordingly was easy, bearing in mind that my photo was easy to replicate and didn’t have many tough spots. Some of it had to be redone in Photoshop, and what was really a challenge was creating the grass that had to stand out along the the curb.

Fortunately, using an alpha channel did the trick, and it certainly helps to sell the effect and add an interesting parallax to the picture. Next up was modeling and texturing a mailbox, which is completely another topic. Anyway, fast forward to the next day and i had my geometry in place and my camera moving around my 2D-3D picture.

But obviously, without having any reference whatsoever on the original lighting of the scene, there was no way that i could make the mailbox completely realistic. Yeah, it can be faked somehow and adjusted in composition to make it look like it was there, but the results are not as good as what you could get with a light probe.

So that will be my next step, getting a nice “gazing globe” to take HDRI and use them as environment maps.
