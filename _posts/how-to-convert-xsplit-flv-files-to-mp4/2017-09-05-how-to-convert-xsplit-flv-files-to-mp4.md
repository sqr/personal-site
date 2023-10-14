---
layout: post
title: "How to convert XSplit flv files to mp4"
date: 2017-09-05 09:29:20 +0700
categories: video media
usemathjax: true
---

Recently I have been recording some of my gaming sessions (specially DayZ), livestreaming them through Twitch.tv using XSplit. I wanted to edit some videos in Premiere, but found out that the FLV files that are created locally use a strange audio codec, making it impossible to edit them in Premiere, Sony Vegas or any other NLE I know of.

The next step for my was trying to figure out how to convert them. I tried using different converters I found on the net, but always ended up with audio problems, wether it was sync issues or jitter…Until I found XMedia Recode. This software, which is totally free, will convert your XSplit FLV files to H264, allowing you to later edit them wherever you want.

Once installed, all you have to do is:

    click Open File
    select your FLV
    then in Format tab pick H.264
    in video tab select your preferred settings.
    Finally click on the green + sign and on Encode.

You will have a hassle-free MP4 file to work with.
