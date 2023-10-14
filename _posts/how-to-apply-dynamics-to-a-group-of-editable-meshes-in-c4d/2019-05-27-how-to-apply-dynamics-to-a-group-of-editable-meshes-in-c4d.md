---
layout: post
title: "How to apply Dynamics to a group of editable meshes in C4D"
date: 2019-05-27 09:29:20 +0700
categories: video media
usemathjax: true
---

Applying Dynamics to a Cloner in Cinema 4D is a great way to get things moving! But maybe you have faced the following scenario: You have a bunch of geometry created from a cloner, make it editable, do your thing and THEN you want to apply Dynamics… but nothing works.

That’s because C4D only applies Dynamics to Cloner and Fracture objects, not to nulls with a bunch of geometry inside.

But there’s a quick tip to get this working: You just have to put the geometry inside of a Fracture object, and apply a Dynamics tag to that object, setting the options of Top Level.

Easy! Now you have Cinema4D Dynamics aplied to a group of geometry, treating each object inside the Fracture object independently. However, it might be wise to keep your objects in parametric state as long as you can, as this will provide further control over certain variables of the object that will disappear once you make it editable.

I personally prefer to keep a copy of the parametric objects and cloners before they are editable, mark them as such and keep them in the project save file until further down the line, when i’m mostly certain that they won’t be needed again.
