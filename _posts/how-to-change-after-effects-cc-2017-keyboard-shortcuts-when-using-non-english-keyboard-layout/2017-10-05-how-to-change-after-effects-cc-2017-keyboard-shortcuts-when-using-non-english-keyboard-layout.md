---
layout: post
title: "How to change After Effects CC 2017 Keyboard Shortcuts when using non english keyboard layout"
date: 2017-10-05 09:29:20 +0700
categories: video media
usemathjax: true
---

Recently Adobe decided to improve the keyboard shortcurt interface for Premiere Pro. It was a long overdue change and very well received. But for some reason they have forgotten about After Effects users, as we still have to tinker with TXT edits and obscure key codes to make everything work. Even more so for users that happen to have After Effects in English but use another type of keyboard, for example one with European ISO Layout.

In the following example I will show you how to change the Trim In and Trim Out shortcuts, as well as Zoom In and Zoom Out. These are completely broken if the user has the software in English but a Spanish layout keyboard.

First of all open After Effects and go to Edit -> Preferences -> General and then click on Reveal preferences in Explorer.

Once in that folder you have to edit the file Adobe After Effects 14.1 Win en_US Shortcuts.txt. I like using Notepad++ (free software).

The easiest way to solve the Trim In and Out problem is to search the txt file for the following text: “TimeTrimIn” and assign our desired shortcut. In my case I like using “(Alt+I)” for “TimeTrimIn” and “(Alt+O)” for “TimeTrimOut”. Note that these shortcuts are defined in different sections of the txt file, so they need to be replaced in different lines.

To fix the zoom behavior you have to search for [“CCompCompCmd”]. In that section you will find “CompTimeZoomIn” and “CompTimeZoomOut”. These have to be set to “(Plus)” and “(-)” respectively.

To make the changes effective you have to save the file and restart After Effects. Be specially careful if you use the Creative Cloud auto-update for preferences, as it might overwrite your preference files and roll back the files!

Make sure to check my new post on how to import json data in after effects using python
