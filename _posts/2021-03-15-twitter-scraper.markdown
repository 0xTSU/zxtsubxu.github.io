---
layout: post
title:  "Twitter Image Scraper"
date:   2021-03-15 13:06:28 -0800
categories: projects, blog
---

This script allows you to crawl and scrape images off a Twitter user's page. 

Requires geckodriver and a firefox profile with an account signed in.

{% include youtubePlayer_twitterscraper.html %}

[View code on GitHub](https://github.com/zxtsubxu/ez-twitterdl)


# First step in Python - A Twitter Scraper

As an aside from my coursework, I wanted to dip my toes into various programming languages and see how the basic principles are implemented. Python is a popular language that's extremely easy to learn. I found to my benefit that I was quickly able to adjust to its syntax, learn the indent rules, how to instantiate a class, and how to run programs. 
Despite its flaws, I can see why its one of the most widely used languages for programming.

With it, I created a simple twitter scraper. It utilizes a module called Selenium, which is normally used for web automation. There are many drawbacks to using Selenium in this case, however, it introduced me to concepts such as AJAX programming, the Document Object Model(DOM), and the purposes of a webapps front-end and back-end. 

Selenium's purpose is to launch a headless instance of firefox, and with the code that I've written, it builds an HTML by "scrolling" to the bottom of the page. When the browser reaches the bottom of the page, Twitter's front-end sends a request to their back-end for more data, and in turn, loads more elements onto the DOM which we can extract.

Using xpath, I'm able to navigate, and manipulate the DOM elements to scrape image URLs.

The program inserts unique URLs into a list so the latter half of the program can iterate through that array, and send requests. Once the request is returned, we check the status code(200) to see if its a valid image, check the header to get its MIME-type, and then write the contents to the file with the correct file extension.

Web scraping is a powerful tool. I plan to exploit/utilize/abuse it for my future projects. 