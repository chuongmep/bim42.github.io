---
id: 1091
title: Why I am now a bimsync fanboy
date: 2016-11-26T13:37:21+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1091
permalink: /2016/11/why-i-am-now-a-bimsync-fanboy/
categories:
  - Coordination
image: /assets/2016/11/OniPad2.jpg
tags:
  - Coordination
  - IFC
  - Open BIM
  - Schedules
  - Visualization
---
Those of you who know me know that I recently changed my employer and I am know working for a real estate developer, with a different scope of work than in my previous position. This lead me to put aside Revit and Dynamo for a while, and think more about a project-wide collaboration platform.

Alongside with the ubiquitous BIM 360 platform from Autodesk, there is a lot of more confidential solutions from various developers. Every large BIM editor has its own, and many other companies propose one. Among them, [bimsync](https://bimsync.com/) is a rather discrete application from [Catenda](http://catenda.no/), a Norwegian company. Having eared about it at the [French Revit User Group](http://paris-rug.fr/), I had to give it a test, and I was not disappointed.

What immediately caught my attention is the web viewer, which is the best I have ever tried. They develop their own IFC web-based viewer, and it is not far from perfect. The viewer is extremely easy to use with the left mouse button and the wheel, and include every needed feature. Sectioning the model is also quite well implemented and do a very good job. My only wish here is to have a filled pattern to highlight the difference between fill and void while sectioning.

![SectionnningWithDiff]({{ "/assets/2016/11/SectionnningWithDiff.jpg" | absolute_url }})

The viewer is also quite powerful, I tried it with 1 Go worth of IFC files, it run "almost" smoothly on my iPad.

![OniPad2]({{ "/assets/2016/11/OniPad2.jpg" | absolute_url }})

bimsync does a good job at uploading, viewing and managing versions of various models, and provides a thoughtful way of managing revisions.

You start by creating a "model" which on bimsync is a placeholder where you will upload the various versions of an IFC file. Once this file is processed by the platform, it will be available for review along with the other models. The processing part can be rather slow, it takes more than one hour for a 500 Mo IFC file, but happen entirely online, you don't even have to keep your computer open.

![models]({{ "/assets/2016/11/models.jpg" | absolute_url }})

A key feature of bimsync is the ability to easily extract Excel schedules from the uploaded models. Having the ability to show data from a model in a nice spreadsheet is priceless, and this is something that is generally overlooked by their competitors.

The issue tracking solution integrated in bimsync is also very efficient and well-thought-out, with a lot of nice features.

You start by creating an issue directly on the model, can assign someone responsible for solving this issue, add a due date and write a few lines of comment.

![Issues]({{ "/assets/2016/11/Issues.jpg" | absolute_url }})

These issues are grouped by boards, and you can create as many board as you want. You can also keep track of the resolution of these issues with a few statistical tools and filters, and save reports in Excel.

![statistics2]({{ "/assets/2016/11/statistics2.jpg" | absolute_url }})

You know that I am a big fan of the BCF concept, and bimsync doesn't disappoint me in this regard, by providing a first-class BCF 1 and 2 support. You can export your issues in BCF to display them directly in your authoring platform of choice.

Catenda was kind enough to provide me with an access to their [API](https://bimsync.com/developers), and after a few tests, I found them quite easy to use and powerful. I think this enable very interesting workflows, like automatically displaying key metrics in an easy to consume Power BI dashboard.

I yet have to explore all the features, especially the libraries, but bimsync is now my top choice among the web-based BIM collaboration platforms, and I am eager to explore more workflows with it.