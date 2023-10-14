---
layout: post
title: "How to import JSON files in After Effects CC 2018 to display Twitter data"
date: 2018-05-05 09:29:20 +0700
categories: video media
usemathjax: true
---

The aim of this tutorial is to demonstrate how you can streamline the creation of motion graphics thanks to the new JSON compatibility features in Adobe After Effects CC 2018 using Twitters API and Python. It will be divided in two parts, the first one focused on how to get the data from a tweet to a JSON file, and a second one on how to import this data and use it in an AE composition. If you already have a JSON file (it can be a tweet or any other kind of structured data) feel free to skip the first step.
Step 1: Saving a tweet as a JSON file

In order to do this we are going to use Python and Twitter’s API. An easy way to get going if you don’t have Python is to download Anaconda. You will also need to install Tweepy, which is the package we will use to get data from Twitter using Python.

The next thing we need to do is to create a Python script that takes the ID of a tweet, fetches the data and stores it as a .JSON file in our computer. Thankfully my friend Antonio Verdone wrote a script tailored to this need, that you can find here. Just download “tweet_to_json.py”, open a python prompt (if you are using Anaconda, “Anaconda Prompt” should make things easy), navigate to the directory where “tweet_to_json.py” is located and type the following command:

```bash
python tweet_to_json.py *TWEET_ID*
```

Where _TWEET ID_ is the status ID of the tweet, for example 920729080491859968.

If everything goes well, two folders should have been created next to the tweet_to_json.py file: “Json files” and “images”. One will have the structures JSON file and the other will have the avatar picture of the user posted the tweet. Copy these files and paste them next to your .aep project and get ready for step two!
Step 2: importing JSON file in After Effects CC 2018

In step two we are going to get the files generated with our python script and import that data for display in After Effects. You can download my test AEP and JSON files if that helps you.

First of all we need to import our JSON file in the same way that would be done with any kind of footage.

Then we will create a text layer for every field that we want to import from the JSON file. In my example file we are using five fields: User display name, username, status text, number of retweets and number of likes (formerly favorites).

We need to write a bit of code on each text layer. This is easily done by Alt-clicking the “Source Text” property inside the Text options of the Text Layer.

Lets start with an easy example: User display name. This text layer requires the following code:

```javascript
eval("var username=" + footage("tweet.json").sourceText);
username.user.name;
```

The first line looks in your footage for a file called tweet.json and searches for the field “name” inside the field “user”. The second line prints the value. In order for this to work make sure that the json file that you have imported is called “tweet.json”, or to change the code accordingly to point to your imported json file.

The status text (the actual tweet) is a bit more complicated. The code is as follows:

```javascript
eval("var status=" + footage("tweet.json").sourceText);
status.full_text;

txt = status.full_text;
n = 35;
outStr = "";
newLine = "";
splt = txt.split(" ");
for (i = 0; i < splt.length; i++) {
  if ((newLine + " " + splt[i]).length > n) {
    if (outStr != "") outStr += "\r";
    outStr += newLine;
    newLine = splt[i];
  } else {
    if (newLine != "") newLine += " ";
    newLine += splt[i];
  }
}
if (newLine != "") {
  if (outStr != "") outStr += "\r";
  outStr += newLine;
}
outStr;
```

The first two lines do the same as in the previous layer. The rest of the code makes sure that the tweet is separated into different lines after a set amount of characters. The specific amount before the line break can be set on line 4, defined as “n”.

The rest of the layers are really similar to the first one we looked at:

Username:

```javascript
eval("var screenname=" + footage("tweet.json").sourceText);
"@" + screenname.user.screen_name;
```

Number of retweets:

```javascript
eval("var retweets=" + footage("tweet.json").sourceText);
retweets.retweet_count;
```

Number of favorites:

```javascript
eval("var me_gusta=" + footage("tweet.json").sourceText);
me_gusta.favorite_count;
```

Finally, in my example files the user image is also used, on display next to the username.
