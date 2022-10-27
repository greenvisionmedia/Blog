## Introduction
At GV we often face a few conflicting truths:
 - The internet shouldn't be restricted to only those who know how to code.
 - Custom code often adds to the carbon footprint of a website.
 - To make a truly green website, you really should know a little code.

I'll assume you're on board with the first two, if you're into low-code and sustainable web design. Here's an example of the second.

On this site, the client wanted a youtube video on an already graphic-heavy front page. By the time the page was complete, we had dipped into the red on [websitecarbon.com]().

![[Pasted image 20221025205559.png]]

After some digging, I realized the culprit was the webflow youtube embed. With the help of [this forum post](https://discourse.webflow.com/t/high-performance-native-styled-youtube-embed/97763) and a tiny bit of javascript, I was able to 'lazy load' the video, deferring the costly youtube API call until the point that the user actually clicks on the video. This change alone put me back in the green:

![[Pasted image 20221025204957.png]]

(To get this data, I had to roll back the site and test each version, thereby wasting more carbon. The sustainable web is unforgiving). 

Point is, while Javascript often add bloat and unneccesary complexity to a project, scripting can be important for energy efficiency as well. How can we add JS while remaining efficient, both in the design process and the final page weight? 

## CDN delivery
The most robust, and a very popular method, is to host your scripts online and call them externally, using a service like JSdelivr. This gives the benefit of continous integration; your static site can access the latest version of the script. But using these services means adding even *more* API calls or http requests, which impacts your site's [speed and security](https://blog.wesleyac.com/posts/why-not-javascript-cdn).

## The \<script> tag
This is the most common way many no-code developers start adding functionality to their sites. Simply paste whatever code you need into an html `<script>` embed. It's quick and simple to incorporate, and easy to understand. It's also slow. Script tags are render blocking, same as external scripts, but they also cannot be cached.

## External scripts
This is it fam ^ 







