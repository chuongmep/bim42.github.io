---
id: 753
title: Parametric Bridge
date: 2015-01-10T18:13:24+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=753
permalink: /2015/01/parametric-bridge/
categories:
  - Grasshopper
image: /assets/2015/01/FinalModel.jpg
tags:
  - BIM Manager
  - Civil Engineering
  - Grasshopper
---
_Today, I introduce you Louis-Marie Borione, one of my colleague and friend, to talk about his work with Grasshopper for civil engineering._

Hi everyone, I am a BIM Manager in a large infrastructure engineering company in France, and I thank BIM42 to give me the opportunity the present you my work on parametric Bridge.

I recently worked on a preliminary design for a bridge in the Middle East. When starting looking at conceptual design drawings I came with the impression that we would have to make a lot of hypothesis.

![Bridge]({{ "/assets/2015/01/Bridge.jpg" | absolute_url }})

For example the height above ground at bridge ends is not dimensioned . The idea was to produce any kind of BIM model of this bridge therefore I first thought of using Rhinoceros and Grasshopper.

So I listed all of my hypothesis:

![GH]({{ "/assets/2015/01/GH.jpg" | absolute_url }})

And I started building the wireframe model:

![Rhino]({{ "/assets/2015/01/Rhino.jpg" | absolute_url }})

And the final model:

![FinalModel]({{ "/assets/2015/01/FinalModel.jpg" | absolute_url }})

Then I had to produce cross sections, longitudinal sections and plan views. I tried to do it within Rhinoceros but the result wasn’t good enough. Additionally some cross beam had a different shape, and using Grasshopper it is difficult to customize some elements.

My next idea was to be able to transfer this model to Revit. After a quick tour on Google, I found the grasshopper plugin Hummingbird. Using Hummingbird plugin for Grasshopper you export geometry from Grasshopper to an Excel Spreadsheet and using Hummingbird plugin for Revit you import that Excel Spreadsheet.

![BrideFinal]({{ "/assets/2015/01/BrideFinal.jpg" | absolute_url }})

At the end the process became quite complicated. When changing in input value in Grasshopper it took more 30 minutes to populate that changes to Revit.

I finally thought about using Dynamo to create directly a parametric model of the bridge within Revit. Unfortunately Dynamo is quite hard to use and I think it would make a great subject for a future post on BIM 42.

_Thank you so much for this content, and I must say I totally agree with you about Dynamo, I should already have started to work with it._